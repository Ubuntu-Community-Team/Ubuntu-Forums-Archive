---
title: "tun0 comes always on after internet connection.."
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by dino.tee on 2009-12-08
everytime i start an internet connection, after a couple of seconds a Tun0  interface pops up  in the ifconfig list,
and internet stops working.
Than i have to do the ifconfig tun0 down, and internet works again,
but after a short time ( sometimes, minutes sometimes seconds) the tun0 pops up again and the connection stops again.

I have installed openvpn, but thi happens now even without me starting the VPN.
It feels like i have done something wr4ong with the setting of openvpn for hich the Tun always tries to get connected.

Help

Thanks

---

### Post by Iowan on 2009-12-08
Is VPN in the Startup list? I'm not sure how to check **ps -ef** to look for "it".

---

### Post by uncaspi on 2009-12-08
If tun0 is in /etc/udev/rules.d/70-persistent-net.rules try to comment out the line with tun0 then reboot. Don't know if it helps ,but you could try it.

---

