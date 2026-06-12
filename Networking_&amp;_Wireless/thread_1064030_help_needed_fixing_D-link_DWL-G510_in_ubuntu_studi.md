---
title: "help needed fixing D-link DWL-G510 in ubuntu studio 8.04!"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by vmkarthik on 2009-02-08
Hi,
   i am karthik and i am new to linux. i have installed ubuntu studio 8.04(2.6.24-23-rt) hardy for my music production and i have added the D-Link DWL-G510(Rev C) in that for my internet access. right now i am writing to you through my wired connection which is working well. but i want to shift this system to my music room and i have to enable internet access from there.

    Currently i am not able to successfully configure this wireless adapter to work. 

    i got to see the help for wireless configurations with D-Link DWL-G510 around many places but everything went in vain. I tried all the steps in Raubsau's link [http://ubuntuforums.org/showpost.php?p=3612858&postcount=12](http://ubuntuforums.org/showpost.php?p=3612858&postcount=12) 

   afterthat i tried to connect but couldn't. when i went to the networks and saw the wireless connection was unchecked suddenly. I checked and enabled it and then i tried again, but still no connection.
  
 also whenever i try to run iwlist scan in terminal i get resource busy for wlan0 like the one below.

vmkarthik@ubuntu:~/rt61-cvs-2009020805/Module$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Device or resource busy

**the below is the result of my iwconfig:**

vmkarthik@ubuntu:~/rt61-cvs-2009020805/Module$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT61 Wireless  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

please help me to make my wireless to work so that i can shift my PC to my room soon.

expecting your extended help in this regard :(.

---

### Post by vmkarthik on 2009-02-10
hi any one please help me from scratch to make my D-Link DWL-G510 to work with ubuntu studio 8.04.
  need your help immensely.....

---

### Post by Tripp523 on 2009-02-27
I have the same chipset with my Wifi card; I cannot get it to connect with 8.04, but it works very well with 8.10.

---

