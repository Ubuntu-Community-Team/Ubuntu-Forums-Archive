---
title: "Designing a multi-service server. Can Ubuntu handle it all?"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by Rapture2k4 on 2008-12-03
Good evening all,

I'm wanting to design a machine or two for various home network elements. I have an idea of what I want to design, but unsure of the capabilities of Ubuntu. Let me start off by saying that I am a network technician by trade and am very familiar with Cisco devices and Windows XP. I don't have too much experience with Windows Server 2000/2003 aside from setting up DHCP scopes so I'm not tainted yet when it comes to server OSes.

Here's what I need:
[LIST]
[*]Router
[*]Stateful Inspection Firewall
[*]HTTP Web Proxy/Cache w/Port Address Translation
[*]DHCP Server
[*]QoS Filtering
[*]Antivirus software, maybe part of the firewall?
[/LIST]

Here's what I want:
[LIST]
[*]Multi-terabyte file server
[*]Internal LAN video/audio streaming (movies and the like)
[*]Web server
[*]Teamspeak server (or similar)
[*]VPN capabilities
[*]VoIP capabilities (maybe.. future prospect)
[*]Boot from network drive capabilities (I'll have 4-5 terminal systems in the near future)
[*]802.11n services for mobile devices and cellphones
[/LIST]

What I have on my wishlist
[LIST]
[*]AMD Dual Core System
[LIST]
[*]AMD Athlon X2 4850e 45W 2.5Ghz
[*]2-4GB DDR2 800 Ram
[*](6-7x)WD Caviar WD1001FALS 1TB 7200 RPM SATA 3.0Gb/s Hard Drives
[*]2-3 Gigabit Ethernet NICs
[*]ChiefTec Aegis CX-05B-B-M-OP ATX Mid Tower (Awesome case!)
[*]500-700W PSU
[/LIST]
[*]Mini-ITX HTPC w/MythBuntu or similar
[/LIST]

Systems I currently own:
[LIST]
[*]D-Link 802.11b/g router (really an advanced switch)
[*]Toshiba P206-series Laptop w/Vista Home Premium
[*]AMD Athlon 64 X2 Gaming Rig w/XP Pro x64 & Ubuntu Desktop 8.10 x32
[/LIST]

Now, I know that's a tall order and most would think overkill for a modest home network, but this is more for personal experience and practice.

I recently read SammyDee's article on [_Ubuntu Firewalls/Routers_]("http://ubuntuforums.org/showthread.php?t=926001&highlight=firewall+router"), which was a nice how-to. So I see that making a linux based router/firewall is a very simple task. What I'm curious about is what I will really need for system specs for the above mentioned services. I'd also like to replace my D-Link router and look for a cheap 802.11n wireless access point and see if I can come across a cheap 8-12 port switch. I'm sure I can find a stripped out Cisco switch on eBay or at a nearby military base. Or would I be better off with a store-bought WiFi router? My D-Link makes it impossible to turn off it's PAT and DHCP services (or go into a "pass through mode") which is why I'd prefer a stand alone WAP or two.

**_[SIZE="4"]Security:[/SIZE]_**
Is it possible for Ubuntu to become a WiFi master controller? I will not be using WEP and since WPA was recently cracked, I may have to do some type of certificate/thumbdrive system which I'm completely clueless about. I would also like to do "port-security" as Cisco calls it on my switch and router for each device. I will also need to connect to my home network while I'm on the road so VPN services would be nice, but I haven't seen any articles on that without going into specialized Linux OSes which would require another machine.

My firewall/proxy/web-cache/DNS will need to have a blackhole listing and look into meta-tags for HTTP traffic coming into my network (I've got a young daughter who I expect will be web surfing as soon as she can read). I know the big enterprise servers are capable of this, is Ubuntu? I am also fighting with myself on the aspect of having all those services running on one machine. I know it is safer to have the router/firewall as one box and the other stuff as part of my extranet, but my Mini-ITX router died recently (hence this article). Would it be safe enough?

**_[SIZE="4"]Server Services:[/SIZE]_**
I know I've got alot listed on my wishlist. I'm really curious about these technologies and want to try them out. I'm really curious about doing a bootable network drive. My wife loves World of Warcraft and wants to get into "Multi-Boxing". So I think it would be much easier (and cheaper) to have the multiple machines all use the same single hard drive on my network. I've seen it done on a couple websites using Windows Server 2000, but I wonder if it is possible via Ubuntu. The file server part is mainly going to be used as a backup system for home movies (my wife is converting all of our old VHS tapes to DivX and wants to keep them for whatever assinine reason) and streaming said movies to our soon to be bought HTPC in the living room. 6-7 Terabytes worth of hard drives is alot of space, but I'll be doing some type of mirroring and/or incremental and differential backups on 2-3 of them.

Since there will be some WoW going on, I'd like to have a teamspeak style server going for my internal LAN but also accessible from the web. Anyone know how much bandwidth is needed for this? I only have an 8Mbit pipe through my cable modem (we may be switching to DSL soon) and I will need to setup some type of QoS for that, the web-server, online games, and HTTP/E-Mail traffic.

I haven't even begun researching web-servers, but I can't imagine it is very difficult if I've already got the infrastructure setup.

**_[SIZE="4"]Final Remarks[/SIZE]_**
What I'm really looking for is hardware advice. Is the machine I designed overkill? Am I better off with 2 machines and just doing an Extranet setup? Can anyone suggest a good AM2/AM2+ motherboard with onboard GigE that works well with Ubuntu (or known good chipsets)? If not, are there any really good PCI/PCI-e 1x NICs that work well? Do the ATI based chipsets have video driver issues? I.E. The 790GX boards with ATI HD 3300 on-board. Know of any good rack-server style keyboard/monitor/mouse devices that are cheap? As much as I want to do all command-line for the router, I'd like to still have some type of GUI for emergency web surfing for updates/patches. Know any good sata controllers that are cheap, have 6+ internal connections, can do RAID 1/5/10/15 and work with Ubuntu? Disk duplexing might be a good option too. Can you suggest a good 8-12 port GigE switch that is cheap and reliable? I can go on for ages with questions.

I've been searching around the forums and google trying to find the answers so all these questions, but either I'm entering the wrong search patterns or not many people have attempted this large of a project at home.

Thank you so much for your time and I apologize for the wall of text.

---

