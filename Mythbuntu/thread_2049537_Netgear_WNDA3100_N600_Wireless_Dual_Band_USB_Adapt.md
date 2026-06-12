---
title: "Netgear WNDA3100 N600 Wireless Dual Band USB Adaptor"
date: 2012-08-28
forum: Mythbuntu
---

### Post by kamodan on 2012-08-28
Hey everyone, 
     First time poster here. I just finished building my first HTPC for my home. I'm looking to run it off of wireless, as I have no way to pull ethernet and don't want a cable running the length of my living room.
    I have the wireless USB adaptor as mentioned in the post, but no optical drive as of yet. In searching for a way to get the driver installed for this so I could get wireless access, I ran across this page: [http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html](http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html). Following the instructions there, I've run into a road block. The first driver doesn't work at all, which he mentions there. However, the second driver gives a similar error stating: "*FATAL: Module ndiswrapper not found*. Is the ndiswrapper module installed?" However, after clicking ok to this, the little computer with wrench and screwdriver shows up and it says Hardware present: no. And it is able to detect when I plug in the device, but there's no way to connect to a network.
I've ensured that the wrapper is installed, I've reinstalled it several times and it still produces this same error. I have the driver installed somewhere on my laptop, a Windows 7 machine, and I'm currently going to try a transfer. But if anyone else has any advice or knows why this might not be working, I'd greatly appreciate it!

---

### Post by klc5555 on 2012-08-30
> **kamodan said:**
> Hey everyone, 
     First time poster here. I just finished building my first HTPC for my home. I'm looking to run it off of wireless, as I have no way to pull ethernet and don't want a cable running the length of my living room.
    I have the wireless USB adaptor as mentioned in the post, but no optical drive as of yet. In searching for a way to get the driver installed for this so I could get wireless access, I ran across this page: [http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html](http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html). Following the instructions there, I've run into a road block. The first driver doesn't work at all, which he mentions there. However, the second driver gives a similar error stating: "*FATAL: Module ndiswrapper not found*. Is the ndiswrapper module installed?" However, after clicking ok to this, the little computer with wrench and screwdriver shows up and it says Hardware present: no. And it is able to detect when I plug in the device, but there's no way to connect to a network.
I've ensured that the wrapper is installed, I've reinstalled it several times and it still produces this same error. I have the driver installed somewhere on my laptop, a Windows 7 machine, and I'm currently going to try a transfer. But if anyone else has any advice or knows why this might not be working, I'd greatly appreciate it!

Not really the forum for this thread, which probably ought to go under "networking and wireless".

However, it is possible that the actual ndiswrapper module didn't get installed in the directory structure under /lib/modules/... when the installation routine happened, or, if the module is actually there somewhere, that depmod hasn't run yet after the module was installed to make it known and available for loading by modprobe.

You could check whether the module is present somewhere under /lib/modules/... You could then run depmod yourself from a prompt to make sure the module has been added to the kernel module dependencies and will be findable by modprobe:```
sudo depmod
```You could then see if the module can be loaded by hand by ```
sudo modprobe ndiswrapper
``` and see whether it has loaded by ```
lsmod
```which will list all loaded modules. It may all then work after a reboot brings up networking upstart scripts and loads drivers. 

Or, alternatively, this may be a manifestation of a known error with some workarounds available. See: [http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found)

In general, ndiswrapper is a really awful kluge, allowing an adapter without native Linux support use Windows drivers. Even when it works it's never as fast or as stable as native Linux drivers are. In the long term, an adapter with good native Linux driver support might be the best option.

---

### Post by kamodan on 2012-09-02
Thanks a lot! It looks like that fixed it! And sorry about posting in the wrong section, I'll make sure I post more carefully next time. And like I said, I'm still learning so I'm sure I'll be doing A LOT more research before I go out and just buy a network adapter. Thanks again!

---

