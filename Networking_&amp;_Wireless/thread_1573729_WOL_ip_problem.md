---
title: "WOL ip problem"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by Japsser on 2010-09-13
Hi,

[I]I have a router that doesn't seem to support port forwarding to my complete home network using 192.168.1.255, I can only specify 1 ip. Am I missing something here or is there really no way around this.

Anyways, I figured I could maybe fix it changing settings on my ubuntu server. I started with specifying a static ip (192.168.1.8 ) , yet nothing changed.

Using wakeonlan -i 192.168.1.8 #MAC# won't boot the system.

this however; wakeonlan -i 192.168.1.255 #MAC# works perfectly.

Any other ideas that might be worth giving a shot?[/I]

Edit:

I have tried something similar like BkkBonanza suggested, I checked the source code of the router's port forwarding page and did this:

I set the netmask to 255.255.255.128

afterwards I executed javascript in the adress bar to make the port forwarding script think my netmask was still 255.255.255.0. Resulting in an accepted forward to the network broadcast adress 192.168.1.127.

[IMG]http://i56.tinypic.com/2lvk17r.png[/IMG]

It's obviously still not working, so when I try 
wakeonlan -i *MY IP* -p 44444 #MAC#

the server won't boot.

I tried a remote WOL website too, and I found this in my router's security logs

```
09/16/2010  16:08:41 **Probable ASCEND Probe** 208.77.98.204, 42402->> *MY IP*, 9 (from PPPoE1 Inbound)
09/16/2010  16:08:41 **UDP Loop** 208.77.98.204, 42402->> *MY IP*, 7 (from PPPoE1 Inbound)
09/16/2010  16:08:41 **UDP Loop** 208.77.98.204, 42402->> 192.168.1.127, 7 (from PPPoE1 Inbound)
```

I haven't got the slightest idea what they mean though.

---

### Post by BkkBonanza on 2010-09-13
You might try using telnet to manually set the broadcast address. Also some routers can be tricked by setting a different netmask, and then setting it back after.

eg. 255.255.240.0 , set the forwarding, then set back to 255.255.255.0

or in network notation, 192.168.1.0/22 and then back to 192.168.1.0/24

Sometimes the router control panel uses js to prevent bad data and turnig off js while setting the address will work.

Since WOL depends on MAC level addressing some routers just won't translate the broadcast address correctly anyway. So it's hit and miss.

---

### Post by Japsser on 2010-09-13
Thanks for the response, though none of the tips seem to work. It looks like I have a crappy router or crappy ISP firmware. 
telnet is not supported, disabling javascript disables saving settings as a whole, and I can only edit the last number of the netmask. 

I tried the same suggestions on another linksys router to no avail.

---

### Post by BkkBonanza on 2010-09-13
Is there a computer on the LAN that is always on? You could bounce it off that one with an iptables rule on that machine. Such a rule would redirect one port to the broadcast address.

eg. 
iptables -p udp --dport xxx -j REDIRECT --to 192.168.1.255

then forward router using normal port forwarding.

---

### Post by Japsser on 2010-09-13
That's actually a pretty good idea, I'll look into it :)

I'm messing around with an (identical) router I've got here, trying to flash the crappy firmware. No success so far (it's a pretty unknown model), but I'm not giving up just yet.

---

### Post by BkkBonanza on 2010-09-13
If you can flash the firmware to some Linux based one (like with Linksys WRT54GL), then it should be fairly easy to manually add an iptables redirect rule. I have a WRT54GL here that worked great for me with DD-WRT for ages. I'll probably list it on ebay soon because I'm not using it any more. They go for about $50 last I checked, and would be able to do this. There's also a few other devices around like that little Linksys disk server thing with USB drives - it runs Linux too and likely could be made to bounce packets. (Of course, I've never tried it)

---

### Post by Japsser on 2010-09-16
Since I couldn't flash my router, I resorted to editing the javascript variables to override the router's checking functions. It's still not working though **(See original first post**), so any suggestion is welcome :-)

---

