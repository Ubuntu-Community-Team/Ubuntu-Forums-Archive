---
title: "Issues with network configuring?"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by Colo2 on 2010-12-23
Hello. I'm having some issues with my Ubuntu machine. I want to make it's internal IP address: 192.168.1.113

At the moment:

> ifconfig
```
eth1      Link encap:Ethernet  HWaddr 00:e0:4c:69:4f:88  
          inet addr:192.168.1.159  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe69:4f88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9857096 (9.8 MB)  TX bytes:180881615 (180.8 MB)
          Interrupt:19 Base address:0xc000 

```

However, I've done this in my network manager:


[IMG]http://i54.tinypic.com/2uh08bt.png[/IMG]


Then:

> sudo /etc/init.d/networking restart

```
* Reconfiguring network interfaces...                                                                                [ OK ] 
```

And it still says my old IP: 192.168.1.159

Anyone know what I'm doing wrong?

Oh, and, for some reason, my 

> sudo gedit /etc/network/interfaces 

file is totally blank. Nothing in it.


Thanks

Tom

I know that I'm editing the right connection, because there's only one.


Anyone know whats wrong?

---

### Post by Colo2 on 2010-12-23
;\

---

### Post by miegiel on 2010-12-23
> **Colo2 said:**
> ;\

That's exactly how I would have done it. Have you tried rebooting instead of running ```
sudo /etc/init.d/networking restart
``` (though it should make no difference).

---

### Post by dandnsmith on 2010-12-23
You have it, apart from individual addresses, exactly as I have mine.

I only had one problem - getting the dns address to stay what I wanted (had to do it a couple of times).

I agree with the reboot comment - can often fix things where you don't know why they don't quite look correct.

Check to see if there's a save-configuration option which I've forgotten.

---

### Post by Colo2 on 2010-12-23
Hey
Yeah, rebooting fixed it, thanks :) Saves me having to change the port forwards to that IP :P 

Thanks guys

---

