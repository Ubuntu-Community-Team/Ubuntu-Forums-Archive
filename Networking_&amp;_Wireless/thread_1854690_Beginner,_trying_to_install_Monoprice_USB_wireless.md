---
title: "Beginner, trying to install Monoprice USB wireless N adapter, Ubuntu 11.04"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by severdhed on 2011-10-04
I tried searching the forums, but couldn't find anything of value.

I just picked up a Wireless N USB adapter from monoprice.com

[http://www.monoprice.com/products/product.asp?c_id=105&cp_id=10501&cs_id=1050108&p_id=8072&seq=1&format=2](http://www.monoprice.com/products/product.asp?c_id=105&cp_id=10501&cs_id=1050108&p_id=8072&seq=1&format=2)

it lists Linux as a supported OS.  It came with a CD, that does in fact have a linux folder that apparently contains the drivers, however i can't figure out how to install them.

I was using a Rosewill USB adapter, when i plugged it in, ubuntu automatically picked it up and it started working.  I would like to use this new one however, since it is tiny and should not be as likely to be broken off.

I am relatively good with computers when it comes to Windows...however i just recently switched to Ubuntu on my laptop to try it out. (about 3 months ago).  i really like it so far, even though things seem to be alot more difficult.

anyway, i can't figure out how to install this device.  when i plug it in, nothing seems to happen.  I tried contacting monoprice support, however they can't help me unless I'm running windows.  I connected it to my windows 7 computer to make sure it works, it pops right up with no issues and is detected as:

Realtek RTL8188CU WIreless LAN 802.11N USB 2.0 Network Adapter

I have searched google for a while, and i have found mention of similar issues, with resolutions, but they all seem to be a little over my head. I can't seem to find a good step by step guide that is thorough enough to get through this.  I see threads with steps like (install ndis wrapper) but no instructions on how to actually do that.   I can follow directions and type commands and get things working if someone could help me.  

I have the drivers on the disk, I just need some help getting this thing to work...is there anyone out there that can help me?

---

### Post by pdc on 2011-10-05
sadly it would appear you need to install the realtek drivers;

this thread

[http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux](http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux)

in post #2 describes what worked 

seems you need to:

1) download the compressed file (into your Downloads directory)

2) unzip it.........thus seemingly creating a directory called RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/

3) then you need to get inside that directory, using hte command he quotes

> cd RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.1590.20110511/

4) then he thinks you need to edit the install.sh script

by issuing the command 

> sudo gedit install.sh

etc! Phew: you had better see how you get along with these instructions;

there are some usb that seem to work "out-of-the-box"

eg [http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html](http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html)

---

### Post by severdhed on 2011-10-05
Thank you so much!!!  THe steps defined in post #2 on that link workd very well, i ran through the process and my wireless poped up and started working.  

It's really a shame that is so difficult to do such a thing, i really want to like Ubuntu, but it is processes like this that keep me using WIndows on most of my computers.  At least now i can keep ubuntu on my laptop, which is mainly just used for browsing the internet.  

These little micro usb adapters are great, they are so small and not likely to get broken off....and the price was right.  i guess i should have checked before buying to see if it was supported out of the box, i just assumed that when it listed linux as a supported OS, it would just pop up and work like the several other adapters i had used.

anyway, thanks again for your help.


oh..and as a side note, i had to change the commands slightly to get them to work. i had to remove the % from the beginning of the commands to get them to run.  once i did that, they were fine and everything worked...i'm not sure what that means, but i figured it may be of interest

---

### Post by pdc on 2011-10-06
well done;

you did extremely well to work your way through all those instructions and get the wireless working: great work!

......some of the adapters are "plug and play": it is just knowing which ones .........

---

### Post by spinlock99 on 2011-10-12
I just wanted to leave my future self a how-to on installing these drivers. The monoprice adapter works great but I'm on 10.4 so I need to custom compile the drivers EVERY time I upgrade the kernel. Luckily, it's an easy process:

[LIST]
[*]copy zip archive from cdrom
[*]$ unzip rtl8192CU_8188CU_linux_v2.0.939.20100726.zip
[*]$ cd rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/
[*]$ make clean
[*]$ make
[*]$ sudo make install
[/LIST]

all done :)

---

