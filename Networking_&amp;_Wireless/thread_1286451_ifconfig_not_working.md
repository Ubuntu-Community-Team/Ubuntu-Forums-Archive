---
title: "ifconfig not working"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by klouchis on 2009-10-09
When I try to activate my link 5100 intel wireless card with sudo ifconfig wlan0 up I get this.

> 
kevin@kevin-EE:~$ sudo ifconfig wmaster0 up
SIOCSIFFLAGS: Operation not supported
here is my output of lshw -C network

> 
 *-network DISABLED      
       description: Wireless interface
       product: WiMAX/WiFi Link 5050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:eb:0f:a1:bc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn



Any one have any ideas I can try to get this resolved?

Thanks,
Kevin

---

### Post by PrePenguin on 2009-10-09
Try disabling lan in Bios and enabling the wireless for eth0..

---

### Post by klouchis on 2009-10-09
> **PrePenguin said:**
> Try disabling lan in Bios and enabling the wireless for eth0..

that didn't help, only wireless can be disabled from my bios, but thanks for helping anyways.

---

### Post by PrePenguin on 2009-10-09
All lans can be disabled in the bios if its a onboard and if its enabled it will prevent your wireless card from being used it will conflick.

---

### Post by klouchis on 2009-10-09
I triple checked my bios setup and couldn't find a way to disable anything other then an option to disable wireless lan, i tried sudo ifconf eth0 down to prevent conflicting network devices, but nothing changed when trying to enable my wireless...I feel like it's an issue with the firmware, so I'll keep searching around with regards to that.

---

### Post by t0mppa on 2009-10-09
Disabling your wired interface won't make the wireless eth0. The wireless stack used by the OP's drivers is requesting the logical names wlan & wmaster from the udev and only if you force udev to overwrite those, they will be used. And neither does the wired interface conflict with the wireless, both can be enabled and even used (depending on the software you run them on) simultaneously.

Try running **sudo ifconfig wlan0 up** instead. Wmaster0 is a master device created and solely used by the mac80211 wireless stack and only visible on the current kernels that Ubuntu is using, it should for all purposes be ignored by the user. The wlan0 is the one that concerns the user.

Alternatively, if you're on a laptop, you could just have accidentally switched the wireless off either through a button or a key combination (usually Fn + F5).

---

### Post by klouchis on 2009-10-09
Wireless switch is on and I've tried sudo ifconfig wlan0 up as well too, it yields the same results as with wmaster0

---

### Post by t0mppa on 2009-10-09
Well then, it is probably an IRQ conflict and I see what PrePenguin meant, if you've had it work before, the wired interface shouldn't be a problem though. Anyway, try shutting down and starting (as opposed to mere restarting), to see if settles the issue in a simpler way.

EDIT: Did some further Googling and it seems like the SIOCSIFFLAGS errors for Intel wifi chips can also be caused by the firmware malfunctioning or missing, which should also show up on dmesg, so that's one thing to check.

---

### Post by klouchis on 2009-10-09
I've never had the wireless working on the machine before, I've only had it 3 days now.  It seems like everyone with my wireless device is having lots of difficulty getting it to work and the interference may be coming from WiMAX wireless that the card also provides, I'm going to try disabling the WiMAX to see if the WiFi will work.

---

### Post by t0mppa on 2009-10-09
Ah, looks like I was little slow with the edit.

---

### Post by klouchis on 2009-10-09
Thanks for the find, my gut was telling me it was the firmware, I added what I thought was the correct firmware but I'll double check the file and folder it's in the morning.  I need some sleep for now.

Being an electrical engineer can be frustrating sometimes, sure I can build a wireless device, but getting them to work is so much harder...

---

