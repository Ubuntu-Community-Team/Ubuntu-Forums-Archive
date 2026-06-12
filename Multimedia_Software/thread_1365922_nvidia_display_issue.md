---
title: "nvidia display issue"
date: 2009-12-27
forum: Multimedia Software
---

### Post by chrisch on 2009-12-27
I am sure this question has been answered a million times, but here goes.

I just installed 9.10, and the machine has an nVidia FX 5200 card in it.  I installed the proprietary drivers, and after reboot I can't get better than a 640x480 display.  On a 17 inch monitor I should get at least 800x600.  I have tried monkeying with the Xorg.conf, but buggered up the server.

Can anyone help?

---

### Post by gordintoronto on 2009-12-27
Exactly what monitor is it?  LCD or CRT?

When you run Preferences/Display does it throw you to NVIDIA X Server Settings?  Then can you go to X Server Display Configuration, with a Resolution drop-down?  There's also a button labelled "Detect Displays," which has always detected my display.

---

### Post by chrisch on 2009-12-27
It's a crt.  And yes it does send me to the nvidia settings and the drop down will only let me go to 640x480.  And the detect display doesn't do anything.

---

### Post by lindsay7 on 2009-12-28
I had the same problem when the latest Kernal update came in 2.6.31.17.  This old Nvidia 5200 will not handle the new diver 190 only the 173. I bought a cheap new graphics card with Nvidia Geforce 6200 from Tiger for $25 and that solved the problem.  If you keep your old 5200 it will never handle the new Kernal upgrades going on into the future.

---

### Post by chrisch on 2009-12-28
Thanks, I will give that a try.

---

### Post by VastOne on 2009-12-28
> **lindsay7 said:**
> I had the same problem when the latest Kernal update came in 2.6.31.17.  This old Nvidia 5200 will not handle the new diver 190 only the 173. I bought a cheap new graphics card with Nvidia Geforce 6200 from Tiger for $25 and that solved the problem.  If you keep your old 5200 it will never handle the new Kernal upgrades going on into the future.

+1

Great answer

---

