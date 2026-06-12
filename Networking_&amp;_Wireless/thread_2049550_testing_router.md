---
title: "testing router"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by micahpage on 2012-08-28
Is there a way to test my router from ubuntu 12.04?
I recently have a had a ton of problems with my internet going in and out. I went and got a new modem from the ISP and now I still have some of the same problems.

I mean is there a command, to test the router?

---

### Post by 2F4U on 2012-08-29
What exactly do you mean by test the router, what tests do you intend to perform?

---

### Post by micahpage on 2012-08-31
Well my IPS is horrible. They disconnect you from a long wait on the phone when you are trying to call to complain about their service and get it fixed. I had finally got them to replace the modem. Which my internet hic-ups stopped for a month, and now they are back. My next idea was to either fix/replace my router in hopes that is the cause. 

Sometimes I lose internet and I am not sure why. Sometimes I lose it for a few hours, some times I lose it for a few seconds. 

The tests I was looking to perform was to check when there was an internet loss, to check in the router and see if it still is getting good internet from the modem, or if the modem doesn't even have internet?

IS there a ready made way to do this?

I also heard that you could put linux on the router which will give you more options. Maybe this is one of those options?

---

### Post by Colo993 on 2012-08-31
micahpage,

What type of router do you have?

Linksys routers can be upgraded/changed to run Linux.  There might be other router manufactures that allow you to do this but I haven't heard of any.

Most home routers have a Web page that shows status and log messages.  The status page on my DSL router shows the IP address and current upload/download speeds.

I'm assuming that when you lose your internet connection the modem you are using is also indicating via it's front lights that it has lost the connection?

Colo993

---

### Post by lisati on 2012-08-31
> **micahpage said:**
> Is there a way to test my router from ubuntu 12.04?
I recently have a had a ton of problems with my internet going in and out. I went and got a new modem from the ISP and now I still have some of the same problems.

I mean is there a command, to test the router?

It might not be your router. A few years ago I noticed that my own connection wasn't the greatest and that there was sometimes noise on my phone line. I managed to improve things somewhat by replacing some of the internal wiring in my house for my phone line and by avoiding using extension leads between the phone line and my modem.

---

### Post by nativehound on 2012-08-31
+1 
I had problems a few years ago with dsl line dropping connection when it was stormy or windy.  I had them send a tech out to check the line. He found no Installation on the phone line to the house. It just weathered away. i would make them send a tech out if it were me.

---

### Post by jmore9 on 2012-08-31
I live in an apartment building that has over 100 apartments.  When all the people get their ill leagal hookups going i have problemw with my internet such as loss of speed instead of an xtra fast connection , i only get dialup perfromance.

I have to do a hard reboot on my modem to get my speed back.  Have to do this fairly often.  So as was posted upbove you might have some wiring problems if in own home or if in apartment building other problems with building wiring.

---

### Post by micahpage on 2012-09-02
I do not have DSL. 
I have already had a tech come out a few times and they check for foul play, and they said no problems there. They also replaced the some lines.
A hard reboot of the modem sometimes works, and sometimes doesn't work. Its like it has a mind of its own. It will come in and out so randomly.

My router is a netgear
> Hardware Version	WNR2000v2
Firmware Version	V1.2.0.4_35.0.57NA
GUI Language Version	V1.2.0.4_2.1.17.1
Connection Type	DHCP

I also have had some slow internet connections within the last 6 months, so I had changed my DNS from my ISP to google's in hoping it would run faster. I haven;t seen any difference.

> Domain Name Server 
8.8.8.8
8.8.4.4


> System Up Time 2 days 19:07:09
Port	Status	TxPkts	RxPkts	Collisions	Tx B/s	Rx B/s	Up Time
WAN	100M/Full	37435968	58707241	0	6136	2014	 2 days 19:06:46
LAN1	Link Down	5916351	5433822	0	14059	35039	--
LAN2	100M/Full	 1 days 00:30:55
LAN3	Link Down	--
LAN4	Link Down	--
WLAN	145M	780056	461835	0	3714	246	 2 days 19:06
^^ 2 days up time is very very good in my case. I normally will not have it above 1 day, due to unpluging everything and trying to get it all reset /modem/router


When I lose internet the lights on the modem does not change. I tried explaining to the ISP tech, but thye are quite stupid. He was more interested in the OS I was running. ubuntu, as he never heard of anything other than windows.

---

