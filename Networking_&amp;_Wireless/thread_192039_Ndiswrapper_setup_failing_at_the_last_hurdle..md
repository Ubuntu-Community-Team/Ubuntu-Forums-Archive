---
title: "Ndiswrapper setup failing at the last hurdle."
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by Lemony on 2006-06-08
Hi,
Apologies if this has been covered, I couldn't see a thread that seemed to match my problem though.

I'm setting up my Linksys WUSB54G on Dapper and have so far met with mixed success. I've followed the various wiki and forum instruction sets to get to a point where my machine can see my AP (netgear mr814) and an iwconfig gives me:

```
eth2   IEEE 802.11b   ESSID="my essid"
        mode:Managed  Channel=11 Access Point: 00:09:5b:9e:3e:82
        sensitivity=0/200
        Link Quality:0  Signal Level:0  Noise Level:0
```

At this point the guides normally advise to do a dhclient, this returns ```
No DHCPOFFERS Received.
```

An iwlist eth2 scan returns my access point as having the appropriate MAC address, ESSID and channel, the only differences are that in these results mode is given as master and the link quality as 100.

It strikes me that i'm probably just making a silly mistake but I lack the knowledge to spot it - can anyone help me connect?

Cheers, this forum's already been a lot of help:here's hoping you can give me a nudge in the right direction!
Sam

---

### Post by ComplexNumber on 2006-06-08
i was in a similar position as you in the last few days.
-note that you have to run 'modprobe ndiswrapper' each time you login. or you can just add the statement in/etc/rc.d/rc.local(i think this is the name of the file. it is something.local anyway).
-do you have network-manager and network-manager-whatever(cant think of the exact name right now) installed, running, and configured to start at boot? you can see if this is the case in 'services' in the main menu.
-after you have typed in 'sudo modprobe ndiswrapper', type in 'ndiswrapper eth2  scan' (or it may be 'ndiswraper wlan0 scan'), then printout the results here.

---

### Post by Lemony on 2006-06-08
Cheers for the swift reply ComplexNumber.

- I've been holding off on changing the .local file but have been doing a modprobe ndiswrapper after each boot.

- I don't have any entries in Services settings which match those descriptions, are these packages i need to install?

- I'm not sure you meant "ndiswrapper eth2 scan", that isn't a valid command. Do i need an option switch? Or alternatively, were you thinking of "iwlist eth2 scan"?  If so, the result is as mentioned above.

Thanks again.

---

### Post by ComplexNumber on 2006-06-08
>  - I don't have any entries in Services settings which match those descriptions, are these packages i need to install? install network manager and network manager dispatcher. 
> 

- I'm not sure you meant "ndiswrapper eth2 scan", that isn't a valid command. Do i need an option switch? Or alternatively, were you thinking of "iwlist eth2 scan"? If so, the result is as mentioned above. yes, sorry, i was forgetting that ubuntu is different in that respect. and i was wrong about ndiswrapper. it is iwlist. try 'iwlist ra0 scan'.

---

### Post by Lemony on 2006-06-08
> install network manager and network manager dispatcher
When I attempt to install network manager from the add/remove tool it gives me an error message: 

```
"'network-manager-gnome' is not available in any software channel: 

The appliction might not support your architecture"
```

> it is iwlist. try 'iwlist ra0 scan'
That exact command gives me:
```
ra0    Interface does not support scanning
```

---

### Post by ComplexNumber on 2006-06-08
thats curious about network manager.

---

### Post by Lemony on 2006-06-08
Ok, I now have Network Manager installed, there was an issue with my application installer. There's still no entry for it in my Services Settings though and i can't see anything about network manager dispatcher.

---

### Post by ComplexNumber on 2006-06-08
[quote=Lemony]Ok, I now have Network Manager installed, there was an issue with my application installer. There's still no entry for it in my Services Settings though and i can't see anything about network manager dispatcher.[/quote]
,aybe it needs  a reboot. but there should be a network manager entry in services if its isntalled.

---

### Post by tompagenet on 2006-10-11
I get this ""'network-manager-gnome' is not available in any software channel: 

The appliction might not support your architecture"

exact same message when I try to install network manager from Add/Remove... - I'm trying to get WPA access, and apologise for being completely new to this.

Tom

---

