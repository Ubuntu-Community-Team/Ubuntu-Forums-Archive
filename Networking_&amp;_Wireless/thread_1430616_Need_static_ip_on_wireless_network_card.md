---
title: "Need static ip on wireless network card"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by larbyl on 2010-03-15
I want my Ubuntu desktop to have a static ip-address, i have altered the interfaces file to the below and also filled the info regarding my wireless network card but still every time I reboot the desktop gets the ip 10.42.43.1, HOW is that possible???

I use a apple time capsule router, I want my desktop to run a apache server thats why I need the static ip. I also want the static ip to be set on the wireless network interface. I have an old laptop with an internal Intel pro 2200 card so there should not be a driver problem.

This i my interfaces config:

#The loopback network interface
auto lo
iface lo inet loopback

#The wireless network interface
iface eth1 inet static
address 10.0.1.15
netmask 255.255.255.0
network 10.0.1.0
broadcast 10.0.1.255
gateway 10.0.1.1
wireless-mode managed
wireless-essid "My_Net_Id"
wireless-key1 "My_secure_Key"

My ifconfig shows:
eth1
Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
inet6 addr: fe80::216:6fff:fe79:1d12/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B)  TX bytes:2153 (2.1 KB)
Interrupt:21 Base address:0x6000 Memory:c8400000-c8400ffff

To be on the sure side to get this to work I have configured my router(DHCP) to give my wireless-HWaddress the ip of 10.0.1.15, STILL the ubuntu desktop starts with the false address above.

I am a newbie to ubuntu, and this I must say puzzles me plenty. I have searched several forums regarding this, hope you can help me.

---

### Post by Iowan on 2010-03-15
If the router is capable, it's pretty painless to have it issue a static lease (outside the dynamic lease range)  - based on machine's MAC address. Then, the machine can be left for DHCP address - but it always gets the same one.

---

### Post by larbyl on 2010-03-16
Thanks for your answer!

The weird part, I have set a static ip on the MAC-address in the router, but still the desktop sets a false ip... thats is the puzzle....

//Lars

---

### Post by Iowan on 2010-03-16
What IP does the desktop use? If it's in the 169.254.X.X subnet, it's **avahi** "helping".

---

### Post by larbyl on 2010-03-17
Hi again,

I have now tested to see if I am doing it wrong in the DCHP. I have now set a dedicated ip in the DHCP for my windows and macs at home and that work great. The ubuntu does still not want to take the is.

The Ubunto chooses the same ip every time, it is: 10.42.43.1 and the DCHP cannot even give and address like that. there is a limit on the DHCP to only give addresses that are on the net 10.0.X.X...

So any ideas?
//L

---

