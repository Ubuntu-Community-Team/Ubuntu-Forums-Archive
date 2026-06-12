---
title: "Internet connectivity problems"
date: 2013-04-02
forum: Networking &amp; Wireless
---

### Post by rnadmoiezd on 2013-04-02
[COLOR=#000000]My wireless internet keeps dropping and is really really slow (50 kb/s slow). It stays connected (so it says) but actual internet functionality goes out the window. After a while it asks for my network password. Upon entering it, it does nothing. The only fix is to unplug my adapter and plug it back in. I've tried downloading the drivers converted the .tgz with alien, trying to install and also tried following instructions from users here who have had the same problem installing drivers for it but I have not been able to successfully install them. [/COLOR]**The adapter is an ASUS N-13 USB.**

---

### Post by wildmanne39 on 2013-04-02
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by rnadmoiezd on 2013-04-02
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

Ok, here it is. These are the 2 major problems I'm having right now. The issue with the internet not working even though I'm connected to the network and the download speeds that are topping out at 300 kb/s if i'm LUCKY. The get nvidia current download was going at a whopping 26 kb/s.

Also something I just noticed. Whenever I turn on Ubuntu I have to remove my adapter and plug it back in because it doesn't recognize that there is a wireless adapter plugged in so it doesn't seach for wireless networks. Just FYI.

---

### Post by wildmanne39 on 2013-04-02
Is this the driver that comes with ubuntu or did you compileit yourself?

This driver is a very big problem but we can do somethings to get it working better usually.
Thanks

---

### Post by rnadmoiezd on 2013-04-02
It's the one that came with ubuntu. I tried installing a new one from the Asus site but no luck.

---

### Post by rnadmoiezd on 2013-04-02
Here is a new Netinfo text file if anything changed.

---

### Post by wildmanne39 on 2013-04-02
Please try:
```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```
if it works we will need to make it permanent.
Thanks

---

### Post by rnadmoiezd on 2013-04-02
> **Wild Man said:**
> Please try:
```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```
if it works we will need to make it permanent.
Thanks

Nope still loses connectivity while saying it's connected to the network.

ETA: Speed test . net says that my connection is normal. I would disagree since I've seen the speeds I've been getting though. Also I noticed that if I'm downloading something, ANYTHING, from the internet then the connection doesn't drop out. However, if I'm downloading something from terminal or software center like getting a package or something then it will drop like it's been doing.

---

### Post by wildmanne39 on 2013-04-03
Hi, please install the driver in post one of this link.
[http://ubuntuforums.org/showthread.php?t=2119378](http://ubuntuforums.org/showthread.php?t=2119378)
Thanks

---

### Post by rnadmoiezd on 2013-04-03
I think I fixed it last night. I installed the drivers from realtek and blacklisted the others and it hasn't had a problem yet. I even left it on all night as a test and it's still connected and the speeds have gone up a good bit. I'll report back in a few days If I have any more problems.

---

### Post by wildmanne39 on 2013-04-03
That is what I was recommeding to do as well.

Please post the link to the driver you used and the directions for installing it so the whole community can benefit.
Thanks

---

