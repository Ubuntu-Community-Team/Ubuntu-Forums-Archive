---
title: "which wireless router to purchase with no issues with ubnutu"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2009-12-28
Hi I need to purchase a wireless router or switch which ever is correct for my set up, I have a pc with internet connection then i need cable out to wireless router so laptops can all share internet, i also use VNC to pc from 1 laptop, hope some1 can help or steer me in right direction for what i need

---

### Post by msw on 2009-12-28
There is big difference between a [router and a switch.]("http://compnetworking.about.com/od/homenetworkhardware/f/routervsswitch.htm") In any case, neither are operating system dependent and will work with Ubuntu.

---

### Post by 32034 on 2009-12-28
Are you possibly meaning which wireless adapter/card to buy because that is the real headache for most people! 

I bought a [D-Link WDA-1320]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833127080") PCI card and it worked GREAT in Ubuntu 9.10 with no problems. I'm using the ath5k driver, rather than madwifi.

---

### Post by spiky001 on 2009-12-28
no 32034 the internet comes out of the pc i need it to go into a wireless what ever router/ hub / switch via ethernet cable. Then the laptops can all share the internet at once, I thought the routers supplied the net connection directly but it has to come from 1st pc, hope i made sense wasn't sure what i needed exactly

---

### Post by 32034 on 2009-12-28
Internet --> Desktop --> Wireless router --> Laptops?

Correct?

---

### Post by ddarsow on 2009-12-28
Get a Linksys 
If you install DD-WRT instead of the default firmware they are truly awesome. DD-WRT allows, among other things, for you to set static IP addresses for the machines on your home network making things like SSH much easier.

The best configuration is:

Internet --> modem --> router --> computers

The above is much more secure than: 

Internet --> computer --> router --> computer

---

### Post by spiky001 on 2009-12-28
Yes internet via mobile dongle pc- router -network, it,s the mobile dongle that forces this set up

---

### Post by 32034 on 2009-12-28
Desktop is running Ubuntu or Windows?

---

### Post by spiky001 on 2009-12-28
dual boot xp the kids need to play games so need to work with both, also i VNC in to pc from laptop just to make things worse

---

### Post by 32034 on 2009-12-28
The mobile broadband dongle works in Ubuntu and in Windows? I'm asking a lot of specific questions to help isolate your issue, unlike other people that just blindly tell you that your configuration is wrong and they didn't know you were getting your internet from a mobile broadband provider.

---

### Post by spiky001 on 2009-12-28
sorry about that i just thought that as i connect at the moment internet pc laptop i presummed it would be the same forgive me if i,m wrong. Hence the ethernet to router

---

### Post by running_rabbit07 on 2009-12-29
I got your PM. From what I am reading you need a the same wireless router that we normally use with a cable modem with the exception that the iput side of the router will be connected to the NIC on the PC and may then supply internet to the laptops. I router will have the capability to subnet addresses to the laptops and will only will route them to the PC. Does your Desktop have 2 NICs? One that connects to the modem/ISP and another to connect to the router? If the side where you get your service is from a wireless source, then your network will slow dramatically when feeding multiple systems from it.

Basically this is how your setup should look. 

___________ = Wired

~~~~~~~~~= Wireless

ISP/Modem______PC____Router~~~~~~~Multiple Laptops.

Edit; I just read the last few posts. As long as you have a decent connection speed from your ISP with the mobile broadband, the above setup should work.

---

### Post by spiky001 on 2009-12-29
yes that is how it will look isp connects via usb so what router would be good or is there not much difference Linsky/ Netgear

---

### Post by running_rabbit07 on 2009-12-29
> **spiky001 said:**
> yes that is how it will look isp connects via usb so what router would be good or is there not much difference Linsky/ Netgear

I prefer Cisco/Linsys over Netgear, but that is just a personal preference.

---

### Post by 98cwitr on 2009-12-29
I'm a netgear guy, had mine for over 3 years and not a single issue. Works great.

---

### Post by spiky001 on 2009-12-29
ok thks ppl for your help

---

