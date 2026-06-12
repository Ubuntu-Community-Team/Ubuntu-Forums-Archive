---
title: "1 Gbit speed doesn't work, get only 100 Mbit"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by butyiba on 2012-10-25
Dear All,
 
I have Dell PowerEdge T 1800 server. I have installed ubuntu 11.10 x64 desktop version. The PC has 1 Gbit ethernet card but under Ubuntu the ethernet card is working only 100 Mbit. I have made new installation with the new Ubuntu 12.04 but the problem is same.
The ethernet work well but only 100 Mbit.
I have done all updates nothing is changed.
 
There is any solutions to use the ethernet card with 1 Gbit speed ?
 
Best Regards
ButyiBa

---

### Post by Grenage on 2012-10-25
First, install ethtool:

```
sudo apt-get install ethtool
```

Now check the adapter's advertised abilities:

```
sudo ethtool *eth0*
```

Substitute *eth0* with whatever your adapter is called.

If it lists 1000 speeds, try and force it:

```
sudo ethtool -s *eth0* speed 1000
```

---

### Post by butyiba on 2012-10-25
> **Grenage said:**
> First, install ethtool:
 
```
sudo apt-get install ethtool
```Now check the adapter's advertised abilities:
 
```
sudo ethtool *eth0*
```Substitute *eth0* with whatever your adapter is called.
 
If it lists 1000 speeds, try and force it:
 
```
sudo ethtool -s *eth0* speed 1000
```
 
I have installed the ethtool.
The information is the following:
 
Settings for eth0:
Supported ports: [ TP ]
Supported link modes: 10baseT/Half 10baseT/Full 
100baseT/Half 100baseT/Full 
1000baseT/Full 
Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full 
100baseT/Half 100baseT/Full 
1000baseT/Full 
Advertised pause frame use: No
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
MDI-X: Unknown
Supports Wake-on: umbg
Wake-on: d
Current message level: 0x00000007 (7)
drv probe link
Link detected: yes
 
For the speed is only 100 Mb/s but the LAN card can work with 1000 Mb/s. There is any adjustment for 1000 Mb ?
 
My kernel version: 3.2.0-32
 
Best Regards
ButyiBa

---

### Post by Grenage on 2012-10-25
It's been a while, so I had to check on my machine:

```
sudo ethtool -s eth0 speed 1000 duplex half
```

This command should set the connection eth0 to 1000mb/s at half-duplex - as a test.  It won't make the change permanent, but that change can be made permanent by adding a startup script that runs when the interface comes up.

I appreciate that this is not a particularly pretty or GUI-orientated approach, and Ubuntu may now have an 'easier' way of doing this.

---

### Post by butyiba on 2012-10-25
> **Grenage said:**
> It's been a while, so I had to check on my machine:
 
```
sudo ethtool -s eth0 speed 1000 duplex half
```
 
This command should set the connection eth0 to 1000mb/s at half-duplex - as a test. It won't make the change permanent, but that change can be made permanent by adding a startup script that runs when the interface comes up.
 
I appreciate that this is not a particularly pretty or GUI-orientated approach, and Ubuntu may now have an 'easier' way of doing this.
 
Thank you for the help.
 
I try it but still stay on 100 Mb/s.
If I try ```
sudo ethtool -s eth0 speed 1000 duplex full 
```than network dosn't work.

---

### Post by Grenage on 2012-10-26
Hi again,

I am afraid I'm at a loss, I can change the adapter speed using those commands.  Do you get any error messages?

---

### Post by butyiba on 2013-01-13
> **Grenage said:**
> Hi again,
 
I am afraid I'm at a loss, I can change the adapter speed using those commands. Do you get any error messages?
 
 
Sorry for the late answer.
 
I don't have any error message.
 
Best Regards

---

### Post by rmil on 2013-01-13
Change ethernet cable take at least cat 6. Then play mambo jumbo with ethtools if you need.

---

### Post by tgalati4 on 2013-01-13
Check the cable for kinks or rat-chew.  Could also be bad or incorrect crimps--check with an ethernet cable checker.  Usually a 1 Gbit card will go to 100 Mbits when there is a fault in the cable.  It will go down to 10 Mbits if there is only one pair of working wires.  Of course it could be a defective card--they do tend to wear out.

---

### Post by Rsxhawk on 2013-01-16
What is this server plugged into?  A router?  A switch?  If you're going to hard code the speed to 1000/Full you have to do it on both ends of the connection, not just on the server side.  Having said that, the router or switch this server is plugged into must also be gigabit capable.  I would venture to guess that your server is gigabit capable, but your switch that you're plugged into is only 10/100.

If that doesn't work, make sure both ends are set to auto/auto and then see what speeds they negotiate at.  Even after all that, even IF both ends are 1000/Full capable, sometimes they can only talk to each other at 100/Full speeds - its something to do with the difference in the hardware from end to end.  I've seen it before.

---

### Post by jonobr on 2013-01-16
Hello

I dont know if you have tried this , but if you control both ends and they are both at 1000 , then maybe try disabling auto negotiate at both ends.

---

