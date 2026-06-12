---
title: "How to install edimax EW-7318USg newb"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by DSheth on 2009-11-14
Hello:KS

A few days ago i managed to dual-boot Windows XP and ubuntu on my PC, but now i have the problem of installing the EDIMAX EW-7318USg wireless adaptor on the ubuntu boot so i can access internet on it too, i tried using the instalation disk that came with it but it doesnt seem to work, please bear in mind that i am currently new to this OS and i dont know what to do ive seen its supported on the compatibility page. any help would be appreciated.:p

---

### Post by chili555 on 2009-11-14
According to the compatability page, all you need to do is insert the device and open a terminal and do:```
sudo modprobe rt73usb
iwconfig
```Do you see a wireless interface now? Can you click the Network Manager icon and connect (he asks, optimistically)?

---

### Post by DSheth on 2009-11-14
well heres what happened and it didnt really work:



dipesh@dipesh-desktop:~$ sudo modprobe rt73usb
[sudo] password for dipesh: 
dipesh@dipesh-desktop:~$ sudo modprobe rt73usb
dipesh@dipesh-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by DSheth on 2009-11-14
please help :p

---

### Post by DSheth on 2009-11-14
ok ive nearly got it i think just small help please :KS
 under network tools ive found my wireless edimax listed as wlan0, i tried these commands obviously i entered my own wep key n essid:

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid YOUR_NETWORK_NAME_HERE 
sudo iwconfig wlan0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
sudo dhclient wlan0

but then it didnt work and this is what it was saying:

Listening on LPF/wlan0/00:0e:2e:4d:f0:0f
Sending on   LPF/wlan0/00:0e:2e:4d:f0:0f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



??? i dont know what to do from here i did a scan using 'sudo iwlist scan' and i saw other access points as well as my own router which im trying to connect to please help!:popcorn:

---

### Post by chili555 on 2009-11-14
The manual configuration tools, dhclient, etc., don't work very well with Network Manager. It's like two people pulling on the steering wheel at once!

Please click the Network Manager icon, select your network, put in your WEP key, most likely in 'WEP 40/128-bit HEX' and see if you can connect.

---

### Post by DSheth on 2009-11-14
i couldnt find the network manager icon, when i plug my wireless adaptor it says one or more wireless networks is available but i dont know where to go, its installed it says from the ubuntu software centre

i dont have that icon on the bottom right corner

---

### Post by DSheth on 2009-11-14
ok i tried to type:
nm-applet --sm-disable
in the run menu from Alt-F2, and put that into the box. but nothing happened??:icon_frown:

---

### Post by DSheth on 2009-11-14
HAHA yes it finally worked thanks for your help guys i typed this from the ubuntu partition:KS:KS:popcorn::p:D:o:):P

---

### Post by coffeecat on 2009-11-14
Just in case any other newcomer comes across this thread, the Edimax EW-7318Ug USB wireless adaptor works **out of the box** in both Jaunty and Karmic. You don't have to do any modprobing, iwconfig-ing, installing drivers or anything like that. At least not in this household you don't. :wink:

Click on the network-manager at **[SIZE=4]top-right[/SIZE]** of the desktop. Select your network, type in your WEP/WPA key where prompted and enjoy surfing the internet.

There - easier than Windows! :p

---

### Post by DSheth on 2009-11-14
yeah my problem was i couldnt see the network manager and thought that i had to try complex commands :popcorn:

---

### Post by coffeecat on 2009-11-14
> **DSheth said:**
> yeah my problem was i couldnt see the network manager and thought that i had to try complex commands 

Yes, I know. It's a common misconception that in Linux you have to type a whole load of gobbledegook into a terminal to get anything to work. It comes as quite a shock when people find that configuring wireless can be easier that in certain other proprietary OSs we could mention. :p

I hope you don't think that I was getting at you. Far from it. Although some wireless chipsets are still a pain to configure, it's a fact that with most you just have to do what I described. It always pains me to see people unfamiliar with Ubuntu getting in a muddle with wireless devices that 'just work' - hence my post.

Enjoy your Ubuntu-ing! :)

---

