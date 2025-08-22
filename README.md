1] Fraction:








public class Fraction {
    private int num, denom;

    // Default constructor
    public Fraction() {
        this(0, 1);
    }

    // Integer constructor
    public Fraction(int n) {
        this(n, 1);
    }

    // Two-parameter constructor
    public Fraction(int p, int q) {
        if (q == 0) throw new IllegalArgumentException("Denominator cannot be zero");
        num = p;
        denom = q;
        reduce();
    }

    // Copy constructor
    public Fraction(Fraction other) {
        this(other.num, other.denom);
    }

    // Reduce fraction to simplest form
    private void reduce() {
        int g = gcd(Math.abs(num), Math.abs(denom));
        num /= g;
        denom /= g;
        if (denom < 0) {  // keep denominator positive
            num = -num;
            denom = -denom;
        }
    }

    // Helper gcd function
    private int gcd(int a, int b) {
        return b == 0 ? a : gcd(b, a % b);
    }

    // Invert a fraction
    public Fraction invert(Fraction a) {
        return new Fraction(a.denom, a.num);
    }

    // Add two fractions
    public Fraction add(Fraction a, Fraction b) {
        return new Fraction(a.num * b.denom + b.num * a.denom, a.denom * b.denom);
    }

    // Add fraction and integer
    public Fraction add(Fraction a, int n) {
        return new Fraction(a.num + n * a.denom, a.denom);
    }

    @Override
    public String toString() {
        return num + "/" + denom;
    }
}
