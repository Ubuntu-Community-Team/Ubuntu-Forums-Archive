---
title: "Installing nvidia drivers reboots to black screen in 9.04"
date: 2009-05-31
forum: Multimedia Software
---

### Post by tactx on 2009-05-31
I could really use some help with this if anyone knows how to. I've been bashing my head against a wall for two days now.

My computer: Nvidia nForce 780i mainboard
Intel Core2Duo processor
2x Nvidia Geforce 8800 GTS graphics cards
3x Optiquest monitors

Problem: I have had this rig functioning without issue in 8.04,but since
I just installed 9.04 no matter what method I use to intall the nvidia drivers, when I reboot after the logo loads commands scroll down the page and after it says "checking batteries i get a blinking cursor and the a black screen.


it doesn't this weather I use 32bit or 64 bit Ubuntu 9.04, or if I load the drivers using the restricted hardware drivers app or the envyng script the result is the same.

Again, any help on this will be much appreciated.


Well...I've tried just about everything I have found in posts and on the Nvidia site....In everycase the dirvers load...then I reboot and its hang time again.
...yes I have stopped x-server and installed from prompt...
this is getting rediculous. Time to reinstall 9.04 and try again?...not till I get some direction. :(    see my last post.

---

### Post by tactx on 2009-06-01
Has anyone had this same problem? Can anyone help me or send me in the right direction?

---

### Post by Arup on 2009-06-01
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Follow the instructions given here.

---

### Post by tactx on 2009-06-01
Thank you!...I followed the first post on that page..but didnt see the following posts.. Will try again and check back..
:)

---

### Post by tactx on 2009-06-01
No Dice! :( I followed the instruction to the letter....says drivers load and changes applied when I reboot I come up in tty.

---

### Post by tactx on 2009-06-01
Well, I've freshly re-installed 9.04...anybody got clue as weather this is fixable or not?

---

### Post by fillintheblanks on 2009-06-01
your talking about SLI right?

[http://ubuntuforums.org/showthread.php?t=1172733&post=#5](http://ubuntuforums.org/showthread.php?t=1172733&post=#5)

---

### Post by tactx on 2009-06-01
I finally fixed this by saving my xorg.config file from a working setup and copying it over. ...Duh? Don't know why I have this issue in 9.04 but not 8.04..?

btw...envyng still works beautifully.

---

### Post by spoolboyy on 2009-06-12
I've got this problem as well.  Same deal, I've run this system on Ubuntu since 7.04 (on and off) without any issues.  Dusted it off today to install 9.04 and it installed flawlessly, and ran the graphics at 1920 X 1080 right out of the box.  I installed the first round of updates and the res dropped to what appeared to be 640 X 480, so I installed the nVidia driver hoping this would correct the problem.

It boots, starts to load grub and goes black.  The light on my USB mouse goes out too, (odd?).  Any help would be GREATLY appreciated as I don't have any nVidia config files to copy over as the original poster did in his workaround.  I just reinstalled and am a little afraid to install the updates!

System Specs:
Athlon 64 3500+
2 GB RAM
nVidia Quadro FX550 graphics card (old)

Thanks in advance!

-Adam

---

### Post by MisanthropicOne on 2009-06-14
Hello all, Adam here. Same name, different guy. Anyway, I've been screwing around with this off and on for a while now and finally this evening have it working in 64 bit 9.04 for the first time thanks to this thread and others. So I'll post my xorg.conf file after my rewriting it after installing the latest drivers. You'll most likely have to change the BusID lines to match whatever your lspci reports back as the IDs of your respective video cards.

---

### Post by slamhound on 2009-06-14
In some cases it is a little simpler (no manual editing of xorg.conf).  I followed the instructions on this link ([http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/](http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/))

The main thing is running sudo nvidia-xconfig -a , which configures X for multiple cards.

Also, I think the nvidia drivers that Ubuntu supplies have a bug, so I got an error when nvidia-xconfig looked for the file: libnvidia-cfg.so.1 .  You need to create a symbolic link to the version-specific libnvidia-cfg.so.1 file (as described here:  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863))  It worked perfectly for me after that.

---

