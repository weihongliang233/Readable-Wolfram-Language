# Readable-Wolfram-Language

Wolfram language(Mathematica) is a Lisp-like programming language. It's code is actually abstract syntax tree / S-expression.

Traditional Lisp grammar lacks readability, and there is a [Readable Lisp S-expressions Project ](https://readable.sourceforge.io/). Our readable-WL project implements similar   indention and newline based grammar.

Example:

```
g    
    a
        b+c
        (*comments*)
        d
            e


    a
        
        b[c,d,e]
        
        d
            e
```

Translate it into normal WL expression.

```mathematica
Transform[test]

(* g[a[b + c, d[e]], a[b[c, d, e], d[e]]] *)
```

Import the `Wheel.wl` file and you can use the translator.

```mathematica
<<"Wheel.wl";
test=
"
g    
    a
        b+c
        (*comments*)
        d
            e


    a
        
        b[c,d,e]
        
        d
            e
";

Transform[test]
(* g[a[b + c, d[e]], a[b[c, d, e], d[e]]] *)
```

