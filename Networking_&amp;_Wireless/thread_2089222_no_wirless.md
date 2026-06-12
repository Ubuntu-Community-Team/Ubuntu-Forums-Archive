---
title: "no wirless?"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by mentisafer on 2012-11-28
Hi, I've had a laptop for five years that I set up with Ubuntu and did some set up and have been using it without issues; just a month ago my laptop just doesnt charge anymore so I got a used PC with windows on it, wiped it and installed Ubuntu without issues until I found out wireless isn't working; I have a wired connection, so I didn't notice, but now I need to get the wireless working. My networkin manager says "no wireless networks found", but my phone shows them, including mine. 
Can someone please help me?

---

### Post by wildmanne39 on 2012-11-28
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by mentisafer on 2012-11-28
Ok Thanks! Here it is.

---

### Post by wildmanne39 on 2012-11-28
Hi, I is your wireless adapter an usb device, is it this Bus 005 Device 002: ID 15d9:0a4f Trust International B.V. ?
Thanks

---

### Post by mentisafer on 2012-12-02
so sorry for late reply, was on the road for couple days; I dont think wireless is usb device, if you mean i would have to plug it. I have a desktop with mouse, keyboard and printer pluged in through usb though, but I dont have an idea aobut the wirelessmight be inside, might be missing? The fact is this computer was given to me used from work, they didnt need it but they dont know the specs, it was free.

---

