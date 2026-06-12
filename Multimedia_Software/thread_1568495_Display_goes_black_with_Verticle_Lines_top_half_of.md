---
title: "Display goes black with Verticle Lines top half of screen"
date: 2010-09-05
forum: Multimedia Software
---

### Post by pricetech on 2010-09-05
I've searched the forums and found the same problem, but the solutions don't work for me since I don't seem to have an "xorg.conf" file.

Gateway SB400a computer with Edubuntu Lucid installed.  The problem first cropped up when I installed the Edubuntu packages on Ubuntu.  I did a fresh install with Edubuntu and the problem persists.  I don't want to go back to Ubuntu since this computer is for my Grandkids and I want to the Edubuntu stuff for them.

I don't have the specs handy, but I can get them.  I'll just need some help remembering what I have to do to get them. (it happens when you get old)

EDIT: From my xorg.0.log: (--) PCI:*(0:0:2:0) 8086:2562:107b:4000 Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 3, Mem @ 0xf0000000/134217728, 0xffa80000/524288


Any help appreciated.

---

### Post by pricetech on 2010-09-07
Bump

---

### Post by pricetech on 2010-09-08
Bump and more information.

Ctrl Alt F1 doesn't help.  I did not try F2 and beyond.

Connecting remotely with NX Client works just fine.  Putty (I'm on a windows box) also connects, which is how I did a proper reboot.

It comes back up okay.  When it will freak out again is anybody's guess.

---

### Post by pricetech on 2010-09-14
Bump again in hopes I can get some input.

---

### Post by pricetech on 2010-09-30
bump and a little more information:

Enabled Ctrl Alt Backspace.  Doesn't help.  I still have to shutdown.

---

### Post by pricetech on 2010-12-06
Update:

Grandkids weren't using the Edubuntu stuff anyway so I wiped and went back to Ubuntu.  Problem still occurs.

Something I've tried: It never malfunctions when I am logged in so I created another account with administrative privileges which the kids are to use to see if it malfunctions for them.  If not, then the user account has to have access to something.  I'll sort out what that something is if this works.

Meanwhile, if anybody  has any ideas, please pass them along.

---

### Post by jimmybarcelona on 2010-12-12
Any luck with this? I have this same problem with Ubuntu 10.04 on 3 different desktops. I need to get this fixed. I can find no real pattern as to when it happens. I know that xubuntu 10.04 did it as well.

---

### Post by pricetech on 2010-12-14
No luck at all.  Adding the account made no difference.

I finally put a different video card in it. (a scrounged nvidia) So far it hasn't acted up.

My searches for solutions gave me lots of information, but nothing that applied in my case.  Best I could tell it's because it referred to earlier releases.

---

### Post by jimmybarcelona on 2010-12-16
Have you tried upgrading to 10.10? I did that, and it's too soon to tell, but I've noticed that I haven't had this problem on the few computers I have running 10.10. So I upgraded the 10.04 machines, and so far I haven't had this problem since. Internet research has made me suspect heat issues that Maverick seems to do better with.

---

### Post by pricetech on 2010-12-16
I don't really want to upgrade though.  I like sticking with LTS releases.

Not a mission critical machine though, so I might just do that one day.

---

