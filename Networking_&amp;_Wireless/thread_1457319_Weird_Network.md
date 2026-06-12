---
title: "Weird Network"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by Tux118 on 2010-04-18
Dear Ubuntu Forums,

I have just recently installed Ubuntu karmic on one of my machines. The network worked perfectly until today, when it just wont connect. I have double checked that the SSID and Password are correct. It is a WPA network.

I am sure it is a problem with my computer, not the network, because my brother's laptop (which I am using right now) has ubuntu 9.10 installed on it and the network is working perfectly.

Can somebody please help me?

- Tuz118

---

### Post by carl4926 on 2010-04-18
I take it you tried a reboot already :-)

---

### Post by Tux118 on 2010-04-18
> **carl4926 said:**
> I take it you tried a reboot already :-)

Erm... That fixed it. 

Please dont think of me as a fool.

Thank you for brining me to my senses :P

---

### Post by Iowan on 2010-04-18
Sometimes it's the simple things... :)
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

### Post by carl4926 on 2010-04-18
```
sudo rcnetwork restart
```

should do it too I think

---

