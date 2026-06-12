---
title: "New ATI issue"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by Coty on 2008-01-05
Ok, i think i have the strangest problem around:

I've managed to compile & install kernel 2.6.23.12 and to make those special fglrx packages for the kernel. I have installed them and flgrx doesn't make X11 stop. It seems everything is fine, even glxinfo displays stuff that made me think everything is ok. 

I've tried to run glxgears but the little windows stays black. The same happens when I tried to run a OpenGL screensaver - first time, it didn't run at all, second time X11 stopped...

Do you have any ideas what's wrong?:confused:

---

### Post by acoustibop on 2008-01-05
So what does fglrxinfo give, Coty, what card are you using, what driver are you trying to install, and how?

---

### Post by Coty on 2008-01-06
```
cotizo:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7059 Release
```

I am using a Radeon9550, identified as 9600. I installed the official driver (i think) from ati, the binary from their site produced some files with "8.433_1" in their name, so I think that's the version.

I  compiled kernel 2.6.23.12, installed it, followed the steps in one of the tutorials around here, wich said me to apt-get install the headers for this kernel, but i used the source itself instead... Everything went smoothly with the install and yesterday, after a reboot, it seemed to work ( all OpenGL screensavers were ok, glxgears went smooth... )

Now, when I've turned on the PC, same problem... I am going to inspect the xorg.conf, is there anything that could conflict there?

---

### Post by acoustibop on 2008-01-06
Looks like you have the 7.11 driver installed, Coty; the 7.12 driver is out now.

Looks from fglrxinfo that the driver is properly installed: check the Gutsy section of the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") and make sure you've done all the post installation checks and configuration properly.

FWIW this is the method I always use to install or update the fglrx driver.  Produces a good result pretty much all the time; other methods often seem a bit more hit-or-miss.

---

### Post by Coty on 2008-01-06
Well, i downloaded that binary from ati around 21 hours ago :) missed the new release by little...

Anyway, where is the flaw as long as it was ok once? Now, after a reboot, everything is OK again... It's a common thing, i think i started another topic a couple of months ago, where i said that i had fglrx working at every 2 boots :)... now it is working, but OGL is missing at every 2 boots... strange :(

PS: i know that tutorial, i've followed it every time i installed fglrx, including now.

---

### Post by Coty on 2008-01-06
I think this is another thing related to the driver : sometimes, when i scroll in konsole or yakuake, some gray stripes appear in my bottom-right corner. At a screenshot they don't appear and I can make them go away only by restarting X... what could be the problem?

---

