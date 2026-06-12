---
title: "Intel Corporation Centrino Ultimate-N 6300"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by andelemamy on 2013-05-06
Hey guys I am new to the forum and have a question about my new wireless card I installed today. I got it running just fine and was wondering why this is capping out at 144mgs. My router supports up to 300 mgs and was wondering if I am doing something wrong?

Thanks

---

### Post by praseodym on 2013-05-06
Hi,

there is a bug with the N-mode of the driver. Deactivate N in your router settings or (better) in the driver itself:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by ahallubuntu on 2013-05-06
~

---

### Post by ahallubuntu on 2013-05-06
~

---

### Post by andelemamy on 2013-05-06
I am connecting via WPA2 + AES and its a 5gz connection... I am fairly close to the router actually around 8 feet. I was looking around at other forums and noticed other people were maxing out at 144 exactly... won't go any higher than that. I guess my question is or has anyone with this card achieved higher speeds than the 144?

Thanks again to all who have replied!

---

### Post by ahallubuntu on 2013-05-06
~

---

