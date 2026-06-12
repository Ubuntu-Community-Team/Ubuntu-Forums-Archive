---
title: "getting WPA to autoconnect"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by Genesius on 2010-12-01
Running Maverick 64-bit. I previously had my wireless network set to WEP encryption, and when I'd start my laptop it would automatically connect to the network (with a hidden SSID) and everything was great. In order to use my work laptop at home, I had to change to WPA2 encryption. Now every time I start my laptop, it won't automatically connect to the network - I have to click on Network Manager, select "Connect to Hidden Wireless Network", select my SSID, and enter my password. In my wireless profile I have both  "connect automatically" and "available to all users" checked.

So, what am I missing? Or is the answer to ditch Network Manager and install wicd?

---

### Post by gordintoronto on 2010-12-01
The only difference between your environment and mine is that I don't have a hidden network. My laptop connects automatically. (I've also connected to several other networks.)

If you right-click on the network manager icon and select "edit connections," can you delete the existing connections and set up a new connection which connects automatically?

---

### Post by Genesius on 2010-12-02
I deleted and recreated the connection. Still won't connect automatically.

---

### Post by Genesius on 2010-12-04
deleted network manager, installed wicd. Problem solved.

---

