---
title: "Question"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by Elshentenawy on 2012-10-20
hi every one 
well 
Is there is any way that I can install ubuntu server that can control bandwidth over LAN and WAN networks If not can any one recommend one other than mikrotik !!
&
can I install a streaming server using ubuntu server 
&
can I make afile sharing website using ubuntu server 

IF YES  Please just recommend some topics or website that I can look AT ..
ThanQ

---

### Post by Lars Noodén on 2012-10-20
You can control outgoing bandwidth using iptables.

You can do streaming with [Icecast2](http://www.icecast.org/), [VLC](http://www.videolan.org/doc/streaming-howto/en/), or [ffmpeg](http://ffmpeg.org/trac/ffmpeg/wiki/StreamingGuide).

You can do file sharing by setting up Samba or SSHFS or both. Samba works locally, SSHFS works both over WAN and LAN.

---

### Post by Elshentenawy on 2012-10-20
thanQ 
IS  iptables authorize people to use or not use the internet over the network ?
can you recommend any topics or sites that might help !!!
any way I'll google it  
thanks

---

### Post by Lars Noodén on 2012-10-20
iptables filters the network packets.  That filtering can be done on many, many factors.  

I'm not sure where there is a good, simple summary of the capabilities.  The Ubuntu pages are here
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

There's an older tutorial available:
[http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html](http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html)
If you look at the options available for iptables, you'll get an idea of some of the capabilities.  Since you asked about throttling bandwidth, it was the first tool that came to mind.

---

### Post by Elshentenawy on 2012-10-20
thanks this really gonna  help me alot !!

---

