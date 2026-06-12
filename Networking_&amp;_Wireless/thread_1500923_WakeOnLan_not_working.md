---
title: "WakeOnLan not working"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by cwig on 2010-06-03
I have been fight to get this WOL working for the pass 2 weeks or so and I have had little success.  The 

computer I am currently trying to get to wake from a powered off state is a Inspiron 600m with a ethernet 

controller BCM4401-B0.  It has WOL in the BIOS, and I have enabled it.  I have tried on two different 

routers, a ActionTec GT704-WG and a Verizon 7501 and neither worked.

Right now I just want to get it to work within the local network, but I have also tried from an external 

location with port forwarding set up.  So far I have used a packet sniffer on Inspiron 600m to confirm that 

that the magic packets are getting to the computer.  When I have the computer off, I haven't had any luck 

yet getting it to turn on. I have been using wakeonlan and I have been sending the packets to 

192.168.0.255 or 192.168.200.255, depending on the router I am using.  Any help with this would be 

greatly appreciated. Thanks


-Curtis

---

### Post by ilikeyourflannel on 2010-06-03
How are you sending the magic packet?  I've done this before with the perl module Net::Wake.  In case you're not familiar, (and assuming Perl is installed) to get the package just type "cpan" at the terminal and then "install Net::Wake".  After the package is installed you can run it from the command line as a Perl one liner via the following command:

perl -MNet::Wake -e "Net::Wake::by_udp(undef,'00:00:00:00:00:00')" 

Of course replacing the '00:00:00:00:00:00' with the MAC address you're trying to wake up.  You might also try 255.255.255.255 instead of undef.  Hope this helps!

---

