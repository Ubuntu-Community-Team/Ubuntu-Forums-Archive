---
title: "Vigor N61 (RT2870 chipset)"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by stan01 on 2009-01-09
Hi all,

Just to explain how I made the Draytek Vigor N61 work on Ubuntu 8.10 and 8.04:

1) Download driver from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) You'll only need the RT2870USB driver. 
2) Save this driver in /usr/src/ and type 'tar xjvpf 2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2' to extract the file. After this, change to the newly created directory.
3) make sure you are ready to compile a driver (do a 'sudo apt-get install build-essential')
4) type 'gedit os/linux/config.mk'
5) change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'
6) save file and type 'make' and then 'sudo make install'
6) You need to copy the firmware file 'RT2870STA.dat' to /etc/Wireless/RT2870STA/RT2870STA.dat 'sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat'
7) done :D Maybe you'll need to reboot your machine to make everything work, i don't remember..

---

