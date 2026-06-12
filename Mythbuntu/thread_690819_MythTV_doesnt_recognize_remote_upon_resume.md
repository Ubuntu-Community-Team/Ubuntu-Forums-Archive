---
title: "MythTV doesnt recognize remote upon resume"
date: 2008-02-07
forum: Mythbuntu
---

### Post by yankcrime on 2008-02-07
This title is really better for this question than the last.
I have two questions.  The other is at[http://ubuntuforums.org/showthread.php?t=690815](http://ubuntuforums.org/showthread.php?t=690815).
After wakeup from hibernate or suspend, there is no reaction of MythTV to my remote commands (mceusb2).  lirc seems to work (irw returns results when remote buttons are pressed).  I originally thought that it was because I was unloading the lirc modules while mythtv was still running.  I made sure this didnt happen by the following line in /etc/default/acpi-support:
```
MODULES_WHITELIST="lirc_mceusb2 lirc_dev usbcore"
```
I can't think of any other reason, and while some others report the problem, I can't tell that there has been a reported solution.
The only work-around I can think of is to shutdown mythtv upon suspend and resume would load it again.   It is a bit of an ugly hack, but it just might work.
Thanks for any shedded insight.
To be clear, the remote worked flawlessly before suspend.

---

### Post by foxbuntu on 2008-02-21
Your soultion is about the only I have run across. The issue is that once mythfrontend looses communication with lirc, the only way to get it to return is by restarting mythfrontend.

---

### Post by john.ennew on 2008-07-06
My problem is worse than yours I think. Restarting MythTV frontend after resume from suspend isn't enough and the remote still does not work (despite working flawlessly before suspend).

I took some outputs to see if anyone can diagnose what is happening: 

On first boot:

```

ls -all /dev/input/by-path

total 0
drwxr-xr-x 2 root root  80 2008-07-06 21:23 .
drwxr-xr-x 3 root root 200 2008-07-06 21:23 ..
lrwxrwxrwx 1 root root   9 2008-07-06 21:23 pci-10-1--event-ir -> ../event4
lrwxrwxrwx 1 root root   9 2008-07-06 21:23 platform-pcspkr-event-spkr -> ../event1


```

```


cat /proc/bus/input/devices

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=2040 Product=9950 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:02:05.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:02:05.2/usb10/10-1/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=14afc336 284284d00000000 0 480058000 219040000801 9e96c000000000 90020000000ffd


```

After Resume from Suspend:
```

ls -all /dev/input/by-path

total 0
drwxr-xr-x 2 root root  60 2008-07-06 21:29 .
drwxr-xr-x 3 root root 180 2008-07-06 21:29 ..
lrwxrwxrwx 1 root root   9 2008-07-06 21:23 platform-pcspkr-event-spkr -> ../event1
```

```
cat /proc/bus/input/devices

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=40001
B: SND=6


```

It looks like the ir receiver has vanished from the system.

The remote and the IR receiver are part of a Hauppauge Nova-T PCI 500 DVB-T card.

Any help greatly appreciated!

Thanks,
John

---

### Post by sebrock on 2008-07-17
I have the same thing with my imon pad remote. I need to restart the frontend in order to get the remote back. Kinda sucks actually. Is there no other way to just make the frontend reconnect to lirc upon resume without restart?

---

