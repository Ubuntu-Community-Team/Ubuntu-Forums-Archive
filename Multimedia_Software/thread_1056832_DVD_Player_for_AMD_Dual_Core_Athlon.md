---
title: "DVD Player for AMD Dual Core Athlon"
date: 2009-02-01
forum: Multimedia Software
---

### Post by bumper@comcast.net on 2009-02-01
I just installed 8.10 64 bitlast week on a computer that I built.
ASUS motherboard, 4GB Ram, 500 GB dedicated MS XP, 250 GB dedcated Ubuntu. Uses AMD Athlon Dual Core X2 6000 Mhz CPU.

Cannnot get any DVD player to work.:( Any ideas?

Thanks :)

---

### Post by markbuntu on 2009-02-01
What exactly are you trying to do. Pretty much every EIDE or SATA dvd player/burner should work right out of the box. The only problems I know of are with blank memorex dvd disks and some LG usb dvd players.

---

### Post by bumper@comcast.net on 2009-02-07
I am trying to play a DVD Movie. The Ubuntu Movie player gives an error. I ave a Sata Drive. I installed Ubuntu from it, so the problem is in playing a DVD Movie.
I have the 64 bit version of Ubuntu, and the AMD x 64 bit (dual Core) Athlon - I think the issue is with suitable drivers here.

---

### Post by markbuntu on 2009-02-07
Does the disk show up on your desktop?

---

### Post by bumper@comcast.net on 2009-02-08
:DYes I fixed it via VRG. See nstructions which worked:
[http://www.stchman.com/](http://www.stchman.com/) Click instal medibuntu repositor with dvd css decryption and dvd ripping.You can copy and paste the commands into a terminal.

click applications> accessories> terminal.

Copy and paste a command, hit enter. Enter password...you won't see the password as you type, just type it and hit enter.:D

---

### Post by Yannick Le Saint kyncani on 2009-02-08
> **bumper@comcast.net said:**
> I am trying to play a DVD Movie.

If you can read data dvds but not movie dvds, then you may be missing libdvdcss2, which you can install with medibuntu (google medibuntu libdvdcss2).

---

