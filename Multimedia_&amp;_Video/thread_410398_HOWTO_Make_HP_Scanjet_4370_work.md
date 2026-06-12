---
title: "HOWTO: Make HP Scanjet 4370 work"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by XPerienced on 2007-04-15
Hi,

Howto make HP Scanjet 4370 work i Ubuntu Feisty. Feisty is the only version I tried this in.

01)
sudo apt-get install xsane kooka
- Or feel free to take either of them.

02)
sudo apt-get remove libsane-extra libsane-extras-dbg libsane-extras-dev
- The packages is broke in Ubuntu Feisty. They have to be replaced (see 03-04)

03)
Download: 
hp3900-stdalone_debian_0.8-1_i386.deb (or the current latest version)
hp3900-sane_debian_bin_0.8-1_i386.deb (or the current latest version)
at:
[https://sourceforge.net/project/showfiles.php?group_id=150599&package_id=166435&release_id=499156](https://sourceforge.net/project/showfiles.php?group_id=150599&package_id=166435&release_id=499156)

04)
sudo dpkg -i hp3900-stdalone_debian_0.8-1_i386.deb
sudo dpkg -i hp3900-sane_debian_bin_0.8-1_i386.deb

05)
Start Xsane or Kooka. Scan and enjoy.
- You can't use both at the same time

Done!

Thanks to jkdsoft@Freenode #sane for helping me out!

Additional information:
Run lsusb to see if it's connected.

Look regualary for updates on the application.

I did some other changes, but I update the howto if they are necassary. I'm not sure since they didn't help for me. I'll take them later so I won't change anything unnecessary.

XPerienced

---

### Post by MoebusNet on 2007-04-22
Thank you! Sorry to take so long to get back; I'm out-of-state right now for work. I'll check it when I get home.

---

### Post by lochball on 2007-05-01
I followed your advice and managed to get HP Scanjet 4370 (connected to USB) running on my KUBUNTU 6.10 box - except that it is only running under root/sudo privileges with xsane... so there seems to be a permission problem which is not yet clarified by me... any suggestions would be appreciated so far...

---

### Post by Princey on 2007-05-19
I run the 64bit so those debs won't work for me. I downloaded the source files, how do I combine the two to compile them?

---

### Post by lochball on 2007-11-24
In the meantime I made an upgrade of my box to **kubuntu 7.10** and unfortunately lost my scanner configuration. I installed sane, xsane, hp3900-xxx(version 0.9)  again I had the same problem as I had before when starting to get xsane running.

I got the following message in response to the command: [B]scanimage -T
[/B]
**scanimage: open of device hp3900:libusb:005:003 failed: Access to resource has been denied**

or by using **xsane** (response is in German, sorry):

**Fehler beim Öffnen des Geräts 'hp3900:libusb:005:003': Zugang zum Gerät verweigert.**

Reason for all this time consuming research work was very simple:

the **usb device 005:003** did not have the right **write permission** - that is what to have to be changed!

the command **ls -lR /dev/bus/usb/005/003** gives the following response:

**0 crw-rw-r-- 1 root root 189, 514 2007-11-24 19:54 003**

where we can see that there is no write permission set to others to this particular device (see the numbers in the above mentioned scanimage response, which directly gives us the needed infos to go further)

after changing this with:

**sudo chmod 666 /dev/bus/usb/005/003** we can checkt it again

**0 crw-rw-rw- 1 root root 189, 514 2007-11-24 19:54 003**

...and voila - **scanimage -L** works and the scanner can be started with **xsane** properly without complaining. I hope it helps others too...

---

