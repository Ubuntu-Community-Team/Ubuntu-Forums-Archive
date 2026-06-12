---
title: "Setting up home network"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by noelc on 2009-04-15
H I,m very new to Linux and networks for that matter so hope some one can assist me here.

I currrently run a desktop lets call it "A" via a cable to a modern (ADSL which can support wirless). I,m in the process of purchaseing another desktop lets call this "B" and a lap top lets call this "C". I want to network A and B PC,s to the net and each other via cable (Router > Moderm I think?). I want two monitors to display simultaneously from new PC "B" I also want to easily switch a monitor from "B" to read "A" when necessary as there will be programs in "A" which will not reside in "B"?

In addition to this I want the laptop to be wirelessly networked networked to these desktops and the internet.

All on Linux 64 bit.

Am I dreaming? Or can this be acheived or is their alnternatives?

Thanks:-\"

---

### Post by MaindotC on 2009-04-15
To run A & B through the same monitor, mouse, and keyboard you want something called a [KVM Switch](http://en.wikipedia.org/wiki/KVM_switch).  When they are networked wirelessly, they will be accessible by IP address.  They will also be able to access the internet assuming you are connecting them to a wireless router which is connected to the internet.

---

### Post by noelc on 2009-04-15
> **strAlan said:**
> To run A & B through the same monitor, mouse, and keyboard you want something called a [KVM Switch](http://en.wikipedia.org/wiki/KVM_switch).  When they are networked wirelessly, they will be accessible by IP address.  They will also be able to access the internet assuming you are connecting them to a wireless router which is connected to the internet.

Hmm Ok thanks, Sort of makes the need for a second monitor redundant.I note the switch does do not show a modern which can accommodate Internet access via cable for both machines while supporting wireless laptop access.

Will continue my research thanks again

---

### Post by sedawk on 2009-04-15
First check if your DSL modem is only a modem (one RJ-45 connector)
or a DSL router (4-5 RJ-45 connectors, optionally WLAN (antenna)).

If you only have a modem you can replace it with a 
DSL router (with builtin modem) or add a WLAN router with WAN port.
(WAN port is used to connect to existing DSL modem).

Connect both PCs to the router with a network cable.
The laptop connects via WLAN.

Connecting two monitors simultaniously to one PC (B) depends
on the graphics hardware. Might work but needs some tuning of
the configuration file xorg.conf.

If you buy a monitor with two (or more) inputs you can easily connect
two PCs and switch the source from A and B.
Or you do something similar with software, e.g. "desktop sharing"
via VNC or sharing a existing desktop via x11vnc.

(Using a KVM switch is also an option but I like to have two
 keyboards, two mice and especially many monitors to display
 lots of stuff the same time)

---

### Post by noelc on 2009-04-15
> **sedawk said:**
> First check if your DSL modem is only a modem (one RJ-45 connector)
or a DSL router (4-5 RJ-45 connectors, optionally WLAN (antenna)).

Connect both PCs to the router with a network cable.
The laptop connects via WLAN.

Connecting two monitors simultaniously to one PC (B) depends
on the graphics hardware. Might work but needs some tuning of the configuration file xorg.conf.


If you buy a monitor with two (or more) inputs you can easily connect two PCs and switch the source from A and B.

(Using a KVM switch is also an option but I like to have two
 keyboards, two mice and especially many monitors to display
 lots of stuff the same time)


Ok This is what moderm I have? [http://bc.whirlpool.net.au/bc/hardware/?action=h_view&model_id=653](http://bc.whirlpool.net.au/bc/hardware/?action=h_view&model_id=653)

I,m looking to purchase this monitor (G2400WD)
[http://www.benq.com.au/products/LCD/?product=1323&page=specifications](http://www.benq.com.au/products/LCD/?product=1323&page=specifications)

Computer "B" will have Video Card (ATI) PCI-e 4850 x2 1GB Sapphire but not sure about configuring xorg.conf. Assume it can be done and will worry about that later


Regarding your last point Thats what I,m trying to acheive two monitors displaying lots of stuff from one PC or from two PC,s :(simultaneosly without the need for multiple keyboards, mouse etc.

Thanks for your help

---

### Post by MaindotC on 2009-04-16
If you need to display the output of one machine to multiple monitors you can do that by installing the ATI proprietary driver from their website and it should have an option to display output to more than 1 monitor.  I use an ATI card and I have that functionality of "extending the desktop".

---

