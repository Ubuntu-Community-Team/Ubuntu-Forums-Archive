---
title: "Intel Wifi 5100 very slow"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by Petrick on 2009-01-06
I've just installed ubuntu 8.10 and my wireless Intel WiFi 5100 worked out of the box. However, the speed is extremely slow (downloading and just surfing). D/L at max 50KB. While in Windows I get 500+KB.

```

    *-network
                description: Wireless interface
                product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 00
                serial: 00:21:5d:ad:ef:ac
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=10.11.12.28 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```

```

wlan0     IEEE 802.11abgn  ESSID:"ssid"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:C5:C4:AC:11   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-24 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

My network is b-standard with a simple WEP key.
Any ideas?

---

### Post by x58 on 2009-01-06
Make a speed test at [http://www.speakeasy.net/speedtest/.I](http://www.speakeasy.net/speedtest/.I) believe you will be very surprise at results.Everything is not like looks

---

### Post by Petrick on 2009-01-07
I'm getting pings of 500-2700ms when i ping google. Under Windows its a normal 40ms.

---

### Post by Deve on 2009-01-14
I've got exactly the same problem. I installed the latest Ubuntu version 8.10, the Intel Wifi link 5100 AGN adapter worked out of the box - but is very slow.

I checked that with an internet speedtest site and under the same circumstances. The transfer rates are:
Windows Vista: 548 kbps down / 332 kbps up
Ubuntu: 138 kbps down / 93 kbps up

The machine is a Thinkpad R500 notebook. Btw: I tested a Suse 11 LiveCD and encountered the same behaviour. For me it looks like a driver issue. But on [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) I read that you may only install a new kernel - not only an updated driver.

What do you think?

---

### Post by Petrick on 2009-01-17
I tried ndiswrapper, but it doesn't support it yet...

---

### Post by Petrick on 2009-01-17
> **Deve said:**
> I've got exactly the same problem. I installed the latest Ubuntu version 8.10, the Intel Wifi link 5100 AGN adapter worked out of the box - but is very slow.

I checked that with an internet speedtest site and under the same circumstances. The transfer rates are:
Windows Vista: 548 kbps down / 332 kbps up
Ubuntu: 138 kbps down / 93 kbps up

The machine is a Thinkpad R500 notebook. Btw: I tested a Suse 11 LiveCD and encountered the same behaviour. For me it looks like a driver issue. But on [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) I read that you may only install a new kernel - not only an updated driver.

What do you think?

What network setup do you have? WPA? B, G or N router?

---

### Post by Deve on 2009-01-19
I'll post some configuration details:

```
davidub@david-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ConnectionPoint"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:01:E3:44:9F:2C   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=67/100  Signal level:-50 dBm  Noise level=-77 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

```
davidub@david-laptop:~$ dmesg | grep iwl
[   12.017923] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   12.017926] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   12.095722] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.095752] iwlagn 0000:03:00.0: setting latency timer to 64
[   12.095832] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   12.131879] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.132086] iwlagn 0000:03:00.0: PCI INT A disabled
[   12.133494] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   23.250958] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.251078] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   23.251432] firmware: requesting iwlwifi-5000-1.ucode
[   25.463568] Registered led device: iwl-phy0:radio
[   25.464381] Registered led device: iwl-phy0:assoc
[   25.465680] Registered led device: iwl-phy0:RX
[   25.466358] Registered led device: iwl-phy0:TX

```

```
davidub@david-laptop:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wmaster0  no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.457 GHz (Channel 10)

pan0      no frequency information.

```

I'm using a B router.

---

### Post by Petrick on 2009-01-22
I'm gonna try to test it with my G-router, maybe there's a problem with B-routers

---

### Post by Deve on 2009-01-22
Yes, maybe. Im excited about the results of your test :)

---

### Post by Petrick on 2009-01-23
just did a test on a G-router (cisco 877w), and speed is back to the normal +/-500KB/s

(although encryption is off, might also be an issue)

---

### Post by Deve on 2009-01-26
The same for me: I bought a G router and everything works fine now. My old router only featured WEP encryption so I couldn't check if the encription mode has any influences on the problem.

On the G router both WEP and WPA work fine, though.

---

### Post by espeneppi on 2009-02-03
Bump
I have the same card, got a 11mbit b router and things are very slow compared to what it should be, havent tried a 54mbit router yet, but i am sure i have got the same problem as the earlier posters.
So is there a solution to this problem?

---

### Post by Deve on 2009-02-03
Unfortunately I don't know any expect using another router. But we didn't search that hard to find another solution so there may be one...maybe the driver author's page would be a good starting point: [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)

---

### Post by igknighted on 2009-02-03
> **Petrick said:**
> I'm getting pings of 500-2700ms when i ping google. Under Windows its a normal 40ms.

I've got that card (and a G router) and my ping time to google is 25ms-29ms.  I would guess your problem is in name resolution, not your wireless connection.  Can you ping an IP address with better results?

---

### Post by igknighted on 2009-02-03
> **Deve said:**
> Unfortunately I don't know any expect using another router. But we didn't search that hard to find another solution so there may be one...maybe the driver author's page would be a good starting point: [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)

Sorry to DP, but notice how many versions of the card don't state wireless B support.  Perhaps this is the issue?

---

### Post by Deve on 2009-02-03
At least for me that wasn't the issue as the card worked well with the B router under Windows.

---

### Post by e-rwan on 2009-02-04
hi,
just to say that I had exactly the same problem as you do, and after visiting this link _**[linuxwireless.org]("http://linuxwireless.org/en/users/Download")**_, my problem was resolved.
It makes you install several drivers including the last iwlagn, which is the problem here.
what's convenient is you don't have to compile your whole kernel to install it.
my connection's now at full speed.

bye (sorry for my bad English)

---

### Post by cucisan on 2009-02-14
ooh yeah baby...

using the updated drivers (here compat-wireless-2009-02-14) everything works now...
getting 800kb/s on steam downloads... not only 80kb/s
another side effect:
i didnt look into that matter further BUT:
when i did download stuff (80kb/s - my internet connection is capable of more than 1000kb/s) other clients in the network e.g playing online games startet to lag ..
(before my download: other client had ping of 20ms - when i started to download other client got ping of 1000ms and more)
and downloads on other devices on the wlan startet to slow down
(before my download: 700kb/s - while downloading others dropped to: 40kb/s)

this was 10000% reproducable... very very strange :confused:


ah, im using an Asus WL500gP router running openwrt... and using windows there are no such problems :)

---

### Post by joelgrrr on 2009-02-15
This may also help people suffering similar issues  [http://ubuntuforums.org/showpost.php?p=6737895&postcount=3]("http://ubuntuforums.org/showpost.php?p=6737895&postcount=3")

---

### Post by saresca on 2009-04-08
I'm using Ubuntu Intrepid 8.10, kernel 2.6.27-11-server (I've 4Gb memory and generic doesn't support it)

After running

```
sudo apt-get install linux-backports-modules-intrepid-server
```

Note if you are not running server image please use:

```
sudo apt-get install linux-backports-modules-intrepid
```

Restart and that's all, my network card is working fine with 802.11b

More at: [http://linuxwireless.org/en/users/Download#Buildingandinstalling](http://linuxwireless.org/en/users/Download#Buildingandinstalling)

---

### Post by shmish111 on 2009-05-10
I just switched my router from mixed-mode to G-Only.  Seems to have fixed the problem so if you have a wireless g router you should be able to fix any issues.

---

### Post by Truthiswithin on 2009-08-15
I've still got this problem in Ubuntu Karmic Alpha.  On Windows I can get 500kB/s+, and on Ubuntu, only 100+

Using Intel 5100 agn

Backports doesn't change anything for me, ndiswrapper doesn't seem to work.  Hoping I won't have to go back to using Windows... please help.

Router is a netgear cg814gcmr

Interestingly, using the Ethernet connection to the same router, the download speed is around 500kB/s, but the upload speed is no better.  Here's the speed test results:

wlan4:        
down (mbps) - 0.85
up (mbps)  -    0.54

eth0:
down (mbps) -          5.17
up (mbps)  -           0.54


Windows gives ~ the same results with wireless as I get with eth0 above: 5.3 down and 0.54 up.

Here's a possible problem:

$ dmesg | grep -i iwl

```
iwlagn 0000:07:00.0: lbm-iwlwifi-5000-2.ucode firmware file req failed: -2

```

Here's the whole output after sudo modprobe iwlagn:

```
[ 1776.348960] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[ 1776.348962] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 1776.349320] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 1776.349352] iwlagn 0000:07:00.0: setting latency timer to 64
[ 1776.349401] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[ 1776.389786] iwlagn 0000:07:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 1776.389854] iwlagn 0000:07:00.0: irq 29 for MSI/MSI-X
[ 1776.390174] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1776.401415] iwlagn 0000:07:00.0: firmware: requesting lbm-iwlwifi-5000-2.ucode
[ 1776.403962] iwlagn 0000:07:00.0: lbm-iwlwifi-5000-2.ucode firmware file req failed: -2
[ 1776.403967] iwlagn 0000:07:00.0: firmware: requesting lbm-iwlwifi-5000-1.ucode
[ 1776.408129] iwlagn 0000:07:00.0: Loaded firmware lbm-iwlwifi-5000-1.ucode, which is deprecated. Please use API v2 instead.
[ 1776.408135] iwlagn 0000:07:00.0: loaded firmware version 8.24.2.12
```

---

### Post by Truthiswithin on 2009-08-16
Sorry, I figured it out. What works for me is to remove linux-backports and compat-wireless. Either/or gives me reduced speed on downloads.

Edit: No, sorry, that was wrong... the speed goes up temporarily when I restart the iwlagn module; after some seconds, the speed drops by up to 10x.

---

