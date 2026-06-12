---
title: "Configuring a wired connection (9.10 desktop)"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by Heyjoeh on 2010-10-15
So I recently switched my interent service providers. The technician came today to install the services.

For some reason the internet isn't working on my desktop. The computer says the connection is established and the technician tested the connection on his laptop and it connected no problem. 

In network tools under devices it lists the network device as a loopback interface (lo) I tried setting the device as ethernet interface (eth0) to see if that would fix the problem but as soon as I close out of network tools it switches back to loopback interface

I also tried to ping google.com which froze network tools.

Any ideas?

---

### Post by pricetech on 2010-10-15
Looks like you've lost your NIC.  You should have an eth0, eth1, or eth something.

---

### Post by Heyjoeh on 2010-10-15
> **pricetech said:**
> Looks like you've lost your NIC.  You should have an eth0, eth1, or eth something.

Listed under connections?
I've got autoeth0

I managed to ping my ip address and it worked so I think I'm connected to the internet. It just won't let me browse the web or download anything. All webpages say server not found.

---

### Post by pricetech on 2010-10-15
Are you set up for DHCP; listed as Automatic (DHCP) in network manager ??

Go to a terminal and type ```
sudo ifconfig
```  That should show you what your IP address, Subnet Mask and Gateway are.  Do those look correct for your ISP ???  The technician that set you up should have given you at least that basic information.

What type of connection is it by the way ??

---

### Post by Heyjoeh on 2010-10-15
> **pricetech said:**
> Are you set up for DHCP; listed as Automatic (DHCP) in network manager ??

Go to a terminal and type ```
sudo ifconfig
```  That should show you what your IP address, Subnet Mask and Gateway are.  Do those look correct for your ISP ???  The technician that set you up should have given you at least that basic information.

What type of connection is it by the way ??
the technician was really unhelpful. He hadn't ever heard of ubuntu. He didn't give me any information, he kept telling me that there internet wasn't setup for ubuntu, but I think that's impossible.

I'm setup for DHCP its set under automatic. 

I used the terminal code but I don't have anything to go by to see if its accurate.
I tried entering in my ip my subnet mask and my gateway maunally as well as the DNS code 4.2.2.2

But that didn't change anything any ideas?

---

### Post by Heyjoeh on 2010-10-15
Also its a cable connection

---

### Post by pricetech on 2010-10-15
That DNS server belongs to Verizon.  I recognize it.

What cable company ??

Here's a possibility:

Cable Modems "mate" to the MAC address of the device they are connected to when they boot.  If the technician had his laptop connected, then the modem mated to his laptop's MAC and doesn't want to talk to yours.

With your computer connected, power cycle the cable modem, then try to refresh your IP once the cable modem shows to be connected.  You can reboot the computer to accomplish that.

I'm on and off the forums over the weekend, but I'll try to keep an eye on the thread when I get a chance.

Good luck with it.

---

