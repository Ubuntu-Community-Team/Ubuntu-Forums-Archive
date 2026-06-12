---
title: "Getting network manager to set wireless as default route by default"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by lorderico on 2012-04-13
Hello,

I am trying to get network manager to use our usb wireless card as the default route when it is plugged in.  Currently it uses eth1.  I could do route del default && route add default gw xxxx dev wlan0, but when the computer restarts then it is back to eth1 as default.  And also, this has to work for all gateways.  Is there a way to do this using network manager?  I really am not looking for a solution that would have me write a custom script to connect to a wireless network if I don't have to.

Thanks,

Eric

---

### Post by dandnsmith on 2012-04-13
I think you can just mark the wired link 'disabled' in Network Manager to get the effect you ask for. I had to do this to one of my eth ports when it became unusable (but still apparently there).

---

### Post by lorderico on 2012-04-13
Oh, I forgot to explain: I am using both of them.  Eth1 connects to a local router (so we can connect to the computers next to it).  Wlan0 connects to the internet.  So we need both at the same time.

Eric

---

### Post by dandnsmith on 2012-04-13
OK, so what functionality do you really want/desire?

Is the wlan the only way you will connect to the internet, or does the router also perform this function?

If eth1 is only used for local traffic, then you should set it with a (preferential) route for that range of addresses, and have the default set for the wlan to act as the method for non-local traffic.

I, unfortunately, don't know whether this is within the Network Manager capability - I'd always set this sort of thing by creating entries in the routing table (by hand). If the internet traffic goes (always) via wlan, then you don't have to worry about what will happen when it is disconnected.

---

### Post by lorderico on 2012-04-13
I'd like to create routing entries by hand, I'm just not sure how to deal with connecting to different wireless networks.  Right now the network manager finds (usually) the right network to connect to, and connects to it.  To do this by hand would require using iwconfig to find an appropriate essid, dhclient it, and then add the appropriate routing entry with the correct gateway every time I want to connect to a network, right?

I found a workaround in the form of a shell script that parses the command "route -n" to look for the entry:

72.28.33.0    0.0.0.0         255.255.255.0   U     1      0        0 wlan0

then parse the "72.28.33.0" out using awk, appends a "1" to get the default gateway.  Finally, it deletes the current default route and adds a new default route with 72.28.33.01 as its gateway. The address "72.28.33.01" will change depending on which network we connect to.

That script seems like a hack that I would like to avoid though if I can.

You were right, the router which eth0 is connected to doesn't connect to the internet, and so we need wlan0 to get to the internet.

The goal here is to have the computer connect to a network and set up the correct routes automatically.  It almost does this, except the routes are wrong.  In fact, the previous version of network manager we used did this fine...

Eric

---

### Post by dandnsmith on 2012-04-13
Am I to understand you have more than one wireless interface?
If not, just set the local route through eth0 specifically, and the default to be via wlan0 (you don't need to have the network address it has currently for this)

---

