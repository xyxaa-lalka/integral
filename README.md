# Numerical Integration

A console application for numerical integration of a function on a given interval using various Riemann sum methods, the trapezoidal rule, and Simpson's rule. The program supports both an interactive ncurses-based GUI and a command-line mode.

## Features

- Numerical integration using:
  - Left Riemann sum (LR)
  - Right Riemann sum (RR)
  - Middle Riemann sum (MR)
  - Trapezoidal rule (TR)
  - Simpson's rule (SI)
- Automatic iteration refinement until a specified precision is reached
- Interactive GUI mode (ncurses)
- Command-line mode with formatted output
- Expression parsing via tinyexpr (supports standard math functions)

## Requirements

- C++ compiler (g++ or clang++)
- ncurses library
- tinyexpr (included in the build)

## Build

```
make
```

Or compile manually:

```
g++ -o numerical_integration *.cpp -lncurses -lm
```

## Usage

### GUI mode

```
./numerical_integration -g
```

or

```
./numerical_integration --gui
```

The program will prompt you to enter:
- The integrand expression (e.g. `x*x + sin(x)`)
- The interval `[a : b]`
- The integration method (LR, RR, MR, TR, SI)
- The desired precision

### Command-line mode

```
./numerical_integration f=<expression> a=<lower> b=<upper> m=<method> e=<precision>
```

Parameters:

| Key | Description                        | Example        |
|-----|------------------------------------|----------------|
| f   | Integrand expression               | `f=x*x+1`      |
| a   | Lower bound                        | `a=0`          |
| b   | Upper bound                        | `b=3.14`       |
| m   | Method (LR, RR, MR, TR, SI)        | `m=SI`         |
| e   | Precision (target error)           | `e=0.0001`     |

Example:

```
./numerical_integration f=sin(x) a=0 b=3.14159 m=SI e=0.00001
```

### Flags

- `-g`, `--gui` — launch interactive GUI mode
- `-d`, `--debug` — print the number of iterations used

## Notes

- If no method is specified, Simpson's rule is used by default.
- If the given precision is out of range (less than 0 or greater than 1), it is reset to 0.001.
- The interval is automatically swapped if the lower bound is greater than the upper bound.
