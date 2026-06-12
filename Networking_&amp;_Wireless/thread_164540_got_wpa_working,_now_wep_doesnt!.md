---
title: "got wpa working, now wep doesnt!"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by martial on 2006-04-22
i followed this one tutorial which i don't exactly remember which one... but wpa works perfectly..the second i boot it hops on the network. since i have wpa at home, but i am down in my apartment at school with wep networks surrounding me i am in a bind. when i try to connect to wep networks..it doesnt allow. i know its probably something in my interfaces or wpa_supplicant file, but i am not quite sure what. so if anyone can help me out that would be great.

thanks

---

### Post by firecat53 on 2006-04-23
Just kill the running wpa_supplicant process. It should work fine, then. I'm not sure if it's supposed to work with unencrypted or WEP while it's running, but I've always just had to kill it.

Good luck!
Scott

---

### Post by martial on 2006-04-24
i tried

sudo killall wpa_supplicant

and tried to connect to a unencrypted essid and it wouldn't connect so i don't know whats going on

---

