---
title: "CyberGhost VPN setup"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by Floppyjoe on 2010-01-23
Does anyone know how to set up a VPN connection for CyberGhost in Ubuntu Linux?

I understand that it makes use of OpenVPN and OpenSSL.
The .crt and .key files can be copied over from a windows setup. 
It uses a TAP interface in Windows.  I tried making a ndiswrapper driver with the tap driver files but no luck there.

I installed vtun but not sure if this is what is needed.

Does someone have some ideas?

---

### Post by Chiapo on 2010-03-13
I haven't tried CyberGhost, but have successfully set up UltraVPN by following this How-To:
[U]
[/U][How to Setup Open-Source UltraVPN in Ubuntu | Kabatology ~ Open Source, Linux]("http://www.kabatology.com/11/24/how-to-setup-open-source-ultravpn-in-ubuntu") 
[U]
[/U] I had previously installed OpenVPN using Synaptic.

I was amazed at how easy it was to setup UltraVPN!

Hope this helps!  

Cheers!

---

### Post by Z06Gal on 2010-04-21
I just got ultravpn going is it normal for the internet to slow down so much?  I mean it is big time slow.  When I disconnect it, my connection speeds are perfect.  I tried opendns, google dns, and my isp and it is slow in all when vpn is active.  Thanks.

---

### Post by afrodeity on 2010-06-21
Please post .crt and .key files for cyberghost.

UPDATE: I downloaded the windows client and booted up virtualbox. I now have all the keys but not the gateway information and other setup details.

---

### Post by djtm on 2011-03-10
Any updates here? Did anybody get it running?
You can get a free 10 G premium year right now with the code quale157. ;)

---

### Post by kapetr on 2011-04-06
I cant get it to work in U10.10.

The server is connected. tun and routes created, but no communication is possible :-(

And after timeout the openvpn ends.

--kapetr

---

