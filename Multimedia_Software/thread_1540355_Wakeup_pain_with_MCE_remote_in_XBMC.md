---
title: "Wakeup pain with MCE remote in XBMC"
date: 2010-07-27
forum: Multimedia Software
---

### Post by PrvSAT on 2010-07-27
Hello folks ;)

I hope very much that someone could help me out with my endless pain. ](*,)

I have made myself a HTPC and in January 2010 I have installed Ubuntu 9  and at that time I couldn't fix few issues so I switched in Windows.  Nevertheless, this was a pain and as such, this month I have reformated  the drive that hold only the OS and installed the Ubuntu 10.04. 

I have installed XBMC, LIRC and after days of readings I managed that it  suspends nicely after the set time, it works nice with the MCE remote,  including the Power button that suspends the system.

The problem and my biggest headache is that I can not make it to wake up from remote.
It wakes up from mouse and keyboard but not from remote.
I have followed few procedures found here in wiki.XBMC, ubuntu forums and other sources.

My current config shows:

The remote is Topseed Tech...
 
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1784:0008 TopSeed Technology Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 152d:2339 JMicron Technology Corp.
Bus 002 Device 005: ID 05ac:0220 Apple, Inc. Aluminum Keyboard
Bus 002 Device 004: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
and wake up devices are set in rc.local. I have enabled all USB  ports to make 
sure that other devices like mouse and keyboard wakes up  the computer.
```

```
Device    S-state      Status   Sysfs node
P0P2      S4     disabled  
P0P3      S4     disabled  
P0P1      S4     disabled  pci:0000:00:1e.0
UAR1      S4     disabled  pnp:00:0c
EUSB      S4     disabled  pci:0000:00:1d.7
USBE      S4     disabled  pci:0000:00:1a.7
P0P5      S4     disabled  
P0P6      S4     disabled  
P0P7      S4     disabled  
P0P8      S4     disabled  pci:0000:00:1c.4
P0P9      S4     disabled  pci:0000:00:1c.5
GBEC      S4     disabled  
USB0      S4     enabled   pci:0000:00:1d.0
USB1      S4     enabled   pci:0000:00:1d.1
USB2      S4     enabled   pci:0000:00:1d.2
USB3      S4     disabled  
USB4      S4     enabled   pci:0000:00:1a.0
USB5      S4     enabled   pci:0000:00:1a.1
USB6      S4     disabled  pci:0000:00:1a.2
P0P4      S4     disabled  pci:0000:00:1c.0 
```My current local.rc file:
 ```
echo USB6>/proc/acpi/wakeup
echo USB5>/proc/acpi/wakeup
echo USB4>/proc/acpi/wakeup
echo USB3>/proc/acpi/wakeup
echo USB2>/proc/acpi/wakeup
echo USB1>/proc/acpi/wakeup
echo USB0>/proc/acpi/wakeup
echo "rc.local has completed sucessfully." >> /tmp/resume.log
exit 0 
```
However, I have tried similar script in rc.local but with the same result, it will enable the USB but will not wake from MCEUSB
```
#Enable wakeup for the remote
status=`cat /proc/acpi/wakeup | grep "USB1" | awk {'print $3}'`
if [ "$status" = "disabled" ]; then
echo "USB1" > /proc/acpi/wakeup
fi 
#Enable wakeup for the remote
status=`cat /proc/acpi/wakeup | grep "USB0" | awk {'print $3}'`
if [ "$status" = "disabled" ]; then
echo "USB0" > /proc/acpi/wakeup
fi
exit 0 
```[I]

I have followed info and procedures step by step from:[/I]
     ```
http://lars.werner.no/?p=177
step by step info here too. This oone was the first attempt.
```

```
http://wiki.xbmc.org/index.php?title=Enable_Wake-On-Device
```          

```
http://wiki.xbmc.org/?title=Create_a_resume_script
Followed it step by step, installing curl, creating script.
```

```
http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake
This procedure is incomplete and not clear. It was made for ubuntu 9 and
PolicyKit folder does not exist in ubuntu 10.04
```

```
http://forum.xbmc.org/showthread.php?p=480705
```

I am just exhausted and very upset that everything works but not the wakeup. I have tried different USB  ports but it is still the same. The IR receiver works fine since it  works flawless in XBMC and it did wake the computer in windows. I have  come too far with the setup to quit now. Could anyone please advise me? 

System config:
MB: Asus P5G43T-M PRO
Intel Dual Core @2.8GHz
2Gb DDR3
Video: Intel GMA X4500 on board

Thank you for reading this.

---

### Post by PrvSAT on 2010-07-31
Could anyone please give some direction what to do? Perhaps the message above it too long to be read. 

In short, everything is working fine, the remote (IR02BK) works nicely with XBMC but it does NOT wakeup the system from standby. The mouse, keyboard wakeup the system just fine.
All USB's are ENABLED by "echo USB#>/proc/acpi/wakeup" in local.rc file.
I have followed the three procedures that I could find regarding this issue but with no success. Please help. :(

---

### Post by PrvSAT on 2010-08-04
I really wish to become a ubuntu fan but for some reason I get no advice whatsoever. ;)
Should I buy "official" support?

---

### Post by lostincable on 2010-08-08
Hi there, can you run this command and post back the output?
 
```
 
uname -r -v

```
 
Thanks!

---

