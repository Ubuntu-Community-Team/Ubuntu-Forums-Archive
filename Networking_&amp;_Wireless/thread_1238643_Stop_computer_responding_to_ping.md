---
title: "Stop computer responding to ping?"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by fela on 2009-08-12
Is it possible to add some sort of firewall (or such thing) to stop a computer responding to ping from other computers on the LAN? The reason is mainly to see if it's possible, but also because my dad once caught me late at night on my computer, due to his wake-on-lan app detecting my computer as being on :lolflag:

I'm pretty sure it uses ping to detect what computers are on and connected. Obviously if it doesn't this trick wouldn't work. That's assuming that it's possible in the first place!

---

### Post by Iowan on 2009-08-12
It should be possible to use a firewall to filter out pings (my linux-based dial-up router/firewall could), but (since you mentioned it) forum policy does not condone bypassing security measures.

---

### Post by fela on 2009-08-12
> **Iowan said:**
> It should be possible to use a firewall to filter out pings (my linux-based dial-up router/firewall could), but (since you mentioned it) forum policy does not condone bypassing security measures.

Ok. But how is this bypassing security measures?

---

### Post by lisati on 2009-08-12
> **fela said:**
> Ok. But how is this bypassing security measures?

Good question: my thoughts at the moment is that depening on the circumstances, preventing the resonse to a ping could be seen as a security measure, not the opposite!

---

### Post by fela on 2009-08-12
> **lisati said:**
> Good question: my thoughts at the moment is that depening on the circumstances, preventing the resonse to a ping could be seen as a security measure, not the opposite!

Exactly what I thought!

---

### Post by cariboo on 2009-08-12
You have to send a special packet in order for wake on line to work, a ping won't do it. 

> When the PC shuts down, the NIC still gets power, and keeps listening on the network for a 'magic' packet to arrive. This packet must contain a certain byte-sequence, but can be encapsulated in any kind of packet (IPX, IP, anything). 

It may not even have been anything you were doing, that caused his computer to wake up, unless of course he booby trapped your computer to tell him when you are up to no good. :)

---

### Post by fela on 2009-08-12
> **cariboo907 said:**
> You have to send a special packet in order for wake on line to work, a ping won't do it. 



It may not even have been anything you were doing, that caused his computer to wake up, unless of course he booby trapped your computer to tell him when you are up to no good. :)

No, it's not about the special packet thing. It's an app he has on his computer that automatically detects all IPs on the network, as long as the computer is on (it doesn't seem to recognize NICs whose host computer is off for some reason. Perhaps because you can't ping it :)).

---

### Post by Iowan on 2009-08-12
> **fela said:**
> Ok. But how is this bypassing security measures?From "dad's" perspective?

---

### Post by fela on 2009-08-12
> **Iowan said:**
> From "dad's" perspective?

Nope, I only wanted it so he couldn't see my NIC on the LAN. It's not important though, it was actually mainly just to see if it was possible. He's in no need to ping my computer, nor is anyone else.

---

### Post by Iowan on 2009-08-12
[This]("http://ubuntuforums.org/showthread.php?t=1069540") thread might provide an answer about disabling ping-requests.

---

### Post by fela on 2009-08-12
> **Iowan said:**
> [This]("http://ubuntuforums.org/showthread.php?t=1069540") thread might provide an answer about disabling ping-requests.

Thx :)

---

