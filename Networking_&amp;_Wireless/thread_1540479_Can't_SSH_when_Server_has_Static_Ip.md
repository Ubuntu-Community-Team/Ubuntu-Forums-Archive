---
title: "Can't SSH when Server has Static Ip"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by mparker1113 on 2010-07-27
Hey,
 
I figured that i would like to have a static ip address so that i could always know what the internal ip address was of my server. But when i make the address static, I am not able to SSH in from a different machine on my network. 
 
The network is wireless/wired, through my D-Link router. I can't even ping the server when i give it a static ip. Is there a way that i can have a static ip address and still have it be seen by other machines in my wireless network?
 
I have had to re-install everytime I need to make changes to my etc/network/interfaces file. Otherwise i am told that permission is denied, even for sudo. Is there a way around this ?

---

### Post by Iowan on 2010-07-27
One avenue is to set up a static lease (based on MAC address) in the DHCP server (router?). Otherwise, are you trying to SSH via hostname or IP address (or both)?

Did you change the hostname on the machine? - **sudo** complains if either */etc/hosts* or */etc/hostname* is changed without the other.

---

### Post by mparker1113 on 2010-07-28
I didn't set up a hostname. The only change i made was in the etc/network/interfaces file, to make the machine have a static ip. 

The machine itself seemed to work fine, i just couldn't reach it, and it couldn't ping other machines on the network. Any idea as to if i can have a static ip or a hostname for the machine and still communicate with other machines on the network ?

---

### Post by Iowan on 2010-07-28
The short answer: "You *should* be able to give the machine a static 
IP address. If you haven't upset **sudo** by changing a hostname (you can verify that the names in the two aforementioned files are the same), you *should* be able to edit the file using **sudo nano /etc/network/interfaces**.
It's important to choose an IP address that's in the same subnet, but outside the DHCP address range.

---

