---
title: "Dropped network connection when router is powered off an on"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by unbranded on 2009-05-11
Hi

I have recently encountered a problem with a dropped network connection when the router/gateway it is connected to is powered off and then powered on again while the system itself remains powered on. The system would have to be restarted for the network connection to become active again. 

The problem initially occurred when the IP address was assigned by DHCP. I have since changed it to a static IP address but the problem still occurs.

Ubuntu is 8.10 Desktop. Hardware is pretty standard - Intel DG31GL motherboard with 82562G Ethernet LAN controller. The gateway/router is a Linksys WAG54G v3. I have swapped out the cable for a new cable. The only message I could find in the system log about this was 'e100_watchdog: link down'.

It is almost like the motherboard's network port powers itself off when the connection is lost as its activity LED powers off on the router and doesn't come back on. All the other LED indicators come back on as the other systems are reassigned IP address (two network printers and an XP system) when the router is powered back on.

Any ideas would be greatly appreciated.

---

### Post by sir_nasty on 2009-05-11
just out of curiosity sake... after the router restarts, if you physically unplug the cable from the computer then plug it back in does that make a difference?

I'm wondering if your computer has a wake on lan option in the bios causing some issues....  in the system logs after the router restarts does it show the interface back up?

2nd thought, maybe after the restart run ifconfig, see if the interface is there, if not run, sudo ifconfig INFx up  (where INFx is your interface number) and see if that brings it back up....

---

### Post by Peter09 on 2009-05-11
Does the router port light in this condition. It looks to me like a fault condition is being setup.

---

### Post by unbranded on 2009-05-11
Thanks for the replies guys. In response to sir_nasty first -

I too suspected some sort of power management issues (not specifically wake-on-lan though). 

The system logs do not show the interface as back up. ifconfig reported the static IP details when I checked this when the connection was down. I did not try your second step to see if that brings the connection back up - I will do next time I am on-site.

And Peter09 -

The corresponding LED on the router does not light up. It doesn't light up until the Ubuntu machine is restarted. 

Cheers

---

