---
title: "2 Options"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by OldManRiver on 2009-05-17
All,

I have two options to get my U-Desktop online:
[LIST=1]
[*]Connect to my Windows Network - requires static IP
[*]Use a Link-Sys WUSB54G wireless AP
[/LIST]
Either way it is problematic:
[LIST=1]
[*]Can not get the static IP to see the windows network:
Tried several different edits on the /etc/network/interfaces file to no avail.
[*]Need driver for the Link-Sys WUSB54G, plus signal is weak where machine is located.
[/LIST]
See my delimna!

If you have suggestions, I'm open.

OMR

---

### Post by OldManRiver on 2009-05-17
All,

I got the U-Desktop to take the static IP and now I see the files on the windows boxes, but can not see into the U-DT from Win.

However getting on-line is another story.

Main Win Gateway is down, needs D-Link DWL-G520 re-install, but can not find good drivers.

So using Laptop, which I'm working with here and now.

Laptop connect via wireless, but NIC is set at:
```

Ethernet adapter LAN:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 3Com 3C920 Integrated Fast Ethernet
Controller (3C905C-TX Compatible)
        Physical Address. . . . . . . . . : ##
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.50.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :
        DNS Servers . . . . . . . . . . . : 192.168.15.1
```
so you can see with DNS not is native range, there are some challenges.

I have set default gateway to 192.168.50.0, which holds on main gateway machine, but keeps coming off here, and that is complicating the problem.

Not sure what my next step is, but also downloading the WUSB54G drivers and seeing what I can do there.

OMR

---

### Post by Iowan on 2009-05-18
> **OldManRiver said:**
> I got the U-Desktop to take the static IP and now I see the files on the windows boxes, but can not see into the U-DT from Win. That may require installing Samba-server (AKA samba in Synaptic).
> **OldManRiver said:**
> I have set default gateway to 192.168.50.0, which holds on main gateway machine, but keeps coming off here, and that is complicating the problem.
I've had pretty good luck with Jaunty's manual configuration - although I remember it being a bit tricky to get some information to take.  Seems like I had to hit {ENTER} or click back in the gateway box and hit {ENTER} or wome other "trick" to get it to take.

---

### Post by OldManRiver on 2009-08-22
Option 1:

Samba is installed and configured and error free.

Option 2:
Was on Windows Network without Router, only Hub, and Win Box was refusing to send IP, so moved it to my office where I have router and now get IP assignment.

OMR

---

