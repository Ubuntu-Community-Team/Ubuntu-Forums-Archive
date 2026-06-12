---
title: "Dell Latitude E6400 - Connects to wireless, but doesn't open pages."
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by hking0036 on 2013-06-07
I'm relatively new to linux and ubuntu, but I've heard it's a good starting point so I decided to get it running. I have a fair grasp on setting things up, all the sudo apt-get stuff, and for the most part, it sorted itself out. I had it connected to an ethernet cable during install to get updates before I got it started, and when I unplugged it, it connected fine to the wifi at home, but when I attempted to open google through firefox, it failed to work. I was told to do "sudo modprobe lib80211_crypt" and when I entered that, it says "FATAL: Module lib80211_crypt not found". any help is appreciated, thanks.

EDIT: I'm also running 12.04, not 13.04.

---

### Post by wildmanne39 on 2013-06-07
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by hking0036 on 2013-06-07
Alright, after running the script, it just gave me a .txt, and not a tar.gz, but here it is.

---

### Post by wildmanne39 on 2013-06-07
Please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
copy and paste one line at a time.

Also please change your channel to 1 or 11.

We may have to disable power management.
Thanks

---

### Post by hking0036 on 2013-06-07
Alright, followed those commands and then changed the channel to 1, restarting the router now, I'll get back to you in a moment with the results.

EDIT: Thank you very much, this solved the problem. :D (You can close the thread now)

---

### Post by wildmanne39 on 2013-06-07
Glad it worked.

---

### Post by ahallubuntu on 2013-06-08
~

---

### Post by hking0036 on 2013-06-08
> **ahallubuntu said:**
> I don't consider disabling 802.11n on my wireless cards acceptable except as a very last resort, because I don't want to lose 1/2 my local network speed (or more).  Transferring files over my local network is important to me.   For only browsing the internet, 802.11g is fine I guess.  But I've never needed to disable 802.11n on any of my Intel wireless cards running Ubuntu 12.04.  (I use the WiFi Link 5100 not 5300 in most of my laptops.)
If it was upgraded, it wasn't by me. I got my laptop off of ebay... XD

---

### Post by ahallubuntu on 2013-06-08
~

---

