---
title: "How lame - I can't set the resolution :("
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by mwob on 2006-06-27
Hi,

I just installed Ubuntu on a dual boot system, and I want to set the resolution to my native 1280x1024 (I have a Acer 1L1912 LCD). However, when I use the menu system to navigate to "preferences/screen resolution", the highest choice I have there is 1024x768 :( 

I tried editing /etc/X11/xorg.conf (sudo gedit /etc/X11/xorg.conf), and in there noticed that there was no "1280x1024" string for all the "depths", so I added it to them all, and then rebooted, and still no joy :(

I'm using an ATI Radeon 9550 (Ubuntu seems to think its a 9600 but thats OK I think).

Any ideas? Should it be this hard?!

Thanks!

Matt

---

### Post by Dr. Nick on 2006-06-27
Adding the 1280x1024 should do it for you, mind posting your /etc/X11/xorg.conf file up here?


One other solution would be to run 

sudo dpkg-reconfigure xserver-xorg

and choose a different monitor when it comes to that point

---

### Post by gommle on 2006-06-28
Same happened to me. I changed xorg.conf and used dpkg-reconfigure, rebooted, and still not native resolution.

What i did was just to install the Nvidia driver from the repos. Then it changed after a x restart.

Installed your drivers?

---

### Post by Dr. Nick on 2006-06-28
Also one of the biggest things to look out for when running the dpkg-reconfigure is your monitor/refresh rate. When you come to that part choose the middle of the three options. Not simple but the next one up. 

I find it easier using that one because you can set a more specific monitor type. Not just a generic one.

---

### Post by mwob on 2006-06-28
Woo hoo, I did it :)

I chose the "medium" option as you suggested, and it allowed me to specify 1280x1024

Thanks!

[QUOTE=Dr. Nick]Also one of the biggest things to look out for when running the dpkg-reconfigure is your monitor/refresh rate. When you come to that part choose the middle of the three options. Not simple but the next one up. 

I find it easier using that one because you can set a more specific monitor type. Not just a generic one.[/QUOTE]

---

