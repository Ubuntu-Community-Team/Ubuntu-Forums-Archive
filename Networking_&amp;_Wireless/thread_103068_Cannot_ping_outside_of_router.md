---
title: "Cannot ping outside of router"
date: 2005-12-13
forum: Networking &amp; Wireless
---

### Post by 5-HT on 2005-12-13
Hi, I'm wondering if someone may be able to help me out in terms of a nagging issue I've been having since installing Ubuntu (this has occured under Hoary and Breezy)?

For whatever reason, I'm unable to ping outside of my router (or do a trace route). :(

Apart from that, connectivity is great (web browser, apt, sftp, etc...).

I can ping the router and any computers behind it, but after the gateway there's 100% packet loss.

I've tried using both IP's and domain names.

I've tried using both DHCP and a static IP.

I've tried using both the router as my DNS server, and my ISPs DNS servers.

I have no issues doing so from a windows box (just to rule out any router settings that may have anything to do with it...well under windows, perhaps there's some conflict under Linux).


Anyone have any ideas? :confused: 

It's not a big issue as the connectivity is there, but in terms of possible future problems, it would be nice to get this working for diagnostic purposes.

Thanks for any help!

---

### Post by earobinson on 2005-12-13
I assume that you are doing something like ping google.com?

---

### Post by 5-HT on 2005-12-13
[QUOTE=earobinson]I assume that you are doing something like ping google.com?[/QUOTE]

Thanks for the input.

Yeah, I've tried pinging from both the CLI (with ping <site> and ping <ip>) and GUI. Google seems to reject pings in general, but I've tried many different sites (which I can ping from another non-Linux box) with no avail.

---

### Post by mips on 2005-12-13
Somewhere along the line it sounds like ICMP echos are being blocked/filtered.

This might happen at your router, or on your PC if you have firestarter installed.

Look at the ethernet troubleshooting guide (sticky at the top of the networking forum) and post the outputs of the commands listed there.

Btw, what router (brand/model) are you using ?

---

### Post by 5-HT on 2005-12-19
Thanks for the help, sorry for the delay.


Yeah, at first I thought ICMP echos may be a likely culprit.

But...I explicitly allowed them in firestarter (they weren't blocked before), and no go.

[QUOTE=mips]
Btw, what router (brand/model) are you using ?[/QUOTE]

It's a D-link DI-604 (hardwired only, 4-port).

To remove the firewalls from this completely, I then did a direct connection with firestarter turned off to no effect.


As before, everything except for ping/traceroute etc seem to work under that setup (tried via CLI and the "network tools" GUI).


In terms of some diagnostics as mentioned in the network help sticky (thanks for that guide mlonker):

As expected, sudo mii-tool eth0 gave "link ok"


Sample from ifconfig (pulling valid ip):

```

	   RX packets:1609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1406792 (1.3 MiB)  TX bytes:197415 (192.7 KiB)
```


Route -n gave exactly the same results as shown by mlomker (albeit with my own gateway ip)

Pings to router are great: ```
 9 packets transmitted, 9 received, 0% packet loss, time 8010ms
rtt min/avg/max/mdev = 0.421/0.440/0.482/0.033 ms 
```
Pings anywhere outside either by IP or domain name just time out. 


This seems like a really weird one, any thoughts?

---

### Post by wr0x2 on 2005-12-19
I have the exact same problem. I tried adding my ISP's DNS servers to my /etc/networking/interfaces file, but what good does that do if I can't even reach them? I've tried pinging them, but I can't reach ANYTHING out of my network.

---

### Post by pcatiprodotnet on 2005-12-19
Same thing started happening to me.  Land-line Ethernet works ok for awhile, then all the sudden I can't ping anything outside my local net.  I noticed that the "route" command will suddenly have wlan0 (wireless) listed too; that is when the problem starts  (even though I haven't gone into gtkwifi and clicked connect yet, and no I don't have any default APs set up).  I have to reboot to temporarily fix it.  I'm using gtkwifi and ndisgtk.  Any suggestions?

[update]
I detailed this problem on the gtkwifi forum...
[http://ubuntuforums.org/showthread.php?t=106100](http://ubuntuforums.org/showthread.php?t=106100)

---

