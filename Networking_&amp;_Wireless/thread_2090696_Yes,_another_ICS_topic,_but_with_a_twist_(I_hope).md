---
title: "Yes, another ICS topic, but with a twist (I hope)"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by ChinaJustin on 2012-12-03
OK, so I've found many topics about sharing an internet connection. Most of them generally have to do with the following:

1) "I have a wired internet connection and want to share it via wifi on my laptop."
2)  "I have a wired internet connection and want to share it through a  second NIC that is wired directly to my second computer/via cross-over  cable."

I also know about the (outdated and filled with poor English and lacking in coherency/ease) Wiki over here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

My situation is a tad bit different, and I haven't been able to find an exact solution for me.

I'm  using Mint 13 32-bit XFCE on one computer with two NICs. I want to  share the internet connection (coming in via eth0) through the other NIC  (eth1) and out through a **wireless router**.  I have it set up as a wireless access point (turned of DHCP, etc.) and  it works fine through WinXP. But the ICS wiki noted above isn't quite  what I need, because it first (under the IP Tables section) has just ONE  computer connected to the network (via, yet again, a crossover cable),  while I want to be able to connect multiple devices wirelessly; second,  the "Advanced" networking section has you installing dnsmasq, which  (from one post I found) unless you uninstall dnsmasq-base, dnsmasq won't  work. Unfortunately, this also uninstalls Network Manager, thereby  messing up my internet connection and making it so I can't connect to  install dnsmasq. Installing dnsmasq does nothing, and rather gives an  error message... something about socket 53 being used already (sorry I  don't have the exact wording, I'm on my other computer at home).

Before  anyone asks, it's not as simple as plugging the wireless router into  the wall. I'm in China, where they like to control the internet; at this  university I'm teaching at, they require a login program under Windows  (an 802.1x security login program) that, fortunately, I can just use  Network Manager to connect with. However, trying to get a router to  connect and STAY connected isn't possible. I've tried two different  routers on the network here, and they always get logged off randomly  after a few minutes and have to be logged back in through the router's  setup page (annoying to say the least).

So, looking at the ICS wiki, can anyone suggest any changes that I would need to make in order to do the following:

ISP<<--->>eth0 Ubuntu Gateway eth1 <<--->> wireless router <<--->> multiple devices

Do I need the Ubuntu desktop to do DHCP? Or can I just get the router to do it with some other settings tweaks? Thanks!

---

### Post by ChinaJustin on 2012-12-05
Someone has suggested setting up a VM, installing Squid in the VM, and using it as (basically) a proxy server.

Only problem with that is that since this is an older computer, I have just under 1GB RAM, so even installing VirtualBox with Lubuntu and setting a minimum of 256 MB RAM really slows down my computer. Granted, I just need it as a server, but that seems a bit more involved than what it should be. 

Of course, the whole ICS issue with Linux seems a bit more involved than it should be to begin with, but that has been discussed in other threads I know. I will (just this one time) say that this is where Windows trumps Linux from a usability standpoint, and that being the ability to do ICS by bridging adapters or "sharing internet connection". Having to do all of these changes on IP tables (according to the above referenced/outdated Wiki) is IMHO a bit ridiculous.

But I digress.

Anyone else have any ideas or clues on how to tweak the wiki for my particular situation?

---

