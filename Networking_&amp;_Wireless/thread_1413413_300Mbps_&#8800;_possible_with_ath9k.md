---
title: "300Mbps &#8800; possible with ath9k ?"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by Everybody Loves Hypnotoad on 2010-02-22
Is it correct to assume that it is not possible to get a higher transmission rate than 54Mbps (= 802.11g) from n equpiment when using ath9k in a 2.4GHz network?

I have a dlink router. dir-655 (atheros-based, 2.4GHz only) and a dlink dwa-645 (atheros ar5008 cardbus) card. They are set up according to dlink's instructions for getting 300Mbps out of them (40MHz channel width aka channel bonding aka wideband, and WPA2), and of course delivers max speed in some very popular operating systems. 

In ubuntu though, it has for a long time been crippled to 1Mbps using ath9k (= totally useless), and a real transmission rate of say 3-4Mbps when using dlink's drivers with ndiswrapper. Now with current updates for 9.10 and karmic kernel module backports (to get updated compatwireless) it is as fast as in the laptop's built-in intel 3945, which means 54Mbps. But where are the rest of those missing megabits per second?

I think the wiki page about compatible wireless adapters should be fixed so that it separates n equipment from the old stuff, and also so that it shows what speeds can be expected when used with current drivers available.

I am thinking atheros tech is not the way to go (unless you're into pentesting) in ubuntu, and that something USB with the rt2870  chipset like the wusb600n-eu should be recommended for those who want to get n-speeds out of their n-capable adapters.

<rant>
Going with iwlwifi mini-pcie stuff like intel 4965, 5300 or 6200 might have been a possibility except that intel is not very clear on their newer cards' channel bonding abilities in the 2.4GHz band. 4965 can absolutely not do it, so it will be limited to 130 or so Mbps without a dualband router, the others I am unsure about. To that comes the inability of my HP laptop to accept non HP-branded internal wireless chips (maybe except for broadcom cards)(thank you HP!).

</rant>

---

### Post by northd_tech on 2010-02-22
Well, I'm at home on a Comcast "High Speed" wireless connection (the fastest commercial ISP in my area) using an 802.11n Broadcom "4328" with the proprietary Broadcom STA driver, and I just ran a speed test earlier under Jaunty 9.04 ubuntu.

These were my download speeds that I saw using a Firefox "bandwidth tester" plugin:

Mon Feb. 22, 2010 bandwidth speed tests
Down- 16317, 35848, 14815, 40460, 42974, 16957 kbps
upload- 427, 484, 477 kbps  [Yep, DSL speeds]

These are probably the best speeds that I've seen under ubuntu, and I have disabled IPv6 and also gone to static OpenDNS (which both made noticeable differences).

This is waaaaay better than my Qwest connection at work BTW.

Of course Vista is still much faster (but has the countless "souvenir" problems)...

I'd say you're doing pretty well from what I've seen and read at that 1-4Mbps.

Incidentally, my NVIDIA nForce 100Mbps cabled ethernet wasn't noticeably any faster than the wireless (if not slower) when I ran the same test sequences last night.

edit:  I am considering going back to ndiswrapper for speed testing purposes for a while though- I'll be sure to post my results as I get time.

---

### Post by Everybody Loves Hypnotoad on 2010-02-23
Thanks for the reply northd_tech. Maybe I should not be this obsessed with the wireless rate, but using the 100Mbps built-in NIC I get 50-60/10-12Mbps when doing online speed tests on a nearby server, using the wireless I don't get more than 15/5.

Since I'm on the other side of an ocean I doubt openDNS would make a difference in a good way, but I will check, and I will alsoo try and disable ipv6 (since neither my ISP nor wireless equipment offer that anyway).

Those are some impressive figures there 30+ and 40+ Mbps, but how come you get less tahn half a mbit in upload?

---

