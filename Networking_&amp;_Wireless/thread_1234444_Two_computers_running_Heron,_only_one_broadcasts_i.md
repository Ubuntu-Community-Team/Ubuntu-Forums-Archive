---
title: "Two computers running Heron, only one broadcasts its name to router"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by ladasky on 2009-08-07
Quick question, I hope...
 
I have two computers.  One: an older IBM ThinkPad laptop.  The other: a new AMD triple-core desktop.  Both have had Ubuntu 8.04 installed from the same CD-ROM.  I haven't messed with network settings in a major way, as far as I know.

My home router is a Linksys WRT54G.  I am trying to troubleshoot various networking problems which arose when I starting changing computers and upgrading software.  
 
Ubuntu is supposed to supply a computer's name to a router.  Well, the laptop's name shows up on the router's DHCP client table.  But the desktop machine does not.
 
I have a printer connected to the desktop machine.  I'm thinking that correcting this naming problem might help me restore printer sharing.  Curiously, I designated a folder as "shared" on my desktop machine (the one without the visible name) and, after some software was installed (Samba?), it is visible from the laptop.

Thanks for any advice!

---

### Post by Iowan on 2009-08-07
Check */etc/dhcp3/dhclient.conf* - there's a line:```
send host-name "<hostname>";
```that can be modified to (manually) include the machine name.

---

### Post by ladasky on 2009-08-08
> **Iowan said:**
> Check */etc/dhcp3/dhclient.conf* - there's a line:```
send host-name "<hostname>";
```that can be modified to (manually) include the machine name.

Thank you, Iowan, that solved my problem!
 
Now, I have to say, I'm baffled by the large differences between the dhclient.conf files installed on the two machines.  Yes, I know, one's a laptop and the other's connecting by hard link.  Still, the laptop got a well-annotated, 50-line shell script, and all the desktop got was this:
 
```
request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, host-name, ntp-servers;
```
 
It was formatted without any line breaks, too, exactly as you see there.
 
I added the send host-name command as you suggested.  I got better results when I made the send host-name command the first command in dhclient.conf -- because the second line requests it right back.

---

