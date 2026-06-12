---
title: "NAS Recommendations"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by mildenhall on 2012-01-05
I'd like a 2TB NAS drive that my Ubuntu machines and Android phones can access. Can anyone recommend one please? Preferably a UK version if possible. Thanks

I've seen an Iomega one that lists lots of linux compatability, but not Ubuntu! Doh!

---

### Post by Grenage on 2012-01-05
I'd recommend avoiding the Netgear ReadyNAS products.  Several people here have them (across revisions/models), and all of them have had problems.

---

### Post by mildenhall on 2012-01-05
> **Grenage said:**
> I'd recommend avoiding the Netgear ReadyNAS products.  Several people here have them (across revisions/models), and all of them have had problems.

Thanks - I like to Netgear router so may have gone for one if you hadn't posted!

---

### Post by RagingLoon on 2012-01-05
VortexBox! Buy a pre-built VortexBox appliance or just dust of an old PC, pop in that 2TB drive and you're good to go! Or set yourself up a server running FreeNAS 7.

Edit: Forgot to mention you have to install VortexBox after you dust off that old PC. VortexBox is Fedora-based and it's primary function is a media server, but obviously it can be used as a network share as well. The possibilities are limitless via CLI as it's Fedora-based.

Hope this helps.

---

### Post by mildenhall on 2012-01-05
> **RagingLoon said:**
> VortexBox! Buy a pre-built VortexBox appliance or just dust of an old PC, pop in that 2TB drive and you're good to go! Or set yourself up a server running FreeNAS 7.

A 2TB Vortex box in the UK is £260. The only spare PC I had was given to my parents to reduce the "free telephone support" calls I keep getting so I don't have a spare PC. 

2TB NAS drives from Amazon.co.uk come in at about £180. 

Another option...

Buy a new router with USB NAS support. I have a 1TB USB drive I could use. Also I would then be able to have two wifi networks. One running at 2.4GHz for our phones, and one running at 5GHz for our laptops?

---

### Post by RagingLoon on 2012-01-05
> **mildenhall said:**
> A 2TB Vortex box in the UK is £260. The only spare PC I had was given to my parents to reduce the "free telephone support" calls I keep getting so I don't have a spare PC. 

2TB NAS drives from Amazon.co.uk come in at about £180. 

Another option...

Buy a new router with USB NAS support. I have a 1TB USB drive I could use. Also I would then be able to have two wifi networks. One running at 2.4GHz for our phones, and one running at 5GHz for our laptops?

Buy a Dell OptiPlex GX280 off eBay or something (they're cheap) and throw that 1TB HDD in it and install VortexBox. Why cripple your router just to set up a CIFS with your HDD. I have a router with a 480MHz CPU and over 100MB of free RAM and I wouldn't even do that. I'm just saying.

However, if you do get a new router I'd recommend the  Asus RT-N16. But you'd spend less on an OptiPlex with a 3GHz P4 and a GB of RAM that would be an awesome NAS. I've been up and down this road. :D

Edit...
Here's one on eBay: [http://www.ebay.com/itm/Dell-OptiPlex-GX280-SFF-Desktop-P4-2-8GHz-1-0GB-40GB-DVD-XP-Pro-/320824364852?pt=Desktop_PCs&hash=item4ab29f4f34](http://www.ebay.com/itm/Dell-OptiPlex-GX280-SFF-Desktop-P4-2-8GHz-1-0GB-40GB-DVD-XP-Pro-/320824364852?pt=Desktop_PCs&hash=item4ab29f4f34) 

Here's a GX270 on Newegg: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883155217](http://www.newegg.com/Product/Product.aspx?Item=N82E16883155217) I'd get more RAM (512 isn't the greatest) 2GB is like $30 from Crucial for thees things.


I hope I've given you some ideas.

---

### Post by mildenhall on 2012-01-05
OK, a solution for £42......

[http://www.amazon.co.uk/dp/B002YETVTQ](http://www.amazon.co.uk/dp/B002YETVTQ)

I have a VirginMedia (aka Netgear) superhub/cable modem which has it's MAC address registered with VirginMedia (so must be plugged direct into the cable). I could then plug the new TP-Link TL-WR1043ND into the VirginMedia Superhub,so I have a router plugged into a router. 

1TB Western digital USB hard disk plugged into the TP-Link router that will act as a NAS.

One router is set to 2.4GHz, one is set to 5Gz. So I have 2.4GHz for Android phones, and 5GHz for fast Ubuntu  laptop connections.

What dya fink? Would I still be able to access the USB hard disk on the TP-Link router, if I connected by Wifi via the VM superhub? In other words - how can I access devices on the 2nd router if I connected to the 1st router?

Thanks

---

### Post by RagingLoon on 2012-01-05
Wow, that GX270 has an IDE HDD the GX280's are SATA here's one from Newegg: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883155216](http://www.newegg.com/Product/Product.aspx?Item=N82E16883155216)

---

### Post by carranty on 2012-01-05
> **RagingLoon said:**
> .....an OptiPlex with a 3GHz P4 and a GB of RAM that would be an awesome NAS.

The problem with that is if the NAS box is going to be running 24/7 it'll take up a fair bit of power over a year.  I managed to build a 1GB NAS with a dual core atom processor for <£100 (mostly 2nd hand stuff off ebay). Admittedly a little more than an old Optiplex, but the difference is paid off quite quickly.

---

### Post by RagingLoon on 2012-01-05
> **mildenhall said:**
> OK, a solution for £42......

[http://www.amazon.co.uk/dp/B002YETVTQ](http://www.amazon.co.uk/dp/B002YETVTQ)

I have a VirginMedia (aka Netgear) superhub/cable modem which has it's MAC address registered with VirginMedia (so must be plugged direct into the cable). I could then plug the new TP-Link TL-WR1043ND into the VirginMedia Superhub,so I have a router plugged into a router. 

1TB Western digital USB hard disk plugged into the TP-Link router that will act as a NAS.

One router is set to 2.4GHz, one is set to 5Gz. So I have 2.4GHz for Android phones, and 5GHz for fast Ubuntu  laptop connections.

What dya fink? Would I still be able to access the USB hard disk on the TP-Link router, if I connected by Wifi via the VM superhub? In other words - how can I access devices on the 2nd router if I connected to the 1st router?

Thanks

Your WiFI at 2.4GHz or 5GHz isn't going to make a differance on the load that'll be put on the router that's working as a CIFS with that HDD. I watch the CPU's clock up and my load average spike over the short term on my servers under a media streaming load and while transferring files, etc... 

Bandwidth isn't going to be your limiting factor, it's going to come down to the CPU and RAM in router that'll hurt you. You can try it, but personally I'd kill any one of my routers if I used one to replace even my small 2TB media server. 

Ultimately, you may just have to try it, if that's what you want to do? You're experience may vary, I have a network with over a dozen active LAN's and about that many WiFi devices at any given time.

---

### Post by RagingLoon on 2012-01-05
> **carranty said:**
> The problem with that is if the NAS box is going to be running 24/7 it'll take up a fair bit of power over a year.  I managed to build a 1GB NAS with a dual core atom processor for <£100 (mostly 2nd hand stuff off ebay). Admittedly a little more than an old Optiplex, but the difference is paid off quite quickly.

My 2TB media server (a Dell OptiPlex GX280 w/GB RAM running VortexBox) is $4.88 per month 24/7 And my FreeNAS box with 10TB of HDD's a Sempron 2.8 GHz CPU with 4GB of RAM is $5.64 per month 24/7. I have meter.

Both are by far cheaper to keep on than my PC which is all of $20.00 per month if let her run 24/7. And you can just tap the power button on the VortexBox and let it shut down if you're not using it and just tap it to fire it up when needed. That's what I'd do, but mine are accessible to a small group of friends via the internet so, they'd be screwed if I shut 'em down. 

You already know what I'd do, but honestly a router should be fine (if you don't expect it to do too much).

---

### Post by mildenhall on 2012-01-05
> **RagingLoon said:**
> Your WiFI at 2.4GHz or 5GHz isn't going to make a differance on the load that'll be put on the router that's working as a CIFS with that HDD. I watch the CPU's clock up and my load average spike over the short term on my servers under a media streaming load and while transferring files, etc... 

Bandwidth isn't going to be your limiting factor, it's going to come down to the CPU and RAM in router that'll hurt you. You can try it, but personally I'd kill any one of my routers if I used one to replace even my small 2TB media server. 

Ultimately, you may just have to try it, if that's what you want to do? You're experience may vary, I have a network with over a dozen active LAN's and about that many WiFi devices at any given time.

Re : 2.4GHz and 5GHz.

2.4GHz as my Galaxy Ace and my wife's Galaxy S can't cope with 5Ghz. The problem with 2.4GHz is that most of the channels near by are use up and clash. No one has a 5GHz network locally, so I'd get no clashes and it's faster, especially as I want to stream to/from my UK Tivo boxes.

Anyway, how will I be able to access PCs on Router#2, from a PC connected to router#1?

---

### Post by RagingLoon on 2012-01-05
> **mildenhall said:**
> Re : 2.4GHz and 5GHz.

2.4GHz as my Galaxy Ace and my wife's Galaxy S can't cope with 5Ghz. The problem with 2.4GHz is that most of the channels near by are use up and clash. No one has a 5GHz network locally, so I'd get no clashes and it's faster, especially as I want to stream to/from my UK Tivo boxes.

Anyway, how will I be able to access PCs on Router#2, from a PC connected to router#1? 

Keep in mind, your WiFi band isn't going to alleviate stress on the router when using it as a file share. Having your WiFi turned on whether it be 2.4GHz or a 5GHz band will just eat up more resources. Again, if you don't expect to much out of it you'll probably be ok.

You'll have to disable the WAN on router #2 and set it up as router and not a gateway along with making sure the DHCP server's disabled on router #2. In a nutshell.

Edit: Moreover, you'll want to be sure and set an IP for router #2 outside of router #1's DHCP server's range. In the end, all your devices will see anything connected to router #2 as if they were connected to router #1.

Almost forgot: Your second router will be connected through any one of it's LAN ports to any one of router #1's LAN ports. The WAN port will not be used on router #2 unless your firmware can turn it into a LAN port. Almost any stock router can be used this way just be sure to do all of the aforementioned. Put your strongest router up front as #1 and the weaker router as #2 and plug the USB into which ever router supports it.

---

### Post by RagingLoon on 2012-01-05
> **mildenhall said:**
> OK, a solution for £42......

[http://www.amazon.co.uk/dp/B002YETVTQ](http://www.amazon.co.uk/dp/B002YETVTQ)

I have a VirginMedia (aka Netgear) superhub/cable modem which has it's MAC address registered with VirginMedia (so must be plugged direct into the cable). I could then plug the new TP-Link TL-WR1043ND into the VirginMedia Superhub,so I have a router plugged into a router. 

1TB Western digital USB hard disk plugged into the TP-Link router that will act as a NAS.

One router is set to 2.4GHz, one is set to 5Gz. So I have 2.4GHz for Android phones, and 5GHz for fast Ubuntu  laptop connections.

What dya fink? Would I still be able to access the USB hard disk on the TP-Link router, if I connected by Wifi via the VM superhub? In other words - how can I access devices on the 2nd router if I connected to the 1st router?

Thanks

The TL-WR1043ND has a 400MHz CPU with only 32MB of RAM. The RT-N16 would be more suitable for what you want to do, but it doesn't have 5GHz WiFi [http://www.amazon.co.uk/RT-N16-Wireless-Router-802-11n-FTP-Server/dp/B003HAL4ZA/ref=sr_1_1?s=computers&ie=UTF8&qid=1325797244&sr=1-1](http://www.amazon.co.uk/RT-N16-Wireless-Router-802-11n-FTP-Server/dp/B003HAL4ZA/ref=sr_1_1?s=computers&ie=UTF8&qid=1325797244&sr=1-1)

---

### Post by 1clue on 2012-01-05
+1 for using a second router the way RagingLoon suggests.  I would turn off the radios on this router, hook it up on ethernet and just let it sit there.

I already do this sort of thing with an Apple AirPort.  It hooks up to what used to be my home stereo, so I can use Apple's AirPlay through phones/laptops/whatever throughout the house to play music.

---

### Post by W00ster on 2012-01-06
I bought a fully populated 5x3Tb _[Synology DS1511+]("http://www.synology.com/us/products/DS1511+/index.php") _last year and have been using it as my main storage system. I run OCFS2 as my clustered file system and have set it up with 2 x 1Gb network cards bonded for optimal speed. Works like a charm from all my Ubuntu  boxes.

You can also connect 2 expansion boxes for  total of 45Tb storage and the NAS itself runs Linux and can be managed from your browser.

A real neat thing is that you can add disks of different sizes, Say you have 5x1Tb disks and wants to start adding 3TB. If it is set up as RAID-5, just swap one of the 1GB for with the 3GB and the system will allocate 1GB as part of the RAID. Swap 2 more and the usable space increases with 2TB with a mix of 1 and 3 Tb disks.

---

### Post by Pat201 on 2012-01-07
I also agree with RagingLoon's router setup.  That's exactly how our house is set up here with a couple of old Netgear wireless routers.  I've never measured the throughput but I've never really noticed a lag except for when our crappy ISP is experiencing problems.  We usually have up to 10 devices running including Windows, Linux, Mac OS and whatever my son's Xbox is streaming stuff all over the place..... probably half wired and half wireless.

Another place I like to use for older closeout type models of stuff is Geeks.com.  You can find some good deals there on stuff but I don't know whether their shipping is reasonable to the UK.  I have to admit I'm becoming more and more addicted to Amazon with their free super saver shipping.  :)

Oh BTW, the only thing I'd be concerned about if you go the "old PC server" route is whether or not the BIOS will support whatever size drive you want to stick in there.... you might check before you buy.

---

