---
title: "Zyxel NWD-271N usb adapter will not connect."
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by Zyprexa on 2011-02-08
I'm having some trouble getting my [Zyxel NWD271N]("http://www.zyxel.com/products_services/nwd271n.shtml") usb wireless adapter to connect.

I'm using Ubuntu Desktop 64bit 10.10

What happens is that i'm always asked to enter the wpa key, and i've double and tripple checked that it's entered correctly. The wierd thing is that it has connected once or twice, but lost connection quickly, but i saw that i got an ip.

I'm not sure about the maximum range on the adapter but i would estimate the distance to be no more than 4-5 meters from the wireless point. Also the signal indicator on the list of wireless networks shows strong, if not full. I've also tried moving it around a bit but that didnt help.

when i run **lsusb** i get:

```
Bus 001 Device 007: ID 0586:3417 ZyXEL Communications Corp. NWD271N 802.11n Wireless Adapter [Atheros AR9001U-(2)NG]
```when i run **lsmod |grep ar9170** (saw the command on a german forum so i didn't understand what was talked about, but i got that it was about the same adapter) i get:

```
ar9170usb              54294  0 
mac80211              267163  1 ar9170usb
ath                    10413  1 ar9170usb
cfg80211              170485  3 ar9170usb,mac80211,ath
led_class               3393  2 ar9170usb,xpad
```I'm at my limited wits end, so any help would be greatly appreciated. :confused:

---

### Post by P4man on 2011-02-09
To help narrow the problem down, can you temporarily disable WPA on your access point? 

If that doesnt help, you may also want to connect a ethernet cable and run the hardware driver utility and see if it proposes a restricted driver for your network card.

Lastly, some googling suggests you might have more luck with WiCD

---

### Post by Zyprexa on 2011-02-09
Today i tried disabling encryption all together but that didnt solve it either. I could see the lockpad being gone from the network name in the list of wireless networks but still could not connect. :(

Also i have plugged a cable to it but only restricted driver was the nvidia display driver, and i've installed all ubuntu updates, still nothing :(

** sudo lshw -C network** gives me:```
*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: 40:4a:03:42:2f:37
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ar9170usb driverversion=2.6.35-25-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
```**iwconfig** gives me:```
wlan0     IEEE 802.11bgn  ESSID:"TheNameOfMyNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```EDIT: I've now tried WiCD and the network showed up with 82% signal strength, but the same thing happened, i got the response that the pass/key is wrong. I've tried changing the key on the access point, and i'm sure i have not mispelled them when trying to connect (also since it didnt work with no encryption either, i think that can be ruled out).

---

### Post by Zyprexa on 2011-02-09
From the result i get from lshw (posted above), is it supposed to say```
firmware=N/A
```in the listing of the adapter?

if not, how do i correct it?

---

### Post by Zyprexa on 2011-02-09
I just tried ndiswrapper now with the latest windows driver, and the adapter was recognized using the ndiswrapper driver but the same problem is there.

I also tested the adapter on a windows machine to be sure that the adapter was not broken, and saw that it took quite a while before connecting the first time. Is it possible to raise the timeout limit somehow when connecting to wireless in ubuntu? I'm using WiCD but could not find any such setting.

i've also tried setting the router to WPA+TKIP and WPA2+AES instead of auto, but no luck then either.

This is really grinding my gears since the little bugger decided to connect momentarely in the past and then stiff me of sweet internet goodness for all eternity. ](*,)

---

### Post by Zyprexa on 2011-02-09
I've managed to connect for a while by setting the routers channel to 12 (2.467 GHz), and using network-manager and ar9170usb driver so apparently this wasn't a problem with software.

But is there any way i can tune the adapter's settings so it's more stable and faster?

Going to leave thread unsolved until tomorrow in case someone has any tips.

---

