---
title: "Dell D600 - Broadcom STA alternate drivers - kernel bug"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by tinybilly on 2013-03-18
Hello
I've just installed Lubuntu 12.04 on my dell d600. My other laptop works well (dell mini 10), but the D600 won't connect fo my wifi network, so i tried alternate drivers, but:

If i try to install broadcom STA alternate driver, the setup won't finish and crashes: kernel BUG at "include/net/cfg80211.h:2209!"

What does that mean?

[[IMG]http://www.abload.de/thumb/img_0484ljlw5.jpg[/IMG]]("http://www.abload.de/image.php?img=img_0484ljlw5.jpg")

---

### Post by wildmanne39 on 2013-03-18
Hi, if you can boot ubuntu copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by tinybilly on 2013-03-18
never mind, my wifi isn't configured. Actually, i can't find any wireless network^^

PS: File attached

PPS: I've tried to install this driver manually -> no success. I hope, that won't affect the *.txt file

---

### Post by wildmanne39 on 2013-03-18
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43legacy-installer
```
Reboot
Thanks

---

### Post by tinybilly on 2013-03-18
It works, thanks :D

---

### Post by wildmanne39 on 2013-03-18
Your welcome!

---

### Post by tinybilly on 2013-03-18
sorry, i'm connected to my router now, but can't access to a single website. Something still disturbs... :(

---

### Post by wildmanne39 on 2013-03-18
Hi, delete the info.text file in your home folder and run the wireless script again with your wired connection unplugged.
Thanks

---

### Post by tinybilly on 2013-03-18
Can't get the info.txt, when disconnected.

[TABLE="width: 500"]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[TD]--2013-03-18 19:27:54--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... failed: Connection timed out.
wget: unable to resolve host address `dl.dropbox.com'[/TD]
[/TR]
[/TABLE]

---

### Post by wildmanne39 on 2013-03-18
That is okay just post the new file while connect with wire now that your wireless card is activated.
Thanks

---

### Post by tinybilly on 2013-03-18
wired connection, wifi on

---

### Post by wildmanne39 on 2013-03-18
Set encryption in router to wpa2 only if possible,  change security setting in network manager to wpa/wpa2.

Set your wireless settings to match the screenshots then reboot.
Thanks

---

### Post by tinybilly on 2013-03-18
Done. No luck at all :(
I don't understand it. I've installed lots of linux distributions already, and i always get stuck at wifi connection. windows xp works fine, wifi works, but xp is insanely slow^^

i've run your netinfo-script (wifi only):
connecting to dl.dropbox....  connected
HTTP-request ...  timeout

need another fresh info.txt ?

---

### Post by wildmanne39 on 2013-03-18
How far away from the router is your computer? your signal strength is very low and that effects your speed.

I am about to go to work so hopefully someone else will help out.

---

### Post by tinybilly on 2013-03-18
Signal strength is no problem (60-80%), my router is around 6 meters behind a door...

Thank you for your help anyway, have a nice workday

---

### Post by tinybilly on 2013-03-19
Now, I've plugged in an external tp-link wlan usb-stick (model TL-WN722N). It's working out of the box, no alternate drivers required.
The D600 has only 2 usb ports, so i would like to use the internal wifi card, but it seems impossible xD
Mayby i'm going to buy a different internal card or get a damn small usb adapter, that doesn't stick out...

Anyway, my internal could be damaget somehow, and only win. xp can handle this...?!

---

