---
title: "tightvncserver  ssh compression security"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by bcn17 on 2011-02-18
Currently I am attempting to optimize tunneling a vnc session via ssh. This is what I have done. Questions follow.

```

server$ tightvncserver -depth 8 -geometry 800x600 :1
client$ ssh -C -f -N -L 5901:localhost:5901 user@server
client$ xtightvncviewer localhost:1

```

This works. However the following is less laggy.

```

client$ ssh -Y -C user@server
server$ tightvncserver -depth 8 -geometry 800x600 :1
server$ xtightvncviewer localhost:1

```

I am using the option "Ciphers blowfish-cbc" in my /etc/ssh/ssh_config file on the client machine.

I have three questions. 

1) Almost everywhere I search points to some form of the first option. Is this due to security reasons. If I "man ssh" I notice that there are some security issues with the -X option, although it seems that the -Y option is supposedly secure. Why they didn't just update the -X to the -Y and not have two is beyond me. I suppose there is some reason beyond my comprehension. Basically, do both of these methods seem secure to everyone? I am using keys, non standard ports, etc. 

2) What can I do to achieve further compression? It is still pretty slow. Maybe hoping to achieve real time is just not possible. Currently I am tunneling to a location about 1 mile away. I assume it will get much worse if I try this from further off, which is probably in my future. 

3) How can I get the server to broadcast display :0  ? I would like to have the same display session as the user sitting at the computer. I am using this to help my mother and grandmother, so letting them watch  my mouse move around would be helpful. 

Thanks in advance!

---

