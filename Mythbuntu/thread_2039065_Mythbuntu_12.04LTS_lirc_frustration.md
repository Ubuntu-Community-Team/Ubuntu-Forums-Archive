---
title: "Mythbuntu 12.04LTS lirc frustration"
date: 2012-08-08
forum: Mythbuntu
---

### Post by bobwdn on 2012-08-08
I have recently built a Mythbuntu 12.04LTS box. Most of the install went quite well.

Setting up the remote control is quite a different issue. It seems that my box is one of the (currently) 6 individuals affected by Launchpad bug #1004239. This is a confirmed bug that does not allow lirc to run. The work around suggested has had no effect on my system. Lirc just refuses to run.

What do I do now? Any suggestions?

---

### Post by alien878 on 2012-08-08
Maybe uninstall lirc and let the kernal drivers do the work?  It will probably require changing the keymaps in mythfrontend setup instead of .lircrc, but that is actually easier then the lirc setup originally was.

See here (3rd post down): [http://ubuntuforums.org/showthread.php?t=1975559](http://ubuntuforums.org/showthread.php?t=1975559)

---

### Post by anonymousdog on 2012-08-08
The symlink paths MAY have suffered from wrap; so, double check that.

Then, it appears that lirc is unconfigured as well; so, 'sudo dpkg-reconfigure lirc'.

Then use the MCC to configure lirc for your hardware (and optionally, set top box/blasting).

Then restart lirc and test.

---

### Post by nickrout on 2012-08-09
> **bobwdn said:**
> I have recently built a Mythbuntu 12.04LTS box. Most of the install went quite well.

Setting up the remote control is quite a different issue. It seems that my box is one of the (currently) 6 individuals affected by Launchpad bug #1004239. This is a confirmed bug that does not allow lirc to run. The work around suggested has had no effect on my system. Lirc just refuses to run.

What do I do now? Any suggestions?

There are a number of fixes mentioned in the bug report. Which of them have you tried?

---

### Post by bobwdn on 2012-08-09
Thanks for every ones help. So far I have been tied up in my regular job but, expect to have some time on Saturday to continue. Please bare with me until then. I really appreciate every ones suggestions.

---

### Post by anonymousdog on 2012-08-10
I might be "in", but, first, what are we baring? :P

---

### Post by bobwdn on 2012-08-11
For those of you wondering what I am baring (anonymousdog) well, am I baring my butt (ha-ha) or asking for everyone to allow me the time to return to this and properly answer your questions? Things that make you go hum-m-m!;)

Since my last chance to look at the bug ***[page]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/1004239")*** there have been additional suggestions. I will next consider how to install the 'debdiff' patch suggested.

I downloaded the most recent (as of 2012-08-11) daily build of quantel (12.10) to see if the bug exists there. I installed the iso image to a usb drive (stick) and booted the live cd image on my mythbuntu box. Unfortunately there is no lirc installation candidate available yet. So much for that idea! Oh, well. I want to stay focused on the 12.04 version anyway. It was just one of my crazier ideas.

On to 'debdiff' patch . . . . .

---

### Post by bobwdn on 2012-08-11
Reading through the additional posts at [***bug#1004239***]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/1004239")

Post #10 contains a patch that was believed to correct this lirc issue. (Thanks jbebel)

I found this instruction page: [https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff](https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff)

Following those instructions, the debdiff patch appeared (I am a novice with little experience at this level) to build properly with no errors and created (appeared to be new) lirc-x_0.9.0-0ubuntu2_amd64.deb file.

The final instruction of "BuildFromDebdiff" page is to install with: sudo dpkg -i ../lirc-x_0.9.0-0ubuntu2_amd64.deb

This is the resulting output: [myuser]@mythtv01:~/lirc$ sudo dpkg -i ../lirc-x_0.9.0-0ubuntu2_amd64.deb
dpkg: error processing ../lirc-x_0.9.0-0ubuntu2_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ../lirc-x_0.9.0-0ubuntu2_amd64.deb

So, the patch did not install/work for me.

Clearly, I am at a level that I need all the help I can get. Suggestions?

---

### Post by bobwdn on 2012-08-12
This morning, update upgraded lirc with a 'new install'.

There appears to be hope, but alas, I am tied up a family gathering all day and cannot test this new lirc upgrade.

Bummer, dude!!  :(

---

### Post by bobwdn on 2012-08-23
I have discovered that my issue was hardware related. I was trying to configure the ir on a Hauppaugge HVR-1600. This is quite challenging and impossible for me to complete. (Good luck to any others who try.)

Per the advice of many of the forums I have been perusing answers on, I bought a Windo$e Media Center infrared remote control (suggested on [*[COLOR="Red"]Mythtvcast[/COLOR]*]("http://mythtvcast.com/") webpage.) The lirc program loaded properly and worked!

Although the HVR-1600 card worked, it does not completely work (analog tuner is not operational) and I will be selling it soon on the web somewhere.

---

