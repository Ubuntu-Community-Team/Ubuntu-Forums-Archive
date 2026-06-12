---
title: "Wifi (ath9k, 12.10) really slow, no solution found yet"
date: 2012-11-03
forum: Networking &amp; Wireless
---

### Post by beerbelly on 2012-11-03
Hi all,

After a couple of laptops using Broadcom wifi I carefully picked out a system without it. Unfortunately, I'm in trouble again. It's not an uncommon one, it's just that none of the solutions I've seen so far does the trick for me.

Problem: my wireless internet connection is extremely slow (averages <50K); even pages on this forum don't load completely half of the time.

System: Acer Aspire S3 Ultrabook, using the ath9k driver.

Now, I've tried all solutions I could find the past few days (a lot of which came from Wild Man), but none of them worked. I've tried turning of the hardware encryption trick (options ath9k nohwcrypt=1), added 8.8.8.8 etc. to my DNS entries and I have compiled and installed compat-wireless (3.6 stable)... until now, my speeds stay extremely low.

Symptoms are slow overall speeds (<50K) and going down and up again completely (stalling). Moving closer to the AP seems to help for a short time, but downloading speed then quickly drops again. Speedtest.net shows the same: speed starts out okay, but then keeps on dropping and dropping.

Below is the output of some commands to give insight in the current situation. I sure hope anyone (Wild Man?) is willing to help, working on my brand new system is not a fun thing to do now. Rebooting to Windows is neither.

Problem and (not working for me) solutions are also found here: [http://www.linlap.com/wiki/acer+aspire+s3](http://www.linlap.com/wiki/acer+aspire+s3)

Thanks,

Jeroen

Output for iwconfig:
```
wlan0     IEEE 802.11abgn  ESSID:"Galli"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:F2:C3:F6:28   
          Bit Rate=1 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:54  Invalid misc:170   Missed beacon:0

lo        no wireless extensions.
```

Output for rfkill:
```
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
```

Output for sudo lshw -class network: 
```
*-network               
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 84:4b:f5:74:db:fb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-17-generic firmware=N/A ip=10.0.0.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:c0400000-c047ffff memory:aff00000-aff0ffff
```

---

### Post by dreKion on 2012-11-21
same problem

---

### Post by beerbelly on 2012-11-23
No experts in the house? Perhaps this will trigger: I took my laptop to my workplace today and noticed a significant increase in wireless speed. So maybe it's not really my Atheros card that's giving me trouble directly, but the connection between my card and the AP.

I compared the output of the next commands (ran them at work and then at home):
```

ip addr
iwconfig wlan0
lshw -C network
nm-tool
iwlist wlan0 scan
lsmod | grep ath9k
lspci -v

```

A few things stood out:
```

iwconfig wlan0
	Work: 	Frequency: 2.462 GHz
		Bit Rate=130 Mb/s
		Power Management: off
		Signal level=-52 dBm
	Home: 	Frequency: 2.432 GHz
		Bit Rate=270 Mb/s
		Power Management: on
		Signal level=-42 dBm

lshw -C network
	Work: 	driverversion=3.5.0-17-generic
	Home:	driverversion=3.5.0-18-generic

iwlist wlan0 scan
	Work:
		IE: IEEE 802.11i/WPA2 Version 1
		    Group Cipher : TKIP
		    Pairwise Ciphers (1) : CCMP
		    Authentication Suites (1) : PSK 
		IE: WPA Version 1
		    Group Cipher : TKIP
		    Pairwise Ciphers (1) : TKIP
		    Authentication Suites (1) : PSK

	Home:
		IE: WPA Version 1
		    Group Cipher : TKIP
		    Pairwise Ciphers (1) : TKIP
		    Authentication Suites (1) : PSK
		IE: WPA Version 1
		    Group Cipher : TKIP
		    Pairwise Ciphers (1) : TKIP
		    Authentication Suites (1) : PSK

```

I have no idea what it all means, but especially the different drivers being used seem like a place to start.

Did some test on speedtest.net and at work things were looking as expected. At home, one server gives me 55 Mbps (nice) while the other (same city) only goes up to a download speed of 1 Mbps (not so nice). Watching a video on Youtube has me waiting for buffering all the time and even loading forum pages here takes forever.

Anyone? Any clues?

---

### Post by varunendra on 2012-11-24
> **beerbelly said:**
> Anyone? Any clues?
Umm.. I'll try if you don't mind. If I failed, at least the thread bumping may cry out to WildMan to come to rescue :)

> 
iwconfig wlan0
..
        Power Management: [COLOR=Red]**on**[/COLOR]
 First thing I'd try is
```
sudo iwconfig wlan0 power off
```
Although I'm pretty sure it'll do nothing since it was already off in your first post. But keeping the pm off won't hurt the rest of troubleshooting.

This may be misleading -
> 
lshw -C network
    Work:     driverversion=3.5.0-[COLOR=Red]**17**[/COLOR]-generic
    Home:    driverversion=3.5.0-[COLOR=Red]**18**[/COLOR]-generic

It suggests to me that you had a kernel upgrade in the workplace 'After' trying the commands, which reflected at home when you retried them again. As such, it should be same at your workplace now.

However, this seems to me a more important difference -
> 
iwlist wlan0 scan
    Work:
        IE: IEEE 802.11i/**WPA2** Version 1
..
    Home:
        IE: [COLOR=Red]**WPA Version 1**[/COLOR]
..
Change the encryption type to WPA2-only in your router. Although I guess it should not be related with speeds (only ease of authentication), but still let's try and see if it can help. Also make sure there are no funny firewall or filtering or address translating rules in the router.

And try all of the above while keeping the "nohwcrypt=1" option enabled for ath9k.

If none of this helps, post back (from home, and all of the above applied) -
```
ifconfig
nm-tool
iwconfig
iwlist scan
dmesg | grep ath
```

---

### Post by Linuxisfast on 2012-11-25
Turning off 802.1N in routers fixes this issue for most.

---

### Post by beerbelly on 2012-11-25
Hi varunendra,

I appreciate the help, thank you.

I've addressed your points in order:

- Power Management has been switched of (checked with iwconfig wlan0), as you expected that really didn't change anything.

- I'm not sure (can check on Monday) but I guess you're right about the driver version; that should not change just like that.

- Unfortunately I made a mistake when copying the iwlist output; my home network (the troublesome one) was incomplete. It should've also shown a WPA2 entry. My apologies for this. I did however try to change this setting in my router, and I must say that my connection seems faster but especially more stable (less stalls) than before. Differences are shown in the iwlist outputs below, first command (only WPA2/AES) is the stable, faster one. I've taken the liberty of commenting out some lines (unknowns).
```

WPA2-PSK [AES] (seems stable and fast)
iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:26:F2:C3:F6:28
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"Galli"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000005b2e6b6
                    Extra: Last beacon: 9996ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

WPA-PSK [TKIP] + WPA2-PSK [AES] (unstable, stalls large downloads)
iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:26:F2:C3:F6:28
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"Galli"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000013ba191
                    Extra: Last beacon: 11456ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```

So, all in all things look a lot better now. Making sure nohwcrypt=1 and turning off Power Management didn't seem to do much, but changing to WPA2/AES only seems to change a lot.

I don't want to get excited to fast, but for now you were a great help. If things turn bad again, I'll report back in.

Thanks a lot!

---

### Post by varunendra on 2012-11-25
WPA/WPA2 mixed mode has a very bad reputation here. Causes a lot of authentication problems. So whether it helps or not, keep the encryption to WPA2-only. This is one of the very few things I can recommend with confidence.

Although I must say that I didn't expect any speed gains with that. If it really proves to be helping speed improvement, it will be something new to my knowledge (which is not much anyway).

However, if you notice speed drop-outs or lags after an approximately fixed time of idleness, you can blame it to power management. Keep it turned off! If it turns on after reboot, there are ways to make it permanent.

What *Linuxisfast* suggested above, is also helpful often in cases where the speed drops during large downloads or video streaming etc. (in essence, whenever there is a large amount of fast and continuous traffic).
*[COLOR="DarkRed"][Edit: oops! I had nohwcrypt=1 in mind. The N-channel issue, when and if arises, causes a permanent speed crippling issue - like your original problem was..][/COLOR]*

These are a few things I've noticed over time by looking at such problems and their solutions here, but only feedbacks from real users like you can finally decide if these are facts or just my fallacies.

So.., I'll be eager to know how stable it proved to be.

---

### Post by beerbelly on 2012-11-26
So, I'm back... unfortunately, the improvement I thought I saw was temporary. As far as I can see now nothing much has changed. At times a large download (or HD video on Youtube) comes in at >2MB/sec whilst downloading the same file or video later on results in 1MB/sec peaks and complete stalls (of 20 secs sometimes). Loading a page like this one might go smoothly one minute, whilst it takes forever a minute later. So, the connection is not slow at all times but could best be described as terribly unstable. That also makes it hard to test whether a solution works or not.

Back to the drawing board, I guess. @varunendra: below is the fresh output of the commands you asked for. All changes we talked about have been applied, and still - AFAIK - in effect. Again, any help or suggestions are much appreciated!
```

$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:474686 (474.6 KB)  TX bytes:474686 (474.6 KB)

wlan0     Link encap:Ethernet  HWaddr 84:4b:f5:74:db:fb  
          inet addr:10.0.0.12  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:637054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:923086335 (923.0 MB)  TX bytes:51579156 (51.5 MB)
```
```
$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Galli] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        84:4B:F5:74:DB:FB

  Capabilities:
    Speed:           216 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Galli:          Infra, 00:26:F2:C3:F6:28, Freq 2462 MHz, Rate 54 Mb/s, Strength 81 WPA2

  IPv4 Settings:
    Address:         10.0.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             10.0.0.1
```
```
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Galli"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:F2:C3:F6:28   
          Bit Rate=243 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:346  Invalid misc:3333   Missed beacon:0
```
```
$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:F2:C3:F6:28
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"Galli"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f14d5a23b
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000547616C6C69
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B071F00000000000000000000000000000000000000
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B00010310470010688020C23D4665FE514A6E40342AB57F1021000D4E4554474541522C20496E632E10230009574E5233353030763210240009574E523335303076321042000230311054000800060050F20400011011000E5A4947474F20576972656C657373100800020084
                    IE: Unknown: DD090010180203F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B071F00000000000000000000000000000000000000
```
```
[    1.982532] ath: EEPROM regdomain: 0x6c
[    1.982536] ath: EEPROM indicates we should expect a direct regpair map
[    1.982539] ath: Country alpha2 being used: 00
[    1.982540] ath: Regpair used: 0x6c
[    2.003619] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    2.004117] Registered led device: ath9k-phy0
```

---

### Post by varunendra on 2012-11-26
> **beerbelly said:**
> ..the improvement I thought I saw was temporary.
- like I guessed. However, keep the encryption to WPA2-only. Based on your earlier iwlist scan result, try a fixed bitrate -
```
sudo iwconfig wlan0 rate 54M
```

or, if above doesn't help, -
```
sudo iwconfig wlan0 rate 54M auto
```

Also, does your support N-chanel? If yes, try disabling it as *Linuxisfast* suggested before.

All these while keeping PowerManagement off and *nohwcrypt=1* option enabled. To check that, you can use -
```
cat /sys/module/ath9k/parameters/nohwcrypt
```
It should return "1".

---

### Post by beerbelly on 2012-11-27
Thanks again, I've set max bit rate to 54 MB/sec and checked if it was set okay. I also checked the value of nohwcrypt, and is indeed 1.

I'll give it another day, see what happens...

*edit* Also found a way to get the Netgear router to stop providing N-channel like Linuxisfast suggests. It was matter of setting max speed to 54 or even 145 Mbps, where it was on 300 (enabling N-channel support). Speed seems okay, as well as stability, but I'd have to test a bit longer and in everyday use to make sure it is not a temporary thing again.

---

### Post by beerbelly on 2012-11-30
Varunendra, Linuxfast, you guys are the best... after a few days of testing in the field, I dare to say my wifi connection is stable and much, much faster than it was before.

Kudos to you both, as I feel the combination of both your suggestions lead to this result. Many thanks!

---

### Post by mharpe2 on 2013-04-27
I have been having the same problems and trying the recommendations and finally found a solution.  **I plugged my on Verizon Actiontec modem into my Comcast/Xfinity Arris TG862.**  I'm now connected and browsing using the Verizon's modem wifi.  

Here how to do it:
1. make sure the POS modem is powered on and your other wifi router is powered off.
2. connect cat 5 between them.
3. power on the the other wifi router. (the verizon modem automatically configured itself as an access point, I don't know what your modem will do, you may have to adjust the settings manually)
4. connect to the Wifi provided by the other WiFi router.

I'm fairly certain that the Xfinity modem/router is a POS, not unlike comcast itself. it seems that many people are having problems with the Wireless N on the Arris TG862.

Good luck.

---

