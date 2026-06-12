---
title: "Wireless works but becomes extremely slow"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by Ditchdoc7893 on 2013-04-16
Hello everyone. The problem I am having is on a Toshiba M-55 Satellite. I can get the wireless card to connect to the wireless network after entering the appropriate security credentials. This machine is primarily used for web browsing, and virtually nothing that would put any real tax on the system or available resources. Any web browser (Firefox, Chromium, Chrome, etc) will initially open up whatever page I ask it to; however, when I attempt to navigate through a site, it fails to respond. For example, I navigate to Facebook via the address bar. I then click on a friend's link or other material on the page. While it opens the home page without difficulty, it will not open any other pages via links on any given page (even links provided on a google search). The interesting thing is that when I connect a ethernet cable and use the wired network, I have none of the problems mentioned above. Additionally, I will add that I have done multiple installs of a variety of OSs trying to remedy this problem with no success, so a clean wipe is obviously not the solution. 

Does anyone have any information or ideas?

Thank you in advance for any help!

---

### Post by wildmanne39 on 2013-04-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by Ditchdoc7893 on 2013-04-16
Thanks for your reply Wild Man. Here's the output of the command you supplied:

```
--2013-04-16 21:05:21--  http://dl.dropbox.com/u/57264241/wireless_scriptResolving dl.dropbox.com (dl.dropbox.com)... 107.20.182.97
Connecting to dl.dropbox.com (dl.dropbox.com)|107.20.182.97|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: http://dl.dropboxusercontent.com/u/57264241/wireless_script [following]
--2013-04-16 21:05:21--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 107.20.231.190
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|107.20.231.190|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Saving to: `wireless_script'


100%[======================================>] 1,555       --.-K/s   in 0s      


Last-modified header missing -- time-stamps turned off.
2013-04-16 21:05:22 (188 MB/s) - `wireless_script' saved [1555/1555]

```

---

### Post by wildmanne39 on 2013-04-16
Hi, please read the directions again in the previous post because that is not the file we need.
Thanks

---

### Post by Ditchdoc7893 on 2013-04-16
Apologies Wild Man. The appropriate file is attached.

---

### Post by wildmanne39 on 2013-04-16
Please do:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k

```
Thanks

---

### Post by Ditchdoc7893 on 2013-04-16
Here is the entire return:

```
ryan@satellite-m55:~$ echo "options ath5k nohwcrypt+1" | sudo tee /etc/modprobe.d/ath5k.conf[sudo] password for ryan: 
options ath5k nohwcrypt+1
ryan@satellite-m55:~$ sudo modprobe -rfv ath5k
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko
ryan@satellite-m55:~$ sudo modprobe -v ath5k
insmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt+1
FATAL: Error inserting ath5k (/lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko): Invalid argument
ryan@satellite-m55:~$ 



```

---

### Post by wildmanne39 on 2013-04-16
Hi, just copy and paste the command for accuracy, you have a typo.
Thanks

---

### Post by Ditchdoc7893 on 2013-04-16
Actually, that is exactly what I did for each command. I will try it again just to be safe

---

### Post by Ditchdoc7893 on 2013-04-16
Here is each command copied and pasted separately:

```
ryan@satellite-m55:~$ echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf[sudo] password for ryan: 
Sorry, try again.
[sudo] password for ryan: 
options ath5k nohwcrypt=1
ryan@satellite-m55:~$ 



```

```
ryan@satellite-m55:~$ sudo modprobe -rfv ath5krmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko

```

```
ryan@satellite-m55:~$ sudo modprobe -v ath5kinsmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1



```

---

### Post by wildmanne39 on 2013-04-16
Looks liked it worked this time.
Is your speed better?
Thanks

---

### Post by Ditchdoc7893 on 2013-04-16
For now it seems to be! Thank you for your assistance and your patience! I will mark this as solved. Thanks again!

---

### Post by wildmanne39 on 2013-04-16
Your welcome!
Enjoy!

---

