---
title: "Linksys WPC54G v.2 making me crazy"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by durableapostle on 2006-07-14
Wireless suddenly went dead.  After some reconfiguring, I was able to get it going again.  After each reboot however, I have to reconfigure again.  This time, I have been unable to get it going again.  From what I see, it should be running.  

Am I wrong?  Any ideas out there?

ifconfig -a results:
eth0      Link encap:Ethernet  HWaddr 00:0D:56:38:F2:E1
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe38:f2e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26641 (26.0 KiB)  TX bytes:8458 (8.2 KiB)
          Interrupt:7

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10305 (10.0 KiB)  TX bytes:10305 (10.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:10:EE:0D:1F
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:10ff:feee:d1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20428 (19.9 KiB)  TX bytes:9060 (8.8 KiB)
          Interrupt:11

---

### Post by da1nonlymikeo on 2006-07-14
dude i cant even get my wpc54g to work lol. if you would please let me know how the hell you got yours to work that would be great.

---

### Post by durableapostle on 2006-07-14
Mine is working again--no clue what's going on.

I got mine working with the following:

1) place this line "options acx firmware_ver=1.2.1.34"in /etc/modprobe.d/options
PHP Code:

[INDENT]sudo nano /etc/modprobe.d/options
add line: options acx firmware_ver=1.2.1.34
hit ctr x and save the file [/INDENT]

2) Reboot, or reload the acx module 
[INDENT]sudo rmmod acx
sudo modprobe acx[/INDENT]

That should bring your TX light on, and make it able to "see" your network.

I found this here: [http://ubuntuforums.org/showthread.php?t=186782&highlight=robert114]("http:/http://ubuntuforums.org/showthread.php?t=186782&highlight=robert114/")

---

### Post by tgilbert on 2006-07-19
That worked great for me, thank you so much.

Just curious, did you use ndiswrapper before adding that line?  
Becuase I did and I was just wondering if that was a nessecary step, the thread I was following before finding this one was from Hoary.

ps. the link you have posted might be bad or maybe I didn't know what to look for

---

### Post by durableapostle on 2006-07-19
no...

ndiswrapper is not needed with this card.

---

### Post by Shane10101 on 2006-07-20
<learning>

Hey Durable,

DMAF & step me through this:  

------------------------
1) place this line "options acx firmware_ver=1.2.1.34"in /etc/modprobe.d/options
------------------------

Okay, so I put the line you've quoted here, into the "options" file under /etc/modprobe.d   ??


and where does this go:
---------------------
PHP Code:

    sudo nano /etc/modprobe.d/options
    add line: options acx firmware_ver=1.2.1.34
    hit ctr x and save the file 
----------------------
??  Type them @ the command line?

Thanks for the help!

<I'd close my "learning" tag, but I know that's not even close to happening here! ;) >

Shane
BTW, I'm diggin' your Gadsden flag. Nice!

---

### Post by bubbaprime on 2006-07-22
that rocked!
I have been having problems witht his linksys card and always just used another wifi card instead. Today I felt like crunching it. Thanks for the tip!

bubba

---

