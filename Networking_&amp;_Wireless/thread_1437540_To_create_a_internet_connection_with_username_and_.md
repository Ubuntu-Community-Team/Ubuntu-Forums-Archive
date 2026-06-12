---
title: "To create a internet connection with username and password  in ubuntu 9.10"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by santanihitesh on 2010-03-24
Hi frnds !!!

I m hitesh. I m having a dell inspiron 15 laptop. I m having windows vista in my laptop. I have dial up internet connection in it. Now i have installed ubuntu 9.10 in my laptop. Nw i want to configure that dial up connection in ubuntu. Can anyone tell me hw it can be done ?? i have tried a lot but its nt done.....


Plz help as i m new to ubuntu world !!!!

Thanx....

---

### Post by Soulcage on 2010-03-24
You need to download: gnome-ppp [http://packages.ubuntu.com/karmic/gnome-ppp]("http://packages.ubuntu.com/karmic/gnome-ppp")
wvdial [http://packages.ubuntu.com/karmic/wvdial]("http://packages.ubuntu.com/karmic/wvdial") libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras after you install all of those then paste into a terminal ```
sudo apt-get purge modemmanager
```
Then restart then you can use gnome-ppp to connect. Assuming your modem works im using a USR5637 myself.

---

### Post by al_aeena on 2010-03-24
same problem

---

### Post by dineshs on 2010-03-24
You can try ```
sudo pppconfig
``` pl refer this site
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)
After configuring you can connect using ```
pon abcd
```
where abcd is the name of the provider you gave while configuring and disconnect using ```
poff abcd
```
Once you get internet try to install gnome-ppp to get a GUI tool
```
sudo apt-get install gnome-ppp
```
If you have an internal dialup modem pl refer this link
[http://linmodems.org/](http://linmodems.org/)

---

