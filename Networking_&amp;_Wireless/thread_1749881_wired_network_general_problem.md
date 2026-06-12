---
title: "wired network general problem"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by superdave321 on 2011-05-05
My network connection has been connected to my network via ethernet once, and it got out to the internet. now it won't connect after reboot. I have a static IP, and all the correct LAN info.

the first time i had this problem, i connnected to the network, and I could ping whatever I wanted to. even a dns server on the web. but it wouldn't resolve any URL. i tried putting in two dns servers (4.2.2.1 and 4.2.2.2) but they did not solve the problem. I tried to use dhcp instead, but no dice.

I'm running a recent install of 11.04 on a dell optiplex 4300s

Any ideas?

---

### Post by dineshs on 2011-05-05
Are you using network manager?What is in /etc/network/interfaces?Please post result```
cat /etc/network/interfaces
```

---

### Post by superdave321 on 2011-05-05
yes, I'm using network manager

when I run the command you gave, I get:

auto lo
iface lo inet loopback

---

### Post by superdave321 on 2011-05-05
i see the problem :P I'm connected to the internet now, but now the software updater won't download anything because of "untrusted sources" any idea about that?

---

