---
title: "Using laptop as router switch"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by BobvanderPoel on 2010-06-10
Okay, a goofy problem/request ... 

I have a new sat. dish receiver which MAY have internet connection. Before running cables I'd like to test to see it works (and is useful). I figured that I could connect the receiver to my laptop with a cat5 and enable the wireless on the laptop.

Somehow I need to set the wired connection on the laptop to act like a switch so the router can send an IP back to the dish receiver.

Possible?

---

### Post by nbkr on 2010-06-10
You can bridge to network cards - even if there wired and wireless cards. Use the brctl tool for this. But keep in mind that you need a wireless card that supports briding. Some stop working if they should forward packages that have a different source-MAC address than the card itself.

---

### Post by BobvanderPoel on 2010-06-10
Thanks.

Got the brctl program (it's in the bridge-utils package). It's a bit short on examples ... could you give me a command to try? I'm thinking it should be something like:

   brctl addif eth0 wlan0 

???? Don't have the laptop turned on right now so not sure of the port names, but is this close?

>>Some stop working if they should forward 
>>packages that have a different source-MAC 
>>address than the card itself. 

I assume that this doesn't hurt the card ... just doesn't work?

Thanks.

---

### Post by nbkr on 2010-06-10
You will have to create the bridge first.

```

brctl addbr br0

```

Then add the interfaces:

```

brctl addif br0 wlan0
brctl addif br0 eth0

```

Bridging won't break the card - it just don't work if the wireless card doesn't support it.

---

### Post by BobvanderPoel on 2010-06-10
Some progress :)

I have the software installed on the laptop. But, as soon as the hardwire is plugged in, the wireless link drops. Unplug and I can re-enable the wireless.

So ... how do I tell the laptop to not try to connect to the world (well, my router) when the eth0 is plugged in? This is connected to the receiver/dish so there is nothing there ... and poor linux just loops looking (and hoping).

---

### Post by nbkr on 2010-06-11
You probably have to deactive the networkmanager in order to do this.

---

### Post by BobvanderPoel on 2010-06-11
Networkmanager ... yeah :) I was looking at that trying to find a "don't use wired option" but that's probably not there. So, I guess I kill NM, start wired manually, etc.

I'll give it a go tomorrow.

Thanks.

---

