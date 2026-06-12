---
title: "Total loss of network wireless and wired after power outage."
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by Caesonia on 2009-09-02
To date, my networking capabilities on Ubuntu have been very stable. However, after a bizarre power outage the other night - which was longer than the backup battery - I have completely lost my networking capabilities, both wired, and wireless. 

The wireless connection just shows ' device unmanaged' now, and I can't seem to find out exactly what is supposed to be managing it on this system. The broadcom 34 driver is what is running it, and it is installed. in the /etc/networking/ nothing comes up when enxt to wlano.

Both the wired cards are also not functioning. Netstat on each wired card shows them listening on all the right ports. Though the system recognizes they are there, one gives no connection at all. This is a separate card that I have not used in a while, because the one that came with the board is faster.  It's a linksys card and its about 9 years old. yeah, it could be dead now, but,it was working before this. 

The second card, the one on the mboard, also is failing. You have to keep reconnecting it, and it will work for about 20 seconds, before dropping. The router recognizes it, and reserves an IP for it through the mac - so the router knows - as well as it has been assigned a static on the NIC itself. 

I just find it hard to believe that a power surge blew out all cards, and especially when you have one card now saying - unmanaged -. 

This sounds like an OS update problem.

I am a medium Linux user and have used different Linux OS'es but I have also had really good networking experiences. I admit it has kept me from looking as hard as I should have at the managing software. Wireless less so because, well, its wireless and that comes less into my realm. 


I would REALLY appreciate some good points to start, and definitely don't mind going through the command prompt.

I have tested the wireless and wired service with my Vista laptop, and it works just fine.

Ta in advance.

---

### Post by Iowan on 2009-09-02
Check basics: **ifconfig -a**, **lshw -C network**, */etc/networking/interfaces*. Interfaces defined in */etc/networking/interfaces* will probably show as unmanaged.

---

### Post by Caesonia on 2009-09-03
> **Iowan said:**
> Check basics: **ifconfig -a**, **lshw -C network**, */etc/networking/interfaces*. Interfaces defined in I]/etc/networking/interfaces[/I] will probably show as unmanaged.


Thanks for the command. I really wasn't sure how to get at the unmanaged bit. All Ifconfig showd me was that the device didn't exist.

I DID solve the problem though. First, to verify healthy cards, I used an older 8:10 disk to boot from and run. Once all cards checked out, I looked at the interface file again.It was strange, and confirmed what I saw earlier - text that maybe shouldn;t be there.

Using the GUI interface to assign a static IP. I saw

address: XXX.XXX.XXX.XXX
netmask: 255.255.255.0
broadcast XXX.XXX.XXX.255
network XXX.XXX.0.0

Network? I never saw gateway, besides which the network address would have been wrong for the gateway, and indicated a different level of ip.....

Not sure how this got corrupted.

So, I copied the one from the 8:10 disk, and then rebooted. Got the connections back, and have now chosen to let the router just reserve a lease for the time being, before I start recreating the virtual IP's I need. I am a bit leary of resetting the IC back to static, because of what happened. I want to understand first, though it will need to be done soon, because I have to get those virtual IP's back up.

Thanks for your help.

---

### Post by Iowan on 2009-09-03
> **Caesonia said:**
>  Got the connections back, and have now chosen to let the router just reserve a lease for the time being, before I start recreating the virtual IP's I need. Personally, I like using static leases - simplifies client setup.

---

