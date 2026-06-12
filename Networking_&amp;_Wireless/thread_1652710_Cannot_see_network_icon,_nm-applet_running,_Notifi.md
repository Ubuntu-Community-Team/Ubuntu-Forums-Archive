---
title: "Cannot see network icon, nm-applet running, Notification Area running"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by RonB123123 on 2010-12-25
Hi. I have Ubuntu 10.04, nm-applet is running in the background, my battery icon and sound icon are showing but my network icon has been missing for the past 2 days. It was working fine before but now it's not. How can I fix this issue if I don't have an ethernet cord? Is there a way to roll back the recent updates or do I need to reinstall my network manager?

I've tried restarting the system and I've tried killing nm-applet and reloading it using Alt F2. I get some Debug error. 

When I try to run nm-applet --sm-disable 

It says an instance is already running and then gives me a warning. 
** (nm-applet:1636): Warning **: <WARN> constructor(): Couldn't initialize the D-Bus Manager.

I tried removing "iface eth0 inet dhcp" from /etc/network/interfaces and then tried restarting by "sudo /etc/initi.d/networking restart"

It says: 
* reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0
[OK]

What can I do to connect to the internet? I have a flash stick if its possible to download a .deb package on this mac and transfer it over to my other laptop to fix the problem. If its possible.

Thank you,
Ron

---

### Post by karthick87 on 2010-12-25
Post the output of,

```
cat /etc/network/interfaces
```

---

### Post by RonB123123 on 2010-12-25
#auto lo
#iface lo inet loopback
auto eth0
#iface eth0 inet dhcp

---

### Post by karthick87 on 2010-12-25
It should look like this i guess,
> auto lo
iface lo inet loopback

auto eth0


---

### Post by RonB123123 on 2010-12-25
... that didn't work. :(

---

### Post by karthick87 on 2010-12-25
What type of connection it is?PPPOE?

---

### Post by dineshs on 2010-12-25
Run ```
gksudo gedit /etc/network/interfaces
```and let the file contain only```
auto lo
iface lo inet loopback
```
Then reboot
If there is no luck
Right click on the top panel-click add to panel-select notification area -click add

---

### Post by RonB123123 on 2011-01-11
I tried several reboots and no luck. Then I saw Star Wars IV rebooted and it came back. It was so odd. I guess it was a glitch and I suppose this is solved.

---

