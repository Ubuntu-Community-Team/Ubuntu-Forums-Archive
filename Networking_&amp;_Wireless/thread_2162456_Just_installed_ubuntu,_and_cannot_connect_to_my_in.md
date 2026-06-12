---
title: "Just installed ubuntu, and cannot connect to my internet?"
date: 2013-07-14
forum: Networking &amp; Wireless
---

### Post by ImportantSaltine on 2013-07-14
I just installed ubuntu, but I cant connect to the internet? Im not that good with computers, but im alright with them. It isnt picking up my internet on the networks tab in the top, but on the windows version of my computer my internet works perfectly. 

Thanks in advance!
Videos would be appreciated!

---

### Post by kc1di on 2013-07-14
Hi ImportantSaltine  and welcome to Ubuntu and the forums,

You most likely have a propriety network card , because of licensing issue the drivers can't be install at installation time in Linux.
But most manufactures now support linux and the drivers may be available for your card.  sounds like it's a wireless card.

but in order to help you'll need to give us two things 1.  What wireless card is in your machine. If you do not know go to a terminal and
type this command and list the output here.  ```
lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
```  you can just copy and paste it into the terminal.

Then your going to need a temporary Ethernet (hardwired).  

I'm quite sure we can get you up and running with those things.

also do this command in a terminal and post out put here. ```
rfkill list all 
```
it may be helpful to know which version of Ubuntu you installed as well.

---

