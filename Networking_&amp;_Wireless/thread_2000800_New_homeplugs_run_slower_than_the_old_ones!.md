---
title: "New homeplugs run slower than the old ones!"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by v4169sgr on 2012-06-10
Hi,

I've recently purchased some Solwise 500 Mbps homeplug AV [PL-500AV-PIGGY] to replace some Devolo 200 Mbps AV homeplugs.

I run Ubuntu 12.04 64 bit alternate install with LTSP, and use the homeplugs to power some Intel Atom based thin clients [DELL FX170s upstairs] without lots of wiring. The homeplus are paired through to another homeplug local to the LTSP server, which is then wired to a Thomson Alcatel Speedtouch 510 modem / router [straight out of a museum, with four 10/100 Mbps ethernet ports]

The 200 Mbps hopeplus are a 'known good' - nothing wrong with them, just we can do better with faster technology. Since I am 'selling' more use of the thin clients upstairs, I need to show they can work better than before. Replacing the HP T5525s with these modern thin clients has been a step forwards, but it has not really delivered a dramatic improvement, yet.

I plugged in these Solwise homeplugs [according to Expert Reviews they are based on the same chipset as the Devolo ones], but, even after a lot of fiddling to make sure they are paired correctly according to the manual I downloaded in the location they will be used, I still find then a LOT slower than the old 200 Mbps plugs, to the extent that the thin clients actually abort loading the kernel :(

I should say connectivity works fine: DHCP and TFTP all complete successfully, but they never complete the download.

Now, I have a Netgear N600 DGND3700 four port gigabit ethernet modem / router sitting around that I cannot use for the moment as I am on a UK 'ADSL MAX' service, which is apparently incompatible with the N600. I am considering switching ISP so I can use the N600 [and get FTTC!].

**Question: should I expect the Solwise 500 Mbps homeplus to work a lot better withe the N600 gigabit router, or should I return them to the shop?**

Thanks in advance :)

---

### Post by v4169sgr on 2012-06-10
Some more information: the LTSP is configured through one gigabit NIC, which leads to the 10/100 Mbps router and then out. One TC is wired directly into the router; the other two upstairs access the router via a third connection which is wired through the homeplug local to the server downstairs. They 'see' the router via their homeplugs upstairs.

---

### Post by v4169sgr on 2012-06-12
If anyone can offer an opinion that would be appreciated :)

---

### Post by troffasky on 2012-09-08
You'll need to provide some more detailed mesaure of speed than 'slower' before anyone can give you some useful answers. I suggest you run some speed tests with iperf and if you've got a server that's on full time, might as well stick smokeping on it to give you a history of the connection quality.

Also, no reason you can't use the N600 as a gigabit switch in conjunction with your Speedtouch until such time as you can use it as a router.

---

