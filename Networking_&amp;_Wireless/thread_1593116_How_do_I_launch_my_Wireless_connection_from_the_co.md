---
title: "How do I launch my Wireless connection from the command line?"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by oxf on 2010-10-11
The title about says it! I have a major problem on my laptop after installing updates. Some of my icons in the top panel are broken. So as a first step I need to reinstall a few things. The first step is to start the wireless connection from the terminal. So would someone please tell what the command is?
Many thanks..

---

### Post by ankith13 on 2010-10-11
first check if the iwconfig command is working and showing the wireless extension....

Try setting the key (if enabled) (replace eth1 with your network interface name....)

   $iwconfig eth1 enc your_key 

connect to the essid (access point)

  $iwconfig eth1 essid "network_name"

and then use dhcpcd to request an ip address...
  
  $dhcpcd eth1 -d 

Try man iwconfig, man dhcpcd for an explanation of these commands. 

Cheers,
Ankith

---

### Post by oxf on 2010-10-11
> **ankith13 said:**
> first check if the iwconfig command is working and showing the wireless extension....

Try setting the key (if enabled) (replace eth1 with your network interface name....)

   $iwconfig eth1 enc your_key 

connect to the essid (access point)

  $iwconfig eth1 essid "network_name"

and then use dhcpcd to request an ip address...
  
  $dhcpcd eth1 -d 

Try man iwconfig, man dhcpcd for an explanation of these commands. 

Cheers,
Ankith

Thanks for that anyway. iwconfig reports no wireless extenions. However, this does not now suprise me as the wireless icon was gone. It seems like I have  a much bigger problem that was caused by a kernel update "breaking" my system.
Grrrrrrr

---

