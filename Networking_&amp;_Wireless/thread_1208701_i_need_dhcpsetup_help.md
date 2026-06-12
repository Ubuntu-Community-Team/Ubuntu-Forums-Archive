---
title: "i need dhcp/setup help"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by ullgur on 2009-07-09
Hello.

Im trying to setup my old adsl modem (Xavi x5258-p2) as a AP for my lan.
It works absolutly perfect and at the same time not at all, i cant figure this one out!

He goes:

Ive pluged my xavi adsl modem/router into my cable modem, set it up as bridge and activated the AP with wpa-psk.

From my ubuntu eeepc i can log in to the AP and the bridge seems to direct the traffic over to the cable modem, since my eeepc recives IP from my isp's DHCP server, works just like i want!

BUT!
From my WinXP laptop, it logs in to the AP and it cant get an IP.
I never had any probs with it when the xavi was used as a modem, but now it wont work, so seems to be a defective dhcp client in winxp?

Anyway, ive smacked my head against the wall all day now. Anyone have any thoughts about how to get the winxp machine to work?

I know this isnt the forum for windows help, but since ubuntu solves this situation without any problems i thought you ubuntu guys might know WHY it works. :)

---

### Post by superprash2003 on 2009-07-09
are you trying to do xp and ubuntu simultaneously?

---

### Post by ullgur on 2009-07-09
On different machines.
And have tried both at the same time, and one after another. Ubuntu machine always work, and the xp one dont.
dhcp is activated on the winxp one btw, and it works fine against my neighbours ap.
Just the comp -> ap -> modem setup that doesnt work.

---

### Post by superprash2003 on 2009-07-10
post output of **ipconfig /renew** from the xp's command prompt

---

### Post by ullgur on 2009-07-10
An error occured when renewing the interface Wireless connection: Wireless connection:
A connection to the dhcp server could not be made. Request timeout.

---

### Post by superprash2003 on 2009-07-10
does windows recognize the WLAN connection?? it does seem like it..Have you tried with static ip?

---

### Post by doas777 on 2009-07-10
not sure if this fits the bill, but if you are changing the machine plugged directly into the cablemodem (without a router), then you will have to unplug the cablemodem from power for 45 secs to reboot it each time you change devices. they can't deal with the internal MAC change dynamically, so layer 2 communication breaks down.

---

### Post by RD1 on 2009-07-10
Since the Ubuntu side is working, I believe your modem/router/ap setup is good. Don't mess with it.

I would try re-setting the XP tpc/ip installation. First, go into network connections and delete all connections. Then follow the directions [here]("http://www.petri.co.il/reinstall_tcp_ip_on_windows_xp.htm") to reset tcp/ip. Then reboot XP and allow XP to make a new wireless connection.

Good Luck

---

### Post by Ostry50 on 2009-07-19
Hi,
I don't know if it is right forum, but I'm against the wall.
I have the same kind of router, but it's bricked. During configuration the power cut-off happen and now I need the firmware to recover it. The firmware for X5258-P2 is unavailable in Internet. I've been googling with no result at all. But the firmware can be extracted from operational router as mtd4 block. If anyone can help me and send me extracted from router mtd4 block I will be realy happy.

---

### Post by ullgur on 2009-07-21
Thanks for the help all, sadly it didnt work. I'll just have to use cable for this lap until i figure it out.

Ostry50: I dont know how to do that, but have you tried reseting the modem to factory defaults?
By pressing a small object into the hole in the back of the modem and holding it for 10-20 secs or so, until it starts blinking.

Else tell me how its done, and ill extract it.

---

