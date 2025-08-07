# 🔢 Logarithmic Toolkit

This is a toolkit for simplifying the use of logarithmic expressions with arbitrary bases.

In Java, there is no built-in method to compute the logarithm of a number with a specific base directly.  
Instead, one typically uses: `double log = Math.log(a) / Math.log(b)`, which can be verbose and repetitive when used frequently.

This utility provides convenient methods to perform such calculations more cleanly and efficiently.
That is why I made this extension. 


It enables logarithmic computations involving:
- Arbitrary bases
- Powered values and bases
- Quotient-based arguments and bases

---
## ⚠️
 The name of the class to use is `Logarithm` so it is `Logarithm.logInBase(value, base)` etc.

---
## 📦 Package Overview

This utility is structured as a non-instantiable class exposing only `static` methods.

⚠️ All inputs are strictly validated for mathematical correctness.  
Invalid arguments specific to these methods will result in an `IllegalArgumentException`, 
while standard `Math.log(...)` domain errors will throw the corresponding runtime exceptions.

All calculations are based on `Math.log(...)` using double-precision floating-point (IEEE 754).
## ✨ Features

- ✅ `logInBase(value, base)`
- ✅ `logWithPoweredValue(value, base, power)`
- ✅ `logWithPoweredBase(value, base, power)`
- ✅ `logOfQuotient(numerator, denominator, base)`
- ✅ `logWithBaseQuotient(value, baseNumerator, baseDenominator)`
- ✅ `logOfQuotientAndBaseQuotient(valueNum, valueDen, baseNum, baseDen)`


## 🧠 Design Rationale

- The presence of the basic `logInBase(value, base)` method is due to its absence in java. 

- `logWithPoweredValue(value, power, base)` may seem being unnecessary; however, after computing and analyzing simulation 
  of a million operations between using that method based on the simplification of the logarithm formula with an exponent
  is 40 to 120 ms quicker than performing `Math.log(Math.pow(value, power))/Math.log(base)`. Although the performance gain may seem minor, it can be relevant in simulation contexts where such operations are repeated millions of times.  
  This method also improves readability by simplifying the expression syntax.

- For the `logOfQuotient(numerator, denominator, base)`, `logWithBaseQuotient(value, baseNumerator, baseDenominator)` and
  `logOfQuotientAndBaseQuotient(valueNum, valueDen, baseNum, baseDen)` methods, it appeared to me that it will be easier 
  and quicker to write an expression with those methods instead of casting each time doubles on the fractions to have the 
  best approach value or to remember to put a '.0' after the numbers to make them doubles. 

## 🧮 Numerical Precision Notes

Results depend on `Math.log(...)` and are subject to:

- Rounding errors
- Precision loss for small or very large values
- Instability near base = 1

For critical scientific computation, consider arbitrary-precision math libraries.

## 🛠 Implementation

The core method:

```java
public static double logInBase(double value, double base){
    checkArgument(base > 0, "base must be > 0: " + base);
    checkArgument(base != 1, "base must not be equal to 1");
    checkArgument(value > 0, "value must be > 0: " + value);
    return Math.log(value) / Math.log(base);
}

```

## 🦉 Author 𓂀

**owl**  
🔗 [GitHub – owl](https://github.com/owl-Holmes)

---

## 📄 License

Distributed under the MIT License.  
For more details, see the LICENSE file.
