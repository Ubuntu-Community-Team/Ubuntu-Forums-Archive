---
title: "Trying to setup wifi on ubuntu server 10.04"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by FunkyBluffMan on 2010-09-18
Hi

I just installed ubuntu server 10.04. I want to connect to my wireless router(192.168.123.254). My router normally has wpa but I turned off encryption until I can get the server working. my router has MAC flitering which it has my servers MAC address and  the dhcp server on my router is configured to assigned an ip address of 192.168.123.123 to my server.

On the server I do see wlan0 when I do sudo ifconfig -a

HOw do I setup the rest? I 'm very new with command line and linux so please bear with me.

Many thanks
:guitar:

---

### Post by solar george on 2010-09-18
You'll want to set the connection in /etc/network/interfaces so that it will be activated on every reboot. If you run
```
man interfaces
```
you'll get more than enough information to get wpa working.

To quickly connect to an open network you can do;
```

# sudo ifconfig wlan0 up
# sudo iwconfig wlan0 essid *networkid*
# sudo dhclient wlan0

```

---

### Post by FunkyBluffMan on 2010-09-19
Many Many thanks for your quick connection guide.

My server is now online. how do i add it automatically connect on bootup.

Sorry I'm very new to the commandline and I normally use the desktop enviroment.

---

### Post by solar george on 2010-09-19
You'll need to put the settings in the file /etc/network/interfaces
Take a look at [http://manpages.ubuntu.com/manpages/lucid/en/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/interfaces.5.html) for an explanation of the file (it also includes some examples you can copy/paste and edit for your setup.

---

