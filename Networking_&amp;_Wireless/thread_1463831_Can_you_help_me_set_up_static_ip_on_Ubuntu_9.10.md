---
title: "Can you help me set up static ip on Ubuntu 9.10"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by KixZick on 2010-04-27
I need to know how to set up a static Ip on Ubuntu 9.10 32bit/X84. I would like you to go step by step I example would be open terminal type sudo etc. I would like to not have to use terminal if possible. My connection is etho.

---

### Post by limey_rick on 2010-04-27
You should check here: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

You should be able to do this in the network manager tool. Its normally on the top menu bar, as an ICON in 10.05 its two arrows one up and one down, in 9.10 its a bit like this -o- but rotated anti clockwise a bit. 

If you right click on this, you can edit your network connections and then select the wired one and here you can specify a manual IP address. Read the docs above first to make sure you have all the info you need.

---

### Post by oldfred on 2010-04-27
Your router probalby has a range already allocated for DHCP. You cannot use any of those addresses. Also you end of having to keep a list as you cannot assign any duplicates.

This was mine:

---

### Post by Iowan on 2010-04-27
Depending on your needs, (as previously mentioned) you could either use Network Manager to set up a static address, or set up a static lease in your DHCP server (router?). If you opt for the static address, you'll also need to set up DNS.

---

