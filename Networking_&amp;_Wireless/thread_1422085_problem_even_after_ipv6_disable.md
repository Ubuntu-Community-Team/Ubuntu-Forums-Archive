---
title: "problem even after ipv6 disable"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by vbhide on 2010-03-05
Hi All,

I've disabled ipv6 on ubuntu 9.10 and i used the internet for a month or so. 

Now, its not working again, although i can ping specific ip addresses or telnet to them. If i type, say, [www.google.com](www.google.com) and ping it it says unknown host.

I did a router test and the ATM segment ping test fails, the rest pass. It's definitely not a connection issue becoz i can acess internet from other computers and the router from even my ubuntu.

Can anybody atleast give me a lead ?

---

### Post by r939ick on 2010-03-05
Sounds like DNS.  Does renewing your DHCP lease help?

Can you `ping 8.8.8.8` ?  If so, try commenting out any nameserver lines in /etc/resolv.conf and adding:
nameserver 8.8.8.8
nameserver 8.8.4.4

And see if that works.

Those are Google's public DNS servers.  If that's sufficient, you may want to leave it like that, or you may want to replace those entries with your ISP's.  If you're using DHCP, it might overwrite your resolv.conf file, so check there first if it works for a while and then stops again.

If that doesn't work at all, it's most likely a routing issue, and you'll need to describe your network layout in a bit more detail.

---

### Post by vbhide on 2010-03-08
Hi, r939ick 

Yes I can ping 8.8.8.8 . However, i cant find any resolv.conf file in /etc, would it be ok to make one myself ?

I have disabled my ipv6 from /etc/default/grub. That alone was working until now, god knows what's wrong !

Thank you for your help !

---

### Post by inobe on 2010-03-08
open terminal and do

```
sudo gedit /etc/resolve.conf
```

if you have a blank file' click file then hit open, browse for your resolve conf file, make the edits and click save then close and and restart.

---

### Post by vbhide on 2010-03-08
That didnt work ... anyway, i'm on pendrive linux, not muxh data to lose, so i think ill just re-install properly and do the ipv6 disable, after which it generally works.

---

### Post by karthick ayyapillai on 2010-03-08
hi
if you are using ubuntu 9.10 and facing wireless prob. then you can connect through ethernet and try installing network manager from the synaptic package. Even then it doesnt respond then try installing wicd and remove the gnome network manager. After reboot you might be able to use.

---

### Post by vbhide on 2010-03-09
It's stranger than I thought ..

firstly, apt-get install works fine

secondly, i seem to have a resolvconf.tmp, another resolvconf-dhclient and a resolvconf~ created by Network Manager. ls -al shows one file properly named resolvconf with no permissions specified and which can't be modified / deleted because of some "input/output error".

---

