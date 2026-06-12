---
title: "No wireless Internet found"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by Herner on 2011-05-22
Just got Ubuntu installed and am new to Linux completely.
 
I have been looking around and it seems that having a wireless USB network to connect to the internet is difficult on Ubuntu. 
Wondering if anyone could help me out with this or walk me through. Any information would be great.
 
All I know is that it seems that my wireless linksys network card is a WUSB600N
Anyone that has any commands they want me to put in my terminal I can tell you but from other forums I try to put many in and get no output simply because I believe I do not have the drivers but do not fully know how to even install these drivers in the terminal or am not doing something right.
 
Thanks!

---

### Post by josephmills on 2011-05-22
HYi there and welcome to Ubuntu forums could you please plug in the usb wifi thingy then open you terminal (ctrl+alt+t) then type in ```
lsusb
``` then ```
lspci -nn
``` then ```
rfkill list all 
``` then paste all that here thanks

---

