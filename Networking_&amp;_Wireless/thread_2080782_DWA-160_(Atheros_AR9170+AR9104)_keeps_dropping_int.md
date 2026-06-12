---
title: "DWA-160 (Atheros AR9170+AR9104) keeps dropping internet. (Ubuntu 12.10 64-bit)"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by cmp1988 on 2012-11-05
After about a couple minutes of being turned on, the internet connection drops out on this card.  It still tells me that I'm connected to the wireless network, but I get no internet whatsoever.  I have to unplug it and plug it back in (or rmmod carl9170, modprobe carl9170) to get it back on.  This tends to happen more when I'm doing stuff that uses a fair bit of bandwidth (downloading files, streaming video).

lsusb
```

Bus 001 Device 003: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 004: ID 07d1:3a09 D-Link System DWA-160 802.11abgn Xtreme N Dual Band Adapter(rev.A2) [Atheros AR9170+AR9104]
Bus 004 Device 002: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 005 Device 002: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```

iwconfig
```

wlan1     IEEE 802.11abgn  ESSID:"Nett1"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:23:69:AE:E5:4A   
          Bit Rate=39 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2109  Invalid misc:33   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

```

Any ideas?  I bought this card hoping it would work, considering ThinkPenguin sells wifi cards with the AR9170 chipset.


Edit:  I can get this thing going fine with ndiswrapper, but I'd prefer to use the native driver if possible.

---

### Post by varunendra on 2012-11-06
carl9170 is the correct driver for AR9170 chip. If you wish to try it with some tweakings, you'll have to 'completely' remove ndiswarpper first :
[How to Uninstall Ndiswrapper]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Uninstall_HowTo")
Then you may try :
```
sudo modprobe -rfv carl9170
sudo modprobe -v carl9170 nohwcrypt=Y
```

However, as per [linuxwireless.org]("http://linuxwireless.org/en/users/Drivers/carl9170") :
> It's worth mentioning that the chip was designed, produced and sold in the early 802.11n-draft period. Compatibility will always be an issue. A [known problem]("http://git.kernel.org/?p=linux/kernel/git/chr/carl9170fw.git;a=commitdiff;h=39be7dc384e0dd45dc36b4b517fd9fae874b06f0") is that hardware can not support [frame aggregation]("http://en.wikipedia.org/wiki/IEEE_802.11n-2009#Frame_aggregation") and [QoS]("http://en.wikipedia.org/wiki/Wireless_Multimedia_Extensions") at the same time, meaning the device is not suitable for any serious 802.11n setup. Also  the hardware crypto has some serious trouble with  encrypting/deciphering at high throughput, therefore if possible use  'nohwcrypt=1' as a workaround.

Accordingly, you may also wish to disable 'N' channel in your router if available.

---

### Post by cmp1988 on 2012-11-11
That stuff at the top didn't work out.  However, disabling "N" on the router seemed to do the trick.  The internet is intermittent, but doesn't completely stop now.  Thanks for your help with this.

---

### Post by varunendra on 2012-11-12
You're welcome :)

As a valuable feedback to let us have a peek at the current situation, please run and post back the outputs of the following (when the network speed drops or apparently disconnects) -
```
ifconfig
iwconfig
lsusb
usb-devices | grep -iB2 -A8 3a09
lsmod
dmesg | tail -20
```
Hopefully, it may also give us a clue about the intermittent behaviour so we can further improve it.

---

