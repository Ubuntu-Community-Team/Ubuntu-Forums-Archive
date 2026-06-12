---
title: "Blank screen on boot after configuring mouse"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by Infinitron on 2007-10-30
So I have a strange problem.  Gutsy was working great after a fresh install.  I was using proprietary ATI drivers with my X1600 Mobility under fglrx.  I was trying to get the side buttons on my mouse to work in Firefox, so I searched the forums and found a couple of lines of code to add to the mouse section of my xorg.conf file.  

Like a newb, I didn't back it up first, but I figured something as small as changing the mouse settings wouldn't affect the whole system.  The first time I changed it, I did ctrl+alt+backspace to restart xserver, and logged back in.  I saw my old desktop background image and an error saying nautilus could not start.  So I went back and put the original mouse settings into xorg.conf, and again ctrl+alt+backspace to restart xserver, and this time the screen went blank, so I restarted...

I got to GRUB and started Ubuntu, got past the initial lines of code then the screen went blank.  I could not see anything going on, but my computer was still working.  I reboot back in recovery mode and I could see everything going on there, so I did a "sudo dpkg-reconfigure -phigh xserver-xorg" and got the configuration menu.  I first chose "vesa", but upon hitting enter, the screen went blank.  I could still type in the command "sudo reboot", and it responded by rebooting, but I had no display.  I tried again with "fglrx", but the same thing happened.  I tried one more time with "ati", and I got through to the choose resolution screen.  I chose my resolution, and got back to the recovery command prompt.  Upon restarting, I still have the original issue.

I booted with the Live CD, opened the live xorg.conf, and compared it to mine and they are exactly the same, but I cant boot from the HDD.

Any ideas or do I have to do a fresh install?
Everything worked great until I edited the mouse section of my xorg.conf.
Luckily I installed "/" and "/home" on different partitions so I can just reinstall on my "/" partition.

---

### Post by ofb on 2007-10-30
Weird. There's an open bug on ATI & blank screens. Buggy behavior can be quite capricious so /maybe/ you're running into something releated? Check the release notes.
[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

---

