---
title: "Wna1100(Netgear N150) using usb driver and only reporting speed of 1 Mb/s"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by jhyder on 2011-09-06
I am seriously tired of looking for a solution to this by looking for people having the same problem,so now it's time to start a new thread......
iwconfig output:

 jared@jared-ubuntu ~ $ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"belkin.f8c"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:86:3B:28: DF:8C   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0
This is really starting to **** me off...
Any ideas/solution? :confused: 
I want my 150 Mb/s!!!!!!!!!!!!! :mad: :(
device id is 0846:9030 NetGear, Inc.

---

### Post by praseodym on 2011-09-06
Update the firmware:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1.tar.gz
sudo tar xvf ath_htc_firmware-1.tar.gz -C /lib/firmware 
```
and set the bit rate manually:

```
sudo iwconfig wlan1 rate auto
```
Reboot and check again. I recommend using WPA2-AES (CCCMP) encryption if possible.

---

### Post by jhyder on 2011-09-06
> **praseodym said:**
> Update the firmware:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1.tar.gz
sudo tar xvf ath_htc_firmware-1.tar.gz -C /lib/firmware 
```
and set the bit rate manually:

```
sudo iwconfig wlan1 rate auto
```
Reboot and check again. I recommend using WPA2-AES (CCCMP) encryption if possible.
That firmware did nothing...neither did the others I tried. I changed router config to wpa2 only(not mixed mode) it is using aes...Same outcome....maybe the 3.0 kernel would be a better option?
Or maybe you could inform me of the proper way to do a modeswitch...I read in one post that this card uses mass storage as default(which sounds ridiculous for a wifi card),but it does list usb as the driver.

here is dmesg:

 jared@jared-ubuntu ~ $ dmesg | grep ath
[    2.310367] device-mapper: multipath: version 1.2.0 loaded
[    2.310369] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.925083] usb 2-2: ath9k_htc: Transferred FW: ar9271.fw, size: 51312
[   14.191038] usb 2-2: ath9k_htc: HTC initialized with 33 credits
[   14.626290] ath: EEPROM regdomain: 0x60
[   14.626292] ath: EEPROM indicates we should expect a direct regpair map
[   14.626295] ath: Country alpha2 being used: 00
[   14.626296] ath: Regpair used: 0x60
[   14.631818] Registered led device: ath9k-phy0::radio
[   14.631833] Registered led device: ath9k-phy0::assoc
[   14.631850] Registered led device: ath9k-phy0::tx
[   14.631862] Registered led device: ath9k-phy0::rx
[   14.631865] usb 2-2: ath9k_htc: USB layer initialized
[   14.631893] usbcore: registered new interface driver ath9k_hif_usb

jared@jared-ubuntu ~ $ sudo iwconfig wlan1 rate auto
[sudo] password for jared: 
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan1 ; Operation not supported.


jared@jared-ubuntu ~ $ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"belkin.f8c"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:86:3B:28:DF:8C   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:28   Missed beacon:0

---

### Post by nm_geo on 2011-09-06
jhyder I am testing one a USB that Netgear N150 right now..

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan%d    IEEE 802.11bgn  ESSID:"gfk"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: C0:C1:C0:7C:42:A8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:381   Missed beacon:0

```

Although my router only has 54mbs..
How did you install the ath9k_htc?

---

### Post by nm_geo on 2011-09-06
**Yours**
```
jared@jared-ubuntu ~ $ dmesg | grep ath
[    2.310367] device-mapper: multipath: version 1.2.0 loaded
[    2.310369] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.925083] usb 2-2: ath9k_htc: Transferred FW: ar9271.fw, size: 51312
[   14.191038] usb 2-2: ath9k_htc: HTC initialized with 33 credits
[   14.626290] ath: EEPROM regdomain: 0x60
[   14.626292] ath: EEPROM indicates we should expect a direct regpair map
[   14.626295] ath: Country alpha2 being used: 00
[   14.626296] ath: Regpair used: 0x60
[   14.631818] Registered led device: ath9k-phy0::radio
[   14.631833] Registered led device: ath9k-phy0::assoc
[   14.631850] Registered led device: ath9k-phy0::tx
[   14.631862] Registered led device: ath9k-phy0::rx
[   14.631865] usb 2-2: ath9k_htc: USB layer initialized
[   14.631893] usbcore: registered new interface driver **ath9k_hif_usb**
```

**Mine **

```
dmesg | grep ath
[    1.004471] device-mapper: multipath: version 1.2.0 loaded
[    1.004474] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.016904] usb 1-6: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   15.251885] ath9k_htc 1-6:1.0: ath9k_htc: HTC initialized with 33 credits
[   15.549769] ath9k_htc 1-6:1.0: ath9k_htc: FW Version: 1.3
[   15.549773] ath: EEPROM regdomain: 0x60
[   15.549775] ath: EEPROM indicates we should expect a direct regpair map
[   15.549780] ath: Country alpha2 being used: 00
[   15.549782] ath: Regpair used: 0x60
[   16.279814] Registered led device: ath9k_htc-phy0
[   16.279819] usb 1-6: ath9k_htc: USB layer initialized
[   16.279849] usbcore: registered new interface driver **ath9k_htc**

```

---

### Post by jhyder on 2011-09-06
> **nm_geo said:**
> jhyder I am testing one a USB that Netgear N150 right now..

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan%d    IEEE 802.11bgn  ESSID:"gfk"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: C0:C1:C0:7C:42:A8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:381   Missed beacon:0

```

Although my router only has 54mbs..
How did you install the ath9k_htc?
Fresh install of Natty using  [http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1.tar.gz) firmware

jared@jared-ubuntu ~ $ lsmod | grep ath
ath9k_htc              61400  0 
mac80211              294370  1 ath9k_htc
ath9k_common           13851  1 ath9k_htc
ath9k_hw              323077  2 ath9k_htc,ath9k_common
ath                    23773  2 ath9k_htc,ath9k_hw
cfg80211              178528  3 ath9k_htc,mac80211,ath

---

### Post by nm_geo on 2011-09-06
Here is what I found..

ID 0846:9030 NetGear

    Bought one
    Downloaded the driver installer
    [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/)
    Execute the .deb packet
    Had already connected the WiFi adapter
    Needed the htc_9271.fw (firmware)
    Got it here [http://wireless.kernel.org/download/htc_fw/](http://wireless.kernel.org/download/htc_fw/)   get latest version
    Moved it to /lib/firmware
    
    Rebooted It works my wireless only had g speeds

---

### Post by jhyder on 2011-09-06
> **nm_geo said:**
> Here is what I found..

ID 0846:9030 NetGear

    Bought one
    Downloaded the driver installer
    [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/)
    Execute the .deb packet
    Had already connected the WiFi adapter
    Needed the htc_9271.fw (firmware)
    Got it here [http://wireless.kernel.org/download/htc_fw/](http://wireless.kernel.org/download/htc_fw/)   get latest version
    Moved it to /lib/firmware
    
    Rebooted It works my wireless only had g speeds
Tried that installer,seen that exact same post 20 times...did not work...1 Mb/s ....usb driver still listed

---

### Post by nm_geo on 2011-09-06
Ok, sorry that was what worked for me in Lucid, Maverick, Natty and Oneiric.. There is something very different in our dmesg lists..

I generally run the newest kernel my version will run but even with 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
2.6.38-10-generic

I had to do the installer and firmware..

---

### Post by nm_geo on 2011-09-06
You know I think the 

3.0.0-0300rc2-generic on Natty might just be the ticket for you.  As I looked around i could not see the installer on my Natty ..

---

### Post by jhyder on 2011-09-06
I finally got it fixed....First I unloaded the modules, then I moved these firmwares ar7010_1_1.fw,ar9170.fw,ar9170-1.fw and ar9271.fw.....(I will not delete them..just to be on the safe side)
I already had the htc_9271 firmware from a previous attempt,so I used the installer again,rebooted and now all is well :)
Thanks for all the help...marking as SOLVED......:guitar: :P :P

---

### Post by nm_geo on 2011-09-06
Excellent i been updating all my versions here .. You did well Enjoy ,,
By the way what speed are you getting?  Do you have N router? Curious if you are close to 150..

---

### Post by jhyder on 2011-09-06
> **nm_geo said:**
> Excellent i been updating all my versions here .. You did well Enjoy ,,
By the way what speed are you getting?  Do you have N router? Curious if you are close to 150..
I'm getting 72 Mb/s,(screenshot in my last post)it would be higher...but I'm about 50 ft. from my wireless-N router(using a wok-fi rig,I get anywhere from 36/70-55/70) I don't have direct line of site or it would be about 65/70 or so.....

 jared@jared-ubuntu ~ $ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"belkin.f8c"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:86:3B:28:DF:8C   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:41   Missed beacon:0

---

### Post by nm_geo on 2011-09-06
Not bad in fact very good.. Lots better than 1mbs I bet.. Be Well

---

### Post by walt.smith1960 on 2011-09-07
I'm glad you got it fixed but I'm curious.  Did you ever do a speed test such as speedtest.net to see what speed your device was *really* operating at?  On earlier releases I got the 1 Mb indicated but the device was actually operating much faster.

---

