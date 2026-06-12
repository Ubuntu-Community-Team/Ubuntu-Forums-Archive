---
title: "How to securely share files over the internet?"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by Gorbatsjov on 2013-04-05
Hello everybody,

 I'm really lost, I thought it would be really easy to be able to safely share files that are stored on my server over the internet, so that I can access them from anywhere. But it turns out it's almost impossible! I've tried OpenVPN multiple times, Openswan and even ownCloud, but I couldn't get them to work (except for ownCloud, but I disliked it). Am I missing something? Do any of you know an easy way to share files securely over the internet?

This is what I want:
 - To be able to access my files **through Windows Explorer** (i.e. be able to map the shared folder as a network drive in Windows)
 - To be able to open the files directly, without having to download them first (as is the case with a FTP-server), so I can stream my music files
- An encrypted connection, so noboby can intercept the data I am sending to and receiving from the server

This is what I have:
- A fast internet connection (100mbit)
- A Ubuntu 12.04LTS Server
- Two laptops running Windows 7 - these are the machines that should be able to access the files on the server

This is what I've tried:
- Setting up a VPN (using OpenVPN and Openswan, using all kinds of different VPN Clients)
- 'Tunneling Samba through SSL' - although I don't really understand what this means..
- Setting up ownCloud, but that didn't allow me open the whole shared drive in Windows Explorer and I also doubt the security of it
None of these things worked, obviously.

I'm already running a Samba server which allows me to access the server's files through my LAN, but I don't think it's really secure to open the Samba server up to connections from outside the LAN, or is it?

So my question actually is: **How do I make my files safely accessible through the internet?** There must be an easy way to do this, as this is one of the first things you want to do once you have your own server, right?

 Thanks a lot in advance, I'm looking forward to your responses! (please keep in mind that I don't have much experience with Linux networking)
Gorbatsjov

---

### Post by Gorbatsjov on 2013-04-05
If anybody has the same problem, I got it to work using this guide :): [http://www.nikhef.nl/~janjust/CifsOverSSH/VistaLoopback.html](http://www.nikhef.nl/~janjust/CifsOverSSH/VistaLoopback.html).

All you need is an SSH deamon and a Samba server on your server and PuTTY on your client.

---

### Post by g-nisbet on 2013-08-05
> **Gorbatsjov said:**
> If anybody has the same problem, I got it to work using this guide :): [http://www.nikhef.nl/~janjust/CifsOverSSH/VistaLoopback.html](http://www.nikhef.nl/~janjust/CifsOverSSH/VistaLoopback.html).

All you need is an SSH deamon and a Samba server on your server and PuTTY on your client.

Thanks for that, I'm trying to do exactly the same thing, what SSH daemon did you end up using?

Did you work out any way to do it on a non-windows box?

---

### Post by Gorbatsjov on 2013-08-27
I think it was OpenSSH, but I'm not 100% sure because my server is not working at the moment.

---

