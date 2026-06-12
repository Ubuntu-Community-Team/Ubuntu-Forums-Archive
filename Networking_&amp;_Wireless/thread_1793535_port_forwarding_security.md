---
title: "port forwarding security"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by emdiesse on 2011-06-29
I would like to add port forwarding to my router to allow me to ssh or remote desktop into my pc. Other than having your ubuntu password and the remote desktop password to get through. How else can you beef up the security?

---

### Post by doas777 on 2011-06-29
do not even consider exposing remote desktop (Vino VNC) to the internet. you will be p0wned in mere hours. 

instead, forward SSH, and use FreeNX/NeatX. 
additionally, look into denyhosts and fail2ban to lock down your ssh access, and consider using keys instead of passwords. thats about as secure as you can make remote access.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by CVGH on 2011-06-29
1]fail2ban
2]AllowUsers in sshd_config
3]SSH keys, no password auth
4]root login not allowed
5]I did change the port used on the router to forward another port so 22 looks closed. But nmap will find it anyhow, so probably not too effective.
6]Use rate limiting on port 22 via gufw or whatever you use to set up iptables/ufw....

---

### Post by emdiesse on 2011-06-29
> **doas777 said:**
> do not even consider exposing remote desktop (Vino VNC) to the internet. you will be p0wned in mere hours. 

instead, forward SSH, and use FreeNX/NeatX. 
additionally, look into denyhosts and fail2ban to lock down your ssh access, and consider using keys instead of passwords. thats about as secure as you can make remote access.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Ok thanks for the advice.
In regards to security on anything requiring a port forward what are the definite no's and the acceptable port forwards?

So remote desktop/vnc is out the picture
I take it port forwarding 80 to allow your PC to be a web server is acceptable?
SSH is acceptable but recommended to lock down access

Both denyhosts and fail2ban look great utilities and keys sound like a good idea. Will have to start doing some research into this.

Any indication why remote desktop is more insecure than SSH?

---

### Post by doas777 on 2011-06-29
there are a number of reasons that VNC is not a safe internetwork protocol, including weak passwords (max is 8char) [very easy to bruteforce], plain-text password exchange, no connection encryption, etc. most everyone who has ever been "hacked" on these forums got it via vino. don't get me wrong, vino/vnc is great for lan use, but is not safe for the wider internet.

ssh however has none of these vulnerabilities, and can be hardened well beyond just fixing this list. 

FreeNX is a great remote desktop tool that runs better than VNC, but uses SSH as its transport, so you get all the advantages of both worlds. I think you would like it.

on port-forwarding, there isn't really a lot to configure. it has a listening port, a forwarded server, and a forwarded port. the rest of it needs to be taken care of by the server/service config. unless you know the endpoint(s) that the connections will come from though, there isn't a lot more that you can do, other than hardening your service. 

I haven't worked with apache in production (we're an IIS shop) but yes, appropriately configured apache is quite web-safe.

---

### Post by emdiesse on 2011-06-29
> **doas777 said:**
> there are a number of reasons that VNC is not a safe internetwork protocol, including weak passwords (max is 8char) [very easy to bruteforce], plain-text password exchange, no connection encryption, etc. most everyone who has ever been "hacked" on these forums got it via vino. don't get me wrong, vino/vnc is great for lan use, but is not safe for the wider internet.

ssh however has none of these vulnerabilities, and can be hardened well beyond just fixing this list. 

FreeNX is a great remote desktop tool that runs better than VNC, but uses SSH as its transport, so you get all the advantages of both worlds. I think you would like it.

on port-forwarding, there isn't really a lot to configure. it has a listening port, a forwarded server, and a forwarded port. the rest of it needs to be taken care of by the server/service config. unless you know the endpoint(s) that the connections will come from though, there isn't a lot more that you can do, other than hardening your service. 

I haven't worked with apache in production (we're an IIS shop) but yes, appropriately configured apache is quite web-safe.

Ok, thanks again. Also thanks CVGH
I have successfully managed to generate a key for my client and my server and have logged on. Quite chuffed :) Now for fail2ban and denyhosts. Thanks

---

