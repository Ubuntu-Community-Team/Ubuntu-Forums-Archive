---
title: "i cant connect to wireless!! urgent please help"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by ekfsksk on 2011-03-15
hi im new to ubuntu and i was using windows vista previosuly
but after installing ubuntu i cant connect to wireless network!
im not using a laptop. im using a desktop with wireless usb stick thingy
please help i dont know wats wrong? thank you

im using maverick if it helps

---

### Post by chili555 on 2011-03-15
Drivers are built in for most but not all USB stick thingys. Please open Applications > Accessories > Terminal and run and post:```
lsusb
```We'll figure out what drivers you need.

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> Drivers are built in for most but not all USB stick thingys. Please open Applications > Accessories > Terminal and run and post:```
lsusb
```We'll figure out what drivers you need.

Bus 008 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:8192 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by ammofreak on 2011-03-15
Hi ekfsksk: you provided no info! On install I take it you were not connected to the internet, period! What is the name & model of the USB WiFi device? Is your WiFi router secure with WEP or WPA ? Have you tried Network Manager to configure WiFi network after install? Not an expert, but I will help as much as possible.

---

### Post by chili555 on 2011-03-15
>  0bda:8192 Realtek Semiconductor Corp. Your device is supported by the driver module r8192u_usb that's built in to the kernel. There is frequently a firmware issue. Please post:```
dmesg | grep 819
```> you provided no info! He provided enough.

---

### Post by ekfsksk on 2011-03-15
> **ammofreak said:**
> Hi ekfsksk: you provided no info! On install I take it you were not connected to the internet, period! What is the name & model of the USB WiFi device? Is your WiFi router secure with WEP or WPA ? Have you tried Network Manager to configure WiFi network after install? Not an expert, but I will help as much as possible.

i cant connect to wifi but i can connect to LAN which im using right now.

model of the usb wifi device is Retail Plus wireless N usb adapter
my wireless network is WPA tkip
and i dont think i tried network manager

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> Your device is supported by the driver module r8192u_usb that's built in to the kernel. There is frequently a firmware issue. Please post:```
dmesg | grep 819
```He provided enough.

i got this.....i dont know what it is but i sure see lots of 'fail' stuff... bytheway i am connected to the internet right now using LAN.


dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[   13.838802] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   13.978918] Linux kernel driver for RTL8192 based WLAN cards
[   14.722803] usbcore: registered new interface driver rtl819xU
[   16.211955] rtl819xU:request firmware fail!
[   16.211961] rtl819xU:ERR in init_firmware()
[   16.211964] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   16.211968] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   16.460640] rtl819xU:request firmware fail!
[   16.460645] rtl819xU:ERR in init_firmware()
[   16.460648] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   16.460651] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   47.851917] rtl819xU:request firmware fail!
[   47.851921] rtl819xU:ERR in init_firmware()
[   47.851925] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   47.851928] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 2546.420687] rtl819xU:=============>wlan driver to be removed
[ 2546.430837] rtl819xU:wlan driver removed
[ 2551.083044] rtl819xU:request firmware fail!
[ 2551.083051] rtl819xU:ERR in init_firmware()
[ 2551.083055] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[ 2551.083058] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 2551.308879] rtl819xU:request firmware fail!
[ 2551.308886] rtl819xU:ERR in init_firmware()
[ 2551.308890] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[ 2551.308893] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!


please help :((

---

### Post by chili555 on 2011-03-15
A firmware error, whadda ya know...

It looks like you have an ethernet connection. Remove the device and then please do:```
sudo mkdir /lib/firmware/RTL8192SU
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```Detach the ethernet cable, re-insert the device and enjoy your new wireless.

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> A firmware error, whadda ya know...

It looks like you have an ethernet connection. Remove the device and then please do:```
sudo mkdir /lib/firmware/RTL8192SU
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```Detach the ethernet cable, re-insert the device and enjoy your new wireless.

so i detached my LAN cable and usb stick (BTW you said 'remove the device', so is the 'device' the usb stick?)
but its not working...

i dont know whats wrong?????!!!W
...no comment :(

---

### Post by chili555 on 2011-03-15
> Resolving launchpadlibrarian.net... failed: Name or service not known.
wget: unable to resolve host address `launchpadlibrarian.net'It works for me. Did you copy and pasted from my code box? I just tried it twice and it works. Please try again or grab the attached.

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> It works for me. Did you copy and pasted from my code box? I just tried it twice and it works. Please try again or grab the attached.

yes i copied and pasted it so it downloaded something.

and just to make sure i downloaded the attached file but what now?
sorry for not being smart :(

---

### Post by chili555 on 2011-03-15
Where did it go? Your desktop? If so, please do:```
cd Desktop
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> Where did it go? Your desktop? If so, please do:```
cd Desktop
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```

uh, i copy and pasted it and the file that i downloaded disappeared. :o ??



and this is what i got (i did this with my ehternet cable plugged in if it matters)

daniel@ubuntu:~$ cd Desktop
daniel@ubuntu:~/Desktop$ gunzip rtl8192sfw.bin.gz
gzip: rtl8192sfw.bin.gz: No such file or directory
daniel@ubuntu:~/Desktop$ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
daniel@ubuntu:~/Desktop$

---

### Post by chili555 on 2011-03-15
> gzip: rtl8192sfw.bin.gz: No such file or directoryThen you evidently didn't download it to your desktop. Where is it?```
cd whereveritis
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> Then you evidently didn't download it to your desktop. Where is it?```
cd whereveritis
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```

its in my Download folder but i copied and pasted it on desktop...
sorry :( im new to linux ...


EDIT: ok i did what you told me and got 

daniel@ubuntu:~$ cd Downloads
daniel@ubuntu:~/Downloads$ gunzip rtl8192sfw.bin.gz
daniel@ubuntu:~/Downloads$ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
daniel@ubuntu:~/Downloads$

but my wifi still wont work... omg im so frustrated

---

### Post by chili555 on 2011-03-15
Take a deep breath, sip a cup of tea or other beverage; we're close now. Please leave the device plugged in and detach the ethernet cable and reboot. If it's not working, run and post:```
dmesg | grep 819
```Myself, I'm getting an ice cream!

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> Take a deep breath, sip a cup of tea or other beverage; we're close now. Please leave the device plugged in and detach the ethernet cable and reboot. If it's not working, run and post:```
dmesg | grep 819
```Myself, I'm getting an ice cream!

no hope...
i dont know what these mean but i see firmware errors. i think thats what the problem is?

daniel@ubuntu:~$ dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[   14.218101] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   14.256233] Linux kernel driver for RTL8192 based WLAN cards
[   15.101502] usbcore: registered new interface driver rtl819xU
[   16.160490] rtl819xU:request firmware fail!
[   16.160495] rtl819xU:ERR in init_firmware()
[   16.160498] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   16.160501] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   16.423482] rtl819xU:request firmware fail!
[   16.423488] rtl819xU:ERR in init_firmware()
[   16.423492] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   16.423495] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  109.923323] rtl819xU:request firmware fail!
[  109.923328] rtl819xU:ERR in init_firmware()
[  109.923331] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[  109.923335] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

---

### Post by chili555 on 2011-03-15
Let's make sure it actually went where we wanted it to go:```
ls -al /lib/firmware/RTL8192SU/
```

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> Let's make sure it actually went where we wanted it to go:```
ls -al /lib/firmware/RTL8192SU/
```

daniel@ubuntu:~$ ls -al /lib/firmware/RTL8192SU/
total 76
drwxr-xr-x  2 root   root    4096 2011-03-16 10:42 .
drwxr-xr-x 50 root   root    4096 2011-03-16 10:15 ..
-rw-r--r--  1 daniel daniel 68368 2011-03-16 10:19 rtl8192sfw.bin

(ugh dont worry bout the date and time cause its all messed up)

---

### Post by chili555 on 2011-03-15
Please try:```
sudo chown root:root /lib/firmware/RTL8192SU/*
sudo rmmod -f r8192u_usb
sudo modprobe r8192u_usb
dmesg | tail -n 10
```Any improvement?

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> Please try:```
sudo chown root:root /lib/firmware/RTL8192SU/*
sudo rmmod -f r8192u_usb
sudo modprobe r8192u_usb
dmesg | tail -n 10
```Any improvement?

daniel@ubuntu:~$ sudo chown root:root /lib/firmware/RTL8192SU/*
daniel@ubuntu:~$ sudo rmmod -f r8192u_usb
daniel@ubuntu:~$ sudo modprobe r8192u_usb
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
daniel@ubuntu:~$ dmesg | tail -n 10
[ 1163.579552] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1163.579554] 
[ 1163.817375] rtl819xU:request firmware fail!
[ 1163.817377] 
[ 1163.817380] rtl819xU:ERR in init_firmware()
[ 1163.817381] 
[ 1163.817383] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[ 1163.817385] 
[ 1163.817387] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1163.817388]


so no solution for me? :(

---

### Post by ekfsksk on 2011-03-15
please help meh~~
also bump.

---

### Post by chili555 on 2011-03-15
I believe I made a mistake. I'm sorry. Please see post #29: [http://ubuntuforums.org/showthread.php?p=10342504](http://ubuntuforums.org/showthread.php?p=10342504)

Download the file that's attached. I assume it's going to Downloads.```
sudo mkdir /lib/firmware/RTL8192U
cd Downloads
unzip RTL8192U.zip
cd RTL8192U
sudo cp * /lib/firmware/RTL8192U/
sudo rmmod -f r8192u_usb
sudo modprobe r8192u_usb
```Any improvement?

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> I believe I made a mistake. I'm sorry. Please see post #29: [http://ubuntuforums.org/showthread.php?p=10342504](http://ubuntuforums.org/showthread.php?p=10342504)

Download the file that's attached. I assume it's going to Downloads.```
sudo mkdir /lib/firmware/RTL8192U
cd Downloads
unzip RTL8192U.zip
cd RTL8192U
sudo cp * /lib/firmware/RTL8192U/
sudo rmmod -f r8192u_usb
sudo modprobe r8192u_usb
```Any improvement?

well, im not seeing those 'fail firmware' stuff..
but i do have downloaded stuff on my Downloads folder. see?
[http://img839.imageshack.us/i/screenshotnte.png/](http://img839.imageshack.us/i/screenshotnte.png/)


daniel@ubuntu:~$ sudo mkdir /lib/firmware/RTL8192U
daniel@ubuntu:~$ cd Downloads
daniel@ubuntu:~/Downloads$ unzip RTL8192U.zip
unzip:  cannot find or open RTL8192U.zip, RTL8192U.zip.zip or RTL8192U.zip.ZIP.
daniel@ubuntu:~/Downloads$ cd RTL8192U
bash: cd: RTL8192U: No such file or directory
daniel@ubuntu:~/Downloads$ sudo cp * /lib/firmware/RTL8192U/
daniel@ubuntu:~/Downloads$ sudo rmmod -f r8192u_usb
daniel@ubuntu:~/Downloads$ sudo modprobe r8192u_usb
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

---

### Post by chili555 on 2011-03-15
> but i do have downloaded stuff on my Downloads folder. see?But you don't have RTL8192U.zip attached to the other thread. Please get it and try again.

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> But you don't have RTL8192U.zip attached to the other thread. Please get it and try again.

Woops, sorry!:(
k so hers what i got


daniel@ubuntu:~$ sudo mkdir /lib/firmware/RTL8192U
mkdir: cannot create directory `/lib/firmware/RTL8192U': File exists
daniel@ubuntu:~$ cd Downloads
daniel@ubuntu:~/Downloads$ unzip RTL8192U.zip
Archive:  RTL8192U.zip
   creating: RTL8192U/
  inflating: RTL8192U/boot.img       
  inflating: RTL8192U/data.img       
  inflating: RTL8192U/main.img       
daniel@ubuntu:~/Downloads$ cd RTL8192U
daniel@ubuntu:~/Downloads/RTL8192U$ sudo cp * /lib/firmware/RTL8192U/
daniel@ubuntu:~/Downloads/RTL8192U$ sudo rmmod -f r8192u_usb
daniel@ubuntu:~/Downloads/RTL8192U$ sudo modprobe r8192u_usb
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

---

### Post by chili555 on 2011-03-15
So now what does this tell us?```
dmesg | tail -n15
iwconfig
sudo iwlist wlan0 scan
```

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> So now what does this tell us?```
dmesg | tail -n15
iwconfig
sudo iwlist wlan0 scan
```

i cant post it on here cause its too long :(

---

### Post by ekfsksk on 2011-03-15
daniel@ubuntu:~$ dmesg | tail -n15
[ 3300.895157] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3300.997651] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3300.997655] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.100022] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.100026] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.510745] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.510749] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.613112] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.613115] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.715350] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.715354] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.817584] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.817588] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.919712] ========>ieee80211_parse_info_param(): athros AP is exist
[ 3301.919715] ========>ieee80211_parse_info_param(): athros AP is exist
daniel@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n  ESSID:"%\xCF\x08\xF5\xE9\xE2^S`\xAA\xD2\xB2\xD0\x85\xFAT\xD85\xE8\xD4f\x82d\x98\xD9\xA8\x87uepZ\x8A"  
          Mode:Managed  Frequency=2.432 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

daniel@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:58:ED:6A:91
                    ESSID:"Elena"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality=76/100  Signal level=-58 dBm  Noise level=-108 dBm
                    Extra: Last beacon: 76ms ago
          Cell 02 - Address: 00:21:91:D3:2F:DB
                    ESSID:"baleleng"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality=85/100  Signal level=-57 dBm  Noise level=-112 dBm
                    Extra: Last beacon: 160ms ago
          Cell 03 - Address: 00:1E:E5:04:78:75

---

### Post by ekfsksk on 2011-03-15
ESSID:"pinkpanther07"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:65 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-58 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 106ms ago
          Cell 04 - Address: 70:71:BC:32:D2:62
                    ESSID:"Rogers"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=72/100  Signal level=-58 dBm  Noise level=-106 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 72ms ago
          Cell 05 - Address: 00:22:B0:D4:DF:0E
                    ESSID:"donteventhinkaboutit"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality=95/100  Signal level=-59 dBm  Noise level=-117 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 8ms ago

---

### Post by ekfsksk on 2011-03-15
Cell 06 - Address: 00:26:F3:A1:5B:51
                    ESSID:"SnowChloe"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=71/100  Signal level=-59 dBm  Noise level=-105 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 5ms ago
          Cell 07 - Address: 00:26:F3:A1:5B:52
                    ESSID:"<hidden>\x00"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=69/100  Signal level=-59 dBm  Noise level=-104 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 4ms ago
          Cell 08 - Address: 00:26:75:22:75:0C
                    ESSID:"Amor"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=76/100  Signal level=-59 dBm  Noise level=-108 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2ms ago
          Cell 09 - Address: 00:22:2D:12:EC:24
                    ESSID:"unit603"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality=69/100  Signal level=-59 dBm  Noise level=-104 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1ms ago
          Cell 10 - Address: 00:13:F7:F8:4C:9C
                    ESSID:"WLAN"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:10
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality=72/100  Signal level=-59 dBm  Noise level=-106 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 41ms ago

---

### Post by chili555 on 2011-03-15
So far, so good! Can you click the Network Manager icon and connect?

---

### Post by ekfsksk on 2011-03-15
> **chili555 said:**
> So far, so good! Can you click the Network Manager icon and connect?

YES! i can!  omg thank you so much!!!!!!
<3 u are a genious!!!

---

### Post by chili555 on 2011-03-15
> **ekfsksk said:**
> YES! i can!  omg thank you so much!!!!!!
<3 u are a genious!!!Awesome! Would you like to use Thread Tools at the top and mark the thread Solved?

---

### Post by sbrandon on 2011-03-16
Chili - amazing job - must be the slaw dogs that give you the patience!

---

