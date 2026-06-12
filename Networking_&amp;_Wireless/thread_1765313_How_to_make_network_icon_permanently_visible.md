---
title: "How to make network icon permanently visible"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by yernhoj22 on 2011-05-22
hello guys, i had a problem regarding my network icon missing. two days a go it just work fine and I'm using this desktop pc almost 6 months with no problem.just yesterday the network icon suddenly disappear.I've put the notification area it doesn't solved my problem. well this is odd, because when I go to the terminal and "nm-applet" their the network icon appears from where it is and became visible BUT when I close the terminal/terminate the terminal it disappears. HOW CAN I PUT BACK THIS NETWORK ICON VISIBLE AND PERMANENTLY VISIBLE?

---

### Post by dineshs on 2011-05-23
Did you edit /etc/network/interfaces manually?
To get the icon back either run ```
sudo gedit /etc/network/interfaces
```and edit the file so that it reads only ```
auto lo
iface lo inet loopback
```then restart
OR run ```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```and set```
managed=true
```then restart

---

### Post by yernhoj22 on 2011-05-24
thank you for your response, when i try to "sudo gedit /etc/network/interfaces" a new window will pop-up then its says the same as what youve shown on your first solution.so i did not edit at all and leave it the same. then when i try your second solution "sudo gedit /etc/networkmanager/networkmanager.conf" a new "empty" window will pop-up then i try to input "manage=true" then save and then restart. that wont solve the problem the network icon still missing in the notification area. 
ive try to "nm-applet" at the terminal the network icon will be visible/embedded at the notification are but when i close the terminal the icon disappears.

---

### Post by dineshs on 2011-05-24
Pl see
[http://ubuntuforums.org/showthread.php?t=1545744](http://ubuntuforums.org/showthread.php?t=1545744)
[http://ubuntuforums.org/showpost.php?p=5132230&postcount=3](http://ubuntuforums.org/showpost.php?p=5132230&postcount=3)
I have read somewhere that increasing size of panel may help
(rightclick panel-properties-increase size)

---

### Post by manojyadav001 on 2011-05-24
Hello!!!!
Hi i have the same problem it was after i lost internet connection,when i reinstalled my netgear 111t drivers the network icon had a red cross on it but still said i was connected.

Many thanks

---

### Post by yernhoj22 on 2011-05-24
ive tried all those solutions, i tried nm-applet at the terminal then the network applet shows up, but when i close the terminal it also disappears. i tried nm-applet --sm-disable same result the icons shows at the notification area but when i close the terminal it also disappears.

---

