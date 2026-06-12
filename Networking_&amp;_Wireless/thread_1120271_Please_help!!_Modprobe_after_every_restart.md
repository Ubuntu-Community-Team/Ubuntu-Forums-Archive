---
title: "Please help!! Modprobe after every restart?"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by nigelewan on 2009-04-08
I have a Dell Latitude D400 running the latest beta of Jaunty. Through some stumbling around in the Terminal, I managed to get the wireless card working. But every time I restart the computer, I have to go into the Terminal and do "sudo modprobe ipw2100" for wifi to work. Once I perform this step, everything works perfectly.

Can someone explain to me why this is happening, and/or what I need to do to have it work automatically? Thanks so much!

---

### Post by Sam Lars on 2009-04-10
You could add ipw2100 to /etc/modules.

---

### Post by adalal on 2009-04-10
that, or you could try putting the modprobe ipw2100 in /etc/rc.local:

> 
... ..
modprobe ipw2100

exit 0


jus remember that the command has to be before exit 0...

---

