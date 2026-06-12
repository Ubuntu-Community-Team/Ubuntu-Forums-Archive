---
title: "Teaming NICs"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by gmanpsycho on 2006-06-22
Well, I did some looking and I was not able to find this particular subject mentioned in depth anywhere on this forum. I was wanting to team, or bridge, my NICs, both of which are 3COM 3C905s Tornados,  so that I could get better throughput on the local network side, not neccessarily from the internet connection (which by the way is a 3Mbps/down and 512Kbps/up DSL connection).

I knew that you could running the NICs on seperate networks (a la linux proxy or linux firewall) but I wanted to make them work together.

I did some Googling and finally found [this thread]("http://www.howtoforge.com/nic_bonding"). I did make some modifications for my local network but this worked for me.

I did have to run:
```
sudo modeprobe bonding
```
to get the bonded NICs up and running after rebooting but otherwise this guide worked for me.

Here is a copy of my /etc/network/interfaces.conf:

> # The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#auto eth0

# The primary network interface

#iface eth0 inet static
#address 10.0.0.240
#netmask 255.255.255.0
#gateway 10.0.0.254


#iface eth1 inet static
#address 10.0.0.241
#netmask 255.255.255.0
#gateway 10.0.0.254

#auto eth1

auto bond0
iface bond0 inet static
address 10.0.0.240
netmask 255.255.255.0
#hwaddress ether 00:02:B3:48:50:2C
gateway 10.0.0.254
up ifenslave bond0 eth0 eth1
down ifenslave -d bond0 eth0 eth1

You'll notice that I've commented out (#) some things and added others. In the threads example you could theorectically use a different hardware address but I did not use this aspect.

I hope this would help someone whose looking to do the same. I have been around linux for a while (DSL, MEPIS, GENTOO and now UBUNTU) but I'm still a noob. I guess once a newbie, always a newbie.

Cheers!

---

### Post by mips on 2006-06-22
[http://www.ubuntuforums.org/showthread.php?t=99668](http://www.ubuntuforums.org/showthread.php?t=99668)
[http://www.ubuntuforums.org/showthread.php?t=163453](http://www.ubuntuforums.org/showthread.php?t=163453)

---

### Post by gmanpsycho on 2006-06-23
Thanks mips for just deflating my ego... :) 

I do however feel a bit embarrased... :oops:  I was having some issues with this NIC Bonding after all. Well it seemed to work just fine until I installed a few other programs... DHCPD, SAMBAD and afew others.... just my luck that it would go bananas then....

Oh well, I believe I see part of my mistake and the reasons for the inconsistant internet connections... I'll need to reconfigure my ALIAS.CONF file in the MODPROBE.D directory.

Thanks again for your help... er uhmm corrections.

---

### Post by mips on 2006-06-23
[QUOTE=gmanpsycho]Thanks mips for just deflating my ego... :) 

...

Thanks again for your help... er uhmm corrections.[/QUOTE]

Sorry, was'nt my intention ;) The main thing is you showed initiative and tried on your own which imho is the best way to learn anything and it will take you far in life.

I have the utmost respect & time for those that try compared to those that don't and just ask and not try anything themselves.

Think I said enough now, don't wan't people to start crying into their beers ;)

---

