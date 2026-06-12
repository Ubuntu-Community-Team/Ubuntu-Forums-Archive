---
title: "Disabled wireless after last update in Lucid Lynx"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by onako on 2012-05-21
Recently I started having problems with my wireless connection; actually, I think it was after one of the updates I made. Namely, the wireless icon in the top right corner is always with an exclamation mark and no wireless connections are shown (wireless disabled).

I tried following the steps from 
[http://ubuntuforums.org/showthread.php?t=943848](http://ubuntuforums.org/showthread.php?t=943848)

starting with 10), and it worked for a couple of days (even then the wireless icon had the exclamation mark), but the problem is back. The file I opened with 10), as in the above, has =true. Could you please help me with this?

---

### Post by onako on 2012-05-21
Any help? Note that I'm reluctant to apply the methods I find on the internet, as I'm not sure if the same reason caused the "wireless disable". If you think I should try one, please post which one exactly.

---

### Post by chili555 on 2012-05-21
> Note that I'm reluctant to apply the methods I find on the internetAnd you should be; especially posts written for Hardy in 2008. Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by onako on 2012-05-21
The first produced:


0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)


the second produced:


0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by chili555 on 2012-05-21
Please try this:```
sudo modprobe -r dell-laptop
sudo rfkill unblock all
```Now does your wireless work? If so, please blacklist dell-laptop:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```If not, post back with:```
lsmod | grep dell
```Thanks.

---

### Post by onako on 2012-05-21
After your first line, the wireless network within the range are shown. However, I'm unable to connect to my pass protected wireless. It is possible via my smartphone.

The output of your last suggestion is :

dell_wmi                2177  0

---

### Post by onako on 2012-05-21
OK, after the restart, my wireless is found and it works. However, note that the red exclamation mark is still present over the wireless icon. (Normally, only the full wireless icon is shown when wireless in on). And that was the case also the last time.

Was this an issue of the update, or is it something I did wrong? If the latter is the case, I'm curious to know what it might be that I did.

---

### Post by chili555 on 2012-05-21
Let's look again:```
lsmod | grep dell
rfkill list all
```Did you do this step?> sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exitSince it is dell-*wmi* that is loaded, perhaps blacklisting dell-*laptop* was ineffective.

---

### Post by onako on 2012-05-21
Command 

lsmod | grep dell

produces 

dell_wmi                2177  0 .

Command

rfkill list all

produces


1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

Command after "sudo su" does not produce anything. Strange thing is that it sometimes works, and sometimes not. Now I'm not sure if something is wrong with the router. Any thoughts?

---

### Post by chili555 on 2012-05-21
Does it scan?```
sudo iwlist eth1 scan
```If it scans without complaint or error, my next step would be the router.

---

### Post by onako on 2012-05-21
This is the output:
```

eth1      Scan completed :
          Cell 01 - Address: B0:48:7A:B5:9A:B8
                    ESSID:"TP-LINK_B59AB8"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:5/5  Signal level:-29 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD810050F204104A0001101044000102103B0001031047001000000000000010000000B0487AB59AB81021000754502D4C494E4B10230009544C2D57523934314E10240003322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523934314E100800020086103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 70:F1:A1:0D:0A:32
                    ESSID:"Connectify-me"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-70 dBm  Noise level:-94 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 02:26:26:21:EB:1D
                    ESSID:"Ad-hoc"
                    Mode:Ad-Hoc
                    Frequency=2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: BC:77:37:BC:27:36
                    ESSID:"WIN-K3UQS81NBA9-59520"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-78 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7B0050F204104A0001101044000102103B000103104700106403C525C85CCB4282E65EDA4D018B4110210011496E74656C20436F72706F726174696F6E10230014496E74656C2852292043656E7472696E6F285229102400012D104200012D1054000800010050F204000110110007544F42592D504310080002008C
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s


```

Does this mean I'll have to check the router? Note that I'm currently using a wired connection to the router that is wired "to the wall". So, the router also works, at least with a wire...

---

### Post by chili555 on 2012-05-21
> eth1      Scan completed :
          Cell 01 - Address: B0:48:7A:B5:9A:B8
                    ESSID:"TP-LINK_B59AB8"
                    [COLOR="Red"]Mode:Managed[/COLOR]
                    Frequency:2.442 GHz (Channel 7)
                    Quality:5/5  Signal level:-29 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    <snip>That's pretty weird. 'Managed' is usually the mode for the client wireless card; that is the card will be managed by the Master; i.e. router, that will set the bit rate, channel, etc. Here is the scan from my house, a bit redacted for brevity:> $ sudo iwlist wlan0 scan
[sudo] password for chili: 
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:62:8D:F7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"GBR1"  [COLOR="Red"]<-- my router[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    [COLOR="Red"]Mode:Master[/COLOR]
                    
          Cell 02 - Address: 00:1D:7E:F3:8C:56
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"MAHB" [COLOR="Red"]<---my neighbor Kathy[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    [COLOR="Red"]Mode:Master[/COLOR]
                    
          Cell 03 - Address: 00:13:46:16:40:6A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"default" [COLOR="Red"]<---my neighbor Champ[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    [COLOR="Red"]Mode:Master[/COLOR]               
          
I think you need to reset your router to Master, possibly also called AP mode. Please check.

---

### Post by onako on 2012-05-21
It doesn't work at all in ap mode. So, router is the problem, definitely?

---

### Post by chili555 on 2012-05-21
> **onako said:**
> It doesn't work at all in ap mode. So, router is the problem, definitely?Most likely. I'd try a new one from a Big Box Store that allows returns. My strong suspicion is that you won't want to return it because it will work.

---

### Post by onako on 2012-05-22
The same problem occurs with my friend's router, but it works fine at his place. So, I'll have to trace cables and connectors (since it sometimes works and sometimes not, this might be the actual problem now)

---

