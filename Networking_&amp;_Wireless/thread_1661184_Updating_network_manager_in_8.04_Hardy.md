---
title: "Updating network manager in 8.04 Hardy"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by grey1beard on 2011-01-06
I'm having problems with my wireless networking, and have just discovered that my network manager version is 0.6.6. 
Going to the nm pages, I found version 0.8.1 is available, and the download link lists dozens of different versions.
Could someone guide me to which version I should download for my 8.04, 32 bit desktop please ?
(I am surprised, being still wet behind the ears, that update manager hasn't done this. )
Also, do I need to download the applet separately, or will that be part of the nm download ?
John

---

### Post by grey1beard on 2011-01-06
Update
I've just found the system/admin/Network tools window.
I selected wireless interface(wlan0), then Configure, and up popped a window to say that "The interface does not exist" which is a bit of a surprise !
I then tried eth0 and it says that doesn't exist.
Is it the "Configure" interface that is missing, or what ?
John

---

### Post by snowpine on 2011-01-06
Is there a reason you're using such an old release? (8.04 = April 2008 )

If you provide details of your wireless chipset (use the terminal command 'lspci' if you're not sure) then maybe we can help you troubleshoot. It sounds like your card is not being recognized (since there is no wlan0 interface), which can often be resolved by installing the correct driver. Since I don't know which card you have, I can't provide specific instructions at this time.

But frankly it might be worthwhile trying a Live CD of the current release (10.10), which includes network-manager 0.8.1, as well as a newer kernel, the latest wireless drivers, etc.

---

### Post by grey1beard on 2011-01-06
Sorry snowpine. I usually add a caveat to my enquiries as to why that system needs to stick to 8.04. 
It's because I'm running EMC2 on it, and the latency figure is perfect in 8.04 and useless on 10.04, the next upgrade that supports EMC2. It's a machine thing ;)

I'm running a TL-WN321G usb dongle (no expasion slots for a pci card) and have successfully installed the RT73 driver.

It's specific advice on this final part of the jigsaw that I need, having had lots of help on getting this far.
John

---

### Post by snowpine on 2011-01-06
No worries, there are many valid reasons to use an older, stable release. :)

I am not familiar with the RT73 chipset personally, but perhaps this will be of assistance?

[http://ubuntuforums.org/showthread.php?t=757607](http://ubuntuforums.org/showthread.php?t=757607)

---

### Post by grey1beard on 2011-01-06
That was one of the threads I devoured on my way to getting this far.
Because I'm in danger of double posting, I've tried to limit the request for info to very specific questions, only including what I thought might be relevant.
However, to expand a trifle on the background, I have got the driver installed, and I assume it's installed correctly. 
If I use iwlist scan, it shows the details of my network correctly(as far as it goes), and lshw -C network gives the correct mac address for the device, and ifconfig also gives the expected results.
If I examine the router dchp client list, that also lists the 8.04 pc correctly.

I assumed therefore, that I had not configured the network correctly in the network settings window, which gets me back to the starting point.
Regards
John

---

### Post by grey1beard on 2011-01-06
This may now be a superfluous thread. 
I've just been reading pytheas22's thread "Comprehensive ndiswrapper troubleshooting guide" and working through his first post, I ran the command **sudo modprobe ndiswrapper** to load ndiswrapper.
The icon at the top of the page hasn't changed, not the option when I left or right click on it.
So I went to System/Admin/network tools and could see on the wireless interface entry that packets were transmitting and being received !
I opened Firefox, and we're in business.
Tempting fate, I closed down and did a cold boot, and it still works.

However, the original question remains, do I upgrade my network manager ?

John

---

### Post by PatchesTheCaveman on 2011-01-06
Some people think wicd, another program besides NetworkManager that drives the network icon, works much better.  If you want to try it, run the following commands:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```

---

### Post by grey1beard on 2011-01-07
Thanks Patches. 
I'll let the dust settle for a couple of days, and then give it a try ;)
Regards
John

---

### Post by grey1beard on 2011-01-16
> **PatchesTheCaveman said:**
> Some people think wicd, another program besides NetworkManager that drives the network icon, works much better.  If you want to try it, run the following commands:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```
I followed that to the letter, but got -
> john@fanshop:~$ sudo apt-get install wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wicd

Suggestions please.

John

---

### Post by PatchesTheCaveman on 2011-01-16
Run ```
gksudo software-properties-gtk
``` and make sure you have the *universe* repository enabled.  Then run
```
sudo apt-get update
```
and try installing again.

---

### Post by tekkidd on 2011-01-16
To update it first download the source for the .81 release @ 
[http://ftp.gnome.org/pub/GNOME/sources/network-manager-applet/0.8/network-manager-applet-0.8.0.997.tar.bz2]("http://ftp.gnome.org/pub/GNOME/sources/network-manager-applet/0.8/network-manager-applet-0.8.0.997.tar.bz2")

then extract it, now in the terminal cd into the directory then 
```
./configure
```
make sure to read the errors to see what packages you will need to install
```
sudo make
```
```
sudo make install
```

---

