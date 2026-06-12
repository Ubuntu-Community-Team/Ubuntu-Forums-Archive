---
title: "Creating a Secure internal Network"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by DiGiTGOD on 2009-02-08
Thank you in advance to anyone who can help.

I have a network setup, in which my Ubuntu Desktop (it's running essentially as a server for files, p2p, and Myth, however it's using the ubuntu Desktop release) Machine has 2 Network cards.

One of the networks cards (eth0) connects directly to the network, which in turn connects to a router, and ultimately, the internet.

The second network card (eth1) currently connects to a switch, and then this switch will have some of my neighbours' computers connecting to it (I'll be using a wireless bridge, however that should have no bearing on the setup, I only mention it so as to justify the need for security).

What I would like to do is use the Ubuntu Desktop to run as a bridge between the 2 networks, and therefore allowing the neighbours to connect to the internet.  I do, however, want to be able to restrict their ability to just internet, so filter out any other information (torrent traffic, smtp mail, etc.).  The other issue, is that I will also be using the wireless bridge for my own laptops, and therefore, will need the ability to make certain MAC addresses to appear as if they were in eth0.

What I've thought about doing is running a VM on the Ubuntu Desktop and using one of the virtual appliances to handle everything.  The problem with this is that the machine doesn't have a great deal of RAM, and it's only a 1400 processor, so running a VM would be a tad taxing!

Can anyone point me in the direction of some good tutorials on setting this sort of thing up? or make some suggestions on a valid approach?

Thanks
Martin

---

### Post by FishRCynic on 2009-02-08
a mini isp
(probably voids your agreement with your isp buts thats another issue)

in today's world this is not a good idea but anyway...

depending on what you mean by security... some thoughts/questions

with access to neighbours file shares or without :-)?

unsecured hotspot access by anyone?
this will give your internet ip for everyone's use
(if its tracked your door gets knocked on)

set up your firewall to allow disallow various ip ranges etc.
i.e. set up your ip range set up separately from their ip range and then block it.

are you're neighbours allowing access between ie file sharing or are you advising them to use this only as a gateway?

are you using just a wireless access point or wireless router?
(if its a wireless router use your other router as a gateway
wireless wan port to ethernet port on original router
use a different range for dhcp than your network)

(you do realize your machine/router will have to handle all the traffic being used)

this is just a start - as hardware will definitely play 
a part in making this work

---

### Post by superprash2003 on 2009-02-08
well you could use ubuntu server for this , if your good with command line , if not ubntu desktop.. then enable internet connection sharing either via firestarter or [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) .. then use iptables to block and open ports ..

---

### Post by DiGiTGOD on 2009-02-09
FishRCynic,

I understand your points, and I think I may have not explained things properly...

Neighbours may not be the right word... More friends who live around me...

It will be a secured hotspot... using WPA2-PSK on the access point.

It's an access point and not a router.

It will only be used for Internet access/VPN and possibly a small amount of file sharing from the Server.

As for it having to handle all the traffic, I had assumed this, however I don't know how many hamsters that's going to use up!  I'm presuming my 1.4 Athlon with 512 ram needs more hamsters?

superprash2003,

I'm comfortable with commandline, however, it's run as a master MythTV backend, and this needs a Desktop unfortunately.

I'll have a look into firestarter, however, I don't want the people on the secure part of the network to be able to see the internal wired part of the network...

---

### Post by FishRCynic on 2009-02-09
ufw would even do what you want to do

i was talking more the bandwidth usage rather than the 'puter.
you might notice or might not depending on how heavy the traffic is

---

