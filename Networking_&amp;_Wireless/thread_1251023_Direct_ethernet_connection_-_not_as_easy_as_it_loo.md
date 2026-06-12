---
title: "Direct ethernet connection - not as easy as it looks?"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by njparton on 2009-08-27
I'm trying to connect 2 computers directly using ethernet but it's not as easy as it looks.  I've followed the various other posts in this forum but there must be something specific with my set up that I'm not doing.

My main PC runs Vista x64 home premium and connectes to the internet via a USB2 wireless N adapter. My gigabit wireless N router is setup to act as a DHCP server giving out addresses in the range 192.168.1.2 - 10 (subnet mask 255.255.255.0).

My NAS runs Ubuntu server x64 and is currently connected to the router via a cat 5e cable, but over wireless N the performance isn't great but tolerable (samba).  eth0 is set up as inet static and the workgroup in samba is set to MSHOME as with all my PCs.

I'd like to move my NAS to a direct ethernet connection to my Vista PC but I can't get it to work.  I've enabled one of the onboard NICs on my Vista PC to do this (I used to connect to the internet using that NIC so I'm sure it's working).

My Vista PC has IP address 192.168.1.2 and my NAS usually 192.168.1.10.  When I've moved my NAS to a direct connection I've changed it's address to 192.168.1.20 and so outside the address range of my routers DHCP server (in case there was a conflict). I've also tried it at 192.168.1.10 but no joy.

I've tried both normal patch and crossover cables but neither let me see the NAS in Vista.  In fact the crossover cable causes my Vista PC to shutdown immediately on plugging in (hardware/electrical shutdown not a Windows BSOD).

Any ideas where I'm going wrong? Can I have both a USB2 connection to my router and an ethernet connection to my NAS at the same time?

---

### Post by alexlafreniere on 2009-08-27
I couldn't tell you what's causing your computer to shut down like that, but I know you use a crossover cable to connect two computers directly via their NIC's. And yes you can have a USB connection to your router and a direct connection to the NAS at the same time, but if the NAS isn't connected to your network, then it really isn't a NAS, now is it? ;) I know you may have extenuating circumstances, but I think skipping the direct connection entirely and just keeping the NAS on the network would be easier. Maybe we can help you find a solution to the reason that you need to connect the two machines directly?

---

### Post by njparton on 2009-08-27
Correct, it would no longer be a NAS but I only now connect to it from my Vista PC so it no longer needs to be connected to the wider network.

I should just take out the 2 raid 0 HDD's and 3ware card and stick them straight in my Vista PC for ultimate performance but I've been there in the past and accidentally formatted the array rather than the system hard drive by mistake prior to re-installing windows.  Of course I lost all my data and hence a physically seperate device was called for (after my wife beat me up...).

Anyway I would really like to solve the direct connection problem if possible.  I've read in various places that most gigabit nics can auto crossover themselves (I forget the official terminology) so that a crossover cable isn't needed.  It's a moot point though as I've tried both and neither work (the crossover able obviously being worse and causing a serious issue).

---

### Post by njparton on 2009-09-08
In case anybody else stumbles across this thread I thought I'd bring it to a close by posting how I got this to work.
 
Firstly, it appears that some (most?) gigabit ethernet controllers can now auto switch between a normal connection (to a router or switch) and a cross-over connection directly to another ethernet port. I have got my direct connection working with either a normal patch cable or cross-over cable - it doesn't matter which.
 
The biggest step I made in getting this to work was realising that I had to manually fix the IP address of the NIC I was trying to connect to on the host (or gateway) computer (the vista PC in my case above). I set mine to 192.168.1.11 which is outside of the IP address range of my router and crucially different to the IP address of my wireless adapter which connects to my wireless router and hence the internet. 
 
As soon as I did this I achieved a direct connection to my ubuntu NAS (now a DAS of course).
 
Prior to doing this you should set up your ubuntu ethX NIC with a static IP address as DHCP doesn't seem to work, even when ICS is activated in vista. I set mine to 192.168.1.12 with the gateway IP address set to that of my vista PC.
 
This gave me working samba and openssh connections.
 
The next thing to get fixed is giving access to the internet for my ubuntu DAS through vista as this isn't working automagically. I need to spend some time this evening to see if I can ping my vista PC from ubuntu (and vice versa) and whether I can ping an internet IP address and/or an internet address such as google.com. If I can ping an internet IP address but not a website such as google.com then I have a DNS issue and I need to update resolve.conf with some new nameserver entries such as those provided by openDNS. If I can't ping my vista PC from ubnutu then I have lingering connection problem of some sort although I hope this is unlikely as both samba and openssh are working.
 
I hope this helps someone in the future!

---

### Post by ario on 2010-05-31
It can't help me. I just want to now what are those things:
NAS
DAS
ICS
&...:D

---

### Post by tofsjonas on 2010-08-23
Thank you thank you thank you!

I can now connect directly from my mediaplayer to my nas so that I don't have to keep changing cables in my overcrowded router.

Again, thank you! :)

---

