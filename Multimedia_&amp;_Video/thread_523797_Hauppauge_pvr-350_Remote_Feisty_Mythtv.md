---
title: "Hauppauge pvr-350 Remote Feisty Mythtv"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by UponFirstListen on 2007-08-12
I've spent the greater part of this week trying to reinstall MythTV on Ubuntu Feisty and have made it rather far. I am stuck, however, on getting my remote to work. I've been 'live' blogging the experience here: [http://penguinvirgin.blogspot.com/](http://penguinvirgin.blogspot.com/) which details most of install process and where I found the information. The relevant portions of my attempts to get the remote working have been recreated below. Any and all help would be appreciated.

Ok, back to try out the remote. I remember it being fairly easy last time around, so let's hope that holds trues.

First I setup mythfilldatabase to run on its own using instructions found here: [https://help.ubuntu.com/community/MythTV/Install/WhatNext/Feisty_D](https://help.ubuntu.com/community/MythTV/Install/WhatNext/Feisty_D)

Then I add the themes from here: [https://help.ubuntu.com/community/MythTV/Install/WhatNext/Feisty](https://help.ubuntu.com/community/MythTV/Install/WhatNext/Feisty)
Chose MythCenter-wide as my theme. It appears to be a little bit faster, but not much. Like the clean look of it though.

Ok, remote time. [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

No dice. Followed all the steps (I thought), but when I typed sudo /etc/init.d/ start, I got:

I couldn't load the required kernel modules
You should install lirc-modules-source to build
kernel support for you hardware

Trying again from the top.

Found this post: [http://ubuntuforums.org/showthread.php?t=358469](http://ubuntuforums.org/showthread.php?t=358469) that has the same problem. Fixed it by creating a script as described. irw now reports on the buttons I am pressing.

Using [http://lircconfig.commandir.com/](http://lircconfig.commandir.com/) to setup the buttons. Save the file to my home directory and reboot to see if it's working.

Bring up the terminal and type in irw. No such file or directory. I guess I should have tested that before I started mapping keys, eh?

Followed this guide: [http://doc.gwos.org/index.php/Lirc](http://doc.gwos.org/index.php/Lirc)

Got errors on the 'make' step. Giving up for now.

Found this site: [http://people.mech.kuleuven.be/~wmeeusse/linux.html#remote](http://people.mech.kuleuven.be/~wmeeusse/linux.html#remote)

Need to 'sudo' the modprobe ir-kbd-i2c line.

Need to 'sudo lsinput' but it doesn't give any relevant information to my remote.

While browsing around, I found this guide: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) that while didn't help my remote issues, certainly helped my blocky picture by telling me to deinterlace it as well as setting it to 16x9 for my widescreen LCD.

[http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft#Supported_Hardware](http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft#Supported_Hardware) was no help.

Removed everything I did. Deleted all lirc files I had downloaded. Modified hardware.conf to remove the changes I made, everything (I think). Rebooting now.

Back to this site: [http://people.mech.kuleuven.be/~wmeeusse/linux.html#remote](http://people.mech.kuleuven.be/~wmeeusse/linux.html#remote)

Still need to sudo the ir-kbd line.

Buttons are doing stuff! Finally. sudo lsinput shows the remote at /dev/input/event6

Followed all the steps and seemed to have some success in getting Ubuntu to recognize that I was hitting Volume Up and Volume Down. Rebooted.

Ubuntu doesn't seem to recognize the remote anymore. modprobe evdev and ir-kbd-i2c and it's working again. The question is; does mythtv recognize it? A little bit. The numbers work, but not much else. I think that's where the previous lircconfig.commandir.com comes in. Let's find out.

Nope. Numbers work, but still nothing else. Meanwhile, I added evdev and ir-kbd-i2c to my /etc/modules file to (hopefully) load them at boot. Wish me luck.

Volume Up and Down working on boot. This is a good sign. Load up mythtv, and...nope. Damn it.

Downloaded a new lircd.conf from lircconfig.commandir.com. Reboot again. If it doesn't work, I'm off to bed. If it does, well, I'm probably still off to bed.

Nope. Good night.

Ok, the key bindings seem to be good in the lircd.conf based on what I press and what registers with dmesg. irw reports connection refused, but I digress.

Made a few changes in /etc/lirc/hardware.conf to tell it where to find my files. Figured it was worth a shot. Going to reboot and then try and match each button in lircd.conf with lircrc to make sure they are the same.

I uninstalled everything lirc related.

Been messing with xmodmap and have created a file that looks like this:

keycode 0x17a5 = Return
etc..

I run xmodmap ~/.xmodmap and it runs without error, but the keys still don't work.

Thanks again for any help.

---

### Post by UponFirstListen on 2007-08-20
I was able to fix this on my own using Gizmod.

See here ([http://sourceforge.net/forum/forum.php?thread_id=1799139&forum_id=467994](http://sourceforge.net/forum/forum.php?thread_id=1799139&forum_id=467994))
and here ([http://penguinvirgin.blogspot.com/](http://penguinvirgin.blogspot.com/)) on my progress and my 'solution' to the problem.

---

