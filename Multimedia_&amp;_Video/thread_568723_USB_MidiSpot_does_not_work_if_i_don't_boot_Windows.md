---
title: "USB MidiSpot does not work if i don't boot Windows first"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by 0x656b694d on 2007-10-06
Hello,

I have a midi-keyboard that is connected via USB Midisport adapter.
There are two light indicators on the adapter. When i boot Windows i see they are on, but if i boot linux (first) &#8212; they're not.
If i just reboot my computer from Windows to linux, the adapter works and i see my keyboard in the devices, and it works.

Here is what lsusb says:
```

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0763:1010 Midiman Midisport 1x1
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0424:2504 Standard Microsystems Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```
plugging off and on doesn't solve the problem.

how do i fix this?

Thanks!

-Mike

---

### Post by tbfr on 2007-10-06
Many Midisport devices require a firmware to be loaded onto the device before you can use them. The windows driver is taking care of this.

It's possible to configure Linux to upload the firmware, just search the forums.

---

### Post by 0x656b694d on 2007-10-07
yes, i've read it.
They recommend to upload the firmware on the mapped device.
But my problem is that the device is not mapped on /proc/bus/usb/003/004.
So i cannot upload anything.

---

### Post by tbfr on 2007-10-08
If your device is still at Bus 003 Device 004, do you have an entry /dev/bus/usb/003/004?

Your command to load the firmware should look something like
```
sudo fxload -I /lib/firmware/maudio/MidiSport1x1.ihx -D /dev/bus/usb/003/004
```

---

### Post by 0x656b694d on 2007-10-08
It works, thanks!

I have to turn on the keyboard to get indicators lights. On Windows it lights with the keyboard turned off.

Thanks!

---

