---
title: "VCN over local network only?"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by soccersnowboarder1 on 2010-11-01
Coming from a somewhat in experienced teen trying to figure out why my VCN will not allow me to connect from my phone outside of my home network... When I do open up remote desktop it changes what it says... one day it says only available through Name.Local and then the other day it shows the IP address and says over the local network. I have tried going into gconf-editor and messing around but it still doesn't seem to work.. I'm not entirely sure how to mess around with my router.. and if that is necessary.. Any help?

---

### Post by Iowan on 2010-11-01
VCN, or VNC? I presume you have your router set to port-forward? It's probably easier if the machine has a static address...

---

### Post by soccersnowboarder1 on 2010-11-02
VCN.. remote desktop.. right..? and what exactly is the static IP addres...

---

### Post by CharlesA on 2010-11-02
There is apparently a bug in vino that messes up the config if "configure the network automatically" is enabled.

I would advise against exposing VNC to the internet since it's not encrypted.

If you want to connect via yer phone, use ssh and tunnel VNC over it.

---

### Post by soccersnowboarder1 on 2010-11-02
ok.. can you please explain that a bit more?? haha I use android, and i am using the appp androidVNC where it asks for password of the VNC, address, and port...

---

### Post by CharlesA on 2010-11-02
> **soccersnowboarder1 said:**
> ok.. can you please explain that a bit more?? haha I use android, and i am using the appp androidVNC where it asks for password of the VNC, address, and port...

There should be an SSH client for android as well.

---

