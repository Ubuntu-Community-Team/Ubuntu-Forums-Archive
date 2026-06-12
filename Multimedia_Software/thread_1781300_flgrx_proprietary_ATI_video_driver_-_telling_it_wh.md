---
title: "flgrx proprietary ATI video driver - telling it which monitor I want to use"
date: 2011-06-13
forum: Multimedia Software
---

### Post by datababy on 2011-06-13
Hi,

I have a fixed frequency monitor which normally needs special modelines  in xorg.conf. Ive just started using the flgrx video driver and am  having trouble assigning my monitor subsection to the CRT. 

My Xorg.0.log states

flgrx(0): Output DFP1 using monitor section big-old-crt

[...]

flgrx(0): Output CRT1 has no monitor section


X then goes on to attempt to guess the correct modelines for my monitor. Needless to say, they are wrong.

How do I specify that my "Monitor" section is supposed to be assigned to the output CRT1?

---

