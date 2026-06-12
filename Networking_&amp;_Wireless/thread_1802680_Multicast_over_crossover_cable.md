---
title: "Multicast over crossover cable"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by vodas89 on 2011-07-12
Hello, 
is there any chance to stream multicast over crossover cable from ubuntu machine to another machine ? 

I would like to stream two multicast stream (video - vlc) from ubuntu to one iptv modulator which processes only multicast streams.

---

### Post by jmoorse on 2011-07-12
That's an interesting question.  I think you will need a switch in the middle to handle multicast group memberships.

I don't think a direct crossover connection will suffice for mcast.

---

### Post by vodas89 on 2011-07-12
I thought multicast groups handling could be a problem. Okay and what about transformation multicast streaming to broadcast ... somehow.

Because of one on one network I don't need membership stuff ... If my modulator be able to handle unicast stream, it would be very simple but it is not. 

Do you think is there a possibility to use a broadcast streaming (with VLC of course) ???

---

### Post by jmoorse on 2011-07-12
Yes it looks like you could stream to a broadcast address:

From [http://wiki.videolan.org/Documentation:Streaming_HowTo/Stream_a_File:](http://wiki.videolan.org/Documentation:Streaming_HowTo/Stream_a_File:)

vlc -vvv video1.xyz --sout udp:192.168.0.42 --ttl 1

Use the broadcast address of the point-to-point adapter:

Example from my ifconfig:
Bcast:192.168.122.255 

I think your IPTV is going to be the tricky part.  Good luck and let me know how it turns out.

---

### Post by vodas89 on 2011-07-12
Hmm ... okay i'll give it a try

---

