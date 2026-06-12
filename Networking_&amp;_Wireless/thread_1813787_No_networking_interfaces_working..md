---
title: "No networking interfaces working."
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by GoTTsProfeT on 2011-07-28
Okay to play out the story here... I installed the latest release of Kubuntu on to my dell laptop about 3 days ago, I fell asleep last night and woke up to my laptop not being connected to my wireless(it was when I fell asleep, it didnt reboot or anything overnight an dno one touched it), so I plugged in an ethernet cable and it still did not detect an internet connection, then finally it connected through my phones mobile internet via Usb.

However none of the built in networking devices are working, I have them all enabled.

My WLAN Interface says "Unmanaged" and Networking interface complains the cable is unplugged even when it is not.

I know you guys will need some additional info from me to help me.

I just used my mobile broadband to install Wicd network manager but thats just a temporary fix, as it doesnt fix my ethernet issue and I want to be able to use the network manager itself to manage my networks, all help is much appreciated, thanks.

---

### Post by GoTTsProfeT on 2011-07-28
Update: no this did not fix anything, I still cannot browse the internet.

---

### Post by GoTTsProfeT on 2011-07-28
[SOLVED]

Used the following Command

> sudo kate /etc/network/interfaces

and added in

> 
auto eth0
iface etho inet dhcp
auto wlan0
iface wlan0 inet dhcp


then

> sudo kate /etc/NetworkManager/NetworkManager.conf

and changed

> [ifupdown]
managed=false

to

> [ifupdown]
managed=true

saved both files and did a power off then manually powered back on.

After powering back on I uninstalled wicd, and my network manager was properly handling my connections again.
If you have had this problem and installed wicd simply use the command
> sudo apt-get remove wicd

Hope this helps anyone else with a similar issue. (:

---

