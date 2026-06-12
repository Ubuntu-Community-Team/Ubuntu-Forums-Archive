---
title: "Atheros+Compaq CQ60-120EV Problem"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by benzidirk on 2008-12-17
Hi i just bought a compaq cq60-120ev and installed ubuntu ultimate 2.0 and i have a problem with my wifi and wired network!! linux does not seem to be identifying the devices at all!! what can i do!? all i know is that the wifi adapter is atheros and the ethernet is realtek... please help!

---

### Post by ibutho on 2008-12-17
Hi.

You need to provide us with specific details about the chipsets on your network cards. Can you go to Applications -> Accessories ->  Terminal and enter the commands
```
sudo lspci | grep -i net
sudo lshw -C network
```
Post back the output.

---

### Post by benzidirk on 2008-12-18
Ok... Yesterday after trying some stuff.. it worked! but only until i restarted my system... then the wifi device dissapeared again for some reason...

The Wifi adapter is Atheros AR242x AR5007..

---

