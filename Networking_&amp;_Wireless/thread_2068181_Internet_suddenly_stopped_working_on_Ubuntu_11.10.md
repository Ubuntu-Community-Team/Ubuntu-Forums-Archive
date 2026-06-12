---
title: "Internet suddenly stopped working on Ubuntu 11.10"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by fallfallfall on 2012-10-08
I have been using NoMachine to connect to a Linux box in my lab running Ubuntu 11.10. I was connected and running a program when the Linux machine crashed. When I restarted the machine manually, it wouldn't connect to the Internet. It doesn't recognize the ethernet cable that is plugged in--it says "No network connections available" in the network menu, I tried pinging 8.8.8.8 and it didn't work, and when I try to reload the networking settings via command line it says "Failed to bring up eth0". It is set to have a static IP address.

I didn't change any settings before it crashed, I didn't install any updates recently, and I made sure that it wasn't just the cable failing. I'm not sure what made the internet suddenly stop working, or how to fix it. Does anyone have any ideas? Is there any more information I need to provide to be helpful?

Thanks in advance!

---

### Post by varunendra on 2012-10-11
Welcome to the forums fall..(oh my god)!:)
> **fallfallfall said:**
> Is there any more information I need to provide to be helpful?
Yes, please post the outputs of:
```
ifconfig -a
sudo lshw -C network
lsmod
```
Please wrap the output codes in [ code]..and..[ /code] tags using the **#** symbol at the top of the edit box.

PS:
As a side note, if you can, I'd suggest to upgrade to 12.04. Be aware though that the default upgrading procedure is not always successful, so a 'clean' installation > then transfer your data and settings is the recommended way to upgrade. (or backup your installation before trying to upgrade, just in case..).

---

