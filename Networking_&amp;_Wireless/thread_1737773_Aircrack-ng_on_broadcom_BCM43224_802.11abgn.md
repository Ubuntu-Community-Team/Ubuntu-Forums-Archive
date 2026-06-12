---
title: "Aircrack-ng on broadcom BCM43224 802.11a/b/g/n"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by majorawesome on 2011-04-23
I believe that this wouldn't work with aircrack-ng but i have been searching around and it said there were patches. If someone could confirm that it isn't working with aircrack-ng OR it is working OR there is a patch for it. if there is a patch would someone please take me to the link to download and install. n00b friendly directions :) and i dual boot w/ windows 7. i installed  ubuntu 10.10 through wubi.

---

### Post by |{urse on 2011-04-23
Your current driver isn't supported but you can install a different driver that supports the same chipset as well as promiscuous mode scanning.

[http://wireless.kernel.org/en/users/Drivers/brcm80211](http://wireless.kernel.org/en/users/Drivers/brcm80211) <- this driver supports your chipset and is supported by aircrack-ng.

So far as setting it all up I'm not aware of ubuntu forums' stance on educating others to crack wireless, you'll find a whole bunch of guides online that cover that sort of thing in great detail.

---

### Post by cantormath on 2011-04-23
edit: what |{urse said...

---

### Post by majorawesome on 2011-04-23
THANK YOU! but when i went to the download place kurse put up I can't decide between the downloads... should i get the download by micheal chan : linux-firmware: bnx2: Update firmware and version
?? I looked at the otherones and I didn't think that those were the drivers... and should I uninstall the driver I currently have or will that one overwrite it? and i'm doing this for educational purpose cause i've always wanted to try it.

---

### Post by |{urse on 2011-04-23
yes, that would be the right one but it would really be smarter to go buy a second wireless card that is supported by aircrack. Theres some nice cheapie usb ones that work perfectly out of the box. No sense in potentially screwing up your current wireless configuration just to play around with packet capture.

---

### Post by Joe of loath on 2011-04-23
Grab an internal Intel wifi card. I had a broadcom in my laptop, and in the end I decided £8 from China was a worthwhile expense. Now I don't need to carry around a USB dongle when doing 'penetration testing' for people. ('Your wifi is insecure' 'No, it's got a really long password you won't guess' *Fires up aircrack*)

---

### Post by majorawesome on 2011-04-23
Well you see Loaf guy (I forgot your name in 5 seconds when starting this reply hahaha) I have a $2000 dollar laptop (hp envy 17 almost all specs to the highest possible) and my parents WOULD be pissed as h*** if I broke this. I already broke it by deciding to remove ubuntu the wrong way cause it did't work (Delete the partitions it was on) and kurse, I have a plugin network adapter but it is at my house and I'm in ocean city until tomorrow (leaving in the morning) so ill get back to you when I try it out and if it doest work ill just use the driver thing.

---

### Post by Joe of loath on 2011-04-23
You don't need to break it, on my dell there is hatch you pop, and one screw to loosen the mini pci-e adaptor off. It's a straight swap, almost as easy as changing CD's.

---

### Post by majorawesome on 2011-04-23
ya. but im a wuss and id rather not do anything to something thats already working.and by messing up my configuration does that mean like just screwing ubuntu? cause i can just reinstall that (Praise WUBI!!)

---

### Post by majorawesome on 2011-04-24
How do I install this? the file is 0 bytes so I have no idea what to do

---

### Post by Joe of loath on 2011-04-24
Sure it downloaded OK?

---

### Post by majorawesome on 2011-04-24
BTW it is a .FW file

---

### Post by majorawesome on 2011-04-24
Ya I downloaded it correctly there is directions Ill get back with info if the install went well or not

---

### Post by majorawesome on 2011-04-24
I have no idea how to do it cause I can't find the files i have to have for installation, thanks anyway, ill just be using my linksys plugin usb adapter

---

