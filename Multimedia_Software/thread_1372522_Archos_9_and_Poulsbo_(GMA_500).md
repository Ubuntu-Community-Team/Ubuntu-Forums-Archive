---
title: "Archos 9 and Poulsbo (GMA 500)"
date: 2010-01-04
forum: Multimedia Software
---

### Post by chrismcb6 on 2010-01-04
Hi everyone,
 
New to the forums, fairly new to Ubuntu.
 
I bought the Archos 9 tablet PC ([http://www.archos.com/products/nb/archos_9/](http://www.archos.com/products/nb/archos_9/)) which comes preloaded with Windows 7 - which is fine, once it gets started.
 
I have installed UNR for a friend in the past and liked its simplicity and fast loading and hoped to install dual-booting on my Archos 9.
 
After downloading a whole load of dists and reading pages and pages about the problems with the GMA 500, I've finally became stumped.
 
 
I have UNR 9.10 successfully installed with wireless drivers (Broadcom STA) on and running fine.
 
The graphics, however, runs in VESA mode and is painfully slow.
 
 
After finally settling on UNR with the Ubuntu having the best support for Poulsbo, I followed the clear instructions on the Ubuntu Wiki ([https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)) and performed the installation and configuration of the Karmic (9.10) new method.
 
 
Everything installed perfectly with no problems - until reboot.
 
 
After the initial ubunti logo appears (before the coloured logo bar), the screen goes blank and will not respond to any keypresses to switch to the terminal or CTRL-ALT-DEL. All I can do is press the power button and watch it drop back to the terminal for its shutdown sequence then turn off.
 
 
Rebooting into recovery mode, I view the X log (attached) and am quite confused.
 
The driver seems to be loaded, yet a few things fail, then continue before finally giving up and unloading.
 
 
I believe everything is installed correctly, but it may require some more Xorg.conf configurations specific to this device.
 
 
I have performed the advised "dpkg-reconfigure psb-kernel-source" command to no avail.
 
 
Can anyone spot anything in the log (which is above my head!) that will point me in the right direction to finally get the system running?
 
 
Thanks
 
 
 
p.s. Log file had to be slipt into two due to max file size for .txt files. I've added the current Xorg.conf file for reference

---

### Post by chrismcb6 on 2010-01-05
Should this post have been perhaps made in a different forum?
 
Can anyone help point me to the correct place?
 
 
Thanks

---

### Post by markbuntu on 2010-01-05
It seems the driver is having a lot of problems with your hardware from looking at the logs. 

You should go back to the VESA driver until you can find something specific for the Archos 9 and the poulsbo driver. You could try asking at one of the xorg mailing lists or IRC channels or try a google search: archos 9 linux or something like that. There are archos tablets that archos claims run linux so you could even ask them directly. They have probably tweaked the hardware and bios heavily to run windows 7.

Sorry I cannot help any more than that. I was thinking about getting one of those to so please keep us informed of your progress.

---

### Post by Anfanglir on 2010-01-05
The "new method" on that wiki-page didn't work for me, but the old method on the same page did work (Fujitsu u820 with poulsbo).

Or you may wanna check out Jolicloud, a linux build based on ubuntu but targeted at netbooks etc. Jolicloud has working drivers for poulsbo(!). I dont like the GUI with lots of big icons on the screen, but at least graphics work.

[http://www.jolicloud.com/guides/partition-install]("http://www.jolicloud.com/guides/partition-install")

/ Anfanglir

---

### Post by chrismcb6 on 2010-01-06
Markbuntu - thanks, that's what I thought from the logs, but hopefully something can get it to work while staying with UNR.
 
There's nothing on Google at the moment - perhaps it's just too new - or people haven't tried putting Linux on theirs.
 
 
Anfanglir - I didn't even think to do the old method - assuming the new was a script which just performed the actions of the old one.
 
Followed the instructions - and from what I quickly saw, new packages were downloaded (The Lucazade build of psb-kernel-headers being one), but after reboot, the same thing with the log looking pretty identical.
 
 
I did try Jolicloud in the past while I was installing/reinstalling dists at the rate of two per day, but cant recall specifically why I didn't stick with it.
 
 
I would be quite happy with a basic dist such as Moblin (I just want a fast alternative to Win7 to get me on and online within seconds rather than 5 minutes), but the same issue arose with that - making me come to the same wondering as markbuntu - that there's something custom and non-standard in this device making it fail for them all.

---

### Post by chrismcb6 on 2010-01-08
Can anyone else offer any advice?

---

### Post by ledzepjes on 2010-06-10
Hi guys, I found this while reading your thread, have you come up with anything, I'm assuming you haven't yet. Try this, these guys claim to have the touch screen working, as well as wireless, let me know if it works, it looks like a nice little touch screen pc to have ubuntu on:

[http://gadgetmix.com/index/archos9-ubuntu/](http://gadgetmix.com/index/archos9-ubuntu/)

Copied from the site above:

Archos 9 is a an x86 computer and thus it is possible to install Ubuntu on it. Folks at archoslounge installed it on the Archos 9, but the installation is not so straightforward. You will need to attach a USB mouse, keyboard, Wi-Fi dongle to the Archos as touchscreen and built-in Wireless do not work out-of-the box.

After installing the Ubuntu, to get the wireless working, write the following commands in the terminal:

[COLOR="DarkOrange"]sudo apt-add-repository ACH: gma500/ppa

sudo apt-get update

sudo apt-get install Poulsbo-driver-2d-3d-driver Poulsbo Poulsbo-config[/COLOR]

..and to get the touchscreen working, write this at the terminal

[COLOR="DarkOrange"]wget [http://home.eeti.com.tw/web20/drivers/touch_driver/Linux/20100413/eGalaxTouch-3.01.4001-32b-k26.tar.gz](http://home.eeti.com.tw/web20/drivers/touch_driver/Linux/20100413/eGalaxTouch-3.01.4001-32b-k26.tar.gz) 
tar vxfz eGalaxTouch-3.01.4001-32b-k26.tar.gz vxfz eGalaxTouch tar-3.01.4001-32b-k26.tar.gz 
cd eGalaxTouch32 cd eGalaxTouch32 
sudo ./setup.sh sudo. / setup.sh 
choose PS/2 by pressing "2" choose PS / 2 by pressing "2"[/COLOR]

Change the startup options to enable the touchscreen to be recognized (this causes the loss of the mouse touchpad).

[COLOR="DarkOrange"]sudo gedit /etc/default/grub sudo gedit / etc / default / grub[/COLOR]

It should be added mem = 980mb i8042.nomux content GRUB_CMDLINE_LINUX_DEFAULT line and save.

[COLOR="DarkOrange"]sudo update-grub sudo update-grub[/COLOR]

3. Make the screen visible to the system

[COLOR="DarkOrange"]sudo vim.tiny /etc/rc.local vim.tiny sudo / etc / rc.local[/COLOR]

It should be added [COLOR="DarkOrange"]echo-n "serio_raw"> / sys/bus/serio/devices/serio1/drvctl[/COLOR] just before the exit 0.

4. Restart and calibrate the screen

[COLOR="DarkOrange"]sudo eGalaxTouch sudo eGalaxTouch[/COLOR]

Adjust the compensation by selecting Tool> Linearization> 25 points and clicking at each round that appear on the screen.

---

### Post by chrismcb6 on 2010-06-10
Thanks - my Archos 9 is currently with Archos for repair (faulty power port) - and has been for nearly a month now!
 
I'll be sure to try this if/when I get it back!

---

### Post by yvesdm3000 on 2010-06-11
I have an Archos 9 too. I repaired the faulty powerport myself, and made it better than it was, it is simply badly designed...

I also did some hacking on the Poulsbo drivers and have 3D and accelerated video working now too!

Here are the instructions for the video display:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

You'll also need to install the egalax driver for the touchscreen. 
Here is a thread specific for your Archos 9:

[http://forum.archosfans.com/viewtopic.php?f=50&t=27303](http://forum.archosfans.com/viewtopic.php?f=50&t=27303)

-Yves

---

