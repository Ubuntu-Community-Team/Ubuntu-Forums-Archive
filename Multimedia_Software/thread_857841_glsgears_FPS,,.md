---
title: "glsgears FPS,,"
date: 2008-07-12
forum: Multimedia Software
---

### Post by rk970 on 2008-07-12
I got my Nvidia card working and just did glxgears.  Is 3792 fps a good rate? 
The card comes up with lspci
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)
I just want to be sure its working at its optimum
rk

---

### Post by Melcar on 2008-07-13
glxgears is not a benchmark.  It's more of a test.  If you really want to test your card, use [PTS]("http://www.phoronix-test-suite.com/").

---

### Post by Vadi on 2008-07-13
Yeah it's not bad, but download and install the phoronix test suite (link above), and then run this command in the terminal: 

> phoronix-test-suite benchmark ravenmaster-31540-20265-1617

This will compare your machine against another test someone did on an 7600gt. If your results are more or less equal, you're good!

---

