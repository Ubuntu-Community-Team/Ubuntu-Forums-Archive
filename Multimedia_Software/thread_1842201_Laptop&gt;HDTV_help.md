---
title: "Laptop&gt;HDTV help"
date: 2011-09-10
forum: Multimedia Software
---

### Post by FSMSJ on 2011-09-10
I can not get my laptop to properly display on my HDTV, the tv stretches the screen so I can not see the edges.  Ive had this problem in vista and nvidia had a tool to restrict the screen so that it fit the TV.  Is there something like this for ubuntu?

Specs:
HP DV6000
nvidia 8400m GS
Ubuntu 11.04 64 bit
Nvidia driver 270.41.06
Nvidia XServer 11.0

tv- Sharp Aquos 37" over HDMI cable

---

### Post by papibe on 2011-09-10
In the case of my Sony Bravia and my brother's Samsung, the problems was in the HDTV side.

In the Sony you can fix it by setting 'Full Pixel' to Screen -> Display Area. In the Samsung set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

I hope it helps,
Regards.

---

### Post by FSMSJ on 2011-09-11
Any idea how to strech/constrict the screen size by using the laptop?  This TV was given to me with no remote.  I tried my cable boxes 'universal' remote, but I cant navigate the menu, even after trying the 5 possible codes...  :(

---

### Post by Mekik on 2011-09-11
i am using JVC HDTV + HDMI connection.
install additional driver for Display ATI Catalyst found at Ubuntu software Center (within ubuntu 11.04).

connect HDMI cable between notebook and tv. Activate the hdmi display from tv.

open system setting -> ATI Catalyst Control Center (Administrative).
click on TV icon and change the setting accordingly. 
**by default setting is automatically set for you once the connection active. sometime the ubuntu required restart to apply new settings.

so far i do not have any issue with hdmi connection except ubuntu require to restart to apply new setting. :)

---

### Post by FSMSJ on 2011-09-11
> **Mekik said:**
> i am using JVC HDTV + HDMI connection.
install additional driver for Display ATI Catalyst found at Ubuntu software Center (within ubuntu 11.04).

connect HDMI cable between notebook and tv. Activate the hdmi display from tv.

open system setting -> ATI Catalyst Control Center (Administrative).
click on TV icon and change the setting accordingly. 
**by default setting is automatically set for you once the connection active. sometime the ubuntu required restart to apply new settings.

so far i do not have any issue with hdmi connection except ubuntu require to restart to apply new setting. :)

Thanks but I have a nvidia card.  Read above.

---

