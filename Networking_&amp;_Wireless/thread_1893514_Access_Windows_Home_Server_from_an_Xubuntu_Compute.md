---
title: "Access Windows Home Server from an Xubuntu Computer"
date: 2011-12-10
forum: Networking &amp; Wireless
---

### Post by smartcard on 2011-12-10
I would like to know how to Access Windows Home Server from an Xubuntu Computer on the Network?

In Ubuntu this is possible as per this : [http://www.howtogeek.com/howto/19389/access-windows-home-server-from-an-ubuntu-computer-on-your-network/](http://www.howtogeek.com/howto/19389/access-windows-home-server-from-an-ubuntu-computer-on-your-network/)

And in Lubuntu I can achieve it like ...
File Manager ( PCManFM ) > Go > Network Drives

How can I do it in Xubuntu?

---

### Post by smartcard on 2011-12-10
I found the answer from another thread, and it is working.  Hope it will help others too

   
     > sudo apt-get install gvfs-backends 

After it's installed logout and login again and bring up thunar. In the left side panel should be an item labeled "Newtork" .

---

### Post by lisati on 2011-12-10
Please don't start multiple threads for the same question.

---

