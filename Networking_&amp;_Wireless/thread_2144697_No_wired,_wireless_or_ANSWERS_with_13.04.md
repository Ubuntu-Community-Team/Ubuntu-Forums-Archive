---
title: "No wired, wireless or ANSWERS with 13.04"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by CelestialMechanics on 2013-05-13
My laptop has gained 13.04 and lost the rest of the world
It would seem my network card is working because I can access router control pages, but I can't get anywhere else.
I've tried 3 different wifi networks and a direct wired ethernet connection to no avail.
Searching the problem turns up many similar problems but no definite answers, I have been a huge fan of Ubuntu, but after three weeks of this it's really making me consider looking elsewhere!
Can anyone please help?
Regards
Robin

---

### Post by PowerBarry43 on 2013-05-13
Hi

This sounds to me like yuou don't have a default gateway. Could you post up the output of:

```
route
```

and 

```
ping -c3 8.8.8.8
```

You can also try running:

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw <ip address of router>
```

to temporarily add a default gateway to confirm that this fixes the problem.

Hope this helps!

Barry

---

### Post by CelestialMechanics on 2013-05-14
Hi Barry
route gives me
destination    gateway         genmask          flags   metric   ref   use   iface
default          ufford.wifi.loc  0.0.0.0            UG      0          0    0      wlan0
10.9.0.0        *                  255.255.255.0   U        9          0     0      wlan0
link-local       *                  255.255.0.0       U        1000    0     0      wlan0

The ping says
From 10.9.0.1   icmp_seq=1 Destination Net Prohibited 

and has 3 goes before giving up

route add tells me I've made a syntax error but I can't spot one.

Any thoughts?
Thank you very much for your suggestions
Best
Robin

---

### Post by PowerBarry43 on 2013-05-14
Hi again

route add should have a sudo before but it looks like you already have a default gateway of 10.9.0.1 so assuming this is the correct address and not your laptops address then that's not your problem. You try to ping 8.8.8.8 and your router comes back saying net prohibited which basically means it's blocking you. You may want to have a look at the rules in place on the router. just to be double safe could you post up the output of:
```

 ifconfig ; iwconfig ; echo -n "ufw " ; ufw status ; iptables --list
```

Barry

---

### Post by Silverflyer on 2013-05-14
I have this same problem and it started recently.  My wired and wireless have both stopped working/working intermittently.  I sure would like a fix.

---

### Post by Silverflyer on 2013-05-14
I did something that so far is working ok...

I opened network connections and deleted all the connections, rebooted, and re-added the ethernet connection.  So far it is working well with no disconnects.

---

### Post by CelestialMechanics on 2013-05-29
Further strange developments on this one.
The problem first arose with hotel wifi, so I assumed it was that, but while there I tried two different mobile wifi hotspots from available phones, and it still couldn't get any further than the router control page.  So I thought it must be my PC, that maybe I had updated incorrectly last time I used my home wifi and not restarted before coming to the hotel.
However I got home end of last week and it worked first time with my home wifi as if nothing had ever been wrong!
I didn't get round to posting the ifconfig etc output because I had to transcribe it by hand to the hotel computer in reception, so unfortunately I don't have a record of the network condition, but it seems so strange that it still hadn't worked with the separate mobile wifi hotspots.  Could a defective hotel system (though it worked for everyone else) have been able to overwhelm the mobile outlets?
I'm going to test it out somewhere with free wifi to see what that does.  But my concern is that I have another 3.5 week trip away from home next week and I really don't want to be stuck without web again.
Any thoughts?
Thanks
Robin

---

