---
title: "Wireless networks disconnected"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by aloje on 2010-10-10
I am quite new to Ubuntu, so please give me easy to follow steps.

So, I have just installed Ubuntu 10.10 x64, but cant get my wireless to work. It detects my networks and tries to connect to them - infinitely, whithout success.

I have tried it on an unprotected and on a WPA2-personal protected network with the same results.

My card is a RaLink rt3090.

Please, help me connect wirelessly

---

### Post by aloje on 2010-10-11
No one?

---

### Post by fight2survive on 2010-10-11
I'm getting the same exact problem ever since i upgraded from 10.4 netbook to 10.10 netbook....i'd really like help with this. thanks.

---

### Post by aloje on 2010-10-12
OK, I have partially fixed it.

I was previously using Ubuntu 64bit and wireless didn't work. So I have installed the 32bit version of the OS and then wireless networks were automatically detected and I can now connect to unprotected networks, but not WPA2 protected networks.

While the 32bit OS may not use all my 4GB RAM, I think there is a workaround to use it all.

---

### Post by fight2survive on 2010-10-13
I still need help with this. can anyone help please? the only network i can connect to (mine) is a WPA2...and everytime i try to connect it keeps asking me for the password over and over again...

---

### Post by Uatek on 2010-11-09
In 10.04 I had a simillar issue, then I was able to connect killing NetworkManager and starting it again with sudo, but this does not work on 10.10 for me, since NetworkManager is already running as root.

In both 10.04 and 10.10 iwlist scan worked only as root, not showing anything as normal user.

---

### Post by bzyk3 on 2010-11-09
Try this:

Code:

sudo su
echo "rt2870sta" >> /etc/modules
modprobe rt2870sta
exit

After restart my work.

---

### Post by sukharevd on 2010-11-10
I had a very same problem. Maybe this:[ http://ubuntuforums.org/showpost.php?p=10099497&postcount=5]("http://ubuntuforums.org/showpost.php?p=10099497&postcount=5") can help you. Just try!

---

