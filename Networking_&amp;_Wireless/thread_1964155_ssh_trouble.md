---
title: "ssh trouble"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by mikaelcrocker on 2012-04-23
Hey All,

Kinda embarrassed, but I can't figure out to ssh from my laptop, to my computer at home.  I can ssh using IP or DNS, but I actually haven't done anything without some sort of DNS resolution.

I can get my external facing IP and try and ssh into that, however, that'll just end up hitting the my router and won't get passed that, how can I:

  Connect to my home computer using SSH? I've `man ssh` and It seems like -L and -D are something that I will end up having to use.  Any guidance will be much appreciated!

---

### Post by jonobr on 2012-04-23
In order to ssh to your computer from outside the network, you need to map a port on your router from port 22 to the host that you are sshing to .

So if a request hits your external IP address on port 22, the router knows which host to pass it on to.

If you have the set up and are not sure if its working, then on the ubuntu machine you can run

```
sudo tcpdump -vvv -i any port 22
```


then ssh externally, if you see out put from this command after you ssh you know its working.

Some ISPs also block port 22, so that could be an issue also

---

### Post by haqking on 2012-04-23
you can change the port in sshd_config

```
/etc/ssh/sshd_config
```

then specify the port such as

```
ssh username@domainorip -p <new_port> 
```

adds a little extra security aswell though a simple service scan with nmap will reveal the service anyways.

Peace

---

