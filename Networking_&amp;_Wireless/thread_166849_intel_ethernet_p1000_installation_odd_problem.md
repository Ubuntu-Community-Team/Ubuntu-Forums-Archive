---
title: "intel ethernet p1000 installation/ odd problem"
date: 2006-04-27
forum: Networking &amp; Wireless
---

### Post by s.mcclatchie on 2006-04-27
Hello

I have recently installed breezy badger version of ubuntu on a Toshiba
Satellite pro 100 with an Intel Pro 1000 gigabit ethernet card. As
reported before in this forum, the network adaptor was not found
during instllation. I followed the instructions in
<http://www.ubuntuforums.org/showthread.php?p=741687> to install the
appropriate driver. Modprobe e1000 seemed to be accepted, but the card
is still not detected on reboot.

sudo pppoeconf gives
... no working ethernet card can be found. ...

The /system/administration/networking gui does not show an ethernet card.

lspci gives ... Ethernet controller: Intel corp: unknown device 109a

My /ect/modules is
#...
#...
#..

lp
mousedev
psmouse
sbp2
e1000

My /etc/interfaces is
#...
auto lo
iface lo inet loopback

iface ppp0 inet ppp
provider dsl-provider

auto eth0
iface eth0 inet dhcp
name Ethernet LAN card

Connection properties: lo is receiving and sending packets

Eveything seemed to go OK with the instructions in the intructions at
<http://www.ubuntuforums.org/showthread.php?p=741687> until I got to
the this part:

cd to the /e1000-6.3.9/src directory where you unzipped the driver and type:
sudo make install

The driver I downloaded unzipped to /e1000-7.0.33.
So I cd to /e1000-7.0.33/src and type
sudo make install
I don't see any erros until the end when I get:

cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000

sudo modprobe e1000 
returns nothing.

All of the steps in the Sticky: Wired ethernet troubleshooting process
indicate that the card is not being recognised.



I'm stuck -- why is the ethernet not being detected or activated, please?

Best fishes

---

### Post by mips on 2006-04-27
Do a search here for e1000, there is a guide for it that 'might' help.

---

### Post by s.mcclatchie on 2006-04-29
Hello

The problem is now fixed. 

I searched for the error message ("cannot write to .. using catman mode") using google and found another thread  in these forums where an easy solution was suggested. This was to install a kernel later than 2.6.15.x. I had initially avoided installing the latest build which was a mistake in this case.  Anyway, I did a reinstallation with drake flight 6 and the ethernet card was picked up without fuss.

Good work guys -- thanks!

Sam

---

