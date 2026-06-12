---
title: "mobile broadband usb dongle and wireless/wired networking not working at same time"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by scmcgraw on 2011-11-24
Hi folks just a little background before i start. I'm running 10.10 and 11.04 on two different computers through a belkin router. I do not have a wired connection for accessing the Internet and have to use a Huawei E122 dongle from 3ireland. i can access computers on the network without the dongle in use and i can access the Internet using the dongle with the network disabled from the drop down. I cannot do both at the same time. this is the same case for either version of Ubuntu. also if i am surfing the net and then turn my wired or wireless connection on from the computer i am surfing on it kills the dongle connection. what i mean by this is that, normally when i am browsing the dongle led is a light blue. when i turn on the network it turns back to a darker blue. 
I am fairly new to ubuntu and want to start administering accounts and work on building my development and networking skills  but can't seem to even get out of the starting gate. Once i get this solved i would like to create a shared connection as you would with windows, after that the skies the limit. Any help with this would be much appreciated. How is one interfering with the other. do i need to do something with ports????

Cheers 
Scott:confused:

---

### Post by ptrakk on 2011-11-24
run "apt-get install -y network-manager-gnome" then run "nm-applet &" configure the wired-computer-link with manual (static ip) & set the internet with automatic (dhcp). ..would be my advice.

---

### Post by scmcgraw on 2011-11-24
nope still no luck, plus i had the network manager installed. is there a reason why mobile broadband and wired/wireless will not work together???

cheers 

Scott

---

