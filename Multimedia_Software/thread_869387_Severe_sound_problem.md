---
title: "Severe sound problem"
date: 2008-07-24
forum: Multimedia Software
---

### Post by think13 on 2008-07-24
I have been experiencing a recurring problem that causes my machine to hang, requiring me to do a hard reset.

The problem happens when I run a Java applet which uses sound and start Amarok.  Amarok gives an error on startup: "xine was unable to initialize any audio drivers".  Later, whenever I try to log off or shut down, my computer hangs and I must hold down the power button to shut down.

I have Amarok configured to use alsa as it's output plugin.  
I just figured out that ```
sudo alsa force-reload
``` fixes the problem, but I don't want to do this every time.

Anyone have an idea what's going wrong here?

---

### Post by bdi_fc on 2008-07-26
> **think13 said:**
> 
I just figured out that ```
sudo alsa force-reload
``` fixes the problem, but I don't want to do this every time.



I noticed that in order to get my SPDIF output to function, I have to force-reload alsa in order to get it to work. 

Anyway to make it work by default when the computer starts up?

---

### Post by think13 on 2008-07-29
*bump*

Can anyone help either of us?

---

