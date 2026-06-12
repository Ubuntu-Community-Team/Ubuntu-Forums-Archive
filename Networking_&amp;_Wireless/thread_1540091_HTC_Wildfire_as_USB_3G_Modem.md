---
title: "HTC Wildfire as USB 3G Modem"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by atomp on 2010-07-27
Hello.

I am considering buying a HTC Wildfire and would like to know how compatible it is as a USB 3G modem on Ubuntu 10.04.

I currently use the Samsung S5230 as a USB modem on my netbook which works an absolute dream but GPRS can be so very slow.

I've had a search around but there are very few relevant results, and no up to date results that I could find.

Cheers for your time.

Tom.

---

### Post by pdc on 2010-07-27
well; why don't you go ahead and try it out for us all?

Seems like you have good expertise already; with the Samsung;

google on iphone tether; seems to be working for folks;

will the provider offer you a "*try before you buy*" deal?

If you research the topic, and take your laptop? into a provider and get it all connected? If business is slow, keep the shop employees occupied for a few minutes ..........

---

### Post by atomp on 2010-07-28
The phone is on order, so when it arrives I shall give it a shot and report back here on the results for anyone that would like to know.

P.S. Was the tone of my original post a little off? If it was I apologise, I didn't mean to cause offence.

---

### Post by pdc on 2010-07-28
> *Was the tone of my original post a little off*?

Gosh, no; it is the thing with email stuff: one can't hear the voice! 

Great you have ordered this; I think you will be pleasantly surprised how well it goes; 

if you google ahead on some of the tether stuff, seems like plug in with USB and select the right options ........

folks will be keen to hear from you; best wishes

---

### Post by mario_k8 on 2010-07-30
Hello all,

I was thinking of buying this phone as well, and would be very much interested in knowing if it can work out of the box as a modem with ubunt.  Atomp, by all means, please let us know of your experience when you receive your new phone. ;)

Cheers!

---

### Post by atomp on 2010-08-02
I come bearing good news.

Plug and play 3G tethering with Ubuntu 10.04 on an Asus Eee PC T101MT with the HTC Wildfire.

Ensure that the phone is using the 3G connection (disabling wifi might be necessary), connect with the provided usb cable and select internet sharing connection on the phone. Ubuntu should then recognise the connection as a USB wired connection and there you go, a 3G connection through the phone.

On a side note, Android is awesome (although not quite as awesome as Ubuntu).

On another side note, I'm not sure how doing this affects your contract with your operator. I'm personally operating on a T-Mobile UK PAYG connection with the 6monthweb booster, I'm under the impression that this covers the tethering, on other contracts this might be different.

---

### Post by mario_k8 on 2010-08-02
Oh cheers mate! Thanks so much for letting us know! That is indeed very good news. 

And android does sound pretty cool indeed. I've also read that the wildfire will be getting the froyo 2.1 treatment by HTC soon enough via an update, so there'll be more goodies for you around the corner.  ;)

Have fun with your new phone!

---

### Post by ginestre on 2010-08-14
> **atomp said:**
> I come bearing good news.

.....Ubuntu should then recognise the connection as a USB wired connection and there you go, a 3G connection through the phone.


Enthusiastic newby question: 
How do I know this has happened? I've plugged my wildfire into 10.04 via the USB cable, turned off wireless, turned on internet sharing - both on the phone... now where do I see that the pc and the phone are connected?

---

### Post by atomp on 2010-08-14
> **ginestre said:**
> Enthusiastic newby question: 
How do I know this has happened? I've plugged my wildfire into 10.04 via the USB cable, turned off wireless, turned on internet sharing - both on the phone... now where do I see that the pc and the phone are connected?

There should be a wired connection symbol in the Indicator Applet in the top right on Ubuntu.

(Once HTC gets a move on the Wildfire should hopefully be getting the Wifi tethering capability with Android 2.2 (Froyo) which should simplify this whole process).

---

### Post by Jose Catre-Vandis on 2010-08-19
I can also confirm success with HTC Legend. No notification, nothing to tell me I was connected (but then I am using WICD) which puzzled me for a while, and a bit slow, even with ssh connections, but this could be my location/reception. But it works out of the box. This on an Acer Aspire One with Ubuntu Netbook  Lucid

---

### Post by Ofloo on 2010-11-03
it always worked on 10.04 however once i upgraded to 10.10 it didn't work anymore suggestions, .. and i think it's a routing issue cause i can't even ping the gateway anymore, however when i look at the routes nothing seems wrong.

i did manage to get it to work once however i tried so much crap unplugging replugging reboot, reboot the phone .. so i was wondering if someone knew why this could be.

---

### Post by atomp on 2010-11-04
I can't give any reasoning behind the USB 3G modem not working anymore but I can confirm that the HTC Wildfire is suffering from the same problem in that the functionality no longer works after an update up to 10.10.

I'll continue to experiment with various setups.

---

### Post by janne_oksanen on 2010-11-05
I'm still on 10.04 and it has quit working for me too. Last time I tried it (maybe six weeks ago) it was working fine, but not anymore. It says it's connected but no bits are getting through.

---

### Post by Ofloo on 2010-11-08
from what i can gather it's a routing problem cause i can't even ping the gateway 192.168.100.254 .. ? However when i look at the routes they look fine to me.

```

#dmesg
[397224.892848] usb 2-2.2.2: new high speed USB device using ehci_hcd and address 34
[397225.032183] rndis_host 2-2.2.2:1.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-2.2.2, RNDIS device, xx:xx:xx:xx:xx:xx
[397236.082520] usb0: no IPv6 routers present
#ifconfig usb0
usb0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::xxxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1480 (1.4 KB)  TX bytes:6444 (6.4 KB)
#route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 usb0
0.0.0.0         192.168.100.254 0.0.0.0         UG    0      0        0 usb0
#ping -c 5 192.168.100.254
PING 192.168.100.254 (192.168.100.254) 56(84) bytes of data.

--- 192.168.100.254 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4005ms
```

---

### Post by Ofloo on 2010-11-08
solved the issue by doing

```
#sudo apt-get install linux-backports-modules-net-maverick-generic linux-backports-modules-headers-maverick-generic
#ping -c1 192.168.100.254
PING 192.168.100.254 (192.168.100.254) 56(84) bytes of data.
64 bytes from 192.168.100.254: icmp_req=1 ttl=64 time=0.847 ms

--- 192.168.100.254 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.847/0.847/0.847/0.000 ms
```

---

### Post by atomp on 2010-11-10
Cheers for the solution, I gave it a shot but it didn't seem to work initially, only after being combined with the WildPuzzleROM did it seem to work. (Not to mention the Wifi hotspot ability of 2.2).

---

### Post by colinlues on 2010-11-12
Wow, so many people interested in this phone, I also want to buy it!

---

### Post by Ofloo on 2010-11-28
> **atomp said:**
> Cheers for the solution, I gave it a shot but it didn't seem to work initially, only after being combined with the WildPuzzleROM did it seem to work. (Not to mention the Wifi hotspot ability of 2.2).

indeed i noticed after a few updates that it didn't work again, never tried the hotspot thingy though.

edit:

if anyone has solution not installing new rom..

---

### Post by atomp on 2010-11-29
Well HTC have promised the official 2.2 OTA update within a couple of weeks, which if my 2.2 Rom is anything to go by should fix the problem, that and allow Wifi hotspot capability which means no cable.

Maybe go through the networking backports as suggested earlier until you find one that works although I personally tried and undid this as it was messing with the laptop's Wifi.

Sorry I can't be much more help.

---

### Post by Ofloo on 2010-11-30
well I don't really beleve HTC they where going to release froyo in september, and they still haven't done that, at least that's what i read on several news pages don't have the links atm. They did some update however but it wasn't froyo for the wildfire, ..

---

### Post by Ofloo on 2010-12-11
there is an update today, and guess what the sharing of the internet connection of the phone works. So people with this issue should update, however if you rooted your phone the update won't work, you need to disable signature check and then install the update manually, let the update download then go into recoverymode disable signature check and install from sdcard the file is located on the sdcard under download/downloads directory.

---

### Post by LemFI on 2010-12-20
Hi,

I did the upgrade which indeed solved the tethering issue..... once. Then, now, I am back to the previously described problem where ubuntu sees the connection to the HTC wildfire but no bytes are going through.

I'd love to hear a solution... ;)

Thanks guys!

---

### Post by LemFI on 2011-01-07
hi again, 

Got another update for the wildfire phone to android 2.2.
That brought the WiFi hotspot feature that just works every time and fits all my needs.

so, problem solved!
Thanks and happy new year 2011.

Best regards.

---

