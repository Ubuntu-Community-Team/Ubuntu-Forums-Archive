---
title: "Reconnect to wireless network with network-manager through command line"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by androssofer on 2011-02-03
Hi all,

I'm wondering is there a way to re-connect/connect to a wireless network with network manager through the command line.

basicly i use a php script to monitor active IP addresses on my wireless router... however the router(netgear) seems to dislike it if you access it too often and claims the user name and password r invalid after a while... so the easy work around is just to reconnect to the router ie: click the wireless icon, then click on my wireless network. network manager then disconnects and then re-connects to the wireless. and the router allows access again.

 i was wondering would it be possible to replicate this via the command line? so i can get the script to re-connect to the wireless wen it gets refused access... so it doesn't require my interaction.

i tried looking for network manager command line info(dont even know if it has a cli), but all my searches threw up stuff about configuring network manager through command line and peoples issues with not being able to connect etc. and nothing on commands available etc. i did get the sinking feeling it doesnt hav a cli and i would have to use another method, but beggers cant b choosers,,,

---

### Post by grahammechanical on 2011-02-03
Do not take me for an expert, but I think that the purpose of Network manager is to make networking easier without using the Command Line. You might want to research something called wicd. I have no experience of this utility but I see it mentioned in posts on the forum. Here is it home page:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I notice that it has a Console Interface as well as a Graphic Interface.

Regards.

---

### Post by androssofer on 2011-02-03
yeah i suspected as much haha. was just hoping you could do sumthing like 'gnome-network-manager --connect MyWirelessSSID'. alas.

wonder can u run the 2 together? grown quite fond of network manager and its simplicity.. 

thanks for the advice! will give wicd a whirl and see wot happens :-). 

regards

---

### Post by androssofer on 2011-02-04
***conclusion to this story...***

yeah i can get network manager to re-connect by just restarting the service :-). yes i do feel like a numpty for not realising this...

sudo service network-manager restart

---

