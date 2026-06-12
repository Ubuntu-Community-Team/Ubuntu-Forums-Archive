---
title: "Static IP's, VirtualBox, Port Forwarding..."
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by robmypro on 2009-02-13
I am in the process of converting my Windows network to Ubuntu running VirtualBox (both are excellent IMO). So far everything is going pretty smoothly. I do have one situation I haven't quite figured out yet.

I have a Windows XP machine on my network (static IP 192.168.1.80) that hosts a simulator/game I play (Falcon 4). I forward ports 2934 and 2935 from my router to this static IP. Now I am setting up Ubuntu with VirtualBox, and one of the VM's is going to run XP (and Falcon). I have the VM setup and Falcon runs surprisingly well (host only, I'm not actually playing it from the guest). 

How do I configure my setup so the XP VB guest machine gets static IP 192.168.1.80 and gets this traffic on ports 2934/35? I have the router part worked out, but I am clueless on the VB/Ubuntu side. Also, does Ubuntu need to be a static IP? Right now it is DHCP. 

I tried changing the guest (XP) machine to use a static IP but it didn't work. Yeah, I'm pretty green.

Ideas? I'm new at this so go easy on me. :-)

Thanks guys.

---

### Post by NetworkGuy on 2009-02-13
I think..

Change the network properties of your virtual machine so that your Ethernet card is set to host interface.  Then click on eth0 or whatever interface you want it to use.

Set your static IP address within Windows after you reboot.

---

### Post by robmypro on 2009-02-13
> **NetworkGuy said:**
> I think..

Change the network properties of your virtual machine so that your Ethernet card is set to host interface.  Then click on eth0 or whatever interface you want it to use.

Set your static IP address within Windows after you reboot.

Damn! Worked like a charm. Talk about fast service too!

Thanks Mate!

---

### Post by delatun on 2010-02-27
Great post!! That helped out quite a bit. I bridged my adapter and that allowed the physical router at my place to become the DHCP server instead of the VirtualBox. Now it's just like another client on the network. Works really well. 

Saludos,
Jimmy

---

