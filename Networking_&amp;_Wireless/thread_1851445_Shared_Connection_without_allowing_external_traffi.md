---
title: "Shared Connection without allowing external traffic"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by DMcA on 2011-09-28
Hello, having a problem with a new setup.

I have an ubuntu (desktop) machine running a webserver, which is connected to the internet. I wish to allow access to the webserver only from specified IP adresseses, which is straightforwad with ufw: 

```

sudo ufw default deny incoming 
sudo ufw allow from ip.address.of.mask/24 to any port 80
```

which seems to work. However, I also have second (windows) machine that is sitting behind the server with a shared connection (via network manager). This works fine too and the windows box can connect to the internet (and the webserver if a second ufw allow is added with the internal IP address). However, I would like the windows machine to be completely locked down (it's primary purpose is to run equipment) with the exception of of connecting to the internal webserver (and maybe one or two other services like samba. 

Is there a straight forawrd way to do this with ufw on the ubuntu server, i.e. have it act as a (very restrictive) firewall for the machine behind it? Cheers

---

### Post by DMcA on 2011-09-28
so changing the lines in /etc/ufw/sysctl.conf 

```
net/ipv4/ip_forward=0
net/ipv6/conf/default/forwarding=0

```

does seem to achieve this but I'm not sure if this is really safe. Anyone know if traffic can still pass through to my windows machine from the outside world?

---

### Post by DMcA on 2011-10-17
Also, this doesn't work after restart and I'm not sure why. Can anyone point me towards the proper way of sharing a connection to an internal computer that you do not want to be accessible from outside?

---

