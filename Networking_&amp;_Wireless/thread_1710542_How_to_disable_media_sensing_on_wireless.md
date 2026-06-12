---
title: "How to disable media sensing on wireless?"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by schuler101 on 2011-03-20
Hi...

I am doing some experiments comparing the performance of wireless under 3 different cases:

(i) without media sensing (carrier sensing). 
(ii) with media sensing but no RTS/CTS
(iii) with media sensing and RTS/CTS

I know RTS/CTS can be controlled by
iwconfig interface rts {N|auto|fixed|off}

However, what about media sensing? Can it be disabled? If yes, how?

---

### Post by schuler101 on 2011-03-22
bumped...anyone plz?

---

### Post by conneco on 2011-03-23
sounds like you're trying to create a wireless jammer, 

If you could turn media sensing off and you did then no one would be able to communicate because your wifi card would technically have turretts. I believe that in 802.11 RTS & CTS are optional however CSMA-CA is very much not.

---

