---
title: "Radeon proprietary Drivers"
date: 2013-05-17
forum: Multimedia Software
---

### Post by AngerIssues42 on 2013-05-17
I know this comes up fairly regularly, and I have trolled through 20+ threads but none of them seem to help me.

So I have a Toshiba L850D with AMD A10 cpu/gpu with an external HD77**M in crossfire. The problem I am encountering seems to be common, yet different everytime.

I have installed the proprietary drivers (post release drivers) from the Ubuntu "Additional Drivers" program, yet it says they are "This driver is activated but not in use".

Now I got the drivers from AMD website to work on Debian 7 which I have removed due to being very immature at the moment and packages seem to be always broken for me so I am on Ubuntu now, can't remember the version but the latest as of 16-May-2013.

The Realtek drivers I have installed are showing in the additional drivers program, but are showing activated and in use.

Are my Radeon drivers actually in use but the program is trying to troll me?

Now I am fairly new to Linux, so please bare with me, but if you give a code to throw into term I can do it and sometimes be able to understand what the hell is going on. But don't expect me to be able to suggest and try things myself =S (sorry).

Chris.

---

### Post by deadflowr on 2013-05-17
This should give you all you need to know:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But typically though, all you need to do after installing the drivers is run

```
[FONT=UbuntuMono, courier, monospace][COLOR=#333333]sudo amdconfig --initial[/COLOR][/FONT]
```

This generates an xorg.conf file that the system reads.

---

### Post by AngerIssues42 on 2013-05-18
grrrr... still no go... and now my onboard keyboard and touchpad have stopped working, external kb/m are fine.

fglrxinfo is stating the drivers are working though (I think) here is the output:

chris@L850D:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7500/7600 Series
OpenGL version string: 4.2.12172 Compatibility Profile Context 9.00.11

any idea? on either... the additional drivers program problem still exists too, should I just try and install the drivers from the amd website? that worked on debian...

sorry about the late reply, Someone tried to kill me yesterday with bad chicken...

---

### Post by QIII on 2013-05-19
To get both graphics controllers working, both have to be initialized.  You probably only have on initialized.

Also, the -updates versions seem to be more problematic than useful.

Clean up all the drivers:

```
sudo apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```

Rename your xorg.conf:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf
```

Reboot to get back in with the default Radeon driver.

Now install fglrx

```
sudo apt-get install fglrx fglrx-amdcccle
```

Now initialize all of your adapters:

```
sudo amdconfig --adapter=all --initial
```

Reboot.

---

### Post by AngerIssues42 on 2013-05-19
just want to confirm your rename of xorg.conf before I continue...

from your code i'm renaming xorg.conf to xorg.conf (From what i understand)... is this right??? or did you mean xorg.conf.BAK??

---

### Post by deadflowr on 2013-05-19
I would assume QIII meant what you think should be done. Typo, probably..
Renaming it the same name seems redundant or something.

---

### Post by QIII on 2013-05-20
My apologies!

Yes, .bak

---

