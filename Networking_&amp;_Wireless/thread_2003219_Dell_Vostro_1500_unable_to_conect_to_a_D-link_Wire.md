---
title: "Dell Vostro 1500 unable to conect to a D-link Wireless 150 Router with Ubuntu 12.04"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by Chots on 2012-06-13
Hello I formatted my Dell Vostro 1500 to Ubuntu 12.04 LTS about a week ago and I've been having problems trying to connect to the wirless network that I have where I live. I have an Intel Corporation Pro/Wireless 4965 AG chipset and My kernel version is 3.2.0-24-generic pae i686. I'm able to connect wirelessly in my school but not in the house I'm living in right now and I'm blaming it on the router, but I'm no expert as to be completely sure. The router model here is a D-link Wireless 150 router and the network has a WPA2-PSK (AES) security encryption. I don't have much acess to the router due to the fact that Im living as an exchange student here with an older woman. The problem that I have manifests itself like this; whenever I connect to the wireless network, ubuntu promts me with an "Authentication requiered by wireless network: Passwords or encyption keys are required to access the wireless network 'X'." I go ahead and input the network's password and it stays "connecting" for a couple of minutes before promting me with the same authentication screen ad infinitum. It has only established connection 2 or 3 times an it usually happened after trying out different gnome appearances. Does anyone have any suggestions to make things work?

---

### Post by wildmanne39 on 2012-06-23
Hi, please do:
```
echo "options iwl4965 11n_disable=1" | sudo tee /etc/modprobe.d/iwl4965.conf
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965
```
does that help?
Thanks

---

