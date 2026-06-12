---
title: "having some issues with nvidia 8400gs"
date: 2010-02-27
forum: Multimedia Software
---

### Post by Greensystemsgo on 2010-02-27
just installed x32 9.10.

first time, i installed restricted drivers before update and it would freak out and go to a tty1 black login screen that would flicker.

second install i updated, then installed drivers. now it will run in safe graphics mode, but that does me no good, this is supposed to be a htpc :)

errors its giving me during boot are

(EE)NVIDIA(0): failed to inizalize the nvidia graphics device PCI:1:0:0
(EE)NVIDIA(0): please check your system kernal log for additional error
(EE)NVIDIA(0):messages and refer to chapter 8 common problems in the 
(EE)NVIDIA(0): readme for additional information
(EE)NVIDIA(0):failed to inizalize the nvidia graphics device!
(EE)Screen(s) found, but none have a usable configuration

then when i go to system, admin, nvidia x server settings i get this error

You do not appear to be using the nvidia x driver. please edit your x configuration file (just run nvidia-xconfig as root), and restart the x server.

running 'nvidia-xconfig' as root returned an error the first time, but not the second. still only booting in safe graphics mode :(

any ideas? i used to know of a program that would install the appropiatenvidia driver, had a purple icon or something but that was a while ago :)

also, screen is a 1360x768 hd tv, gpu is using dvi out, tv is using hdmi in, hdmi-dvi cable.

other system specs
GA P35 DS3L
e6300 1.87ghz conroe
2gb ram

---

### Post by solitaire on 2010-02-27
What version of the Nvidia drivers did you install? 185, 190 or 195?

The Best ones to try is 190 version.
195 are in Beta so might not work 100%

NVIDIA-Linux-x86-190.53-pkg1.run
[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)

---

### Post by gradinaruvasile on 2010-02-27
The 195.30 works perfectly. I use it on a nvidia 8200 (IGP), GF 210, Quadro NVS 135M and another computer that isnt mine but runs without problems with 7600 GS. All work perfectly well. This is the driver from the site BTW. The 210 and 8200 flies with 1080p movies (VDPAU).

I suggest install the 195.30 (i know there is a 195.36, didnt test it extensively though, but it seems to be working). It has VDPAU related fixes.

From the error messages, it seems the driver isnt installed correctly (if at all).

---

### Post by Greensystemsgo on 2010-02-27
ok so i downloaded those drivers, the .run file. now what. i found many guides on how to custom install drivers, however they are all different and am afraid to trial and error. that and gf wants to watch a movie. NOW. lol

---

### Post by Greensystemsgo on 2010-03-03
k i found a way FINALLY to kill x, and install 195 drivers!

CTRL+ALT+F1
user xxxx
pass xxxx
sudo service gdm stop
sudo sh nvidia.run (follow prompts to install)

and after reboot still in safe graphics mode. yet again have done NOTHING but reformat, update, and attempt to install nvidia gpu. what is going on why all the troubles?

bfg 8400gs

---

### Post by Greensystemsgo on 2010-03-03
175 drivers post just fine. However XBMC says my card is not supported, yet xbmc says any 7k+ cards. soooo ARGH. time for a windows media center style program :/

---

### Post by ianmidd on 2010-04-20
Do you happen to have a TV-Tuner card as well?

I was getting the exact same message.  I had to set vmalloc=256 in my boot options with a Hauppauge HVR-1600 card. 

I can dig up the post I found if you need it.  It was on these forums.

---

