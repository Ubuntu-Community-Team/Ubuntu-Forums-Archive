---
title: "Setup ubuntu server as router/gateway"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by cstone1983 on 2011-05-29
I am hoping someone can point me in the right direction. I have been searching google for a while now and have not found exactly what I am looking for. I would like to use my fresh install of ubuntu server 11.04 as my router/gateway for my home. I am not an expert at linux by any means but I can usually figure stuff out. I believe I need iptables, bind, and a few others probally. It eventually will also be a samba server but I have done a little with samba before. 
I do have 2 network cards, my router at the moment is starting to die and would love to have a more powerful router. I would also like to figure out how to do port forwarding in the router, as well as be able to see the load on the network cards. Maybe there is a program to show usage by user? As well as be able to do packet pritorization. 

If anyone can help me I would appreciate it. Like i said i am not the best at linux but I am willing to learn :)

---

### Post by Toz on 2011-05-29
Perhaps this can help: [http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001)

---

### Post by cstone1983 on 2011-05-29
that looks promising thank you. :)

---

### Post by JKyleOKC on 2011-05-29
I/m doing exactly what you propose, except that I'm running xubuntu 10.04 LTS. You'll find iptables to be your best friend in this endeavor; almost all of the features you want are handled by iptables rules, including the port forwarding.

I found it necessary to create special udev rules to guarantee that my two network cards always got the same interface names, but that's fairly easy to do -- the upstart boot procedures do not guarantee that the cards will always be found in the same sequence! The udev rules use the MAC address of each card to force the consistent naming. This is necessary since the iptables rules work on interface names rather than on MAC addresses.

I realize that this may sound horribly complex since you're new to the whole situation, but feel free to ask in more detail about anything confusing. I'll be tracking this thread...

EDIT: Note that the how-to referenced above dates from 2008 and may not be totally applicable to your 11.04 installation. It's good in general, but details may vary a bit!

---

### Post by Iowan on 2011-05-29
[Another]("https://help.ubuntu.com/11.04/serverguide/C/index.html") place to check.

---

