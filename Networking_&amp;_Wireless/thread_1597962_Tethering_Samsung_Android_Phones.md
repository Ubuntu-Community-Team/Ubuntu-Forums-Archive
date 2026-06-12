---
title: "Tethering Samsung Android Phones"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by warstoke on 2010-10-15
i have the samsung intercept and want to be able to tether using easy tether pro 
it world perfectly on windows but i cant find samsung adp drivers for ubuntu 
currently running ubuntu LL but im willing to reinstall with 10.10 if that will do it out of the box

---

### Post by bobpaul on 2010-11-20
This isn't merely a tethering issue, but a USB issue period. Samsung's USB is doing something weird on connection that linux's usb stack doesn't like. Here's what dmesg showed when I plugged mine in:

```
[976909.108060] usb 1-1: new high speed USB device using ehci_hcd and address 111
[976909.232054] usb 1-1: device descriptor read/64, error -71
[976909.460050] usb 1-1: device descriptor read/64, error -71
[976909.676065] usb 1-1: new high speed USB device using ehci_hcd and address 112
[976909.800046] usb 1-1: device descriptor read/64, error -71
[976910.028055] usb 1-1: device descriptor read/64, error -71
[976910.244063] usb 1-1: new high speed USB device using ehci_hcd and address 113
[976910.575171] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[976920.652054] usb 1-1: device not accepting address 113, error -110
[976920.764049] usb 1-1: new high speed USB device using ehci_hcd and address 114

```

and lsusb shows bupkis:

```
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 004 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

If we can get usb working then USB Mass Storage will work and adb should work as well (and then your tethering). I haven't had this problem with other android phones, so I don't get why this one is "windows only".

---

### Post by jdp on 2011-01-17
My Intercept would not connect to my Ubuntu machines until I finally tried it on a Windows machine. Since that one time it's been working as it should unless I cancel the USB Connect Mode on the phone, then it starts throwing the errors again.

---

### Post by bobpaul on 2011-01-17
> **jdp said:**
> My Intercept would not connect to my Ubuntu machines until I finally tried it on a Windows machine. Since that one time it's been working as it should unless I cancel the USB Connect Mode on the phone, then it starts throwing the errors again.

Oh, excellent! Now it's working. To clarify, where is this "USB Connect Mode" that I should avoid canceling? I've been able to disable and re-enable Settings->Applications->Debugging->USB Debug Mode, and I've been able to click "Turn Off USB storage" after unmounting without causing problems. Heck, it even seems to persist a reboot.

I don't understand. I've had this connected multiple times to both WinXP and Win Vista at work, but before today, it's never worked on Ubuntu.

It would be nice to have a clear: "Steps to Make it Work" and "Steps to Break it Again".

---

