---
title: "b43-fwcutter"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by SeaSnacks on 2009-11-25
Hello when I try to install the b43-fwcutter from the hardware drivers it freezes at 0% and I have to force quite.  When I try to install it from the synaptic package manager i get the error message:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

i am not sure what to do and i am new to linux, anything would be helpful.

---

### Post by Metaljaz on 2009-11-26
Under Synaptic Package Manager > settings > repositories > other software  make sure they are both checked. From the terminal window type:
sudo apt-get update
sudo apt-get install b43-fwcutter

---

### Post by Metaljaz on 2009-11-26
Under Synaptic Package Manager > settings > repositories > other software  make sure they are both checked. From the terminal window type:
sudo apt-get update
sudo apt-get install b43-fwcutter

---

