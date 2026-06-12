---
title: "NVIDIA, DVI, 'shimmering' lines"
date: 2005-11-27
forum: Multimedia &amp; Video
---

### Post by Bil-E-daKid on 2005-11-27
Hey guys,

I just upgraded my old 32Mb Geforce2 MX 200 to a 128Mb Geforce 5200.

Since the new card has a DVI interface on it, I decided to use that to connect to my Hitachi 17" flat panel instead of the old VGA connector that I used to use.

I finding now that, in Breezy, there are sometimes bits of the screen that 'shimmer' or 'flicker' - kind of like the pixels are changing colour. Sometimes a  whole line of them across the screen will do this - and it seems to be more noticable on the Ubuntu login screen (standard Ubuntu GDM theme) and after the monitor has gone into power save mode for a little while.

It doesn't seem to do this in XP at all and it seems to go away once logged into to Breezy, if I change the refresh rate. But it always appears (in varying degrees) at the login screen.

I've tried adding various Nvidia driver options to the xorg.conf but so far have not been successful in getting rid of this odd artefacts completely all the time.

I've also had a look around and can't seem to find anyone else having come across this sort of problem before - though I could be searching for the wrong description of the problem!  :-)

Anyone have any ideas?

thanks
Bil-E-daKid

---

### Post by Bil-E-daKid on 2005-11-28
This morning, I dropped back to using the 'nv' driver and the problem has gone away. Now I'm doing some googling for 'linux nvidia dvi strange'.

Hopefully something useful will show up!  :-)

---

### Post by Bil-E-daKid on 2005-12-01
Poos and wees - the nv driver started exhibiting the same problems a day later.

Haven't found anything useful to help either - and I seem to be talking to myself here....  ;-)

I've gone back to using the standard VGA connector for now. Maybe it's the DVI side of my Hitachi flat panel that is causing the problem? I think it's out of warranty now anyway. Oh well.

---

### Post by bihe on 2006-02-20
exactly same problem; tried with breezy - and yesterday dapper flight 4
no problem at all in SuSE 10.0 or WinXP
hast to be a strange kernel - xorg - nvidia combination

edit: filed a bug
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/32191](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/32191)

---

### Post by Bil-E-daKid on 2006-03-30
Yay - someone else has it too!  I just tried a couple of days ago with fully patched Flight 5 and still have the same probs.

I'll update that bug report.

---

### Post by Vulpus on 2006-03-31
This may be something different but I have had a similar problem with TFT screens.  The problem has been that they are not working at optimum resolution.  If you change to a higher or lower (in my case higher) resolution the problem dissapears.  

In the case of my monitor, when I ran it in XP the fonts were fuzzy.  When I ran it in Ubuntu I got shimmering lines.  In both cases increasing the screen resolution solved the problem.

---

### Post by Bil-E-daKid on 2007-04-16
A wee update here.

Just recently tried my DVI cable after upgrading to Feisty.  This problem still exists even now - boy am I glad I don't have a DVI only graphics card!

---

