---
title: "Routing between LAN and WAN"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by Chitown on 2012-10-24
VV----Router #2 Setup----VV
###########Local IP: 
192.168.0.254/24:
###########Gateway: 
192.168.0.1

VV----My LAPTOP LAN----VV
#####Local IP:
192.168.0.1/24

VV----My LAPTOP WiFi Setup----VV
###########Local IP:
10.10.10.129/24 
###########Gateway: 
10.10.10.1

VV----Router #1 Setup----VV 
#####Local IP:
10.10.10.1/24
-----------------------Ping stop Laptop WiFi-<--------<----------<-----------<-------<Ping start ANDROID
AP#1<-WiFi->Laptop WiFi<-IPTABLE->Laptop Lan<-Wired->AP#2<-WiFi->ANDROID
Ping starts at ANDROID and stops at LAPTOP WiFi

    LAPTOP (IPTABLES -nvL) <------ Working properly
   pkts bytes target       prot opt in     out     source                 destination         
    2    168    ACCEPT     all  --  eth0   wlan0   192.168.0.0/24  10.10.10.0/24       
    0    0        ACCEPT     all  --  wlan0  eth0    10.10.10.0/24    192.168.0.0/24 


                     +-----------------------------------------------------------------------------------------------------------------------+


As you can see if you can read this diagram properly, I can't ping past my WiFi card on my laptop. This is that last hop until i reach A.P. #1, I can talk to the subnet 10.10.10.0/24 as I can ping 10.10.10.129/24 from 192.168.0.100. But I can not ping 10.10.10.1/24 from 192.168.0.100???? Please if you have any experience please let me know, I would appreciate it greatly. Thanks in advanced!!!

---

### Post by Chitown on 2012-10-24
BUMP

Here are the commands I have used thus fare to forward traffic between 
ETH0 and WLAN0:

Enable IP forwarding:

sysctl -w net.ipv4.conf.all.forwarding=1

Rules to allow packets to be forwarded between ETH0 and WLAN0:

iptables -I FORWARD -i eth0 -o wlan0 -s 192.168.0.1/24 -d 10.10.10.129/24 -j ACCEPT

iptables -I FORWARD -i wlan0 -o eth0 -s 10.10.10.129/24 -d 192.168.0.1/24 -j ACCEPT

UPDATE:
It seems as if the packets are making it out of the wifi card and to AP#1, I can see the traffic going out. The routing is broken some how coming back from AP#1 into the laptops WIFI ... Just some thoughts anyway??

---

### Post by Chitown on 2012-10-25
Here is a YouTube video, maybe this will explain my situation a bit better, also there is a picture of my network diagram at the end of the video if you need to see it. Thanks!!! I really some one can give me a hint here.....

youTube Link:
[http://www.youtube.com/watch?v=JBXN8xNPhn8&feature=youtu.be](http://www.youtube.com/watch?v=JBXN8xNPhn8&feature=youtu.be)

---

