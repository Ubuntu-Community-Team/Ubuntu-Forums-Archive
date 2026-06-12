---
title: "USB Wireless Card, No Connection"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by ooboontwo on 2010-10-17
EDIT: Having exact same problem as this guy: [http://ubuntuforums.org/showthread.php?t=1440864](http://ubuntuforums.org/showthread.php?t=1440864)

He has given up and is buying a new adapter. I'd like to stick it out and try and fix this.

**When I load the Windows XP 64 bit drivers ndiswrapper freaks everything out. The GUI won't respond and I get the same exact errors as the guy in the thread above. I have tried Win7, Win2k and Vista drivers for 64 bit. None work, I get the "couldn't load driver" error in tail /var/log/messages...**

Hello,

I am new to Ubuntu but quite familiar with computers / hardware / networking in general. Nevertheless, I have searched and tried many different things in order to get my wireless USB device to work in Ubuntu but to no avail.

Here are the details:

OS Version: Ubuntu 10.04 (Lucid) installed with WUBI.
Processor: AMD 64 Bit Dual-Core @ 2.6 Ghz
Memory: 2 GB
Wireless Device: Fry's FR-54USB, Realtek 8192su chipset

PLEASE NOTE: I have seen and attempted the fix from this thread: [http://ubuntuforums.org/showthread.php?t=1491058](http://ubuntuforums.org/showthread.php?t=1491058)

Ndis is properly installed, along with the appropriate driver. Also, Ndis shows that the device is connected.

lsusb shows that the device is being recognized as a "D-Link Systems" device.

However, wlan0 never shows up anywhere (is this the proper term?) and network manager doesn't even have the option to "Enable Wireless".

I am, of course, new to terminal commands so I don't know what else to try. Most of what I have attempted was using the GUI.

What should I try next?

Also, I didn't ask Ubuntu to install a 64 bit version of the operating system; does it do this automatically or something? I am running dual-boot with Windows Vista 32 Bit. Could this be a part of the problem? Or is it that Ubuntu / Linux doesn't have separate 32/64 bit operating systems like Windows but just goes with the highest support of one's processor? (In my case, 64 bit.)

Thanks for the help.

Cheers,
Cody

---

### Post by ooboontwo on 2010-10-18
More information and a bump:

tail /var/log/messages shows:

loadndisdriver: load_driver(358): couldn't load driver net8192su

But ndiswrapper - l shows: Driver Installed, Device Present

Hope this info helps.

---

### Post by ooboontwo on 2010-10-19
:confused: Bump. Help a brother out?

I do not have any new ideas... but would like to get Ubuntu working with internet sometime soon.

Cheers,
Cody

---

### Post by ooboontwo on 2010-10-20
Any thoughts at all to get this working?

---

### Post by mojo6911 on 2011-03-05
Same problems here. You get it fixed?

---

### Post by ooboontwo on 2011-03-24
Never fixed this problem. Shame. I don't know how to code my own driver, so I guess I just have to go without wireless internet.

---

