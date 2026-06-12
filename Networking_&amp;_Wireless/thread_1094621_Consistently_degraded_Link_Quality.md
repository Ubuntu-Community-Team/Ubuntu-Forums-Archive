---
title: "Consistently degraded Link Quality"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by vyco10 on 2009-03-12
[SIZE="4"]=====
Info
=====[/SIZE]

**PC**: Dell Latitude 110L
**Operating System**: Intrepid Ibex (8.10)
**Wireless Brand, Model, Chipset**: Network controller Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
**Wireless Driver**: b43
**Interface check**:
```
          Mode:Managed  Frequency:2.437 GHz  Access Point:    
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=71/100  Signal level:-40 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**Wireless Router**: Linksys WRT54GS V2.0/Firmware: Tomato

[SIZE="4"]=====
Issue
=====[/SIZE]

As you can see from the output of the iwconfig command, the Link Quality is at 71/100. It is almost always in that range. Considering that I'm no more than five or six feet from my wireless router shouldn't it be at least 95%, if not 100%, consistently?

Is this something that is an issue with the b43 driver and this particular card and not fixable, or is there some configuration change I can make to increase the link quality?

NOTE: Considering that I have the Tomato firmware installed on the Linksys router some may wonder if this is the reason for the degraded link quality, but this has been an issue before and after the Tomato install, which I did just this afternoon. I even boosted the Transmission Power to 84mW thinking that it might help the issue, but it hasn't affected it at all.

Thanks for help anyone can provide.

---

### Post by vyco10 on 2009-03-13
Bump

---

### Post by vyco10 on 2009-03-13
Bump +2

---

### Post by helgman on 2009-03-14
> **vyco10 said:**
> As you can see from the output of the iwconfig command, the Link Quality is at 71/100. It is almost always in that range. Considering that I'm no more than five or six feet from my wireless router shouldn't it be at least 95%, if not 100%, consistently?

The man page for [iwconfig]("http://linux.die.net/man/8/iwconfig") says:

> **Link quality**
Overall quality of the link. May be based on the level of contention or interference, the bit or frame error rate, how good the received signal is, some timing synchronisation, or other hardware metric. This is an aggregate value, and depends totally on the driver and hardware.

But I also see that your Bit Rate is 1Mb/s and I'm not sure that's a part of the 802.11G standard or if it's only supported in 802.11B (maybe someone else (Google) knows) - if you are using 802.11G this might be worth investigating. Have you tried with it with some other wireless client? Also, is there any chance of interference from other appliances using the 2.4GHz spectrum?

Guess I'm not helping much ... just bumping the thread for you. ;-)

Regards,
Helgman

---

### Post by vyco10 on 2009-03-14
> **helgman said:**
> The man page for [iwconfig]("http://linux.die.net/man/8/iwconfig") says:



But I also see that your Bit Rate is 1Mb/s and I'm not sure that's a part of the 802.11G standard or if it's only supported in 802.11B (maybe someone else (Google) knows) - if you are using 802.11G this might be worth investigating. Have you tried with it with some other wireless client? Also, is there any chance of interference from other appliances using the 2.4GHz spectrum?

Guess I'm not helping much ... just bumping the thread for you. ;-)

Regards,
Helgman

Wanna see something really screwy I didn't see until just now (*thanks to your pointing out the MB/s rate*)? Here are back-to-back iwconfig commands and their outputs:

```
wlan0     
          Mode:Managed  Frequency:2.462 GHz  Access Point:
          **Bit Rate=18 Mb/s**   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=70/100  Signal level:-42 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and...

```
wlan0       
          Mode:Managed  Frequency:2.462 GHz  Access Point:
          **Bit Rate=54 Mb/s**   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=70/100  Signal level:-42 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Oh, and here is yet another instance...

```

Mode:Managed  Frequency:2.462 GHz  Access Point:  
          **Bit Rate=1 Mb/s**   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=68/100  Signal level:-43 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Back to 1MB. And yet another...

```
          Mode:Managed  Frequency:2.462 GHz  Access Point:
          **Bit Rate=12 Mb/s**   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=75/100  Signal level:-37 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Maybe I'm barking at a reflection of myself in the mirror, this is confusing the crap out of me. [IMG]http://www.websitetoolbox.com/images/boards/smilies/confused.gif[/IMG]

---

### Post by vyco10 on 2009-03-19
Bump

---

