---
title: "updates screwed with NIC"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by joshlegs on 2011-07-28
I don't really need support anymore, as I got the issue resolved. But I wanted to ask, and didnt see it already posted here. I installed the updates that I guess were released on 7-26-11 on my ubuntu 10.10 desktop. When I did, the hardwired ethernet port going to the router quit working. It also didnt work when i dual booted into windows or if i connected it straight to my modem. I troubleshot it with several people in the #ubuntu IRC channel (and other ubuntu-related channels) and we couldnt figure out anything other than the nic seemed to be recognized, but it wouldn't connect at all. One guy who seemed to have a pretty good grasp of things said the updates may have messed with the NIC's configuration. I ened up using windows restore to restore everything to pre-update status, and that got my NIC working again.

Basically my question is how could the update have affected my NIC? and what should i have done if i hadn't had windows restore available ? (its a tacky way to solve the issue but it worked). And how can i figure out what got messed up ??

I think among the commands we used were ifconfig, something with sudo /etc/init.d/something/ network-manager stop, several other things with the network manager, and some dhcp stuff too. I just dont remember it all. (i'll go through my recent term commands tomorrow when i get my desktop back up -- im in bed on my laptop now -- and post more details of our efforts).

Any feedback would be appreciated.

Thanks
josh

---

