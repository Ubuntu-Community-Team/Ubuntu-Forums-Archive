---
title: "Simple networking question...."
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by Kaneda187 on 2009-03-18
Just Installed Twonky Media with the how to supplied with the downloaded file. the paragraph below is the only thing im having issues with... what exavtly do i have to do here, if you can help can you please make you advice idiot proof PLEASE and THANKS!!

"[I]Make sure that the server file, plugins and the cgi scripts have the exe bit set.
If not, try:
"chmod 700 twonkym* cgi-bin/* plugins/*"
Eventually it is necessary to have a multicast route set for the
server by issuinge, e.g.:
"route add -net 224.0.0.0 netmask 240.0.0.0 dev eth0"[/I]"

---

### Post by Kaneda187 on 2009-03-18
I just need help with this bit really when i put this into the terminal it says its not permitted

```
route add -net 224.0.0.0 netmask 240.0.0.0 dev eth0
```

---

### Post by Kaneda187 on 2009-03-19
bump!

---

### Post by sahabcse on 2009-03-19
Hi

Networking Set-up follow below url

[http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html](http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html)

---

### Post by mbfrog on 2009-03-19
> **Kaneda187 said:**
> I just need help with this bit really when i put this into the terminal it says its not permitted

```
route add -net 224.0.0.0 netmask 240.0.0.0 dev eth0
```

may be because you need to do this as root (using sudo):

```
sudo route add -net 224.0.0.0 netmask 240.0.0.0 dev eth0
```

---

