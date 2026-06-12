---
title: "How To Set  A Static IP Address"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by Muhnamana on 2011-01-11
So I'm very new to linux world. But installed Lubuntu on my old, maybe old as dirt PC.

A couple of issues hopefully someone can help out with.
#1: Where can I assign a static IP address on my lubuntu box?
#2: Also, is it possible to see the lubuntu box from a Windows machine? If so, how does that work?

Any help would be appreciated.

---

### Post by mikewhatever on 2011-01-11
1. Try the network manager, really easy.
[http://www.liberiangeek.net/2010/06/how-to-configure-static-ip-addresses-in-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/06/how-to-configure-static-ip-addresses-in-ubuntu-10-04-lucid-lynx/)

2. Will need samba for that.
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by SteveDee on 2011-01-12
> **Muhnamana said:**
> So I'm very new to linux world. But installed Lubuntu on my old, maybe old as dirt PC.

A couple of issues hopefully someone can help out with.
#1: Where can I assign a static IP address on my lubuntu box?
#2: Also, is it possible to see the lubuntu box from a Windows machine? If so, how does that work?

Any help would be appreciated.

On Lubuntu (10.10) you access the network interface by right clicking on the network icon in the panel, then select Edit Connections. Then you can more or less follow the instructions as per the link in post #2.

To use Samba in Lubuntu see here: [http://ubuntuforums.org/showthread.php?t=1623346](http://ubuntuforums.org/showthread.php?t=1623346)

---

### Post by Muhnamana on 2011-01-12
Sweet! I appreciate the help guys.

---

### Post by woodyg on 2011-12-15
In the network interface/manager, I believe I know my gateway (from route -n) and netmask (from ifconfig), but where can I find my (IP) address and the DNS?

---

### Post by SteveDee on 2011-12-16
> **woodyg said:**
> ...but where can I find my (IP) address and the DNS?

If you have a network connection, just right-click on the network icon in panel, then select Connection Information.
...but maybe that's not your question?

---

### Post by woodyg on 2011-12-16
That was my question, and it seems to work. Cheers!

---

