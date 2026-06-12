---
title: "hp elitebook8530p+Cisco Aironet 350"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by geamantan on 2009-03-22
Hey all,


Excuse me if I double post (i didn't find anything similar tho). I just installed an 8.10 on my HP EliteBook 8530p and have trouble with hooking up to my home AP which is a Cisco Aironet 350 802.11b oooold model. Thing is that although in Windoze works great, Ubunto doesn't even see my AP. It sees though all my neighbors' routers, mine - not. I'm q freshman in Linux and stuff, I looked allover, but still have no clue into how should I fix it... Any advice?? Thanks in advance!!

Geam.

---

### Post by chili555 on 2009-03-22
Please see post #8 here:  [http://ubuntuforums.org/showthread.php?t=917267&highlight=aironet](http://ubuntuforums.org/showthread.php?t=917267&highlight=aironet)

Post back if that doesn't help.

---

### Post by geamantan on 2009-03-22
Hey, and thanks for replying. I read that topic before, but is of no help, as my card is an integrated one, which actually works fine in finding wireless networks _others_ than mine. The problem I have is that my AP is not seen by my laptop, so I have to define the connection manually. I try to do that but the authentication fails. Any suggestions?? I have no control over the AP, it has been pre-configured, works fine in Windows (sorry to say that). Thanks again for help.

---

### Post by chili555 on 2009-03-22
I had an Aironet integrated into a Thinkpad T40 (until I dis-integrated it and integrated an Intel 2915ABG) and I needed the blacklist fix for mine to work properly. I think it's coincidental that the post I referred you to is concerning a PCMCIA card. At their hearts, they all use the *airo.ko* module.

Please post the output from:```
sudo iwlist eth1 scan
```Substitute your wireless interface if it's not eth1.

---

### Post by geamantan on 2009-03-22
Here you go:

tudor@kagemusha:~$ sudo iwlist eth1 scan
[sudo] password for tudor: 
eth1      Interface doesn't support scanning.

tudor@kagemusha:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:51:6E:F2:5B
                    ESSID:"Foreigners-Inside"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/100  Signal level:-88 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000002bc9ffc4c9
                    Extra: Last beacon: 1620ms ago


Thanks,
Tudor

---

