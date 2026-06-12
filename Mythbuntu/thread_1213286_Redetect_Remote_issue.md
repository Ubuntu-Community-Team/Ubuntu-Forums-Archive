---
title: "Redetect Remote issue?"
date: 2009-07-14
forum: Mythbuntu
---

### Post by AquaNature on 2009-07-14
Hello everyone!

The times that I restart my computer, mythtv automatically starts up and I can control it with a usb keyboard.  The problem is my usb remote doesn't work until I exit mythtv frontend (which was autostarted), then unplug the usb remote receiver, plug it in, and then run the frontend again.  Then the remote will work perfectly after that. 

I thought it was just the frontend, so I exited that and ran it again, but it still won't pick it up until I unplug/plug the receiver.

Any ideas?

Thanks for your time! :D

---

### Post by ds_pablo on 2009-07-14
This sounds as though the usb device is not actually being recognized when you first reboot.  Try running lsusb after a fresh reboot, prior to unplugging and replugging in the device and see if it is seen at all.

---

### Post by AquaNature on 2009-07-15
You're right, ds_pablo. I did lsusb before and after. Before I restarted, when the remote was working, this device was listed:

Bus 002 Device 007: ID 0471:060c Philips 

But when I restart, it's no longer listed there. So it doesn't recognize it when it first starts. So is there a way to manually put it in so it doesn't have to search or detect it? 

I'm familiar with having the hard drives mounted in /etc/fstab is this a similar solution?

---

