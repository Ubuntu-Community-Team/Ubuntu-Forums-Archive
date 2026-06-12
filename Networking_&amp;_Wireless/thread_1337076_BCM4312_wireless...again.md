---
title: "BCM4312 wireless...again"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by porchrat on 2009-11-25
Hi all it has been a while since I last posted here.

Having issues getting a Broadcom card running on 9.10. Normally under these circumstances I would just resort to ndiswrapper but I am struggling to locate the XP drivers for this module ATM and honestly it looks to me like the card's drivers are at least partially functional and it would be nice to see them working instead of ndiswrapper.

When I run "lshw -C network" I get this:

```
*-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth2
       version: 01
       serial: 00:21:00:bd:82:ce
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d2000000-d2003fff
```

Then when I run ifconfig I have an "eth2" device which is in fact the wifi card. When I run "iwlist scan" it does actually pick up my access point, however I just can't get it to associate. In fact when I look at the logs on the access point I can see the bloody thing attempting to associate but for some reason it never establishes a connection.

These sort of things tell me that the driver is at least partially (if not completely) functional.

When I left-click on the network manager icon in the top right corner of the Desktop it tells me wireless is disabled and the wireless options are greyed out. Which is strange considering it can still scan, detect the access point and show up in the access point's logs.

Additionally: The wireless drivers do indeed show up under "Hardware Drivers" and are enabled.

Any ideas for debugging would be most appreciated.

---

### Post by howcanireachthesekids on 2009-11-26
I have the same card and could not get it working in Ubuntu 9.10 :( hope someone gives some worthy help

---

### Post by coffeeaddict22 on 2009-11-26
Hi,
can you both post the output of ```
nm-tool
```
I've got a 4312 card working without any problems; the Broadcom Driver seems to work well for me at least.

---

### Post by georg.65 on 2009-11-26
> **coffeeaddict22 said:**
> Hi,
can you both post the output of ```
nm-tool
```I've got a 4312 card working without any problems; the Broadcom Driver seems to work well for me at least.

I've some problems too with b43 driver don't like to work, the Broadcom Driver (wl) works ok, but for kismet I'll need the b43.


Here my post:

orion@orion-laptop:~$ lspci -vnn | grep 14e4
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
orion@orion-laptop:~$ nm-tool

NetworkManager Tool

State: connected


** (process:3143): WARNING **: Tried to set deprecated property gsm/band
- Device: eth2  [Auto Big C Supercenter WiFi] ----------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        00:21:00:D8:BD:56

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    8140018:         Infra, 00:1A:70:33:2B:69, Freq 2442 MHz, Rate 0 Mb/s, Strength 20 WEP
    S259:            Ad-Hoc, 16:25:38:B4:EE:F9, Freq 2442 MHz, Rate 11 Mb/s, Strength 20 WEP
    8140018:         Infra, 00:1A:70:33:29:FB, Freq 2422 MHz, Rate 11 Mb/s, Strength 40 WEP
    SpiderHotspot   077-960871: Infra, 00:22:6B:7F:FE:8C, Freq 2417 MHz, Rate 54 Mb/s, Strength 20
    *Big C Supercenter WiFi: Infra, 00:13:F7:8D:50:F4, Freq 2462 MHz, Rate 54 Mb/s, Strength 255
    SpiderHotspot@SE-ED big C SAMUI: Infra, 00:22:6B:8C:51:67, Freq 2442 MHz, Rate 54 Mb/s, Strength 20
    8140018:         Infra, 00:1A:70:33:2A:BE, Freq 2462 MHz, Rate 11 Mb/s, Strength 20 WEP
    8140018:         Infra, 00:1A:70:33:2A:D3, Freq 2462 MHz, Rate 11 Mb/s, Strength 40 WEP

  IPv4 Settings:
    Address:         192.168.2.151
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:23:5A:45:17:A4

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


b43-fwcutter is installed but the driver don't like to work (no wlan0), thanks for help

---

### Post by ublintu on 2009-11-26
Hi, 
Did you try to install it like in here (the first post, NO ndiswrapper): [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
I have broadcom as well

---

### Post by justyellowboy on 2009-11-27
I've done most of these steps for my 4312 card, but I can't seem to Activate my drivers. It tries to download and install them, which makes zero sense. Is there any other way to manually install these offline?

---

### Post by snowpine on 2009-11-27
Connect to a wired network

System, Administration, Hardware Drivers

Choose "Broadcom STA"

Enjoy!

---

### Post by justyellowboy on 2009-11-27
Thanks for responding, Snowpine. Well, yes, I can choose it, but when I do, it starts attempting to install it, but it says that it is downloading (like, from the internet? Or what does it mean?), and regardless of the source of where it downloads from, the installation kind of "lags out," or something. It makes zero progress and it doesn't close, so I have to basically force in a non-clean restart. I'm wondering if I'm forgetting something.

---

### Post by snowpine on 2009-11-27
> **justyellowboy said:**
> Thanks for responding, Snowpine. Well, yes, I can choose it, but when I do, it starts attempting to install it, but it says that it is downloading (like, from the internet? Or what does it mean?)

Yes, you must be connected to the internet to download the proprietary Broadcom driver. Broadcom makes it available for free, but you have to download it yourself... Ubuntu is not allowed to distribute it.

---

### Post by Nburnes on 2009-11-27
Broadcom STA works fine for me. Here is the driver so you can download it right now and use a USB drive or something and move it to your machine.

[http://packages.ubuntu.com/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/karmic/bcmwl-kernel-source)

---

### Post by ublintu on 2009-11-28
The link what I posted is not working for you? (In the post 5) In that guide, to install what you need, you don`t need to use the internet, just the CD!!!

---

### Post by justyellowboy on 2009-11-28
I re-installed fwcutter and the fakeroot/dkms/bcmwl-kernel group once more to be sure I had it all, but I didn't realize that the driver could be found on my CD! D'oh! I feel just plain silly not realizing this. All this time I thought I had to install it from the internet that I didn't have! Lol. Yes, Ublintu. It worked. Thanks so much.

---

### Post by ublintu on 2009-11-28
Welcome. I`m happy, because I could help.

---

### Post by porchrat on 2009-12-01
OK as an update.

I got fed up with trying to get the thing working and thought that there might have been something wrong with the install.

I first believed that when I noticed that fwcutter was not available to me and all I could use were the proprietary STA drivers.

I reinstalled and eureka fwcutter all of a sudden showed up next to the STA driver. I activated the STA driver and straight away everything worked.

Thanks for all the suggestions and I am glad this thread has given others some hope :p

EDIT: Upon further reflection I think that the reason fwcutter was made available was that the old install was a dual-boot configuration with Vista (I know...I know...). now that Ubuntu is all by it's lonesome I think it is able to use the fwcutter option as I can't imagine fwcutter would be good for Vista's functionality. Who knows, just a thought.

---

