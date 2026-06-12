---
title: "Strange problem w. Wifi coming on and off."
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by Lord_Helmet on 2010-08-08
Hello all.. I've got this extremely annoying problem I've been wrestling with for a number of days. I hope someone has the solution to this because I am at my wit's end on this one. 

I built a HTPC using Zotac ION ITX A 330 (has an onboard **Atheros AR9285 **according to lspci) and the plan was to connect this to my **Netgear WNR2000** using WiFi. The OS is **Ubuntu 10.04**. I can connect to the router fine. Signal strength stable between 65-72% so this shouldn't be an issue (other hardware including two laptops running Vista (DELL XPS) and OSX (MBP) connect just fine at the same location). I stay connected for everything between five to 60 minutes then i lose the connection. According to the syslog i get **deauthenticated due to reason 2**.  I've tried the backport modules but this didn't help at all. I've also tried wicd instead of the standard gnome Network manager. No difference. 

Open to suggestion here, folks. This is driving me nuts. 

Regards
Richard.

---

### Post by Lord_Helmet on 2010-08-08
Also; I've tried to google to find out exactly what the "Deauthenticated due to reason 2" means with no success.  

No ideas?

---

### Post by Lord_Helmet on 2010-08-08
No-one with even the slightest idea?

---

### Post by XJ12C on 2010-08-08
I am also having the same problem with the Zotac MAG HD-ND01-U which has the same AR9285 wireless adapter.  Received the unit Friday and installed 10.04 netbook-remix.  The wireless will connect initially and a few minutes later the dialog box comes up asking to re-enter the wireless password.  After this point the wireless will not connect again.

Sorry that I don't have any solutions.  I will be watching this thread to see if there are any suggestions to fix this.

John  [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#000099][/COLOR][/SIZE][/FONT]

---

### Post by Lord_Helmet on 2010-08-10
It's a very odd problem.. This is really getting to me now.. I've had lots of problems with Wifi and Linux. I've been thinking about buying an Ethernet cable to solve my problem. Thing is though that I have the router in another room so I will need a very long cable. 

As it looks now, the only thing I seem to be able to do is to get W7 installed instead. 

Let me know if you solve the problem.

---

### Post by JonathanSG on 2010-08-10
I had v similar problems with Win7 and Ubuntu10.04 and wireless networking to my D Link DIR-655. The problems were partly the  with the OS but the onboard Intel wireless network cards on my t60 laptop / Desktop. The router by default will switch channels if it detects alot of interference or other router broadcasts on that channel, they call it something like enable auto channel scan. Both Ubuntu and Win7 the wireless network card utilities requires the card to be set to a channel and it will only look for it on the specific channel. Disabling the auto channel scan and fixing it to one channel solved this issue for me. Funny thing was I never had this problem with Win XP on a desktop or Vista on the same T60.
Having said that I still find 801.x to be a bit flaky and always try and connect wired if I can, there are probably a 1000 other possible reasons for this but you may want to check this may be this simple for once.

Regards

Jon

---

### Post by Lord_Helmet on 2010-08-10
Hello Jon, 

Sadly I've already disabled auto-channel so that can't be it. Thanks for the tip though. You don't happen to know what the "Deauthentication due to reason 2" means? That's the piece of information I've got so far from the logs.

Regards,
Richard.

---

### Post by Lord_Helmet on 2010-08-10
Hello all.

So I have somewhat of an update for you. Now I'm more confused than ever. The connection has remained unbroken for over 7 hours now. That's a definite record. It rarely lasted ten minutes. Fine by me. Thing is though I haven't done squat for it to suddenly work. Still open to suggestions and an explanation of that "deauthentication due to reason 2"-thing. 

Stay tuned, I'm sure this won't be the end of it.

/R

---

### Post by JonathanSG on 2010-08-10
If that code is anything like Cisco routers the code means you are associated to the access point but not authorised to access the LAN. most probably due to some coms error between the router and network card in my experience due to encryption getting fouled up in the headers or IP confusion between router and radio lease times
I have always found that 801.x is much more stable if you use DHCP reservations or static routing table on the router and  fixed IP settings on the PC (IP, subnet, WINS, Gateway DNS, etc). I am not an expert and don't know why but apparently DHCP generates significantly more network traffic than Static IP addressing and you can also get problems between the lease time on the router and the lease time from the radio / OS appearing different. Even though it's been around years DHCP does not seem to be that stable over 801.x - even with win XP and same brand radio's / routers I have had problems with it dropping out - nearly always solved by switching to static addressing. Perhaps someone more knowledgeable can explain why this appears to be the case

Regards

Jon

---

### Post by XJ12C on 2010-08-10
Have given up with google searches.  Have only found the backporting suggestions which I can't seem to get installed correctly.

I am also using the DIR-655 router.  Was going to change the auto channel scan (although two other netbooks running 10.04 in the house have never had a problem) but the Zotac connected this evening and has been up for about an hour.......will leave it going overnight and report back tomorrow.

John

---

### Post by rstoya05-lx on 2010-12-20
Did anyone get further on this problem? I've had all along on 10.4 and have been using a cable but would really like to solve it.

---

### Post by keshavdks on 2012-01-18
I'm having the exact issue with my zotac motherboard and ubuntu 10.04 as my OS for my HTPC. (XBMC)

---

