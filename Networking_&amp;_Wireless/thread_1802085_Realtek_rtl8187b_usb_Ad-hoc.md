---
title: "Realtek rtl8187b usb Ad-hoc"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by dragonclan1tnt on 2011-07-11
i don't know if this is known already but i didn't see any thing in any site on this 


for the the past week or so i was trying to get Ad-hoc mode on my Advantek USB WiFi dongle (AWN-USB-54R) so i can do some testing and expanding of my mesh network

and i finally came across the answer

i disable the linux drivers by add it to the blacklist and install ndiswrapper, use the windows drivers and i got Ad-hoc working 

sudo rmmod rtl8187

sudo gedit /etc/modprobe.d/blacklist
add "blacklist rtl8187"

after that, download and install the window driver via ndisgtk:D

---

### Post by bapoumba on 2011-07-11
Moved to Networking & Wireless.

---

