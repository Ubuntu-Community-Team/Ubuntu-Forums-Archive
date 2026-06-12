---
title: "eth1: auto-negotiating..."
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by bilkay on 2010-08-15
I'm getting this error every 10 seconds on a new installation.

eth0 is connected to a router, and eth1 is  network card that I used to use to connect another computer before I got a router. It's not connected to anything now, and I don't need it.

So, do I need to pull the card, or is there some way for the system to ignore it on startup? I'd rather do the latter and learn something.

---

### Post by Iowan on 2010-08-15
If eth1 is controlled by Network Manager, you can disable (uncheck) the "Connect Automatically".

---

### Post by bilkay on 2010-08-15
Where is Network Manager?

I have System->Preferences-Network Connections which doesn't have any controls other than to delete the eth1 entry, which I did.

I also have System->Administration->Network Tools which doesn't seem to be able to control anything other than "delete", and it shows eth1 after I've deleted it. The message persists even after reboot.

I may not be able to physically remove the interface as it's built into the computer. The functioning eth0 is a plug-in card. I tried switching the router to eth1 and the connection was unbelievably slow. I think the NIC is foobar. I really NEED to disable it completely.

I've been having another problem which might be related. 
The command sudo service smbd restart
returns "restart: Unknown instance:"

Looking that up, I ran across a bug report that suggests a connection between "Unknown instance" and interface communication problems. I'd like to get this solved to either fix that problem or narrow it down.

---

### Post by Iowan on 2010-08-15
Network Manager icon is usually in the upper-right corner. Appearance depends on version - from two computers, to wireless strength bars, to diagonal plug, to picture of an ethernet plug. On newer versions, right-clicking the icon gives you the option to Edit Connections.

To completely disable the interface, you might check the BIOS.

---

### Post by bilkay on 2010-08-16
> **Iowan said:**
> Network Manager icon is usually in the upper-right corner. Appearance depends on version - from two computers, to wireless strength bars, to diagonal plug, to picture of an ethernet plug. On newer versions, right-clicking the icon gives you the option to Edit Connections.

To completely disable the interface, you might check the BIOS.
The icon brings up the "Network Connections" tool which doesn't show eth1 (I deleted it earlier to no avail).

I've tried ```
sudo ifdown eth1
``` and it returns "interface eth1 not configured."

Update:
```
sudo ifconfig eth1 down
```seems to have stopped the messages. This is a kluge, not a fix. I suppose I could try putting that command in /etc/rc.local.

---

