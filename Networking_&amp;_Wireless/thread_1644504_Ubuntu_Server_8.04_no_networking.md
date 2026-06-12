---
title: "Ubuntu Server 8.04 no networking"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by robertahilljr on 2010-12-13
Hi all,

I could really do with some help please, the other night I reinstalled Ubuntu server, now, as always I have to start off with 8.04 then upgrade to 10.04, and I've never had a problem with this before on this machine or any other for that matter. The problem is, this time I have installed and Ubuntu installer cannot see a DHCP, I go a head and install anyway and fire up Ubuntu and there is no internet access, I have two network cards plugged in, when I type in ifconfig it shows only lo and no network cards, and yet when I check lspci ot shows both network cards are there and when either are plugger in it shows connection on both the connector at the stack end and on the router. has anyone got any idea what to do as I havn't a foggiest.

Thanks in advanced,

Rob

---

### Post by snowpine on 2010-12-13
Use the "lspci" command to figure out exactly which network card you have. Use the forum Search feature to see if any other users have posted a solution for this card. 

It might also be worth checking whether your card works "out of the box" with the current release. 8.04 was released April 2008 and therefore does not have support for newer hardware.

---

### Post by robertahilljr on 2010-12-13
Both network cards I have been using in this server for a couple of years now and work perfectly fine, and work out of the box wonderfully, in fact, the PCI one I have exactly the same on in my desktop machine too. The problem has only started when I formatted and reinstalled.

Thank you for you swift reply though to my post :D

Rob

---

### Post by snowpine on 2010-12-13
I wish you the best resolving this issue. Since you won't tell us which network card you have, I cannot offer further assistance.

---

### Post by robertahilljr on 2010-12-13
Sorry, I miss understood the message, sorry. Unfortunatly the PCI one is now playing up on me and has gone intermittent. But I do know with no dout in my mind that the on-board network card works.
This is:

Ethernet Controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller

This is copied straight from lspci.

Sorry to be a inconvinience.

Kind Regards,

Rob

---

### Post by furlabs on 2010-12-15
Assuming there is nothing wrong with the onboard NIC, DHCP server, cable, switch etc, the following should help.

First, find out the interface name of your onboard NIC. Usually this is eth-something. Run the following command soon after boot:
```
dmesg | grep eth
```

You should see a couple of entries like the following:
```
eth0: RTL8168c/8111c at 0xf810a000, 00:11:22:33:44:55, XID 1c4000c0 IRQ 27
eth1: RTL8168c/8111c at 0xf810a000, 66:77:88:99:AA:BB, XID 1c4000c0 IRQ 28

```

One will be your onboard, the other the PCI card. 

You will need to be root to do the rest:
```
sudo -s
```

Now edit /etc/network/interfaces. From what you have said I am guessing it will only have the following:
```
# The loopback network interface
auto lo
iface lo inet loopback

```

Add the following at the end of the file (substituting eth0 for the interface name of your onboard NIC):
```
auto eth0
iface eth0 inet dhcp
```

Make sure the NIC is plugged into the switch, then bring it up with this command:
```
ifup eth0
```

It should then get an IP from DHCP.

---

