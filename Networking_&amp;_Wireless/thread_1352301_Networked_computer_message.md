---
title: "Networked computer message"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2009-12-11
I have a computer on the network that I want to send me a system message when it has booted up, how do I do that? Something like 

"This Computer has connected to the network."

That way I can know when I can remotely log onto it.

Thanks,

Ben

---

### Post by pepsifx357 on 2009-12-11
Ok so I found Xmessage, I can log into the computer via ssh and type:

> xmessage Audio Computer Is Now Operational -center -display :0 &

It will display a popup box in the center of the screen.  However, I need this to happen without my input over the network when the computer boots up.

Kind of like the system beep for servers so you know they're booted up.

---

