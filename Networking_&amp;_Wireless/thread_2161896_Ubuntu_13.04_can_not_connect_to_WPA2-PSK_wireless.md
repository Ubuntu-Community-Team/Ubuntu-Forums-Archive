---
title: "Ubuntu 13.04 can not connect to WPA2-PSK wireless"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by Mirabilis on 2013-07-12
Good morning,
i'm writing here just to not create a new post.
I have a similar problem using Ubuntu 13.04: the wireless connection seems to be activated but when I try to surf on the Internet, Firefox doesn't find Google.com. So I tired to ping [www.google.com](www.google.com) from the terminal but it gave no answer. Then I turned everything off and restarted everything: the ping this time worked but when I tried to open the browser, it failed again, as the browser did. 

Thinking Ubuntu had some problems (I'm new on this OS), I download and installed Lubuntu, hoping something could change. Actually it didn't. Nothing different. Finally I checked what kind of driver was being used and, for Ubuntu and Lubuntu, it was the same: lw4965. The driver is not working properly? Should I change it? 

Thank you for any help!

---

### Post by Elfy on 2013-07-12
Please do not hijack other threads.

There could be completely different issues at play - if nothing else you aren't using the same version of software.

---

### Post by Elfy on 2013-07-12
Please do not hijack other threads.

There could be completely different issues at play - if nothing else you aren't using the same version of software.

---

### Post by wildmanne39 on 2013-07-12
Hi, please try:
```
echo "options iwl4965 11n_disable=1" | sudo tee /etc/modprobe.d/iwl4965.conf
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965
```
Thanks

---

### Post by wildmanne39 on 2013-07-12
Hi, please try:
```
echo "options iwl4965 11n_disable=1" | sudo tee /etc/modprobe.d/iwl4965.conf
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965
```
If it still does not connect please copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks
Thanks

---

