---
title: "Xubuntu 9.1 wont WPA authenticate 5100 AGN wireless"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by GodzKnightZ on 2010-02-14
I am pretty new to Linux and from everything i've read Ubuntu was pretty user friendly so someone who isnt too experienced with Linux. I installed Xubuntu 9.10 and I have a Intel(R) 5100 AGN wireless card. The problem i'm having is that I can't get my wireless card to authenticate (WPA/WPA2 personal) to my router. I can connect to unsecure networks fine but can't connect to any WPA connections.. 

any and all help will be greatly appreciated...

---

### Post by chili555 on 2010-02-14
What seems to work for some, but not all cases, is to open a terminal and do:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
```If this works for you, we will have to take additional steps to make it permanent.

---

### Post by GodzKnightZ on 2010-02-14
nope sorry still couldnt connect to my router :(

---

### Post by GodzKnightZ on 2010-02-14
bump

---

