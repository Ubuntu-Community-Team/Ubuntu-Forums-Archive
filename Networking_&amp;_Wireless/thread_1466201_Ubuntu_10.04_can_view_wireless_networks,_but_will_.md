---
title: "Ubuntu 10.04 can view wireless networks, but will not connect"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by jdsmash on 2010-04-30
Okay, so today I installed the final build of ubuntu 10.04 on my toshiba a200 laptop and am in need of some help. My wireless card can see my home network, but it will not connect to it / it is extremely unstable on the rare occasion when it actually connects. I have an Atheros ar5007eg wireless card in my laptop, and wifi worked well under 9.10 (albeit a little slow). Hopefully someone who knows their way around the terminal better than I can give me a hand.

The lspci command reveals this:

> 04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)Though as I have said earlier, I actually have an AR5007EG. (maybe this is a generic driver?)

Also when I use the dmesg command after trying to connect, I get this which repeats a couple times:

> 
[  942.075379] wlan0: direct probe to AP (router MAC address) (try 1)
[  942.077935] wlan0: direct probe responded
[  942.077945] wlan0: authenticate with AP (router MAC address) (try 1)
[  942.080571] wlan0: authenticated
[  942.080612] wlan0: associate with AP (router MAC address) (try 1)
[  942.280103] wlan0: associate with AP (router MAC address) (try 2)
[  942.480087] wlan0: associate with AP (router MAC address) (try 3)
[  942.680136] wlan0: association with AP (router MAC address) timed outSo the wireless card actually authenticates with my router but cannot associate with it.

Lastly, on the off chance it actually connects (i think it connected for a few minutes right after a fresh install of 10.04), ping times are horrible (like 13000ms per packet).

Does anyone have a clue on how to remedy this issue?

---

### Post by amrose on 2010-04-30
I am having the same problem.  When I ran 9.10 in VM with XP it connected fine ( and slow) like yours.  Now that I have an actual install of 10.04 in its own partition I cannot connect.  The driver is Atheros 7.4.2.105.  It sees the network fine, but will not connect no matter what I try.

---

### Post by eltonw on 2010-04-30
It is a known problem with LUCID. There is a patched kernel that can be downloaded from HERE:[http://rsalveti.net/pub/ubuntu/kernel/lucid/linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb]("http://rsalveti.net/pub/ubuntu/kernel/lucid/linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb")

---

### Post by jdsmash on 2010-04-30
> **eltonw said:**
> It is a known problem with LUCID. There is a patched kernel that can be downloaded from HERE:[http://rsalveti.net/pub/ubuntu/kernel/lucid/linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb](http://rsalveti.net/pub/ubuntu/kernel/lucid/linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb)

Thanks for the feedback, but the patched kernel does not help my issue. Another thing to note is if I try connecting with wicd, it eventually gives the error "bad password", but I am 100% sure the password is correct. Also it says bad password even if I disable security on my router.

---

### Post by TheVisitors on 2010-04-30
I'm having the same problem (64bit ubuntu 10.04), but if I turn off my routers security I can connect (which isn't wise).

Have you run the update manager? Someone else said this fixed the problem they had (hasn't for me).

---

### Post by amrose on 2010-04-30
Thanks EltonW and TheVisitors ...no luck with either.  Same deal.  

sigh

---

### Post by amrose on 2010-04-30
Wow, I am not sure what I did, or if I did anything exactly.. I added a new connection to my router with the same name and added the router mac address into the settings.  Almost the second I saved it, the other connection began to work.  

She falls down a well, her eyes go cross. She gets kicked by a mule.  They go back. I don't know. :shock:

---

### Post by krage on 2010-05-10
I have the same problem on my Thinkpad t500, it worked fine in ubuntu 9.10 and horrible in 10.04.. :-(

---

### Post by El_Perro_Perduto on 2010-05-24
dito here. Same problem with an "...Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)" on a Toshiba Satellite running an AMD 64bit processor. 

I'm contemplating switching to madwifi as the driver, however, the website says that the current drivers are now obsolete.

Has anyone found a workaround?

---

