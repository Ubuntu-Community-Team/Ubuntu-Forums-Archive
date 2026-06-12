---
title: "Both Wired Ethernet and Wireless Unclaimed"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by kven512 on 2011-11-29
Hi
I installed Ubuntu 10.04 in dual boot with Windows 7.  The wireless works fine with Windows 7 but I am completely unable to connect to the internet, either through the wireless or wired connection in Ubuntu.  The command lshw -c network lists both the controllers as unclaimed. Since I am not able to access the net whatsoever, I have not way to download ndisgtk or any other module or file.

Although I have used Ubuntu before, my level is comparable to beginners and would appreciate any guidance to solve the problem. 
Thanks very much.

---

### Post by bkratz on 2011-11-29
> **kven512 said:**
> Hi
I installed Ubuntu 10.04 in dual boot with Windows 7.  The wireless works fine with Windows 7 but I am completely unable to connect to the internet, either through the wireless or wired connection in Ubuntu.  The command lshw -c network lists both the controllers as unclaimed. Since I am not able to access the net whatsoever, I have not way to download ndisgtk or any other module or file.

Although I have used Ubuntu before, my level is comparable to beginners and would appreciate any guidance to solve the problem. 
Thanks very much.

It would be helpful to go to the terminal and copy/paste the output of the following back here, so we can all see what devices are used.


```
lspci -nnk | grep -iA2 net
```

---

### Post by kven512 on 2011-11-29
Thanks for the response. I actually contacted Realtek company which manufactures the wireless network controller for my laptop and they  sent a link to the appropriate Linux driver that I was able to install.  Everything is mostly up and running smoothly, except for the fact that with some internet connections, either the connectivity drops automatically for no specific reason or the connection itself is very spotty and irregular. 

I still need to check if ethernet is working though.

---

