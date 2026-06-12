---
title: "Starting up"
date: 2006-05-20
forum: Networking &amp; Wireless
---

### Post by Eric_c on 2006-05-20
When starting my machine, my wireless doesnt work.. I use ndiswrapper with my BCM4306....  i have to it seems type:  sudo rmmod ndiswrapper   and then sudo ndiswrapper a few times to get it going?  is it A) possible to make a startup script to do this?   and B)  Is there a better way?

---

### Post by fletch on 2006-05-20
I'm having similar problems with my broadcom wireless. Here is a great thread to put you in the right direction:

[http://ubuntuforums.org/showthread.php?t=25683]("http://ubuntuforums.org/showthread.php?t=25683")

---

### Post by avirnig on 2006-05-20
have you tried issuing the command:

sudo ndiswrapper -m

that command actually adds ndiswrapper to the list of modules to be loaded on boot i believe. i could ber wrong, but that is how i understood how it worked.

---

