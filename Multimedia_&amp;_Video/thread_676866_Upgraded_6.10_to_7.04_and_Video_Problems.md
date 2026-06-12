---
title: "Upgraded 6.10 to 7.04 and Video Problems"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by JimmyME on 2008-01-24
After a year with Edgy I reluctantly did an online upgrade to 7.04 last night, now I have the household mad at me as my wife can't homeshool without Ubunutu.

Here is the message I get:
"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

My compuer is a year old and has a GeForce 7900GS card.

Would appreciate any assistance or a pointer to where there may be step by step instructions.

Thank you very much.

Jim in Maine

---

### Post by milton1 on 2008-01-24
try reconfiguring the xserver:

```

sudo dpkg-reconfigure -p high xserver-xorg

```

or, try upgrading to 7.10.

---

### Post by JimmyME on 2008-01-24
Milton,

Thanks for the quick reply.

Pardon my ignorance here, it's been a year since I've had to fart around with Linux and I've forgot a lot...

How do I get  into the linux command line to do this when I cannot boot into Ubuntu due to the error message I'm getting?

I'm in Win XP now as I have dual-boot.

Thanks much,

Jim

---

### Post by ThomasNovin on 2008-01-24
Press ctrl-alt-f1 from any graphical window or just alt-f1 from a console.

You might want to do a 'sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.080124' before reconfiguring X so you have a backup config saved.

---

### Post by milton1 on 2008-01-24
select the recovery mode option from grub. this will boot to a command line, without trying to load X. You will have root privelages here, so the sudo command may not be necessary.

---

