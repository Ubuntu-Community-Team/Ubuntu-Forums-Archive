---
title: "Intel 4965AGN on Ubuntu 10.10 64bit"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by rantunes on 2011-02-25
Hi, I'm running Ubuntu 10.10 64 bits on my Hp dv9000, with the wireless card Intel 4965AGN. I have read and tried so many bug fixes around this forum and on google, and I just can't get to make my card to work properly. I'm having the same symptoms as most people have with this card, with the difference that the solutions and seemed to work for them won't work for me. Most of the things are from threads from a couple years ago and I figure that my problem should be different from what they had back then, still I tried many different things.
I can connect to the router, but after sometime internet will get slow and I won't get any page to load, then I have to restart the connection. After I do that a dozen times, restarting the wireless card won't work anymore, so I have to restart my computer to get it back to work.

I'm not experient with linux, still learning. I tried a bunch of stuff already and none worked, one of the times I not sure what I did but I just couldn't start ubuntu on GUI mode, would just boot straight to the terminal, and I had to re-install it. I hope I can get some advices, I'm getting really frustrated. I love ubuntu and don't want to go back to windows, but I can't get anything done with my internet like that.

Thanks in advance guys.

---

### Post by chili555 on 2011-02-25
Let's take a look at where we are so far. Please reboot so we have a fresh start and then open Applications > Accessories > Terminal and run and post:```
dmesg | grep iwl
ls /etc/modprobe.d
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by rantunes on 2011-02-25
Thanks for answering. He it goes

```
dmesg | grep iwl
[   10.139412] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.139416] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   10.139503] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.139513] iwlagn 0000:02:00.0: setting latency timer to 64
[   10.139561] iwlagn 0000:02:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   10.180269] iwlagn 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.180436] iwlagn 0000:02:00.0: irq 47 for MSI/MSI-X
[   10.228570] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
[   10.284541] phy0: Selected rate control algorithm 'iwl-agn-rs'

ls /etc/modprobe.d

alsa-base.conf              blacklist-oss.conf
blacklist-ath_pci.conf      blacklist-watchdog.conf
blacklist.conf              intel-5300-iwlagn-disable11n.conf
blacklist-firewire.conf     nvidia-graphics-drivers.conf
blacklist-framebuffer.conf  sl-modem.conf
blacklist-modem.conf

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"HOO-HAA"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:29:69:B2:51   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:69:B2:51
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"HOO-HAA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000043b56cc33a
                    Extra: Last beacon: 90ms ago
                    IE: Unknown: 0007484F4F2D484141
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706545720010B10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050700000000000000000000000000000000000000
          Cell 02 - Address: 00:1A:70:7C:BC:4D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"DCAINE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000009bbf1fc4b28
                    Extra: Last beacon: 7360ms ago
                    IE: Unknown: 0006444341494E45
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:19:5B:57:B6:0B
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Alderaan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000007a38f0a88ff
                    Extra: Last beacon: 7170ms ago
                    IE: Unknown: 0008416C64657261616E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608071B0000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E101AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340807030000000F000000000000000000000000000000
                    IE: Unknown: DD820050F204104A0001101044000102103B000103104700100D51ADD6448D3FD689F12E7E7E6453171021000E442D4C696E6B2053797374656D73102300074449522D3635351024000541312F4132104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020000
          Cell 04 - Address: B0:E7:54:06:A0:A1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"dezo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ae0b686181
                    Extra: Last beacon: 7350ms ago
                    IE: Unknown: 000464657A6F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

```

---

### Post by chili555 on 2011-02-25
Your readings look really good except:> wlan0     IEEE 802.11abgn  ESSID:"HOO-HAA"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:29:69:B2:51   
          [COLOR="Red"]Bit Rate=1 Mb/s [/COLOR]  Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
Please do:```
sudo iwconfig wlan0 rate 54M
iwconfig
```Did the 54Mb/s rate stick? If so, we can hopefully make it permanent. Moreover, does it help?

Have you tried other channels in the router? You may have radio frequency interference on channel 1.

---

### Post by rantunes on 2011-02-25
Before I even did sudo iwconfig wllan0 rate 54m like you said, I just did again an iwconfig, and it showed 54m.

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"HOO-HAA"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:29:69:B2:51   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

So I think that when I run the code before, was a "bad moment" for the connection, even tho I had just rebooted. I don't think it would be a radio interference or anything like that, I had used that same computer without changing any router settings for the network for months/years. I had vista on this computer until my HDD crashed 2 weeks ago and I just installed Ubuntu instead of windows, and thats when the problems starts. My wife computer on windows and my phone or the PS3 doesn't experience any problems ever with it, so I don't think I would benefit of a channel change, specially because right now I'm with the computer a few steps away from the router, and still get the problem. I'm postive it got to be some driver issue, even tho you said everything else looks good. I appreciate a lot you are trying to help tho.

---

### Post by chili555 on 2011-02-26
This will be a temporary fix; upon reboot it will revert. If this helps, we can write one file to make it permanent.```
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=0 swcrypto=1
```Any improvement?

---

### Post by rantunes on 2011-02-27
I didn't had a chance yet to make sure it is better. This weeked I just had a chance to use it for a few minutes but it didn't showed any issues. I'll post back ln a couple days after I find out if it really got better. Thank you

---

### Post by rantunes on 2011-03-01
Thanks a lot for your help, I think my issue is solved. I haven't got disconnected at all today, I'm not sure exactly what the code did but it worked. Would I have to do it every time I reboot?
Thanks again

---

### Post by chili555 on 2011-03-02
You would either have to do it on every boot or write a .conf file:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn 11n_disable=0 swcrypto=1
```Proofread, save and close gedit. Also remove one file:```
sudo rm /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf
```On reboot, you should be all set.

---

### Post by florianderouck on 2011-05-05
> **chili555 said:**
> This will be a temporary fix; upon reboot it will revert. If this helps, we can write one file to make it permanent.```
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=0 swcrypto=1
```Any improvement?

Thanks so much. Unbelievable. Just when I lost all hope this solution fixes the issue completely. 

I am very gratefull Chili555.

---

### Post by lazychris2000 on 2011-11-30
I would also like to thank you.  I got my dv9000 to connect to 802.11n networks with that quick fix.  Thanks again!

---

