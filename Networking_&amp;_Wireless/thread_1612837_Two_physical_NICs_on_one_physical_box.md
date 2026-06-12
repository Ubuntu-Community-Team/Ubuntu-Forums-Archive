---
title: "Two physical NICs on one physical box"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by bibble235 on 2010-11-03
Hi folks,

Managed to get my r8169 driver working after exchanging my RealTek 8169S-32 for 8169SC.

Now I have a problem with having two nics.

I have an ADSL/Router which I connect to. This server is used as a mail server and a web server for home.

Interfaces are set as follows

auto eth0
iface eth0 inet static
        address 192.168.1.127
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

auto eth1
iface eth1 inet static
        address 192.168.1.128
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

If I enable both nics the internal network works but getting out does not. i.e. ping yahoo.com does not work. Taking one down makes it work as before.

Configured on my router is 3 virtual servers (well more really) which point to .127 and let me ssh, mail and web serve. All has worked well for years but now this is broken.

Scanning the web and this forum points to the fact I need to probably configure something in ARP or routes or both. I am a bit new and only know some aspects of this kind of configuration so if you have an answer please be gentle.

Iain

---

### Post by SeijiSensei on 2010-11-03
You can't have them on the same network segment; in your case they're both in 192.168.1.0/24.  

You could set up the second NIC to connect to a different network, say 192.168.2.0/24.  Why do you need the second NIC at all if you only have one network, though?  A second network interface would be useful if you want to route traffic between two different network segments.  Otherwise I'd just leave it disabled at boot and ignore it altogether.

---

### Post by bibble235 on 2010-11-04
Thanks for replying,

Key reasons is on my internal lan the PS3 and 2 PCs drain the server when we are all watching an avi. If the best way is to put them on a second lan how would I get the PS3 to get out to the net from this second lan

---

