---
title: "Wireless not working on Lenovo 3000 N200 with Intel 3945ABG Wireless"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by tizzidale on 2013-04-05
I'm an admitted absolute newbie with Linux. Sorry in advance. I've loaded 12.04 on a Lenovo 3000 N200 laptop. Wired network works. The laptop has a physical wireless network switch and it is on (Bluetooth is working). However, I can't connect wirelessly. I cannot enable the wireless network. Any help is appreciated.

---

### Post by wildmanne39 on 2013-04-05
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by tizzidale on 2013-04-05
Thanks for your help. I attached the document.

---

### Post by wildmanne39 on 2013-04-05
Hi, please try:
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by tizzidale on 2013-04-05
Wildman, thank you! That did it after I rebooted. Connected wirelessly now.  I'm not entirely sure what we just did, but I'll take it :)

---

### Post by wildmanne39 on 2013-04-05
That module we blacklisted sometimes acts up and does not tell thekernel to turn the wirless on so we removed it from loading.
Enjoy!!!

---

