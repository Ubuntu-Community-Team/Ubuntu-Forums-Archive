---
title: "Broadcom wireless driver - connection dropping/not connecting"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Proxmty on 2012-03-11
I've installed the broadcom driver for the BCM4312 (downloaded from the broadcom website, followed the instructions on the readme file which got me connected - this readme file involved building a wl.ko file, disabling and blacklisting bcma, ssb, b43. The only thing I didn't do was the part where it asks ubuntu users to rename the other wl.ko files, the command failed (so this could be a clue? I've no idea)
 
When I log in now, the wireless card seems to be working in that the option is visible and it shows a list of wifi connections including mine. But it just won't connect anymore. (remember it did initially, but not when I restarted)
 
Any help greatly appreciated.

---

### Post by ts3 on 2012-03-11
> **Proxmty said:**
> I've installed the broadcom driver for the BCM4312 (downloaded from the broadcom website, followed the instructions on the readme file which got me connected - this readme file involved building a wl.ko file, disabling and blacklisting bcma, ssb, b43. The only thing I didn't do was the part where it asks ubuntu users to rename the other wl.ko files, the command failed (so this could be a clue? I've no idea)
 
When I log in now, the wireless card seems to be working in that the option is visible and it shows a list of wifi connections including mine. But it just won't connect anymore. (remember it did initially, but not when I restarted)
 
Any help greatly appreciated.

Hi, until someone more experienced steps in to troubleshoot your wireless (it sounds like you're almost there) you can try the steps in [https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html](https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html)

This is the 11.10 guide, you might need another one depending on which ubuntu you are running.  

At this stage I don't want to confuse the issue b/c it looks like you installed a driver and just need to get the wireless up and running (see the troubleshooting guide) but I was wondering why you wouldn't use the b43 driver and b43 firmware (downloadable from the Ubuntu Software Centre if you have a wired connection).  The open-source b43 should work with your BCM4312 (see [http://linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43#Supported_devices) for a lot of info on b43).  In addition, you can take a look at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) for more info on the broadcom drivers.

Also, running ```
lspci -k
```

is a quick way to find out what modules you have loaded and which driver is in use.

---

### Post by Proxmty on 2012-03-20
Many thanks for your reply. As it happens, my wireless card ended up burning out on me! Was quite surprised by that, must have been all the playing around I was doing...but yeh, it wouldn't even work when I dual booted into windows so it was gone. I've since been using a usb which was quite unproblematic so even though I bought a new internal card I don't wanna rock the boat (for now). 

But will try what you've posted at some point so thanks again. BTW wired connection is something else, never worked in fact. But that's a different thread I guess.

---

### Post by ts3 on 2012-03-20
> **Proxmty said:**
> As it happens, my wireless card ended up burning out on me! Was quite surprised by that, must have been all the playing around I was doing

If that were the case mine would have burst into flames long ago.

> I've since been using a usb which was quite unproblematic so even though I bought a new internal card I don't wanna rock the boat (for now). But will try what you've posted at some point so thanks again. BTW wired connection is something else, never worked in fact. But that's a different thread I guess.

Glad you found a solution and yes, a new thread for the wired connection is probably best.  If you have a moment would you mind posting what usb wireless are you using?  Thanks and cheers :)

---

### Post by Proxmty on 2012-04-05
Sorry for the delayed reply (do you know if it's possible to set up some sort of notifications on this when you receive responses? I always miss them)

Yeh, sure. It's a NetgearN300 WNA3100. Was incredibly surprised by how easy it was to set up. Just took the inf file from the windows installer CD and stuck it in the Windows Wireless Drivers tool - worked first time - oh tell a lie, had to do rfkill, then it worked. Plus as a bonus because I'm running Mint I didn't have to bother with ndswrapper or whatever it's called. Though am sure it's not so hard even with that.

---

### Post by Proxmty on 2012-04-05
also, just in reference to the os version, as I said I'm on Mint now - but I get EXACTLY the same wifi card issues with ubuntu 11.10. Which Mint 12 is based on. I'm just not in to Unity. Think my puny CPU struggles with it.

---

