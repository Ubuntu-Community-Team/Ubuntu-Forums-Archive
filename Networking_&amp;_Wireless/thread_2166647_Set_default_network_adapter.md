---
title: "Set default network adapter"
date: 2013-08-10
forum: Networking &amp; Wireless
---

### Post by Linux90s on 2013-08-10
Ubuntu 13.04

When i searched for this there was nothing relevant to my situation, so here's how i did it...
Hopefully, it will be useful to someone out there...

I have 3 network interfaces in my system, 2 onboard ethernet, 1 onboard wifi.

On my system
"Wired Connection 1" is eth1
"Wired Connection 2" is eth0

Which is the opposite under Windows where "Wired Connection 1" is Lan1 and "Wired Connection 2" is Lan2                

To set default network adapter :

Click the Network Icon at the top right of the screen, next to your sound/date area (i have unity, select as is
appropriate for your X-windows system)

Select "Connection Information" to determine which network the adapter relates to...
eg. Ethernet -> Wired Connection 1 -> eth1 192.168.2.1
     Ethernet -> Wired Connection 2 -> eth0 192.168.1.1

(Your subnet/ip will probably be different i.e 192.168.x.x, 10.x.x.x etc)

if you want the 192.168.1.1 adapter as default (eth0 / Wired Connection 2):

Click the Network Icon at the top right of the screen, next to your sound/date area
Click "Edit Connections"

(in this instance)
Select "Wired Connection 1" NOT "Wired Connection 2"

Click "Edit"
Click the "IPv4 Settings" tab
Click "Routes" at the bottom
Click the "Use this connection only for resources on its network" checkbox
Click "Ok"
Click "Save"
Click "Close" in the "Network Connections" window.

You can use the command "sudo service networking restart" in a terminal window, however, on my system i had a fault window
come up which also resulted in an issue with lightdm... you experience may vary

I had to reboot and everything worked as intended

Remember - edit the connection you DON'T want as the default.

-OR- you could go through
System Settings in the control panel, followed by "Networks" and you can see the network/adapter information for your
interfaces, and then click "options" in the bottom right to get to the same place as above.


There are other ways to do this, such as set the "Metric" value of the interface you want as default to 1 and the "Metric" value of any other interface(s) to a value higher than 1, so you could use 2 or 3 or 10 or 100, that's down to you.

You could modify the routing table directly if you wish but that is best done if you know what you are doing.

This principle is relevant across Ubuntu versions though earlier/later versions may procedural differences.


For a quick & easy solution, this works fine.
If you have other routes/gateways to specify, you will have to add additional routes yourself, which can also be done in the same window
where you "ticked" the checkbox.

All the best!

---

### Post by JsDad on 2014-07-23
I had a on-board 100MB adapter and an additional 1000MB adapter. This was the solution that I wanted to change the default config.
**Good Job** Linux90s!
Thanks

---

