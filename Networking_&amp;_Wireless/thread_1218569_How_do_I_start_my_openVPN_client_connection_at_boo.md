---
title: "How do I start my openVPN client connection at boot?"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by Abdus on 2009-07-20
How do I start my openVPN client connection at boot?

I would like it to start at boot, so I could also mount some remote disks using /etc/fstab/ I do not want it to require a login, just booting.

I read some threads about loading apps at boot, but I can hardly understand those, to be honest. I found none straighforward step-by-step manual of things to do. I also have no idea how to provide the pasword for my user certificate to the openvpn starting on boot.

Will appreciate your help.

---

### Post by Abdus on 2009-07-21
That task seems impossible to me now. :)

I copied my .ovpn file along with ca, cert and privkey to /etc/openvpn. I changed its name from client.ovpn to client.conf, so that it is autostarted by openvpn. I changed /etc/rc5.d/K80openvpn to /etc/rc5.d/S96openvpn (96 instead of 20 to ensure network is on already). It doesn't work, I mean my openvpn connection doesn't start on boot, however it does after:
```
$sudo /etc/rc5.d/S96openvpn restart
```
What do I do wrong?

---

### Post by paulisdead on 2009-07-21
You need to add that to run level 2 I think, not 5.  Ubuntu doesn't follow the conventional runlevels that redhat and it's derivatives do.

I'm surprised it doesn't start up automatically off the bat for you.  Every time I've installed it in ubuntu with apt-get, I have to disable it from starting up on bootup.

---

### Post by Abdus on 2009-07-22
Doing it in rc2.d did the job. Thank you very much for your tip, paulisdead. It works!

---

### Post by Davie In Dubai on 2009-09-28
interesting... does your client connection require any credentials to connect to the server?

I'm about to try this myself and I recall an error stating that I had to compile this app if I wanted it to look into a file for username as pwd.

Would you mind sharing what exactly you had to do to get it to work?

Thanks 

D.

---

