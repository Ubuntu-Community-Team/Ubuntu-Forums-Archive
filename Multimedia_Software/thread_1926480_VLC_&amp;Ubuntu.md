---
title: "VLC &amp;Ubuntu"
date: 2012-02-16
forum: Multimedia Software
---

### Post by shalexsh on 2012-02-16
Hello dear experts.
  Please, advice me with VLC application, installed in the Ubuntu environment system.
   
  First about versions details:
  Ubuntu: 11.10
  VLC: 1.1.12
  In the computer 2 network cards: eth0 and eth1.
  On eth1 I have defined 4 sub interfaces:
  eth1.101
  eth1.102
  eth1.103
  eth1.104
  I want to open 4 applications of VLC, each of them should be running of in depended sub interface. 
  I try to make it by the following command:
   
  vlc -- miface eth1.101 udp://@225.1.1.1:1234
   
  According of Wireshark I see, that report leaves through necessary interface
  with tag 101. I see also, that multicast traffic comes on interface eth1.101,
  But VLC for some reason doesn't play it, as though he expects the traffic in other place.
  How to force it to listen necessary interface? Who knows, please help me.
  I will be very grateful. Thanks. Alex

---

