---
title: "Wireless issues in ubuntu 9.10"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by Amenotep on 2009-11-12
Hello all,
I've been using ubuntu for a while now, and i just decided to install it on my primary laptop. I did that along with some college friends. I had windows installed before the linux installation and in windows i could access wireless networks with no problems at all - all of them anywhere. 

However since i installed ubuntu i've been having a lot of problems with wireless connections, problems my friends don't have. 

First of all it will only connect to wireless networks if the wireless signal is higher than 90%, and even so it is really slow. So i'm thinking it's a compatibility problem with my wireless card and ubuntu, but i have no idea how to solve it. Wired networks work just fine the problem resides really in wireless networks. And since my college has a wireless network implemented i really need it to work. 

I would appreciate any help you can give me. My pc is an insys 8761SU upon running the command I found out that my wireless adapter is Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter . 

Thanks in advance.

Amen

---

### Post by Amenotep on 2009-11-12
I've searched the web and i found a linux driver for this adapter. However it's extension is tar.bz2 and i have no idea on how to install it. Any1?

---

### Post by t0mppa on 2009-11-12
Download the file to /home/<your_user_name>/realtek/ for instance. Then open up a terminal (Applications / Accessories / Terminal), change into the directory you downloaded it with **cd realtek**, then run **tar xjf <file_name>** to extract the files from the archive. After that there should be a README or INSTALL file which you can consult to for further instructions and if you need more help, just post another question here.

---

### Post by Amenotep on 2009-11-12
Thank you for your help. But really all i had to do was installing the file and then use the .inf with ndiswrapper. 

To everyone who has this same problem the solution is quite easy, just get ndisgtk, then from a console type sudo ndisgtk, then click install new driver and chose the .inf file.

Has it stands, it's working better than in windows.

Ubuntu - 99, windows - 0

---

