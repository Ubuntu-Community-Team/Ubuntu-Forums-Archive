---
title: "Calculator with no decimal point?"
date: 2010-09-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by teachop on 2010-09-18
Is it really true that the Calculator in Mode == Programming no longer has a decimal point?  We have to switch out of Programming mode to do a simple calculation?  Is there an option some place I am missing?

---

### Post by panaut0lordv on 2010-09-18
Can't you just type it on your keyboard? It's faster than clicking buttons with mouse xD

---

### Post by MacUntu on 2010-09-18
> **teachop said:**
> Is it really true that the Calculator in Mode == Programming no longer has a decimal point?
No.

---

### Post by QwUo173Hy on 2010-09-18
> **teachop said:**
> Is it really true that the Calculator in Mode == Programming no longer has a decimal point?  We have to switch out of Programming mode to do a simple calculation?  Is there an option some place I am missing?Just checked there and I don't see a decimal point.

---

### Post by MacUntu on 2010-09-18
Oh, you mean as button. Yes, no button there, but who uses those buttons to enter things? :D

---

### Post by ronacc on 2010-09-18
someone without a number pad .

---

### Post by teachop on 2010-09-18
I do understand, yes, that the period (and 0,1,2 etc) on the keyboard will work.

---

### Post by Mr. Picklesworth on 2010-09-18
Of course!
A real programmer works in either binary, octal or hex *all the time* and refuses to damage his mind with silly concepts like decimal numbers.

---

### Post by ranch hand on 2010-09-18
> **Mr. Picklesworth said:**
> Of course!
A real programmer works in either binary, octal or hex *all the time* and refuses to damage his mind with silly concepts like decimal numbers.
I am beginning to understand the rules here better.

It is wrong for most of us to criticise, but fine for "members" to imply that users are not "real" programmers.

Kind of like Mr Shuttlesworth saying that if you really care for F/OSS you just have to be with Ubuntu.

Well this sucks the big one.

Good by is to good a word so I'll just say <snip>.

---

### Post by cariboo on 2010-09-18
I do believe Mr. Picklesworth was joking.

---

### Post by Longinus00 on 2010-09-18
> **Mr. Picklesworth said:**
> Of course!
A real programmer works in either binary, octal or hex *all the time* and refuses to damage his mind with silly concepts like decimal numbers.

I know you are jesting but I'd like to point out that it's possible to represent fractions in whatever base you choose, in fact calculator can handle them.

---

### Post by Mr. Picklesworth on 2010-09-18
> **Longinus00 said:**
> I know you are jesting but I'd like to point out that it's possible to represent fractions in whatever base you choose, in fact calculator can handle them.
It's always baffled me how that works, to be honest. Now you've reminded me, I'm going to stare at this for a while and see if I can get a proper feel for it&#8230;
(I see how they're converted back and forth, but I'm obviously not grasping something because I keep thinking it feels wrong somehow)

> **ranch hand said:**
> It is wrong for most of us to criticise, but fine for "members" to imply that users are not "real" programmers.Some of us just tend to be very set in our ways. It's the danger of fussing over a single distro for so long ;)

Really, though: being a big fan of touch screens, this affects me as well. I filed a bug report upstream for you, teachop. You can add yourself to the CC list (at the bottom) if you want to see where it goes.

[SIZE="3"][https://bugzilla.gnome.org/show_bug.cgi?id=630021](https://bugzilla.gnome.org/show_bug.cgi?id=630021)[/SIZE]

---

### Post by Longinus00 on 2010-09-18
> **Mr. Picklesworth said:**
> It's always baffled me how that works, to be honest. Now you've reminded me, I'm going to stare at this for a while and see if I can get a proper feel for it&#8230;
(I see how they're converted back and forth, but I'm obviously not grasping something because I keep thinking it feels wrong somehow)

It's simple really, let me give you an example.

```

½ is ...
decimal - binary - octal - hexadecimal
0.5       0.1      0.4     0.8

5 is ½ of 10 in decimal
1 is ½ of 10 in binary (1/2 in decimal)
4 is ½ of 10 in octal (4/8 in decimal)
8 is ½ of 10 in hexadecimal (8/16 in decimal)


¾ is ...
decimal - binary - octal - hexadecimal
0.75      0.11     0.6     0.C

75 is ¾ of 100 in decimal (7.5 out of 10)
11 is ¾ of 100 in binary (1.1 out of 10) (3/4 in decimal)
6  is ¾ of 10 in octal (6/8 in decimal)
C  is ¾ of 10 in hexadecimal (12/16 in decimal)

1/16 is ...
decimal - binary - octal - hexadecimal
0.0625    0.0001   0.04    0.1
etc...

```

One obvious difference compared to base 10 is that fractions with prime factor of 5 in the denominator do not have finite representations (1/10 in binary is 0.000110011...).

---

### Post by ronacc on 2010-09-18
a decimal is just the ratio of the number to the base , for example in decimal ( base 10) .6 is 6/10 .

---

### Post by Mr. Picklesworth on 2010-09-18
> **Longinus00 said:**
> It's simple really, let me give you an example.

```

½ is ...
decimal - binary - octal - hexadecimal
0.5       0.1      0.4     0.8

5 is ½ of 10 in decimal
1 is ½ of 10 in binary (1/2 in decimal)
4 is ½ of 10 in octal (4/8 in decimal)
8 is ½ of 10 in hexadecimal (8/16 in decimal)


¾ is ...
decimal - binary - octal - hexadecimal
0.75      0.11     0.6     0.C

75 is ¾ of 100 in decimal (7.5 out of 10)
11 is ¾ of 100 in binary (1.1 out of 10) (3/4 in decimal)
6  is ¾ of 10 in octal (6/8 in decimal)
C  is ¾ of 10 in hexadecimal (12/16 in decimal)

1/16 is ...
decimal - binary - octal - hexadecimal
0.0625    0.0001   0.04    0.1
etc...

```

One obvious difference compared to base 10 is that fractions with prime factor of 5 in the denominator do not have finite representations (1/10 in binary is 0.000110011...).

Wow, nice!
That does make things clearer for me. Thank you :)

---

