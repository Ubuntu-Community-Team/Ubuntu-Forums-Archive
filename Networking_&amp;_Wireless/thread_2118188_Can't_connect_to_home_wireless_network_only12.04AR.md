---
title: "Can't connect to home wireless network only/12.04/AR9287"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by keyshawn on 2013-02-20
I have had my laptop (Acer 5560-7414) with ubuntu 12.04 installed for 8 months, I haven't made any network hardware changes since I bought my laptop. 

My wireless network is set up by my router: linksys WRT54G (v5) v1.02.7 router. 

My problem: 
Within the past 24 hours, I'm suddently no longer able to connect to my home wireless network. When attempting to connect to it through the network manager, I receive message that says, "wireless network authentication required" and asks to insert my password. I've verified my password is correct and click ok, the icon in the upper right hand corner rotates for a minute, then the message appears again. I've typed in my password manually to double check the password is correct and still receive the message and unable to connect to the wireless network. 

In the past, I'd experience this problem about once every couple weeks, would click ok, and then able to reconnect to my wireless network. 

I am able to successfully connect to each of my next door neighbor's wireless networks. More puzzling is that my phone (an android) is able to connect to my home wireless network without any problems like normal. 

HERE is the syslog output while I am trying to connect to my wireless network, egged. 
[http://pastebin.ca/2316700](http://pastebin.ca/2316700)

I have already unplugged my cable modem and my router, waited a couple minutes, plugged them back in;  had same problem as described above. I've also rebooted the laptop and still experience the same problem. 


Also included is my information from the sticky thread -http://ubuntuforums.org/showthread.php?p=6183681 

1. Acer 5560-7414. 

2. lspci:
Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)

3. iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```4. lsmod 
[http://pastebin.ca/2316693](http://pastebin.ca/2316693)


5. dmesg 
 [http://pastebin.ca/2316699]("http://pastebin.ca/2316694") 

6. 
$ sudo lshw -C network
[http://pastebin.ca/2316694](http://pastebin.ca/2316694)

7. iwlist scan: 
I am able to connect to my neighbors' wireless network - ESSID:"2WIRE944" and 2WIRE858. 
'egged' is my home wireless network that I am unable to connect to. 

[http://pastebin.ca/2316698](http://pastebin.ca/2316698)


8. Ubuntu 12.04.2 LTS
9. 3.2.0-38-generic-pae i686

---

### Post by keyshawn on 2013-02-22
I finally fixed this by changing my wifi network password and changing my security from wpa1 personal to wpa2 personal...

---

