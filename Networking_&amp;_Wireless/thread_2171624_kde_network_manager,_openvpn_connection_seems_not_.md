---
title: "kde network manager, openvpn connection seems not to work at all"
date: 2013-08-31
forum: Networking &amp; Wireless
---

### Post by remyvrs on 2013-08-31
hi guys,

I have tried to configure a openvpn connection using the gui interface from the network manager, 
and even thought it appears after poping up the systray icon, after clicking it , it seems not to work at all...
no error , no waiting time ...  nothing ...

I should manage that I have successfully configured the openvpn connection using client.conf and starting the service accordingly
but I would very much prefer to be able to start and stop the connection using handy gui features...

thank you in advance for any support :)

---

### Post by alexandari on 2013-08-31
sounds like a bug in the network manager itself. check this out [http://askubuntu.com/questions/39652/how-to-restart-kde-network-manager](http://askubuntu.com/questions/39652/how-to-restart-kde-network-manager)

---

### Post by SeijiSensei on 2013-08-31
Unless you are actually sending traffic over the VPN, it will just sit idle and consume few resources.  I prefer having my tunnels start at boot and remain at the ready.

---

