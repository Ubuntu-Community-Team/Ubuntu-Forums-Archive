---
title: "Intel PRO/Wireless 3945ABG slow speeds"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by djoelsson on 2006-07-08
Hello,

I'll try to make this as succinct as possible. I have an old Linksys wireless router (802.11b), a Sony laptop, and a homebuilt desktop. Both are running Dapper and connect wirelessly without problems. I usually get a speed around 3Mbps.

I just bought a new laptop (Toshiba Satellite A105) with a Intel PRO/Wireless 3945ABG chipset. It's a core duo so I installed the 686 kernel. I can now only connect with around 300 kBps. A direct connection is as fast as the other computers. The wireless works fine in Windows XP on the same laptop.

I have tried turning off IPv6, ndiswrapper, and changing the settings on my router, but nothing seems to work.

iwconfig give me the following:

eth1 IEEE 802.11b ESSID:"dansnetwork"
Mode:Managed Frequency:2.462 GHz Access Point:00:06:25:9A:1F:7C
Bit Rate:11 Mb/s Tx-Power:14 dBm
Retry limit:15 RTS thr: off Fragment thr: off
Power Management: off
Link Quality=86/100 Signal level=-46 dBm Noise level=-47 dBm
Rx invalid nwid:0 Rx invalid crypt:52 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:10971 Missed beacon:0

As you can see, the "invalid misc" number is very high. My other laptop has a 0.

Any ideas?

Thanks for your help!

Dan

---

### Post by bioS on 2006-07-10
Hi Dan,

it won't help you, but I have exactly the same problem on a new Dell Inspiron 9400 with the same wireless chipset. It runs well for a few minutes (or only seconds sometimes), and then runs very slowly or even not at all. Under Windows XP, the speed is always maximum.

*iwconfig* gives me something really similar to yours.

Anybody has an idea ?

---

### Post by djoelsson on 2006-07-12
I have battled with it some more and I haven't gotten anywhere.  Using ifconfig I have figured out that I'm dropping Rx packets, but Tx packets are all fine.  Strange...

I'll make sure to post if I get any closer.

Dan

---

### Post by jct3 on 2006-07-17
Sorry not to offer any help but I'm getting the same thing on my Satellite.

---

### Post by ileavache on 2006-10-07
I can only join your club guys...
I have dapper on my thinkpad t41p / IPW2200BG
Using the speakeasy speed test, WEP on or off, I barely get 900k/s with ubuntu wireless while I get more than 4M/s with Ubuntu wired and XP wireless.
Did you ever figure it out?
Thanks,

---

### Post by Helen1950 on 2007-06-09
I have the same chipset in my acer aspire 5630.  I am using a d-link router model DI 624.  The first connection speed I got using cable was 10mbs. I wasn't very happy with that .. switched to DSL and it was the same. .. I then purchased a d-link cardbus adapter Model DWL-G650 ... My connection speed has now jumped to 108mbs.

Hope this helps ... most of the newer routers will process higher speeds, but only using their own adapters.

They must be learning this from Mac's and Bill Gates .... lol

Hi Dan .. Just read your message again .. I once had the same router .. linksys .(made by Cisco) .. In the configuration, if u change the setting from all to "only g devices" it will boost your speed up to 11mbs.  For some reason types a and b devices slow it down.

---

