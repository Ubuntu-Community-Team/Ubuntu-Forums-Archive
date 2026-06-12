---
title: "Black screen on booting"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by Kimbie on 2007-08-14
Right got Ubuntu reinstalled and grub working.  However when i run the normal mode I just get a black screen with the hdd doing stuff and the desktop never pops up.  However if I use recovering mode then run StartX i can get to the desktop.

I have used Envy and the drivers are all installed and nvidia settings program works and set the display up and saved them to the X config.  However it does not work

Any ideas?

Kimbie

---

### Post by gumbald on 2007-08-19
Could you give us more details of your hardware and paste in a copy of your xorg.conf please? :)

---

### Post by Kimbie on 2007-08-19
Intel E6400, 2Gb DDR, BFG 8800GTS 640Mb, Gigabyte DS3P

Will post the config a bit later

---

### Post by pkarlos_76 on 2007-08-24
A solution I found was the system was showing a fake monitor in the Xorg.0.log, so I switched my DVI cable from the 2nd DVI port to the 1st DVI port on the video card and I got my desktop back, the 2nd DVI port was working find under vesa drivers, but doesn't seem to work under nvidia drivers for me. It is possible to use override statements too,but changing connector is more easy. This might help!

---

### Post by podstep on 2007-08-28
I've got the same problem. My machine is AMD Athlon 64bit, nvidia nForce4, 1.5GB ram and radeon x700. When I'm choosing in grub my ubuntu I have a black splash, but in recovery mode averything is ok. please help me.

---

### Post by Marat Galiev on 2007-08-28
hmmm,
for nvidia graphic card try this:
1)Install packages xserver-xorg-dev,pkg-config,libc6-dev.
You an find them at packages.ubuntu.com.
2)Press ctrl+alt+F2.
3)sudo nano /etc/init.d gdm stop
4)cd /there/your/driver/location
5)sudo sh NVIDIA-100.14...-xxx.run --ui=none
(without GUI menu).
To the question with nvidia-xconfig answer "Yes".
6)sudo nano /etc/default/linux-restricted-modules-common
Edit line
DISABLED_MODULES="nv nvidia_new"
7)sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia.ko /lib/modules/2.6.20-15-generic/volatile/
8)sudo modprobe nvidia
9)/sbin/ldconfig
10)/sbin/depmod -aq
11)reboot
12)step 7
13)cd /lib/modules/2.6.20-15-generic/volatile/
13)sudo insmod ./nvidia,ko
14)sudo modprobe nvidia
15)step 9
16)step 10
17)sudo /etc/init.d/gdm start
18)reboot
19)cd /lib/modules/2.6.20-15-generic/kernel/drivers/video/
20)sudo cp nvidia.ko nvidia_new.ko
21)sudo insmod ./nvidia.ko
22)step 9
23)step 10
24)ctrl+alt+F7
25)sudo nvidia-xconfig
26)rebootFor x700 card...hmmm,when you see black screen,press ctrl+alt+F2,and edit you /etc/X11/xorg.conf
find section
Driver "ati"(or Driver "xxxx")
and edit it to
Driver "vesa".
Then restart gdm
with sudo /etc/init.d/gdm restart
then install ati official linux driver.

---

### Post by Kimbie on 2007-08-28
This problem is NOT to do with X.

It is a problem with the splash screen used by Casper.  If you edit your grub menu and remove the "quiet splash" from the end of the line this should fix the problem with it going to a black screen.

You can test this from the grub menu, highlight your ubuntu install and press E to edit and edit the long line and remove the quiet splash then press b to boot if you did it right it will load fine, however you will get the ugly boot screen with all the text flying past rather than the sex boot screen.

Oh well

Kimbie

---

