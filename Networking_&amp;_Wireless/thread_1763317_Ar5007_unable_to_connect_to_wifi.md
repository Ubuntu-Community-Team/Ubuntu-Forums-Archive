---
title: "Ar5007 unable to connect to wifi"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by Dhezballah on 2011-05-20
I recently changed from Windows Vista to Ubuntu 11.04 and ever since I have not been able to connect to wifi.
The connections show up in the connections area but it will never connect and will keep alerting me to enter my WPA2 password.
I have been searching for a solution to this problem for a few days and have still not found the answer.
Also when I use lspci | grep Wireless it tells me that my card is an Atheros Ar5001 when it is actually an Ar5007eg.

Hope someone can give me some help.

---

### Post by josephmills on 2011-05-20
hi there could you please open your terminal and type in ```
lsmod | grep ath 
``` and ```
dmesg | grep ath 
``` and  ```
rfkill list all 
``` Please paste all here thanks

---

### Post by Dhezballah on 2011-05-20
Thank you for the reply.
```
jeremy@jeremy-Satellite-L300:~$ lsmod | grep ath
ath5k                 144412  0 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211
ath_rate_sample        17279  1 
ath_pci               183044  0 
wlan                  224640  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               398701  3 ath_rate_sample,ath_pci

``````

jeremy@jeremy-Satellite-L300:~$ dmesg | grep ath
[    3.732372] device-mapper: multipath: version 1.2.0 loaded
[    3.732376] device-mapper: multipath round-robin: version 1.0.0 loaded
[   16.710230] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.710246] ath_pci 0000:03:00.0: setting latency timer to 64
[   17.330911] MadWifi: ath_attach: Switching rfkill capability off.
[   17.372739] ath_pci: wifi0: Atheros 5424/2424: mem=0x94600000, irq=17
[   28.176016] ath0: no IPv6 routers present
```and rfkill list all came out with nothing

---

### Post by josephmills on 2011-05-20
I see a couple of things that are wrong but before we do anything we need to see ```
lspci -nn  | grep Ath 
``` thanks

---

### Post by Dhezballah on 2011-05-20
```
jeremy@jeremy-Satellite-L300:~$ lspci -nn  | grep Ath
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
```On a side not "I typed your symptoms into the thing up here and it says you could have network connectivity problems." I totally lost it when Andy said that.
[LEFT][COLOR=#000000]

[/COLOR][/LEFT]

---

### Post by josephmills on 2011-05-20
before we put on are glasses and start the linux geek out lets try this go to ubuntu software center then go to EDIT-->SOFTWARE SOURCES then make sure all is ticked see pic then close out of software sources and ubuntu software center and then open your terminal and type in ```
sudo apt-get update
``` then ```
sudo apt-get upgrade 
``` then rebootwith out the cat5 cable in  and post back ```
rfkill list 
``` thanks

---

### Post by Dhezballah on 2011-05-20
Thanks again for helping me out.
I did all of that, still no wireless and rfkill list didn't list anything.

---

### Post by josephmills on 2011-05-20
left click on the network managers icon can you enable wireless or is it greyed out? do you see networks when left clicking on the network managers icon? could we also see a ```
iwlist scan 
``` thanks again

---

### Post by Dhezballah on 2011-05-20
Wireless is enabled and I can see my network.
```
jeremy@jeremy-Satellite-L300:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:22:A4:F3:83:D1
                    ESSID:"BigPond9984"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-25 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by josephmills on 2011-05-20
so when you try and connect with out the cat5 cable in it just sits there and spins and asks you for you passwrd again?

---

### Post by Dhezballah on 2011-05-20
Yeah it will just keep trying to connect and keep asking for my WPA2 password for a few minutes then say wireless is disconnected.

---

### Post by josephmills on 2011-05-20
try this ```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2008-10-31
make
sudo make install
sudo make unload
sudo make load
``` then reboot anything ? if there are any errors please post. I should also note that I dont know if this will work with 11.04 thanks

---

### Post by Dhezballah on 2011-05-20
```
jeremy@jeremy-Satellite-L300:~$ wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2
--2011-05-21 11:47:13--  http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2
Resolving wireless.kernel.org... 78.46.109.217
Connecting to wireless.kernel.org|78.46.109.217|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-05-21 11:47:15 ERROR 404: Not Found.

``````
jeremy@jeremy-Satellite-L300:~$ tar jxvf compat-wireless-2.6.tar.bz2
tar (child): compat-wireless-2.6.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
``````
jeremy@jeremy-Satellite-L300:~$ cd compat-wireless-2008-10-31
bash: cd: compat-wireless-2008-10-31: No such file or directory
```The rest gave out make: *** No targets specified and no makefile found.  Stop.
I'm guessing this is bad?

---

### Post by josephmills on 2011-05-21
arghh could we see ```
cat /etc/network/interfaces

``` thanks

---

### Post by Dhezballah on 2011-05-21
```
jeremy@jeremy-Satellite-L300:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by josephmills on 2011-05-21
please see [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by Dhezballah on 2011-05-21
Will do. 
Thanks man

---

