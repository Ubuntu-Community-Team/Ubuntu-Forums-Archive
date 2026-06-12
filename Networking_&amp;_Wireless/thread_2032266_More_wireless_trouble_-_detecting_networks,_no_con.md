---
title: "More wireless trouble - detecting networks, no connection"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by mang0 on 2012-07-23
Hey all. 

I've always had a bit of a problem with my WiFi card (Broadcom),  but I've managed to fix it in the past by using b43-fwcutter, as stated on the wiki page  about it. However, I've just updated to Ubuntu 64-bit 12.04 from 32-bit  12.04 (new comp) and tried the b43-fwcutter fix, but it only worked till I  rebooted. Now it doesn't work at all...Ubuntu is detecting the network, tries to  connect, asks for the WPA2 key, and then doesn't connect...I've tried  "sudo modprobe b43", still nothing. Any ideas?

I can't actually get cable internet on this computer at the moment, so if I need to install anything I'll need to have a .deb of it (or whatever file type it may be) so that I can copy it to a memory stick and use dpkg -i. (Or whatever the equiv is for that file type!)

Thanks a lot, I'll be around to give more info if needed.

---

### Post by praseodym on 2012-07-23
Install "linux-firmware-nonfree", it contains the b43 firmware:

[http://packages.ubuntu.com/precise/linux-firmware-nonfree](http://packages.ubuntu.com/precise/linux-firmware-nonfree)

---

### Post by mang0 on 2012-07-23
> **praseodym said:**
> Install "linux-firmware-nonfree", it contains the b43 firmware:

[http://packages.ubuntu.com/precise/linux-firmware-nonfree](http://packages.ubuntu.com/precise/linux-firmware-nonfree)

Ah, thankyou very much. I've just downloaded it and transferred it to my Flash drive, going to try it now. I'll post tomorrow morning whether it worked or not, I've got to sleep now!

---

### Post by mang0 on 2012-07-24
> **mang0 said:**
> Ah, thankyou very much. I've just downloaded it and transferred it to my Flash drive, going to try it now. I'll post tomorrow morning whether it worked or not, I've got to sleep now!

I tried it; un-archived it, went into the "firmware" folder and copied all the .fw files to /lib/firmware. I then re-booted, and still no fix....damn.

It was also suggested to me by someone in ##linux on Freenode IRC that I could also perhaps try taking the firmware from the old 32-bit install that I still have, and used successfully before this, and using that instead; as it's for the WiFi card, whether the OS is 32-bit or 64-bit doesn't matter. What do you think of that?

EDIT: Tried it, still no fix. I think I'm just going to re-install.

---

### Post by praseodym on 2012-07-24
Save it in "Downloads" and install via:

> sudo dpkg -i ~/Downloads/linux-*.deb

---

### Post by mang0 on 2012-07-24
> **praseodym said:**
> Save it in "Downloads" and install via:

Uh, it's an archive not a .deb...

---

