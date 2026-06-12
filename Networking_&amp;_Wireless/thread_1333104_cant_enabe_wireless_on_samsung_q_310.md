---
title: "cant enabe wireless on samsung q 310"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by 5PUTN|K on 2009-11-21
hi fellas here is my problem i cant enable wireless on my samsung q310 latop  in windows i can enable it using Fn+F9 but some of the Fn shortcuts dont work properly in ubuntu and Fn+F9 seems to be one of them... i tried enabling it using the network icon on the panel but nothing happens when i click the enable wireless box i suppose the wireless driver doesnt work any more here is the output i get when i run iwconfig

```
deniz@deniz-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

deniz@deniz-laptop:~$ 

```and also i guess this is the device i need to get working <<Intel Corporation Wireless WiFi Link 5100>>

```

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
deniz@deniz-laptop:~$ 


```any ideas ??  i hate having to use windows   T_T

---

