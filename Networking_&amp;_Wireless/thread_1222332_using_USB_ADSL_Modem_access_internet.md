---
title: "using USB ADSL Modem access internet"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by say2sky on 2009-07-24
I use SpeedTouch 330 USB ADSL Modem
and I set it under Ubuntu by using br2684ctl

```

sudo cp -a speedtch-1.bin.4 /lib/firmware/
sudo cp -a speedtch-2.bin.4 /lib/firmware/

modprobe ppp_generic
modprobe pppoatm
modprobe br2684
br2684ctl -b -c 0 -a 8.35
ifconfig nas0 192.168.1.100 netmask 255.255.255.0 up 
pon dsl-provider

```

Now I want to use same USB ADSL Modem in Vyatta router box.
I also can use above setting steps in Vyatta system.
But the resulted  nas0 and ppp0 interface will not recognized by Vyatta configuration so I cannot combine qos or firewall with nas0/ppp0. 

How I can do to let it all be recognized by Vyatta configuration system. 
Thanks for help!

---

### Post by say2sky on 2009-07-24
help needed.

---

### Post by say2sky on 2009-07-25
anyone can give some suggestion?

---

