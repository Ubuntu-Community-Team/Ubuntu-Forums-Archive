---
title: "Setting up VPN access to my server?"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by Chris of Arabia on 2013-08-29
I'd like to see if I can establish a VPN connection to my server, but due to circumstances think this may be slightly more tricky than normal.

For most of the year, I live and work in Saudi Arabia, which is where my server is (64-bit 13.04). It sits inside my home network and is not exposed to any sort of public access. My Internet connection is provided via a local ISP, but that is in the form a shared connection in what could best be described as a campus arrangement; large feed comes into a residential compound on fibre, and is then distributed to around 400 subscribers. The large feed has proxies, firewalls, DSLAMs and so on at the 'front door', and there's no way I am likely to be able to convince the ISP to provide me with a public IP address that I could make use of.

When I'm not in Saudi, I can usually be found in the UK where I have my real home. What I'd like to see if I can do, is to continue working on my server remotely from the UK. As it's basically a LAMP server, I'm mainly thinking of web-based access, perhaps with the ability to establish FTP connections to upload/download files as necessary.

Given that I don't see any immediate way of presenting my server on a public IP address (I don't really want to expose it that way anyway), I'm thinking it should be possible to establish some form of VPN tunnel between the server and my PC back in the UK. What I'm not too sure about though, is how I'd go about navigating my Saudi ISPs firewalls and what have you. Conceptually, it feels as if I need some sort of middle man out on the Internet to bridge the two ends together; I establish a VPN connection from the server here, then when I am back in the UK, the middle man has a public presence I can connect to from my home PC, and voila, I'm connected to my server and able to do what I need to. One thing that it can't need though, is someone present at both ends to establish the connection and make it work - I just need to permit the server access from this end, then get on a plane home, and be able to pick that connection up.

Assuming this is possible, can someone give me a few pointers on how you'd go about. I'm not averse to subscribing to a paid service if I need to, but that needs to be at a sensible price, bearing in mind there are perhaps only 6-8 weeks a year where I'd need to do this. Your thoughts?

---

### Post by SeijiSensei on 2013-08-29
OpenVPN lets you build tunnels that connect a device with a public IP and one behind a firewall.  This will work if your UK computer has a public address, or is behind a local firewall router that you can configure to forward packets back to your computer.  I use this method to "see" machines in client offices through their firewalls.  On the hidden machine I use the OpenVPN "remote" directive to tell it to connect at boot to the server listening on the public IP.  

I use the simplest method, a [shared static-key]("http://openvpn.net/static.html") arrangement.  All that's needed to make this work is the ability to send UDP packets between the two machines.  Usually I pick an entirely arbitrary "high" port above 1023.  Whether the Saudi networks pass such arbitrary traffic to the Internet, I obviously cannot say.  

The connection uses SSL so the traffic is encrypted from end to end.  You have a choice of encryption algorithms; the default is Blowfish, but I have one tunnel that uses AES256 to comply with US government regulations.

---

