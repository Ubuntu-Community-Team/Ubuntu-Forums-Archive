---
title: "Broadcom 43XX airforce one"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by AJB2K3 on 2008-12-15
2 question
1 How do I get this working on my encrypted modem.
2 How do I block the none encrypted modem in the area. (stopping my lappy from connecting to it.)

I can see secure connections I just cant connet to them.
BTW using the FWcutter method I think?
Says the 43XX is loaded in hardware drivers.

---

### Post by AJB2K3 on 2008-12-16
Can anyone help?
Ok Did a bit of searching and
iwconfig 
```
wlan0     IEEE 802.11bg  ESSID:"**********"  <blanked for privacy
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:19:7d:40:c6:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Should I give up and buy a new wifi card?


Edit its the 4318 card again.

---

### Post by Ayuthia on 2008-12-16
Have you tried to manually connect?  Also, what kind of encryption are you using?

You are most likely using the b43 driver because the Broadcom STA driver does not support your card and you would know it if you installed NDISwrapper.

If you are not sure about what kind of encryption you are using, please post or check:
```
sudo iwlist scan
```It will scan for wireless sites and also tell you what kind of encryption it is using.

---

### Post by AJB2K3 on 2008-12-16
```
 Cell 04 - Address: 00:1B:9E:97:17:9C
                    ESSID:"TalkTalkc5cfj"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/100  Signal level:-41 dBm  Noise level=-71 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000002bd7523585
                    Extra: Last beacon: 104ms ago

```
Yep I'm using the b43 via fwcutter.
Going through Wicd it just sits there saying obtaining ip address.
I have never had this truoble before using Talktalk whatever.

---

### Post by Ayuthia on 2008-12-17
> **AJB2K3 said:**
> ```
 Cell 04 - Address: 00:1B:9E:97:17:9C
                    ESSID:"TalkTalkc5cfj"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/100  Signal level:-41 dBm  Noise level=-71 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000002bd7523585
                    Extra: Last beacon: 104ms ago

```
Yep I'm using the b43 via fwcutter.
Going through Wicd it just sits there saying obtaining ip address.
I have never had this truoble before using Talktalk whatever.

Let's see if you can connect from the Terminal:
```
sudo iwconfig wlan0 essid TalkTalkc5cfj key <passkey>
sudo dhclient wlan0
```
Replace <passkey> with the password (without the <>).

---

### Post by AJB2K3 on 2008-12-17
> **Ayuthia said:**
> Let's see if you can connect from the Terminal:
```
sudo iwconfig wlan0 essid TalkTalkc5cfj key <passkey>
sudo dhclient wlan0
```
Replace <passkey> with the password (without the <>).

Says invalid argument for the passcode.

---

### Post by thepenguinisatlarge on 2008-12-17
This card works for Ubuntu 8.10, go to system --> Administration --> Restricted drivers

---

### Post by AJB2K3 on 2008-12-18
> **thepenguinisatlarge said:**
> This card works for Ubuntu 8.10, go to system --> Administration --> Restricted drivers
Don't have restricted drivers.
Only have windows drivers and hardware drivers.
Hardware drivers reports driver enabled.

---

