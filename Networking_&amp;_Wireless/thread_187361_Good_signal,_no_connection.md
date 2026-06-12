---
title: "Good signal, no connection?"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by livingword26 on 2006-06-02
I have been messing with several different distros trying to get one to work on my toshiba laptop. None so far. I have installed the new Ubuntu distro and no luck. I am recieving a strong signal, but cannot connect to the internet. I know absolutely nothing about Linux, but would like to learn. Any suggestions?

---

### Post by elamericano on 2006-06-03
Using encryption or authentication? Is ethernet connected simultaneously? Static IP or DHCP? Do you know the wireless card model? If by strong signal, you mean that it associated to an AP, that usually means the wireless module is not the problem.

---

### Post by livingword26 on 2006-06-03
[QUOTE=elamericano]Using encryption or authentication? Is ethernet connected simultaneously? Static IP or DHCP? Do you know the wireless card model? If by strong signal, you mean that it associated to an AP, that usually means the wireless module is not the problem.[/QUOTE]

Using the default 64bit encryptions that came with my 2wire dsl modem, encryption is enabled and number inserted. I don't know what you mean by "is ethernet connected simultaneously". DHCP. Atheros AR5005G Wirless Card. When you click on the "Connection Properties" icon on the task bar it shows and 81% signal and sending and recieving packets with Ath0. The "Wireless Assistant" Shows my network name (Essid), correct channel, link quality, and encryption, but it shows that the link failed.

---

### Post by livingword26 on 2006-06-03
**Additional Information**

Iwconfig:

Lo           No wireless extentions

eth0        No wireless extentions

ath0          IEE 802.11g          essid "2wire346" 
Mode:managed                  Frequency:2.437
Access Point:00:00:9e:ad:a3:a1
Retry: off          RTSthr: off           Fragmentthr: off
Power management: off              Link quality=49/54
Signal level=-46dBm            Noise level=-94dBm
Rx invalid nwid:93             Rx invalid crypt:0
Rx inavalid frag:0              Tx excess retries:0
Invalid misc:0              Missed beacon:0

sit0     No wireless extentions

---

### Post by livingword26 on 2006-06-03
Bump...Still hopefull

---

### Post by Taranis on 2006-06-03
I am having a similar problem.  
I used this helpful guide to get my driver and the network manager installed.
[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

 I can see my wireless network via network manager in linux.  I can connect via windows, but not by via linux.
I'm using a 2wire router/switch, DHCP, wep with standard encryption.
Now the standard encryption key is 10 digits.  In windows, the encryption key shows 8 numbers, although I can't remember what I put in.  (it might help if anyone knew how to figure out what that key in windows is...all i see it 8 dots.

Also, i'm not familiar with teh linux network manager in the above linked guide.  There are three options.  passphrase; hex;  asci;  how can i tell which i should use?

Thanks in advance if you have any ideas.

---

### Post by 12quality on 2006-06-04
I had a similar problem where I had a good signal (according to the gtkwifi applet), but it wasn't actually connecting.  I eventually solved the problem by typing 
```
sudo ifdown eth0
sudo ifup eth0
```
where in most cases eth0 would be replaced by ath0

i don't know why it didn't automatically connect, but it appears that Dapper handles this stuff much differently than Breezy did, as evidenced by the contents of /etc/network/ .

---

### Post by elamericano on 2006-06-04
Respond if any of that helped. When I said "ethernet connect similtaneously" I just meant if you have "wired" connection plugged in at the same time you are testing the wireless connection - it can complicate things.

Did you re-enter you WEP key? You will still associate and send data if the keys are wrong, but it will be useless data. (it's short, I know, but be sure.)

The atheros chipset is well supported. I use one myself. I'd recommend the NetworkManager package, which makes ssid selection simple and is good about initiating the DHCP at the right time.

---

### Post by livingword26 on 2006-06-05
The first time I installed ubuntu, I did not have an eth0 connection. I connected that later to download additional programs and updates to try to get the wireless running. I tried a couple of other distros and had no luck. I came back and reinstalled ubuntu with my ethernet hooked up. At the end of the installation it downloaded a couple of things, one of them I think was for my wireless card (cant remember the name). When I rebooted I installed network manager and knetwork manager and it worked.

---

