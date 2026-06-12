---
title: "rfcomm listen"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by ninja123 on 2009-11-30
Hello All,

I have an Ubuntu Jaunty machine. I have an embedded board with embedded linux. Now these two have bluetooth sticks and try to communicate. I have some services running on these machines like DUN, Hf etc. When I do an 'rfcomm connect 0 <bd addr of ubunutu> 7' from my embedded board, the connection gets established.

But although I have a service running on ch7 in my embedded board, when I do 'rfcomm connect 0 <bd addr of emb board> 7' the connection is refused.

I finally got it working by putting channel 7 on listen mode.

However what I dint understand is, is it by default in listeing mode in Ubunu?

The bluetooth start script has a 'rfcomm bind all' command though.

Can anybody tell me how this is set in Ubuntu?

---

