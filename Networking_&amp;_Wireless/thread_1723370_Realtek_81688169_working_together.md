---
title: "Realtek 8168/8169 working together"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by Chrus on 2011-04-07
I'me using a mobo with an onboard realtek RTL8111/8168B NIC, adn i've got an addon card with 3 Realtek RTL-8110SC/8169SC NICs.

Out of the box, the 3 NIC's on the addon card worked, but the onboard NIC was having problems. Managed to find a solution here ([http://ubuntuforums.org/showpost.php?p=4563405&postcount=2]("http://ubuntuforums.org/showpost.php?p=4563405&postcount=2").

Installed the new driver and blacklisted r8169. The onboard NIC started working... but the 3 addon NICs that use that driver stopped. If I unblacklist the driver, all 4 NICs will use it and the onboard wont work.

Is there a way I can force the onboard NIC to use the r8168 driver and the other 3 to use the r8169 driver?

Thanks

---

### Post by chili555 on 2011-04-07
You might try writing some alias files; something like /etc/modprobe.d/r8168.conf:```
alias wlan0 r8168
```And then /etc/modprobe.d/r8169.conf:```
alias wlan1 r8169
alias wlan2 r8169
etc., etc.
```You might have to fine tune the directives.

You might also look in and adjust /etc/udev/rules.d/70-persistent-net.rules.

I have been brief in my explanation because you seem to be pretty knowledgeable. If you need further guidance, post back.

---

### Post by Chrus on 2011-04-07
Thanks mate. Will have look into that and let you know how it goes.

---

### Post by Chrus on 2011-04-08
Tried setting up the Alias... but still no joy.

eth0 is onboard, eth1 is addon.

ethtool -i eth0 gives
   driver: r8169
   version: 2.2LK
   firmware-version:
   bus-info: 0000:02:00.0

ethtool -i eth1 gives
   driver: r8169
   version: 2.2LK
   firmware-version:
   bus-info: 0000:04:04.0

lsmod shows both r8168 and r8169 are there.

I had a look at persistent-net.rules, but couldnt work out what was needed. It would seem I need to change DRIVERS=="?*" to something else... but i cant for the life of my figure out what it needs to be.

---

### Post by chili555 on 2011-04-08
> It would seem I need to change DRIVERS=="?*" to something else... but i cant for the life of my figure out what it needs to be.I have never seen that filled in. It may be helpful or not.

I'd be looking at whether these parts match. I've used an example from my own system:> # PCI device 0x8086:0x109a ([COLOR="Red"]e1000e[/COLOR])
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:16:41:e6:xx:xx", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="Red"]eth0[/COLOR]"Of course, in your case, the driver is r8168 or r8169 respectively, not e1000e. You can amend as needed and reboot. I am not sure I have many more suggestions.

---

### Post by Chrus on 2011-04-12
So after doing some reading on how udev rules work, I found out DRIVER(S)== is read only, it cant be used to set a driver. How unfortunate.

I dont really know a whole lot about modprobe/insmod/etc, but i would assume there would be a way to tell a particular device to use the ko i want it to use.

The other option im concidering it to ditch the realtek addon card and replace it with an intel card. That way I will (in theory) be able to blacklist the r8169 driver and have the onboard card use the r8168 driver and the intel card should use a different driver all together. But this option is only a last resort.

---

