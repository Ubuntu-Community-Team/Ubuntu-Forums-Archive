---
title: "P-to-P network for video conferencing over the LAN"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by Manish Tiwari on 2011-11-02
I am trying to
-capture and synchronize video and audio
-compress the captured data
-transport the compressed data using suitable protocols
-decompress the received data at the other end
-and finally playing it over the LAN.

So, which protocols should I use: H.323 or RTSP or anything else? Which are the best suitable APIs for the above steps?
Also, tell me if I should proceed in some other way.

---

### Post by jonobr on 2011-11-02
Hello

Maybe others have a different opinion here,  but

The questions your asking are ok, but they are normally why you would hire a consultant or network engineer with networking knowledge to tackle this complexity.

Theres a lot omitted from your lines like bandwidth requirements,  available hardware, QoS requirements,security requirements expectations, codec requirements for voice, how does ubuntu come into all of this?

For example, I could propose something as simple as Skype for your voice and video requirements,  but I take it that this is more a complex network design question, in which case I would start discussing the merits of SIP vs H323, of TCP against UDP,
Of using Frame Relay as opposed to MPLS, 


However, the question is pretty general.....

---

