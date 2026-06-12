---
title: "False wireless connection on startup"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by friedsoup on 2013-04-06
Whenever I boot up or return from sleep, my laptop automatically connects to my wifi, but no applications have internet access. Once I disable and re-enable wireless, all applications work fine. What can I do to solve this? 

I searched as much as I could to avoid posting a new thread, but I couldn't find this specific problem

---

### Post by wildmanne39 on 2013-04-06
Hi, copy and paste this command in the terminal when you can not connect wirelessly using a wired connection (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by friedsoup on 2013-04-07
> **Wild Man said:**
> Hi, copy and paste this command in the terminal when you can not connect wirelessly using a wired connection (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

The connection to dropbox times out even with the wired connection.
Can I dl that script with an active connection, then run it after a reboot?

---

### Post by wildmanne39 on 2013-04-07
Follow the directions at this link for no internet connection.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

---

### Post by friedsoup on 2013-04-07
> **Wild Man said:**
> Follow the directions at this link for no internet connection.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

Here is my netinfo.txt
[http://pastebin.ubuntu.com/5687832/]("http://pastebin.ubuntu.com/5687832/")

---

### Post by wildmanne39 on 2013-04-07
Please try:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```
Also change encryption in router to just wpa2 if possible.
Thhanks

---

### Post by friedsoup on 2013-04-08
> **Wild Man said:**
> Please try:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```


This resolved the issue. Thank you :)

---

### Post by wildmanne39 on 2013-04-08
Your welcome!
Enjoy!

---

