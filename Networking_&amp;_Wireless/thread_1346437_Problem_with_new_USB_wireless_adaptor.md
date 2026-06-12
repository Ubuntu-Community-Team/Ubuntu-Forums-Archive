---
title: "Problem with new USB wireless adaptor"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by 2blue on 2009-12-05
I am trying to configure my new Wireless card. The only name I can find is on the installation manual "Ralink". It came with a installation CD that also will not work, at least not right away. The installation CD are made for Windows, Mac, and Linux included. 

Ubuntu often recognise different hardware right away, but not this one. When I connect wireless adaptor to computer, nothing is detected. When I use the installation CD it will not "unpack" and the wizard that are suppose to appear does not. 

Any Ideas?

---

### Post by raffaele181188 on 2009-12-05
I also have a ralink-powered card, and it works just fine out of the box :)
What's your kernel version? The module should be included, maybe you miss the firmware for license issues. Post
```

find /lib/firmware/ -name 'rt*'

```
If it outputs something, then try plug off/in your card and post
```

dmesg | tail

```

---

### Post by 2blue on 2009-12-05
I get this: 

my-laptop:~$ find /lib/firmware/ -name 'rt*'
/lib/firmware/rt2561s.bin
/lib/firmware/rt2661.bin
/lib/firmware/rt73.bin
/lib/firmware/rt2561.bin
/lib/firmware/rt2860.bin
/lib/firmware/rt2870.bin
my-laptop:~$ dmesg | tail
[18771.662094] phy9 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf70e1d94
[18773.756079] usb 1-1: new high speed USB device using ehci_hcd and address 9
[18773.926908] usb 1-1: configuration #1 chosen from 1 choice
[18773.975833] phy10: Selected rate control algorithm 'minstrel'
[18773.976962] Registered led device: rt2800usb-phy10::radio
[18773.976986] Registered led device: rt2800usb-phy10::assoc
[18773.977009] Registered led device: rt2800usb-phy10::quality
[18774.090519] udev: renamed network interface wlan2 to wlan9
[18774.098134] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
[18774.610762] ADDRCONF(NETDEV_UP): wlan9: link is not ready
my-laptop:~$

---

### Post by raffaele181188 on 2009-12-05
It seems OK .  Mmmmmm Try
```

sudo iwconfig -a

```

---

### Post by 2blue on 2009-12-05
After a reboot and plugging USB wireless in and out a couple of times it is detected, but it's not active, no networks detected. My laptop has the original inbuilt network still in place, but the reception is rather low in that card. I was hoping that the USB wireless would have better reception since it has an antenna. My PCMCIA wireless card is working all right.

---

### Post by 2blue on 2009-12-05
my-laptop:~$ sudo iwconfig -a
-a        No such device

my-laptop:~$ ^C

---

### Post by raffaele181188 on 2009-12-05
If it is a reception problem there's nothing you can do :(
Also my card suffers from this problem. I totally solved (ubelievable) with a "cantenna" :) which raised up my signal strength from 0 to 70%!!! But mine is a desktop machine; if you have a laptop I doubt you can do the same
Also your PCMCIA has an antenna, I guess ;)

---

### Post by raffaele181188 on 2009-12-05
My fault
```

sudo iwconfig

```
:)

---

### Post by 2blue on 2009-12-05
I don't know if you can make any sense of this. I don't know if reception will get any better, but the USB wireless card should at least work? It has a antenna input with standard plugin, and it can take any ordinary wireless antenna that a stationary computer use. However, the reception is not the main problem, it is making it work at all. Sorry about making such a fuzz about it. 

```
my-laptop:~$ sudo iwconfig
[sudo] password for my-laptop: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:10:44:41:AC   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:3551-7311-3C46-5AE3-B3E0-CCA8-FDE8-5975-9666-9AFF-81B9-51EC-107B-556C-FF42-FBA6 [3]
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster2  no wireless extensions.

wlan11    IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 


```

---

### Post by raffaele181188 on 2009-12-05
It's a bit strange. When you plug the card
```

[18774.090519] udev: renamed network interface wlan2 to wlan9

```
but in the last post there's no wlan9 (wlan2 neither). I guess you rebooted, so you should repeat the key-steps to get your actual wlanXXX (namely plug off/in, then `dmesg | tail | grep wlan`. Then you should get your device name, so you can `sudo iwconfig wlan<N>`). Anyway it seems that the kernel side is Ok. What wireless GUI do you use? NetworkManager? WICD?

---

### Post by 2blue on 2009-12-06
I'm not shore if I give the correct answer, but I use Network Manager. (When I right-click wireless icon on the top-line application bar, then "about" I get "NetworkManager Applet 0.7.996"). 

I have three network cards on my laptop when the new one is plugged in, the working PCMCIA card, and the original in-built. The reason for new wlan numbers might be because I did plug and unplug them to see if anything happened.

---

### Post by uncaspi on 2009-12-06
I think you have to disable the cards that is not in use. ifdown wlan<N>

---

### Post by 2blue on 2009-12-15
I have been struggling with my new USB wireless card for some time now. I have looked up different threads and Ubuntu wiki pages, but still stubbornly difficult. 

I tried to follow [this]("http://ubuntuforums.org/showthread.php?t=1285828") among them, but it's too advanced for me, I get too many error messages that I can't fix. This is an instruction on how to down load the drives from the Ralink-site and add it to the active driver list, but it's just straight forward. 

When I bought this card I was under the impression it came with a wizard installer for the drivers, but it doesn't work. I seriously contemplate buying a new one, but I want one with antenna input, and there's not that many available. 

It there another way around this? I would love to find the drivers in some kind of package or version that install manager takes care of. 

Anybody who are willing to take a look at this?

---

