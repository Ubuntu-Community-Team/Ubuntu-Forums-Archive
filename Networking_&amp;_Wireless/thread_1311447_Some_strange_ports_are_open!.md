---
title: "Some strange ports are open?!?"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by WesLee on 2009-11-02
Hello,

this is a part of the output from netstat -l:

tcp        0      0 *:5900               *:*                     LISTEN     
tcp        0      0 *:ftp                  *:*                     LISTEN     
tcp        0      0 *:ssh                 *:*                     LISTEN     
tcp        0      0 *:ipp                 *:*                     LISTEN     
udp       0      0 *: xdmcp            *:*                                
udp       0      0 *:55220             *:*                                
udp       0      0 *:bootpc            *:*                                
udp       0      0 *:mdns              *:*                                
udp       416  0 *:ipp                  *:*

I recently installed kde to enable xdmcp on Karmic Koala.
Now suddenly there are a few processes on the list that I didn't see before or they where never there before..?

ftp, ssh, ipp and xdmcp I'm familiar with.

mdns is for my NAS I think (Please correct me if I'm wrong..)

But what about 5900 (I'm really concerned about this one, because I found out that this port is used for VNC but I never installed that!), 55220, bootpc and ipp on udp?

I know that ipp is for my printer, but why is it also on udp?

---

