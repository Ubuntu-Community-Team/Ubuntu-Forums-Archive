---
title: "GDM or X Restarts after seconds of being ready"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by Boynas on 2006-08-04
Everything was working perfectly until i did a couple of Eye candy changes (No GXL or anything fancy).
I just add a couple of gdesklets, remove one of the toolbars (the top one) and put almost everything in a single one, add some transparency to the bar, etc...

Now when i restart (or turn on) the system sometimes the X (or GDM) restarts and asks me to log back in... sometimes i have to repeat the login screen for 3 times to get a successuful login and get the Graphic envirioment stay.
This is the worst of all, sometimes it just comes all the way up the first time... It is killing me, impossible to trouble shooting, tried "ATI" driver, "Radeon" driver, even install "Fglxr" (or however it spels)... I thought about some module in the task bar crashing so i disable amost all of them (you know, power management, network module, etc).
I took gdesklets out from Startup applications in the sessions menu...

Any Ideas... this is a Laptop... is a Dell Inspiron 600m it has an ATI Radeon Mobility 9000.. which i think it translate to some kind of Ati R250...

Please help.. any advice will be highly appretiated.

---

### Post by Boynas on 2006-08-08
I can't believe this is so uncommon...
For real?, nobody had had this problem?

---

### Post by lmzmendes on 2006-08-09
Yep, I have it. 

Didn't do anything fancy either. It just keeps looping on my login screen.

Have you had any luck?

Lucas

---

### Post by tseliot on 2006-08-09
Try this and tell me what happens:

Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
apt-get install kdm
```

at a certain point it will ask you to select between "kdm" and "gdm".

Select "kdm"

then reboot:
```
reboot

```

Boot as usual and see if anything changes

---

