---
title: "LinkSys 802.11b Card not working"
date: 2005-03-12
forum: Networking &amp; Wireless
---

### Post by Admstng on 2005-03-12
Hey Guys.. first post

I just installed Ubuntu and everything is great execpt for the wirless part

I go in "device manager" and I see the Linksys card as "RT8180L 802.11b MAC" (does this mean I do not hjave to install the Ndiswrapper?" 

Now I go into "Network Settings" And the card is not listed? actaully, at the time none were, so I added the eth0 with no problems... i selected "devices" and oit was right there.. but when I go through the process of adding a wirless card, i hit the drop down and the wireless card is not htere? 

any help is appriciated.

Thanks,
Adam

---

### Post by somuchfortheafter on 2005-03-12
okie dokie get your windows drivers in a folder *the .inf files*
then
sudo ifconfig etho up
sudo find the ndiswrapper command to link it to the drivers
ifconfig 
your done
well thats how i got my intel card to work.

---

