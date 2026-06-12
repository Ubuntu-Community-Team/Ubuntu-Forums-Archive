---
title: "Wireless Internet through terminal commands?"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by ffahog on 2009-02-06
I have an old laptop that I used to run Xubuntu on, until I got fed up with its slow speed. The CDrom connects to the computer through the PCMCIA card slot&#8212;for whatever reason, both PuppyLinux and DSL won't install through it. What I've found is that only alternate-install CDs will work.

I've seen that people sometimes 'build' a system by installing Ubuntu server and decided to try it. The installation went fine, but now the problem is that I cannot connect to the internet to install a GUI. Once I can get a GUI I should be set, but I'm having a hard time with only the command prompt.

What I need is to be able to connect to the internet. I have a Linksys WPC11 card in, which is read natively by Ubuntu 8.10. When I type iwconfig, the output is:

```

wlan0

IEEE 801.11b ESSID:""
Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7  RTS thr:off Fragment thr=2352 B
Power Management: off
Link Quality:0 Signal level:0 Noise level:0
```


Now, how can I connect myself to the wireless router using the terminal? I have the ESSID and password in front of me. This laptop has no wired ethernet connection, only this wireless reader.

Any help would be appreciated.

---

### Post by ffahog on 2009-02-07
bump. . .

Anyone here know how to connect a computer to wireless internet using the Ubuntu server command line?

---

### Post by kevdog on 2009-02-07
Yes, I wrote the guide which is linked to in my signature.

---

### Post by bikramac on 2011-05-21
try this, this might address your problem

sudo ifconfig wlan0 up (enable your wireless LAN)
sudo iwconfig wlan0 mode managed (change to manage mode)
sudo iwconfig wlan0 channel 11 (give chanel number)
sudo iwconfig wlan0 essid networkname (give ssid or network name)
sudo iwconfig wlan0 key FEFEFEFEFE (Encryption Key)

or for more help please refer [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Thank you
Bikram Acharya

---

