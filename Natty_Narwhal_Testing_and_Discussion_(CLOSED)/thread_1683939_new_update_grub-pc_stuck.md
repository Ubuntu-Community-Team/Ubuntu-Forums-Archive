---
title: "new update grub-pc stuck"
date: 2011-02-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-02-08
at
Setting up grub-pc (1.99~rc1-2ubuntu1) ...
it's been there for 15 minutes. That's not good then :-)

Aha! If I click on any menu item in firefox (like bookmarks or tools) I am getting a choice to "accept the package maintainers version/keep the current version etc etc. So I assume that a config window should be open to make some sort of selection (as is usual when grub-pc is updated). Buuuuuuuut, no window is open! And there's a dead zone as well, where, presumably, the config window should be.
I've tried to select "keep the version locally installed" but it has no effect. It's still stuck. I can't get out of it and I don't fancy shutting down with grub-pc not configured.
Any ideas please  ?  :-)

---

### Post by philinux on 2011-02-08
> **Quackers said:**
> at
Setting up grub-pc (1.99~rc1-2ubuntu1) ...
it's been there for 15 minutes. That's not good then :-)

Aha! If I click on any menu item in firefox (like bookmarks or tools) I am getting a choice to "accept the package maintainers version/keep the current version etc etc. So I assume that a config window should be open to make some sort of selection (as is usual when grub-pc is updated). Buuuuuuuut, no window is open! And there's a dead zone as well, where, presumably, the config window should be.
I've tried to select "keep the version locally installed" but it has no effect. It's still stuck. I can't get out of it and I don't fancy shutting down with grub-pc not configured.
Any ideas please  ?  :-)

It should be ok to reboot as your old config file will still be there. Just run sudo update-grub before you reboot.

I just had this update but via chroot. My grub is not customised at all though.

Once your back in you'll need sudo dpkg --configure -a. In fact you could give that a go anyway.

---

### Post by Quackers on 2011-02-08
Thanks philinux, I was just writing a reply to your post and as I submitted it the pc crashed to a black screen with lots of lines of white writing.
Some of the text mentioned dirty files/dirty somethings, but then it just went black.
I reisub'd and was greeted by a black screen with
Mountall: disconnected from Plymouth
read error 64 (or something like that)
which repeated a few times and then went black, then booted into the next installation in the grub menu, without any input from me!

The sudo dpkg --configure -a failed due to dpkg being locked by another process, and the sudo update-grub just sat there with a flashing cursor - no activity.

---

### Post by philinux on 2011-02-08
Reboot into recovery mode and see how far you get.

---

### Post by Quackers on 2011-02-08
Ok, will do

---

### Post by Quackers on 2011-02-08
Er no, the installation has disappeared from grub menu!
When I boot into another system I am getting
read/64 error -110 a few times then
read/64 error b a few times (or similar)
unable to enumerate usb device (the installation is on a usb flash drive)
but the (usb)mouse also stops working for the first few minutes.

Unless there is another suggestion, I will try to chroot in and purge-re-install grub, but not too confident with the usb error!

---

### Post by Quackers on 2011-02-08
I opened gparted and the drive was not recognised. I unplugged it, then re-plugged it and gparted saw it again. I ran a check on the file system, which went ok.
I'll purge-re-install grub.

---

### Post by Harry33 on 2011-02-08
I have upgraded my grub (grub-common and grub-pc) to the version 1.99~rc1-2ubuntu1.
Upgrading went fluently without any requiries.
Also no problems with booting what so ever.

I admit it is a bit irritating to break a system with non-functional grub.

---

### Post by mc4man on 2011-02-08
Until the whole unseen window deal gets squared up you may want to place a desktop launcher in the bottom r. corner of the desktop to restart compiz (compiz --replace

That area is fairly immune to 'dead area's and can be useful to  recover and expose an unseen window without a logoutout/in or restart and also works if the launcher locks up

(though at this point not to sure that a compiz restart doesn't make a UPS issue more likely later in a session.

---

### Post by Quackers on 2011-02-08
Well that was a strange thing.
I chrooted in to the sdc1 installation from my sda5 installation and purges/re-installed grub. All went well, except that my sda5 system disappeared from grub menu! I was booted into that one!
Anyway, I rebooted and the problem system (sdc1) booted fine. I then ran sudo update-grub (even though I had run it twice while in chroot) and sda5 came back. 
Spooky, but all is well.
Thanks for the help philinux :-)

---

### Post by Quackers on 2011-02-08
> **mc4man said:**
> Until the whole unseen window deal gets squared up you may want to place a desktop launcher in the bottom r. corner of the desktop to restart compiz (compiz --replace

That area is fairly immune to 'dead area's and can be useful to  recover and expose an unseen window without a logoutout/in or restart and also works if the launcher locks up

(though at this point not to sure that a compiz restart doesn't make a UPS issue more likely later in a session.

I suspect the dead zone was the area where the grub-pc config window should have been asking me a question. But it's not a bad idea mc4man :-)  Thanks

---

