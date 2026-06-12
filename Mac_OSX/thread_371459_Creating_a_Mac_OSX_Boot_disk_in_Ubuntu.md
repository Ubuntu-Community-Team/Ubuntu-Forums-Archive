---
title: "Creating a Mac OSX Boot disk in Ubuntu"
date: 2007-02-26
forum: Mac OSX
---

### Post by Yaraher on 2007-02-26
I've recently adquired a Macbook (C2D 2Ghz) which no longer boots :P
I was working with Parallels loading a BootCamp Windows partition, and left my laptop unattended for a while, discovering later my brother had hibernated it (which is, a "no-no" situation when loading the Windows partition via emulation).

When I turned it on, the keyboard didn't respond, neither the mouse, so I was left with the only choice of rebooting.

After doing that, the laptop won't boot up again. I've tried loading it with the Apple Installer Disc, entering single user mode, etc., but the Boot CD won't start up and when I try to mount the partition for write permissions on the single user mode, a kernel panel arises.

I CAN see my data in single user mode, and all of it seems fine, so I figured it should be a matter of using a repairing tool for it, and remember I got a Diskwarrior image at my Ubuntu machine. 

Giving it's a "*.cdr" image, I tried burning it with k3b, brasero, GnomeBaker but without much success. After reading something on the net, I change the *.cdr extension to *.iso and burned it with brasero.

Apparently, it works -I could see the files of the iso on the Cd., but when I use it to boot on my Macbook, after trying to load it, the "Circle with a stripe on the middle" symbol appears, I'd say because it isn't recognizing it properly as a booteable cd.

Is there any way to create a booteable CD with Ubuntu using the *.cdr image?

Thanks in advance for your suggestions!

---

