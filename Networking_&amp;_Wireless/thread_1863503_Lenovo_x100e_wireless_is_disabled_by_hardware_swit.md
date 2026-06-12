---
title: "Lenovo x100e wireless is disabled by hardware switch"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by funcrusher on 2011-10-17
Hi, relatively new convert  here - my Lenovo x100e Win7 install failed to boot one too many times, and I (somewhat rashly...) decided to wipe the whole thing and install Ubuntu 11.10 instead.

Now almost everything is working perfectly. Except the wifi. In the status bar I see a message saying "wireless is disabled by hardware switch".

rfkill list tells me the same thing:

```
$ rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```My hardware details:
```
$ lspci | grep Wireless
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:9f:91:64  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```I've read around and tried various things, including installing the proprietary drivers mentioned [here]("http://http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II") and [here]("http://justinsomnia.org/2010/02/ubuntu-on-a-lenovo-thinkpad-x100e/"), but this has no effect on the hardware block message. I'm inclined to believe that the adapter really is currently turned off by a hardware lock rather than it being a straightforward driver issue, even though it is enabled in the BIOS.

Now that all seems fine, but here's where I'm really stuck: in Windows, the wifi is normally controlled by Fn+F5, but of course this does nothing in Ubuntu. If I was dual-booting then this would be fine - I'd just boot into Win7 and turn on the wifi using the hotkeys. Unfortunately, as I mentioned earlier I wiped over my Win7 install so I can't do this.

Any thoughts?

---

### Post by funcrusher on 2011-10-24
Well I finally have the Realtek RTL8191SE wireless adaptor working in 11.10 but in the end I had to temporarily reinstall Win7 in order to remove the hardware lock. If anyone else is having this problem, here's what I did to fix it:

[LIST]
[*]Ripped the .iso from a Windows 7 Ultimate 32bit (Student upgrade) DVD I had lying around.
[*]Created bootable installation media using [WinToFlash]("http://wintoflash.com/home/en/") and installed it.
[*]Installed and ran [Lenovo System Update]("http://support.lenovo.com/en_US/downloads/detail.page?LegacyDocID=MIGR-73695") to get OEM drivers. At this point Windows would always hang on a black screen whenever I tried to install the Realtek drivers.
[*]Reflashed the BIOS with the latest version (11.32), rebooted and tried installing the Realtek driver again, this time it succeeded and WiFi was working in windows.
[*]Did a clean install of Ubuntu 11.10, Wifi worked straight out of the box.
[/LIST]
Moral of the story: NEVER wipe your Windows installation before you're SURE that you have all of your drivers working with the distro livedisk!

---

