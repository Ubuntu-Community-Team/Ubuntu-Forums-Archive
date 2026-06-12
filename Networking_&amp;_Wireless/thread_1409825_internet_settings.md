---
title: "internet settings"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by mirinamulhaq on 2010-02-18
hi my dear friends
i want to know how can i use my terminal for doing my internet settings like setting IP addres.DNS, netmask etc for enabling internet on my ubuntu karmic os.

---

### Post by iponeverything on 2010-02-18
configure the interface via the file /etc/network/interface

This will make it so that it is no longer managed by networkmanager.

---

### Post by mirinamulhaq on 2010-02-18
sorry to tell that i didnt got you,can you explain in a bit detail if possible.

---

### Post by mosquetero on 2010-02-18
Use the ifconfig command.

Type
 
> man ifconfig 

in the terminal and you will see all the possible options. If you need more help tell us.

Regards

---

### Post by LintonHanes on 2010-02-18
you could:
ifconfig eth0 up
ifconfig eth0 down,, ath0? wlan0? whatever

dhcpcd stop|start
or
dhclient

ping [www.this'n'that.com](www.this'n'that.com) -c 2 (2times)
 
::you could even google this stuff::

---

