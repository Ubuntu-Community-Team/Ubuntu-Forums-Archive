---
title: "Netgear WNDA3100v2 N600 Wireless USB"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by MrOfdensen on 2013-02-16
Hello hello Ubuntu forums. I've been going for about four hours now trying to install the drivers for my Netgear WNDA3100v2 N600 Wireless USB Adapter.


Googled many different things, tried many different things, and I've tried following posts from others on these forums. Unforunately, none of it worked. 

Everyone's resolution came in some form or another involving ndiswrapper, but I've followed said instructions, and when I get to the point of typing into the terminal "sudo modprobe ndiswrapper" after the driver installation claimed it was completed, it returns with "FATAL: Module ndiswrapper not found."


I hate to be one of those people to post an issue others are having, but I haven't seen anyone run into this yet on the multiple threads I've followed.

Any help would be very much appreciated.

---

### Post by praseodym on 2013-02-16
Which Ubuntu version do you use?

For 12.04:
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms
```

For 12.10:

```
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo apt-get install linux-headers-generic linux-headers-$(uname -r) build-essential dkms
```

Download the patched packages from this link:

[http://forum.ubuntuusers.de/topic/fritz-wlan-stick-probleme-mit-der-installation/#post-5254662](http://forum.ubuntuusers.de/topic/fritz-wlan-stick-probleme-mit-der-installation/#post-5254662)

and compile ndisgtk according to this:

[http://forum.ubuntuusers.de/topic/wlan-pci-wird-nicht-bei-jedem-start-erkannt/#post-3842662](http://forum.ubuntuusers.de/topic/wlan-pci-wird-nicht-bei-jedem-start-erkannt/#post-3842662)

scroll down.

Driver download here:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz
```

From here:

[http://forum.ubuntuusers.de/topic/installation-eines-netgear-usb-sticks-wnda/#post-2955302](http://forum.ubuntuusers.de/topic/installation-eines-netgear-usb-sticks-wnda/#post-2955302)

---

### Post by MrOfdensen on 2013-02-16
Thanks for the response! I will have to wait until I can get my Ubuntu machine hooked back up to the net, but I will try what you recommended ASAP.

Oh, yes, it was somewhat silly of me to not post specifications.

I'm running 12.10 Ubuntu 64bit.

---

### Post by MrOfdensen on 2013-02-16
Okay, sorry that took me so long. I had just gotten to be able to reconnect this computer to the Internet using a bridged connection from a laptop.

So, I followed all the instructions I could, and it seems everything has installed correctly. I even got the computer to recognize my wireless device and attempt to connect. Unfortunately, no connections could be made to my router, and after a system restart, the computer no longer acknowledges that I have a wireless device.

I've come this far, I'm sure the rest isn't very difficult either. I'm just not a Linux wiz, so I'll need a bit more help to get this sorted out. I can provide any information needed. Thanks again !

---

### Post by MrOfdensen on 2013-02-16
Okay, in regards to the post I last made, I tried disconnecting and reconnecting the wireless adapter from my computer. It turns out after restarting my machine, it did not recognize it until I disconnected it and reconnected.

I ran lsusb and found that my wireless adapter wasn't listed, so I tried reconnecting it. My computer recognized it when I reconnected, and I now have wireless Internet.

Is there any way for me to get my computer to recognize the device after restarts? Or am I just going to have to disconnect and reconnect it every time I reboot?

---

### Post by praseodym on 2013-02-17
Try to add the driver to the whitelist:
```

echo ndiswrapper | sudo tee -a /etc/modules
```

---

