---
title: "YAWN-BUI [Yet Another Wireless Network Boot-up Issue]"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by Pathogenix on 2006-01-13
Greetings to thee and thine,

I've just reinstalled Ubuntu on a thinkpad T3 with the ubiquitous 3COM office connect card. I was patting myself on the back for getting it all up and running in five minutes (down from 18 hours last time, and three solid days the time before) when I realised that my network is not connecting at boot. After I've booted I can ifup wlan0, or ifup -a and everything is pretty much perfect, but ... my girlfriend has a command line phobia, so if she needs to reboot, she's cut off from the outside world.

The card powers up after hotplug does it's hotplugging thing and the link light flashes madly to itself until I ifup. 

I know it's not a failure of the card, because the previous two installs **did** connect at boot, and I'm stumped as to the difference.

I'll post my interfaces file in a moment, but firstly, is there a log file which shows all the bootup activity? syslog and dmesg seem to show bits and pieces, but they're missing the chunks I'm interested in (ie. where my network fails to connect).

And can anyone point me in the direction of a decent runlevels 101 because I'm a bit hazy about when various scripts are executing and how I twiddle with them.

Good stuff, here's the interface file, I've tweaked it a bit and it's made no difference. To view it in its original, uncut glory, remove the wlan0 hotplug mapping and uncomment the eth1 lines - they looked like a duplication to me and I zapped them in case that was the problem.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script echo
        map wlan0

#mapping hotplug
#       script grep
#       map eth1

#iface eth1 inet static
#address 192.168.1.3
#netmask 255.255.255.0
#gateway 192.168.1.1
#wireless-essid LineNoize

iface wlan0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid LineNoize

auto wlan0

```

---

### Post by AgenT on 2006-01-13
I had a similar problem, but with power management instead of a reboot not enabling the network.

Try this: Delete your line auto lo at the top and find your last line that is auto wlan0 and replace with this: ```
auto lo wlan0
``` You want this to be the last thing the script does. Hopefully that fixes your problem. In addition to this, hotplug may not be working correctly. Since you are using a static IP, remove the hotplug section (comment it out).

---

### Post by Pathogenix on 2006-01-13
Nay, hotplug commented out, auto lo wlan0 added as the last line, no dice.

Card continues to flash madly at me without conencting until I ifup.

---

