---
title: "Wireless and GUI Configeration"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by danielgroves on 2009-07-14
Hi,

I hope I have put this in the correct category as it kinda fits into two categories.  

I have configured my wireless in the 8.04 GUI, but now wish to remove the GUI so that it has a server-type command-prompt set-up.  

So, basically I need to remove the GUI and have the wireless automatically connect on boot-up.  Is there a way I can do this?  

Thank in advance,
Dan.

---

### Post by superprash2003 on 2009-07-14
take a look at this [http://www.linuxquestions.org/questions/linux-wireless-networking-41/connect-to-wireless-network-348868/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/connect-to-wireless-network-348868/)

---

### Post by martinbaselier on 2009-07-14
in 
/etc/network/interfaces
you can setup your network

use 
man interfaces
for info on the different options
it basically uses mostly the same commands as ifconfig/iwconfig

For WEP encryption it's easy. 
simple example:
```

auto lo eth1
iface eth1 inet dhcp
wireless-essid YOURNETWORKNAME
wireless-key s:YOURKEYINCHARACTERS

iface lo inet loopback



```
For WPA you'd need a wee bit more work. I still you need to research that. In the isolated place where I live, I normally would not even use WEP if the router would allow me.

---

### Post by danielgroves on 2009-07-14
Ok, so I can do that, but what about removing the GUI as well?  Will I have to login for it to connect to the network?

---

### Post by martinbaselier on 2009-07-14
The easiest way is to remove the network-manager via aptitude/apt-get or synaptics. If you have the network setup by using interfaces, it will connect automatically before you login.

---

