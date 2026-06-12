---
title: "[server] eth0 unplagged &amp; wlan0 conncted"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by lospo on 2011-04-06
Hi and good morning,
I have installed an ubuntu server 10.10, everything ok.
plugged the cable to install ssh and wireless-tools: ok
Configured as follow:

eth0 dhcp 192.168.2.101 

wlan0 static 192.168.2.40

ssh to 192.168.2.40, login and password, everithing ok.
(also ssh to 192.168.2.101 works)

BUT

when i unplag the cable from eth0 i cannot log no more to 192.168.2.40 (the wlan address).

Why? Someone has the answer?

they have the same gateway, netmask... i think that everything is configured in the right way.

---

### Post by lospo on 2011-04-08
No one?
No ideas?
Sadness :(

---

### Post by vigneshsrinivasan on 2011-05-12
Sorry, I don't have an answer for this
but I am here to say, I am too facing the same issue.

I tried few things like ethernet bonding [http://www.cyberciti.biz/howto/question/static/linux-ethernet-bonding-driver-howto.php](http://www.cyberciti.biz/howto/question/static/linux-ethernet-bonding-driver-howto.php)

but I am not successful, may be you could give it a try.

---

