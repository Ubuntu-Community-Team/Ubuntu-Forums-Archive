---
title: "Wireless not working with ubuntu 8.04/8.10 and 2wire DSL modem"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by lcohan on 2009-04-10
Hi there,
Anyone else lost wireless connection after switching DSL modems?

I ran ubuntu 8.04 for quite some time (1+year) with Dlink DWL G132 wireless but after switching my DSL wireless modem to a 
"2wire" brand DSL modem ubuntu is dead...I mean the wireless connection is dead which is the same considering the internet connection is gone.(of course I updated the wpa/wpa2 wireless key). I unistalled everything including ubuntu 8.04 and got 8.10 thinking that wireless improved but...still dead after one day of trying it all. 

The network driver is installed and configuration is the same as before (with WPA/WPA2 key - DHCP), and I can see it attempting to connect on both my DWL lights flickering and modem wireless but nothing hapens. Of course if I plug in a network cable is all pinky and working but that's not what I realy expect especialy it was working before.
Any ideas/suggestions much appreciated.
BTW - the same hardware works like a chanrm with Win XP SP2.

---

### Post by superprash2003 on 2009-04-11
post output of **iwlist scanning** from the terminal

---

### Post by lcohan on 2009-04-11
Here's the iwlist cut short to only my own wireless network. I noticed that the wpa password I put in is converted to some hex chars if I check box "show password" and is this natural? I'm not sure if win xp does the same thing when you key in the wpa password. 

here's iwlist from my ubuntu 8.10
cohan@cohan:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 02 - Address: 00:24:56:BC:EA:A1
                    ESSID:"BELL778"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
 
And just to mention this exact configuration, hardware,dlink DWL G132 card and drivers worked fine with my older DSL modem wep authentication. I think is something with either authentication or IP on the new config.

---

### Post by lcohan on 2009-04-11
I know this card is pretty old (2005) and I'm willing to buy a new wireless card for my desktop but do I have any guarantee that will work? Is there anything that we know is 100% working? I'll buy that card if anyone has details about drivers and how to install configure it...

---

### Post by Moman19 on 2009-04-11
> **lcohan said:**
> Hi there,
Anyone else lost wireless connection after switching DSL modems?

I ran ubuntu 8.04 for quite some time (1+year) with Dlink DWL G132 wireless but after switching my DSL wireless modem to a 
"2wire" brand DSL modem ubuntu is dead...I mean the wireless connection is dead which is the same considering the internet connection is gone.(of course I updated the wpa/wpa2 wireless key). I unistalled everything including ubuntu 8.04 and got 8.10 thinking that wireless improved but...still dead after one day of trying it all. 

The network driver is installed and configuration is the same as before (with WPA/WPA2 key - DHCP), and I can see it attempting to connect on both my DWL lights flickering and modem wireless but nothing hapens. Of course if I plug in a network cable is all pinky and working but that's not what I realy expect especialy it was working before.
Any ideas/suggestions much appreciated.
BTW - the same hardware works like a chanrm with Win XP SP2.

Have you tried WEP instead of WPA?  I'm running Xubuntu on an old Toshiba laptop.  While it runs great with my 2Wire DSL via WIFI with WEP security, I cannot get it to run WPA no matter how hard I try.  Perhaps that's the issue you're having.

I too, don't have this issue with Win XP, so I doubt it's the modem.

---

### Post by lcohan on 2009-04-12
Thanks and indeed that did it indeed!!
If I think that’s only other thing beside the modem that I changed but....there's definitely something else wrong with ubuntu because after authenticating with WEP, connecting with WEP to the internet through wireless and being asked to re-start now is getting stuck on "Starting Bluetooth" but why??? I did not configured any blue tooth...but wireless network that was working before the restart so anyone has any clue what’s going on?
I did a few re-installs and configured/connected to my wireless LAN successfully but got stuck over and over at the same restart "Starting Bluetooth" with same results :(:(:(:(:( so...maybe it's less costly to use Windows XP after all...

---

