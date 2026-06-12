---
title: "[SOLVED] &amp;quot;Enable Networking&amp;quot; Disappeared"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by LinuxLars on 2008-12-08
I think I've just figured this out - but am posting anyway as reference in case others have this issue (which sadly I've been fighting with for a few hours now):
***********************************************************************


Need some help here. 

Wireless has been working fine on my Lenovo X61s running with 8.04.

I'm offsite a hotel, and require a wired connection in the room. Taking the machine to the lobby for wireless, back to the room for wired, and repeat, and voila next time I'm in the lobby there's no wireless. 

Clicking on the menu applet, there is no longer an "Enable Wireless" menu option. Oddly, under "Edit Wireless Networks", I see all of my previous wireless definitions. 

Running System->Administration->Network, I no longer have Wireless as an option (there are only 2 now, Wired and Point to Point").

I've reinstalled all of the network manager packages, rebooted several times, and nothing brings it back.

Contents now of my /etc/network/interfaces file:

auto lo
iface lo inet loopback

iface eth0 inet dhcp
address 12.23.69.11
netmask 255.255.255.248
gateway 12.23.69.10

auto eth0

The only thing with "wireless" today in /var/log/messages is:
<computername> kernel: [ 6806 : 161484 ] Kill switch must be turned off for wireless networking to work.

After much research, it looks like there's a hard switch on the bottom of my computer that enables/disables the wireless. I've turned it back on, and at least the options appear in the applet menu and Network Settings. 

I'm going to apparently have to restart to see if this really works. Back in a few...

---

### Post by LinuxLars on 2008-12-08
And voila! After a reboot, the wireless is back.

Who knew.

---

