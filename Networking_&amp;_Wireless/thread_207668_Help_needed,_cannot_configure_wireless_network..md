---
title: "Help needed, cannot configure wireless network."
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by davoid87 on 2006-07-02
I have a Marvell W8300 wireless card, and have set it up using ndiswrapper, and the hardware is installed and appears in System -> Administration -> Networking. I have set up the configuration using this menu to choose the essid and the encryption key, and set it to dchp, but it wont connect to the network. When I type iwconfig, it shows that my network isnt connected, even though I have set it up, it doesnt show the settings I put. When I try the command:

sudo iwconfig wlan0 essid bert

it comes with some error saying I can't do that, something to do with an invalid argument. I am posting this from Windows XP from memory, so if anyone wants the exact messages, just ask. If I type:

sudo iwlist wlan0 scan

then it scans successfully and shows my wireless network "bert". I just can't get it to connect to it.

If anyone could help me that would be greatly appreciated.

---

### Post by davoid87 on 2006-07-05
Anyone at all?

---

