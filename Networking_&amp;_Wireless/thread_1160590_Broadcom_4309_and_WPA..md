---
title: "Broadcom 4309 and WPA."
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by t0mppa on 2009-05-15
Well, long story short: setting up linux for a friend and ran into some trouble with the wlan chip.

Running Kubuntu 9.04 and 02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02). Set it up to work through NDISWrapper, since fwcutter refused to cooperate. It only manages to get a connection through an unsecured network; maybe WEP too, but from what I've read, there ain't much of a difference between the two.

WPA just plain refuses to work. Tried installing WICD and it connects unsecured lightning fast (as compared to the minute of waiting with network manager), but refuses just as quick when I change my router to use WPA. Also tried setting things up from command line with the help of [this thread]("http://ubuntuforums.org/showthread.php?t=571188"), but that just kept saying "Authentication with <MAC address> timed out.". So, starting to run out of ideas here. I guess I could leave it at this, since it IS illegal over here to use other peoples open wireless networks without their consent, but I hate leaving things halfway done and that's a little annoying to keep watch over day after day.

Another problem is that every reboot puts b43-pci-bridge (driver associated with ssb module) in control of the wireless and I always need to manually unload the ssb module and re-enable NDISWrapper, even though ssb is blacklisted and NDISWrapper is listed in /etc/modules. A minor inconvenience, but just in case someone knows how to fix that.

I'd really appreciate some help on how to get the WPA up and running though.

EDIT: Eventually NDISWrapper started producing kernel panics and thus freezing my system, so I removed it and went with the b43 + FWcutter route and now things are just peachy.

---

### Post by t0mppa on 2009-05-18
Bump.

I knew I should've at least bashed Ubuntu and claimed Vista is superior to it to get some replies out of the folks here. :)

---

### Post by Ironweaver on 2009-06-06
Hello,

My setup sounds quite a bit similar to yours.  Like you, I've been able to connect wireless to unsecured networks using b43-fwcutter, but not to anything using WPA/WPA2.  Apologies in advance, I'm very new to Linux.  If I've read your post correctly, you've managed to get WPA or WPA2 working with this wireless card, and I'm interested to know the steps.

From clean install, not doing anything but the basic system updates, it appears the installation thinks it can connect wirelessly, but in attempting to connect the Network Manager returns the statement "Disconnected, you are now offline".  When attempting to connect wirelessly, the ethernet cable is unplugged from the laptop.

Details on my setup:
System: Dell Inspiron 5100
OS: Jaunty (Ubuntu 9.04)
Installed card & chipset(lspci -nn):
02:02.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 02)
Home wireless network setup:
 -- SSID not broadcast
 -- Security WPA/WPA2 mixed
 -- 802.11 n/b/g mixed

---

### Post by t0mppa on 2009-06-07
Yes, with b43legacy there's been no trouble with it and it connects to WPA and WPA2. Check if you're using b43 or b43legacy, can do that by running **dmesg | grep b43** from terminal.

Jaunty had b43 as default driver, but that failed for me (probably wrong version of the firmware) and picking the proprietary driver from Hardware Drivers also refused to install, so I had to set it up the hard way. [Here]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy")'s a page with good instructions that I used to install the firmware. The wgets are HTTP requests from the terminal, so you'll need either Internet access through wired or then to DL them on another computer and copy the files over. And /lib/firmware worked just fine as the firmware directory for Ubuntu.

---

### Post by johnnydopefish on 2009-06-26
> **t0mppa said:**
> 
Another problem is that every reboot puts b43-pci-bridge (driver associated with ssb module) in control of the wireless and I always need to manually unload the ssb module and re-enable NDISWrapper, even though ssb is blacklisted and NDISWrapper is listed in /etc/modules. A minor inconvenience, but just in case someone knows how to fix that.

That might be related to [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558") bug.

---

