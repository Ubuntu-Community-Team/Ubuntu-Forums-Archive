---
title: "Improve Intel GM965, GMA X3100 performance?"
date: 2010-04-02
forum: Multimedia Software
---

### Post by quadomatic on 2010-04-02
I'm using Ubuntu 9.10 with the default installed drivers for my Intel GM965 GMA X3100 (xserver-xorg-video-intel).

Now that I've finally figured out how to get 3D applications working in WINE properly, does anyone have advice on how to improve performance? Running Half-Life in D3D mode was choppy. I was miraculously able to get Braid running as well, and while certainly playable, I felt it could've been better.

Any advice?

---

### Post by glaze on 2010-04-02
I haven't tried it yet, but many people say that 3D is faster in Ubuntu 10.04 due to the updated Mesa OpenGL driver.

---

### Post by quadomatic on 2010-04-02
> **glaze said:**
> I haven't tried it yet, but many people say that 3D is faster in Ubuntu 10.04 due to the updated Mesa OpenGL driver.

Is there any way to install it in 9.10?

Update: upgrading to Ubuntu 10.04 beta, it's less than a month away anyways...I would move back to Arch but I don't have the time

Update 2: uhh...is the intel driver version in 10.04 2.1.1? Intel's driver goes to 2.11...any way to upgrade?

Update 3: installed ubuntu 10.04, seems to run better overall. Ran some benchmarks as well. Then enabled xorg-edgers repo and install newer intel driver 2.11 and mesa 7.9. Very marginal performance increase:

[http://global.phoronix-test-suite.com/index.php?k=profile&u=aneesh-15945-20119-20369](http://global.phoronix-test-suite.com/index.php?k=profile&u=aneesh-15945-20119-20369)

default [http://global.phoronix-test-suite.com/index.php?k=profile&u=aneesh-17893-340-18912](http://global.phoronix-test-suite.com/index.php?k=profile&u=aneesh-17893-340-18912)
new [http://global.phoronix-test-suite.com/index.php?k=profile&u=aneesh-29566-6954-23805](http://global.phoronix-test-suite.com/index.php?k=profile&u=aneesh-29566-6954-23805)

---

### Post by HeadHunter00 on 2010-11-06
d3d will be slower than opengl on linux no matter what. did you try running the application using "wine [path to .exe] -opengl"? putting the opengl flag at the end should increase the performance. i dont know by how much, but it should. also, did you turn off compiz? type in "metacity --replace" after pressing alt+f2. that will increase the 3d performance by about 75%(not bang-on precise)

---

