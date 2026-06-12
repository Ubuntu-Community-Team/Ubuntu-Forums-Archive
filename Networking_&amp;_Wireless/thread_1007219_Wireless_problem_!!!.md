---
title: "Wireless problem !!!"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by Bigmon on 2008-12-10
Hi !! Wonder if anyone can help ? Been at this for days now and its driving me insane !!

Trying to connect xp and ubuntu computers wirelessly ad hoc. Both wireless cards are working fine as i can gather as can both ping loop back address 127.0.0.1. When i create a new network in ubuntu, the windows computer sees the new network and can connect to it. It assigns itself an IP address but I cannot ping this address from the ubuntu side. The ubuntu computer says it is also connected to the same network ( i have manually assigned it an ip address ) but i cannot ping this address either from windows. The little bars at the top of the screen that indicate the strength of the reception are virtually always empty on the ubuntu computer even though the computers are next to each other. I can go to network on the ubuntu computer and see the windows computer and see its shared files - sometimes !!! I cannot however see the ubuntu computer in my network places at the windows end. The status of the wireless connection on the windows computer is always good when connected - strength good !!

Can anyone help. I am new to ubuntu by the way (this may appear obvious )

Bigmon

---

### Post by iponeverything on 2008-12-10
ok. from the linux box post:

sudo iwconfig 
sudo route -n

from the windows machine post:

ipconfig /all

---

