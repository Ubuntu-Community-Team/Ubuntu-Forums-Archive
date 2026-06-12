---
title: "Slow (really slow) Network speeds, config problem?"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by fisheater on 2009-07-20
Slow (really slow) Network speeds, config problem?

The setup:
Wireless router: WRT54G running DD-WRTv24
NAS: D-Link 323 2x 1T HD
Ubuntu 9.04 64 bit with 10/100 LAN cable ~15 feet to router
Also on the network: Laptop WinXP, Laptop Ubuntu 9.04, print server.

schematic setup:
9.04 <--via LAN cable--> WRT54G <--LAN cable-->D-Link 323 NAS

The transfer
NAS -> 2nd HD in tower of Ubuntu 9.04
Max speed 4.4 MB/sec
289 GB has taken almost 24 hrs to copy

This seems like a very long time and I dont know how to calculate how long it would take 4.4 MB/sec to transfer 289 GB (I am sure the units are different).

Q:
1.Is this a long transfer? Do the numbers make sense?
2.If not, what can I do to improve my transfer rate to the hardware ratings?

Thanks!

FE

---

### Post by TangoPappa on 2009-07-21
I have a similar problem using a Zyxel NSA-220, with 2 x 1TB drives in a RAID1 configuration.

I'm connecting over a WiFi link to my router, then to a public share in the NSA-220.

I'm connecting using a network connection to 192.168.1.122, the hardwired NSA-220 IP, with the network connection configured to connect as a Windows share, using Nautilus for the transfer.

Ubuntu 9.0.4, dual boot with XP SP3 on a Dell D620 laptop, dual 250 GB drives, 1 GB RAM, with both XP and Ubuntu installed on the C: drive.  The image to be transferred is stored on the D: drive.  Other than the Linux partitions, the drives are formatted as NTFS.

I was trying to transfer a 38 GB drive image from my laptop to the NSA-220.  After several hours, I'd transferred less than 3 GB of that file, and Nautilus was telling me that it was projecting another 15 hours for completion.  Transfer rate had dropped to somewhere around 600 kB/s from the initial 850 kB/s or so.  I aborted the transfer at that point.

This is about 4 times slower than it transfers in Windows over the same WiFi connection.  (Well, maybe slower.  It seems that the Ubuntu transfer was slowing down the further it got into the transfer.)

I'm new to Ubuntu, and Linux in general.  I suspect I have the network connection configured incorrectly, but haven't been able to figure it out with the reading I've done so far.

I'll be very interested in the responses you receive.

Tom

---

### Post by martinbaselier on 2009-07-21
It's probably a problem with the samba configuration.

open a terminal and enter (you can paste to it) the following line:
**sudo gedit /etc/samba/smb.conf**

and search for
SO_RCVBUF=8192

Just remove the # in front of the two lines you see there (the comments in the file will explain)
you might want to add a comment line (a line starting with #) to remind yourself you made that change. 
save & exit
then type:
**sudo service samba restart**
to restart samba

And check if this improves the speed. 

A speed of 4.4 MB/sec is quite low. You probably have a 100mbps LAN. 
the speed is usually shown in bits per second, or kilobit/s or megabit/s

1 megabyte/s  =  8 megabit/s

mpbs = mega bit per second = megabit/s or mb/s

sometimes a lowercase b means byte and a capital B means bit, but this is not used consequently.

---

### Post by TangoPappa on 2009-07-22
> **martinbaselier said:**
> It's probably a problem with the samba configuration.

open a terminal and enter (you can paste to it) the following line:
**sudo gedit /etc/samba/smb.conf**

and search for
SO_RCVBUF=8192

Just remove the # in front of the two lines you see there (the comments in the file will explain)
you might want to add a comment line (a line starting with #) to remind yourself you made that change. 
save & exit


In my file, that line contained 8192 for both the receive and transmit buffers.  I uncommented the line.

> 
then type:
**sudo service samba restart**
to restart samba
tom@D620:~$ sudo service samba restart
$samba: unrecognized service
tom@D620:~$ 

So I did a reboot instead.

Any idea why it doesn't recognize 'samba?'  That looks like a big red flag to me.

> 
And check if this improves the speed. 
If anything, it's slower now.  The transfer started at about 530 KB/s instead of 850 or so before, and Nautilus projected the transfer at 19 hours for 38 GB.

Back to the drawing board.

Thanks for your response, Martin.  

Tom

---

### Post by vmanisme on 2009-07-22
yep same here it only from slower from 3mbps to .3-.6

---

### Post by martinbaselier on 2009-07-22
service is used for scripts in /etc/init.d/
ls /etc/init.d/s*
should shed some light on it.

I just googled and found this link, which seems quite useful. 
[https://calomel.org/samba_optimize.html](https://calomel.org/samba_optimize.html)

---

### Post by doas777 on 2009-07-22
if you want to restart samba, use 
```
sudo /etc/init.d/samba restart
```

as for your nic, what do you see from 
```
sudo ethtool eth0
``` (substitute your interface name for eth0)?

there are many potential problems that could be at play. one of the first troubleshooting steps after establishing that the host network stack looks good, is to swap out the cable.

I usually get about 30MB/s from samba-to-samba over a Gigabit network, and usually about 8MB/s over 100Mb/s lines, and I do notice that that traffic is not all data transfer. for instance if I look at the copy dialog, it says 23MB/s but looking at the network traffic received on the catching end, it's more like 30-40 MB/s, though it seems like the overhead goes down as the connection speeds up.

also look at your duplex settings (from ethtool above) and make sure that your router is kewl with the settings (if one is auto, set both to auto; if one is explicitly configured, the other shoudl be too.) repeat that with eh link from the nas to the router. make sure that both lines are running at 100-full.

finally, how long has it been since you rebooted your router? I need to a couple times a year.

good luck,

---

### Post by doas777 on 2009-07-22
> **TangoPappa said:**
> I have a similar problem using a Zyxel NSA-220, with 2 x 1TB drives in a RAID1 configuration.

I'm connecting over a WiFi link to my router, then to a public share in the NSA-220.

I'm connecting using a network connection to 192.168.1.122, the hardwired NSA-220 IP, with the network connection configured to connect as a Windows share, using Nautilus for the transfer.

Ubuntu 9.0.4, dual boot with XP SP3 on a Dell D620 laptop, dual 250 GB drives, 1 GB RAM, with both XP and Ubuntu installed on the C: drive.  The image to be transferred is stored on the D: drive.  Other than the Linux partitions, the drives are formatted as NTFS.

I was trying to transfer a 38 GB drive image from my laptop to the NSA-220.  After several hours, I'd transferred less than 3 GB of that file, and Nautilus was telling me that it was projecting another 15 hours for completion.  Transfer rate had dropped to somewhere around 600 kB/s from the initial 850 kB/s or so.  I aborted the transfer at that point.

This is about 4 times slower than it transfers in Windows over the same WiFi connection.  (Well, maybe slower.  It seems that the Ubuntu transfer was slowing down the further it got into the transfer.)

I'm new to Ubuntu, and Linux in general.  I suspect I have the network connection configured incorrectly, but haven't been able to figure it out with the reading I've done so far.

I'll be very interested in the responses you receive.

Tom

4.4MB/s is not bad at all for a type-G wireless connection. 54Mb/s is about 1/20th of 1000Mb/s, and i get about 30MB/s at gigabit. by that reasoning, you already have about 3 times the bandwidth I'd expect (1.5 MB/s).

morale of the story, is that wifi is only useful for web surfing.

---

### Post by martinbaselier on 2009-07-22
@doas77 
FYI:

These 2 commands are equivalent:
sudo /etc/init.d/samba restart
sudo service samba restart
see:
man service

---

### Post by TangoPappa on 2009-07-23
> **doas777 said:**
> what do you see from 
```
sudo ethtool eth0
``` (substitute your interface name for eth0)?


First, to identify my wireless port:

tom@D620:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:1f:cf:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.0.7 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

<snip>

Next, to get eth0's settings:

tom@D620:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: Unknown! (65535)
    Duplex: Unknown! (255)
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: d
    Current message level: 0x000000ff (255)
    Link detected: no
tom@D620:~$ 


Does that tell you anythhing?


> 
there are many potential problems that could be at play. one of the first troubleshooting steps after establishing that the host network stack looks good, is to swap out the cable.
As I mentioned in my first post, I'm comparing the transfer speed in Ubuntu with the transfer speed I get in Windows, with all other conditions the same.  The transfer rate is over four times slower in Ubuntu than it is in XP.

> 
finally, how long has it been since you rebooted your router? I need to a couple times a year.
Good idea.  I didn't think of that.  However, rebooting my router didn't fix it.

Thanks for your response.

Tom

---

### Post by TangoPappa on 2009-07-23
> **martinbaselier said:**
> service is used for scripts in /etc/init.d/
ls /etc/init.d/s*
should shed some light on it.

I just googled and found this link, which seems quite useful. 
[https://calomel.org/samba_optimize.html](https://calomel.org/samba_optimize.html)

Thanks, Martin.

I'm studying the linked article, and the one linked within that one on the config file ins and outs.  I'll do some screwing around and, if I'm able to solve the problem, I'll post my results.

Tom

---

### Post by doas777 on 2009-07-23
> **TangoPappa said:**
> 
<snip>
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: Unknown! (65535)
    Duplex: Unknown! (255)
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: d
    Current message level: 0x000000ff (255)
    Link detected: no
</snip>


this shows that there is somthing wrong with your wired nic, or that you are using an interface other than eth0. 

note the "Link Detected: no". also the Unknown speed and duplex, usually indicates that the link is not capable of carrying the signal at that speed, or that the switch port capabilities could not be autonegotiated (or the cable is not up to that spec).

---

### Post by TangoPappa on 2009-07-23
> **doas777 said:**
> this shows that there is somthing wrong with your wired nic, or that you are using an interface other than eth0. 

note the "Link Detected: no". also the Unknown speed and duplex, usually indicates that the link is not capable of carrying the signal at that speed, or that the switch port capabilities could not be autonegotiated (or the cable is not up to that spec).

OK, thanks.

I'm a Linux novice; that stuff is way above my pay grade.  I'll take the easy way out and just use Windows for large file transfers.

Thanks for the help, everybody!

Tom

---

