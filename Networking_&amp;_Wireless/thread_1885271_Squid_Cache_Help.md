---
title: "Squid Cache Help"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by at7371 on 2011-11-22
I have installed squid in order to cache some videos from a website that we use which when accessed without caching consumes the bandwidth on our internet circuits.  

When I run the video from the ubuntu server running the squid software the video is rendered from the cache jus fine.

When I run the video from a client pointing to the ubuntu server as a proxy server, the client does run the video at all.  I see that in the access.log that the cache is being hit.

I am thinking it is permissions somewhere in the squid.conf file but I have not been able to find it.  Any help with people experiencing this issue would  be very helpful.

The video is a windows media file format which also has the pragma: no-cache in the header.  So the developer of the files really don't want these video's cached.

---

### Post by SeijiSensei on 2011-11-22
Squid abides by the caching policies that a website imposes via the Pragma or the Cache-Control HTTP headers.

---

