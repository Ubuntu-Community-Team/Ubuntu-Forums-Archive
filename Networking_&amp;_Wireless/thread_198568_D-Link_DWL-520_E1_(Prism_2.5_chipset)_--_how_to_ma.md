---
title: "D-Link DWL-520 E1 (Prism 2.5 chipset) -- how to make it work"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by liquideath on 2006-06-17
I finally got this card to work. DON'T read the [wiki guide]("https://wiki.ubuntu.com/WifiDocs/Device/DWL-520vE1?highlight=%28WifiDocs%2FDevice%29"), it probably only works for Breezy. I tried the wiki article, as well as ndiswrapper to no avail. It seems the hostap modules were already installed in the first place, all you need to do is blacklist the orinoco drivers to get them to load. 

Check to see if you have them installed:
```
find /lib/modules/$(uname -r)/ -name hostap*.ko
```
This should return a set of four hostap drivers in wireless/hostap/, and there shouldn't be any in wireless/, otherwise a conflict will occur.

Edit /etc/modprobe.d/blacklist and add:
```
blacklist orinoco_pci
blacklist orinoco
blacklist hermes
```

[COLOR="Red"]Update[/COLOR]: Apparently, you still have to follow the **Prepare The Firmware** and **Setup The Network Interfaces** steps in the [wiki article]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1"). I forgot that I did that also. I'll try to update the article to reflect this.

You may also need to install hostap-utils and hostapd with apt. I have hostap-source installed too, but I doubt that matters. If you followed the wiki instructions, you need to remove the package that you installed. This seems to work with any kernel (I've tried i386 and k7).

---

### Post by az on 2006-06-17
[QUOTE=liquideath]I finally got this card to work. DON'T read the [wiki guide]("https://wiki.ubuntu.com/WifiDocs/Device/DWL-520vE1?highlight=%28WifiDocs%2FDevice%29"), it probably only works for Breezy. I tried the wiki article, as well as ndiswrapper to no avail. It seems the hostap modules were already installed in the first place, all you need to do is blacklist the orinoco drivers to get them to load.[/QUOTE]

Please edit that wiki page accordingly so that more people can know.

---

### Post by kraonn on 2006-06-18
What about under Edubuntu 6.06? I'm trying to install that on a machine my kids use. It has this NIC and I'm having no success in getting it set up.
:confused:

---

### Post by Jason_25 on 2006-06-18
[QUOTE=kraonn]What about under Edubuntu 6.06? I'm trying to install that on a machine my kids use. It has this NIC and I'm having no success in getting it set up.
:confused:[/QUOTE]
Same as ubuntu.  Try the orinoco (default) drivers first.  If they don't work, do what he said and blacklist the orinoco modules, and reboot.

---

### Post by kraonn on 2006-06-18
Yes, thanks - I've tried this and hostap does not seem to be a part of the default Edubuntu 6.06 distro that I installed from the DVD, nor does it appear on the DVD that I can find. Orinoco does not work for my Intersil 2.5 card - the firmware seems to need to be downloaded to the card.

I have taken the .debs from the Ubuntu 6.06 libraries and tried loading them into the Edubuntu 6.06 system, and that seems to work. What seems to be missing from the original Wiki from a year ago is how to cause the firmware to be loaded into the card so it will work. 

Under Edubuntu I see the card listed as WLAN0 and WIFI0 but it never can seem to connect to an access point.

---

### Post by Jason_25 on 2006-06-18
Yeah I had to update the firmware on mine a few months ago actually to get the hostap drivers working right.  

[http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)

I used the " Linux-based prism2_srec flashing steps".

---

### Post by kraonn on 2006-06-18
I'll try this - thanks so much for the quick replies!

I'm curious - the information I'd read up to this point about this chipset was that the firmware actually needed to be downloaded freshly each time you powered up. It was not stored in flash but dynamically loaded, was my understanding. Was this incorrect?

---

### Post by liquideath on 2006-06-18
This kind of card doesn't have permanent firmware, so the firmware has to be downloaded every time the device is activated. The drivers should take care of that. If the card is working correctly, you should be able to do a "iwlist wlan0 scan" to view available AP's.

---

### Post by eh270 on 2006-06-19
After adding those to the blacklist file, what next? you just reboot and voila!, it works?

---

### Post by liquideath on 2006-06-19
[QUOTE=eh270]After adding those to the blacklist file, what next? you just reboot and voila!, it works?[/QUOTE]

Oh, I just realized that there's something you else you probably have to do that the wiki article suggests. I updated my initial post and the wiki article to include it.

If you still have problems, check your startup messages:
dmesg | grep wlan0
dmesg | grep hostap
dmesg | grep orinoco
dmesg | less

Those might contain juicy details to diagnose the problem.

---

### Post by This_is_me on 2006-06-19
When using the hostap drivers, dmesg contains the error "Assuming no Primary image in flash - card initialization not completed."

what is this problem...?

---

### Post by liquideath on 2006-06-20
[QUOTE=This_is_me]When using the hostap drivers, dmesg contains the error "Assuming no Primary image in flash - card initialization not completed."

what is this problem...?[/QUOTE]

Mine has that message also, but it works fine. I guess it means that the card has no firmware stored in its flash - which is normal from what I understand.

Curiously enough, today I tried to boot the k7 kernel, but the wireless didn't work. It didn't even show up in networking gui. I booted the i386 and everything works fine again. Both have the hostap drivers...I will have to investigate this further.

If anyone else has this card working, tell me what you did/did not do to solve the problem.

---

### Post by Rouge8 on 2006-06-22
Attempted to get a DWL-520 E1 working on a friend's PC, using the k7 kernel, build essentials, the kernel headers, and hostap installed. Also tried using the i386 kernel.

However, it does not appear to work.

'sudo modprobe hostap' does not return anything, nor does 'dmesg | grep orinoco'.

' dmesg | grep hostap' gives: 

[17179588.440000] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179588.440000] hostap_pci: Registered netdevice wifi0
[17179588.456000] hostap_pci: first command failed - assuming card does not have  primary firmware
[17179588.956000] hostap_pci: assuming no Primary image in flash - card initiali zation not completed

---

### Post by Rouge8 on 2006-06-22
Realized those errors were due to an error in the wiki:        fw_secondary /etc/firmware/rf010803.hex should be:         fw_secondary /etc/firmware/rf010804.hex

After correcting that, the wireless card is not detected at all, even with lspci.

---

### Post by liquideath on 2006-06-24
[QUOTE=Rouge8]'sudo modprobe hostap' does not return anything, nor does 'dmesg | grep orinoco'.

' dmesg | grep hostap' gives:

[17179588.440000] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179588.440000] hostap_pci: Registered netdevice wifi0
[17179588.456000] hostap_pci: first command failed - assuming card does not have primary firmware
[17179588.956000] hostap_pci: assuming no Primary image in flash - card initiali zation not completed[/QUOTE]

I think this means things are working properly. 

[QUOTE=Rouge8]Realized those errors were due to an error in the wiki:        fw_secondary /etc/firmware/rf010803.hex should be:         fw_secondary /etc/firmware/rf010804.hex

After correcting that, the wireless card is not detected at all, even with lspci.[/QUOTE]

You could try using the the 1.8.3 version firmware from [http://www.red-bean.com/~proski/firmware/](http://www.red-bean.com/~proski/firmware/). Don't know if that makes a difference, but its the one I'm using. When I used the newest one, it seemed to hard lock the computer when I modprobe'd hostap_pci. What's in the kernel messages now?

---

### Post by Rouge8 on 2006-07-17
I don't remember how, but I did eventually manage to get it working. After a few days and (I assume) reboots, it stopped working. Would I need to run all the steps that it took to get it working again at every boot? If so, is there any way I could automate it?

---

### Post by liquideath on 2006-07-18
> **Rouge8 said:**
> I don't remember how, but I did eventually manage to get it working. After a few days and (I assume) reboots, it stopped working. Would I need to run all the steps that it took to get it working again at every boot? If so, is there any way I could automate it?

Did you update the kernel? Right now I only seem to be able to get the 2.6.15-23-386 kernel to work properly, fresh updated kernels don't work. Like you I'm in a similar position. I guess something I did to the kernel modules caused hostap to start working.

---

