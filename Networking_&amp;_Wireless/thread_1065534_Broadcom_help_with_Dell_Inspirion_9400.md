---
title: "Broadcom help with Dell Inspirion 9400"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by tototime on 2009-02-10
Hi all,
I used to have ubuntu on my computer about a year ago, but I completely forgot how I got my wireless to work.  If anybody could give me a quick tutorial it would be greatly appreciated.  I have a Dell Wireless WLAN 1390 mini card. I am running Ubuntu 8.10

---

### Post by Ayuthia on 2009-02-10
> **tototime said:**
> Hi all,
I used to have ubuntu on my computer about a year ago, but I completely forgot how I got my wireless to work.  If anybody could give me a quick tutorial it would be greatly appreciated.  I have a Dell Wireless WLAN 1390 mini card. I am running Ubuntu 8.10

You might first try going to System->Administration->Hardware Drivers and see if there are any Broadcom options available.  If not and you have a working internet connection, try installing b43-fwcutter.  If you don't you might try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
```

Hope that helps.

---

### Post by tototime on 2009-02-10
Hey thanks for the post I tried installing the b43 fwcutter and I enabled it in my hardware drivers but it still did not work.  I then tried the sudo modprobe commands and those did not work.  It now does not show the option to even enable wireless.  Are there any other solutions?

---

### Post by tototime on 2009-02-10
Sorry i Have now restarted and updated and it shows enable wireless but if I click on it the checkmark does not appear

---

### Post by Ayuthia on 2009-02-10
Can you post the results of:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo ifconfig wlan0 up
dmesg|grep b43
sudo iwlist scan
```

This will load the b43 module again and check to see if it had any problems loading.  Then it will scan for wireless sites.

---

### Post by tototime on 2009-02-12
hey thanks for your help it now is working successfully

---

