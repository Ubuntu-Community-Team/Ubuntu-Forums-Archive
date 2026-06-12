---
title: "Intel Wifi 5300 AGN wireless A mode not working in Ubuntu 9.04 ?"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by ConRong on 2009-05-08
Hello everyone,

I am very new to Ubuntu community. Having trying Ubuntu for couple days now and like it a lots compare to other Linux distro out there. I have an issue with my wireless connection. It seems to connect to wireless G mode fine but can't connect to wireless A mode. This seems very strange because I know that wireless A mode work very well in Windows. Can anyone shine me some light here, greatly appreciate?

Thanks so much,

---

### Post by chili555 on 2009-05-08
I have an Intel 3945ABG and connected to an A network just a few days ago. I configured manually.```
sudo iwlist wlan0 scan
```I learned that the ESSID was 'guest,' encryption was off and the channel was 36.```
sudo iwconfig wlan0 channel 36
sudo iwconfig wlan0 essid guest
sudo dhclient wlan0
```If you are using Network Manager, you may need to disable it first.```
sudo /etc/init.d/NetworkManager stop
```

---

### Post by ConRong on 2009-05-08
I did all that and still not detect my wireless A mode. It must be the driver or some tweaking. Does anyone know?

---

