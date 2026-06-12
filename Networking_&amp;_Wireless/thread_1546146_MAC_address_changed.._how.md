---
title: "MAC address changed.. how??"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by solitaire on 2010-08-04
I've set up my router to give out fixed IP addresses linked to MAC addresses
(so that my laptop and wireless devices can connect using HDCP and i know what IP address they will have.)

But for some reason the MAC address stored on my router is different for the Wired LAN's MAC address on my Laptop (it was working last week before I reinstalled Ubuntu on the laptop.)

Would reinstalling Ubuntu cause the MAC address on my wired adapter in the laptop to change? (The wireless MAC address on the laptop is the same!) 

*note* I did wipe the 64Bit version off and instralled the 32bit on the laptop

Or should I be checking my router for any funny business??

---

### Post by sikander3786 on 2010-08-05
Can't say why it happened. Don't know if it is a router fault.

Still you can change your mac address to correspond to the one stored on the router.

```

sudo gedit /etc/network/interfaces

```

Add your mac address underneath

```

auto eth0
iface eth0 inet dhcp
       hwaddress ether xx:xx:xx:xx:xx:xx

```

Restart networking and see what happens.

HTH.

---

### Post by Vincentlaborant on 2010-08-05
The MAC address of your computer is based on the hardware of the computer (Remember that the MAC address is also called "Hardware address" in numerous manuals of some manufacturers).

So unless your hardware is changed, the MAC address should not change. Events that might force a MAC address change included changing the main bord (MOBO), the wireless adapter, LAN ports (adding/ replacing) and changing the CPU (since the CPU handles the networking).

Then we have your router. Is the router been cut of power for some time/ reseted to manufacturers defaults/ change of ISP? If all questions are answered with "NO" , then you have bad luck. Simply reconfigure the router settings (first back to manufacturers defaults, then setting to your wishes via wired LAN).

---

### Post by Joe of loath on 2010-08-05
I know my router actually assigns static IP's (Badly) using hostnames. Maybe yours is doing the same?

---

