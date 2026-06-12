---
title: "Wired ethernet connection not working.........Ubuntu 13.4"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by grunzmeniroj on 2013-07-08
hey,  I am having Internet connectivity problem, while  using wired (ethernet ) connection........... 
I am using 14r-se dell 7420  ..*.. I had installed windows 8 and Ubuntu 13.4 ...........   Every thing is fyn and working in ubuntu....... But when I plugged network cable.... I could not access  the Internet........ Whe I see in Network Connection Automatic dhcp was enabled........ and in  conection information every thing looks fyn.... Ipaddress, gateway , subnet mask , dns.... Every thing is shown there......
when I  ping gateway and DNS server both are respondin................ but i could not browse the webpage......   

In the same laptop when i boot with  Windows 8 ...... with same Gateway, DNS and IP Internet is connected and I can surf Internet....... 

anybody  who can figure out What is wrong with my ..... ubuntu 13.4

Thanks in Advance.............

Niroj Paudel

---

### Post by grunzmeniroj on 2013-07-08
hey, guys............ plz help....... Its really urgent

---

### Post by praseodym on 2013-07-08
Please open a terminal with CTRL+ALT+T and show the outputs of the commands:
```

uname -a
lspci -nnk | grep -iA2 net
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig -a
```
Does wireless work?

---

### Post by sanderj on 2013-07-08
What's the result of

mtr -nrc2 8.8.8.8

Post the output here.

---

### Post by 2Stoned on 2013-07-08
See if the DHCP match between what you see from the network manager GUI and from the terminal. Try to browse the net with another browser just to see if that works or not, it could be FF related.

Let us know..

---

