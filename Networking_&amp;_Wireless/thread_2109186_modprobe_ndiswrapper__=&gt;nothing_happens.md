---
title: "modprobe ndiswrapper  =&gt;nothing happens"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by Spaceracer1212 on 2013-01-26
Hey guys, I am a beginner with ubuntu and I have just started to use this operating system a couple days ago.   I am having a very hard problem with installing this wna3100 wireless adapter through ndiswrapper. I have installed ndiswrapper and the wireless adapter driver through it, but still it doesn't seem to work.   iwconfig doesn't show wlan0 modprobe ndiswrapper/ sudo modprobe ndiswrapper doesn't give me any results.   ndiswrapper -l : tells me that the driver is installed and the device is present.  I am currently running gnome, 32-bit. I have been scouring the searches for the past three days and that has left me at this point. If there is any knowledge out there for me I would greatly appreciate it.

---

### Post by Spaceracer1212 on 2013-01-26
also the command: lshw -C Network gives me : PCI (Sysfs) for a couple seconds, then becomes :SCSI  and does nothing else

---

### Post by Spaceracer1212 on 2013-01-26
actually with lshw -C Network, no wireless interfaces are recognized, only eh0 and eth1, similar to iwconfig.  odd that some commands recognize my wireless adapter like: ndiswrapper -l, and lsusb

---

### Post by nanders on 2013-04-26
I experience this same problem. Worked perfectly in Ubuntu 12.04 (actually Mint 13), and just switched to 13.04 (X86) and "sudo modprobe ndiswrapper" gets stuck and keeps blinking.
Using ndiswrapper from the repository (1.58), trying to install my [SITECOM N300 wireless adapter]("http://www.sitecom.com/en/wi-fi-usb-adapter-n300/wla-2102/p/1567") using the WinXP drivers

```
ndiswrapper -l
```gives:```
netrtwlanu : driver installed
    device (0DF6:0070) present
```So it seems like its properly installed. 

Anyone solved this yet?
Thanks



EDIT: Oh woops, two reboots and it worked. (shame)

---

