---
title: "dial-up ICS using a switch + webramp"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by sir_cheats_a_lot on 2009-10-14
this setup is just plain ugly. alright here's the deal *takes a deep breath*; ok i want to setup internet connection sharing, between my computer and my Mom's old(dying) HP.  the problem lies in that my cords just aren't long enough to directly from the switch to the HP, so i have one cord which i plugged into port #1 on the switch going to my computer.  i have another cord plugged into port #5(uplink) going to an old webramp(switched to hub mode) port #1; and another going from webramp's port #2 going to the HP's NIC card.

   Both of them can access the webramp. but i'm using the HP as the host for this dialup connection sharing.   I am pretty sure it'd probably work if i had a direct connection between the switch and the HP, instead of this mangled mess, but i don't have a splitter/coupler for the cables.  what's odd is the webramp is showing up as a DNS; ip: 192.168.1.1
ifconfig shows:
```
eth0      Link encap:Ethernet  HWaddr 00:10:5c:ea:45:bc  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5cff:feea:45bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:314861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:315698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20588968 (19.6 MB)  TX bytes:17333519 (16.5 MB)
          Interrupt:17 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:263717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13187648 (12.5 MB)  TX bytes:13187648 (12.5 MB)
```

with these troubled economic times we're going to have to drop the second phone line, so i need to be able to at least share the dial-up connection or me and the people of the house are going to be fighting over it.  any thoughts on how best to get this running?  or should i be using my desktop to play host?  suggestions?  
 
 i'm painfully aware of how slow it'd end up being.. but it'd still faster then what i'm getting on the second phone line at the moment(barely 18-20k i'm sure).  it's tolerable for surfing, but when i start downloading...well... not so much.

---

### Post by sir_cheats_a_lot on 2009-10-15
*BUMP!*


alright got samba going, and can share files and use the printer in the kitchen.  the final hurdle, i think is the ICS.  what would be the best way of getting around it?

---

### Post by sir_cheats_a_lot on 2010-01-02
mmhmmm... yes.. dead silence... what everyone likes to see, :lolflag:  only bothering you poor folks because firestarter doesn't seem to like me enough to work properly, so i've been doing this the whole time without it's assistance.  if only i had a longer cord i wouldn't need the ancient webramp, *sighs*  or would i? 


  oh... and incidentally the situation is changing slightly: i've got an old eMac sitting in my room with Ubuntu in mid-install since i've no legit OS X CDs, just ISO files, and a lack of CD-Rs.  got it from salvation army, for $5.25(i figured why not) so absolutely nothing came with it. im going to need a way to get at least these two computers sharing the net, as it's the second model, with 1ghz cpu, 256MB ram(upgraded to 768MB), and a CDROM drive.  has no built in dialup modem, does have an ethernet card though(probably the only good news).

---

### Post by sir_cheats_a_lot on 2010-01-05
HA.. ok i've got internet going on the eMac though my computer.  you know... all those how-to's out there telling you to use firestarter for this situation fail to tell you, something rather important in this particular instance.  you need the dhcp-server package installed, along with the dnsmasq, and ipmasq in order to have any hope of this working...go figure.   just wish I could have made it over the webramp hurdle.  how'd i figure out i needed the dhcp package?  well i was looking at the switche's manufacturer's website(Dynex), when it mentioned needing some sort of dhcp serving software in order to actually be able to split an internet connection.  simply opened up synaptic, and searched for both words in name and desc. bingo: "dhcp3-server", installed, restarted networking, and I finally had a progress bar show up on firefox, it was able to be used yet, but.. it was a glimmer of hope, and it got rid of the annoying eth0 is not ready message. reran ipconfig eth0: reset the IPs again, to 192.168.0.1, and 192.168.0.2, reset networking again and on I am, loading the new software packages on the eMac. graphics is going to be top priority now i think, now that I wont have to hunt down dependencies and move then via flash-drive.  sure splitting a dialup connection doesn't seem worth while to most...but for some that's the only choice.

    what's funny though is i think the webramp itself can handle DNS.   oh well it's good enough for me i think. have installed ubuntu on the eMac.  just gotta find a way to install the proper video driver; am still using fbdev,that i specified in xorg.conf to get the xserver going so i could actually do the install from liveCD.  would like to get nwn going on it if possible.

 Alright folks: this is mostly solved, so i guess i shall mark it as such.

---

