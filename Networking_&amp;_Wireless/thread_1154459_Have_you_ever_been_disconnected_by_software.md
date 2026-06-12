---
title: "Have you ever been disconnected by software?"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by joewski on 2009-05-09
I was happily installing programs in Ubuntu in bulk. At some point I became unable to connect to the network.

I tried a live distro that worked fine so it wasn't hardware issue.

I tried 
$sudo lspci  #list pci drivers before and after and found no change

I tried
$sudo lshow -C network  #no difference

I tried
$sudo ifconfig    #no difference except for a wireless network disabled. But that don't matter because this network is also hardwired.

I tied 
$sudo ping 192.168.1.1 #to ping my router and get the following messeage

ping: sendmsg: Operation not permitted

I tried reconnecting the network with the gnome network tool no effect except to tell me I am connected.

An ip address is being assigned by my router to the machine.

I thought it was some sort of firewall or blocker or something. So I started uninstalling everything that I thought could possibly casue the problem.

What software would block or take over the network connection?

Any clues would be most appreciated.

Is there some way for me to reset the network or reinstall it?

---

### Post by joewski on 2009-05-10
Bump. Sorry but nobody seems interested.

This is the second time this has happened to me. There is one application somewhere in the repository, that I suspect in accessories that is stopping network connections. Has anybody had a similar experience?

---

