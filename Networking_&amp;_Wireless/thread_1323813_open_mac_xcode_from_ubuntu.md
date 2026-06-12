---
title: "open mac xcode from ubuntu"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by harishbayyavarapu on 2009-11-12
hi,
 
I am in urgent help from the experts. I am developing a iphone interface. I don't have mac with me so my professor suggested me to remote login to the mac using putty client and then try to do it.
 
I did the X11 forwarding in the putty client.
When I tried to open the xcode from the xterm it doesn't show up anything.
 
$ open -a xcode &
[1] 12468
 
Any help from the experts how to open the xcode on my computer.
 
Thanks very much

---

### Post by jollysnowman on 2009-11-12
Putty is only an ssh client iirc.

Use vnc.

edit: I see you said you did X11 forwarding; I guess that should work, but try using a "regular" vnc client.

---

