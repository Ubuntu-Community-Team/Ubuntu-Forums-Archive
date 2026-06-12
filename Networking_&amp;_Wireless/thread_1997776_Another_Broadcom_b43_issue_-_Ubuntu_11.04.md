---
title: "Another Broadcom b43 issue - Ubuntu 11.04"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by larryj54 on 2012-06-05
Hello Chilli, here is the results of ..
lj@LJ-Compaq:~$ lspci -nn | grep 0280
02:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

lj@LJ-Compaq:~$ dmesg | grep b43
lj@LJ-Compaq:~$ 

lj@LJ-Compaq:~$ rfkill list all
lj@LJ-Compaq:~$ 

LJ

---

### Post by chili555 on 2012-06-05
Now let's have a look at:```
ls /lib/firmware/b43
sudo modprobe b43
dmesg | grep b43
```In the case of the first command, we just need to know if you have the folder and if it contains lots of files; you don't need to list them all.

---

### Post by larryj54 on 2012-06-05
lj@LJ-Compaq:~$ ls /lib/firmware/b43
ls: cannot open directory /lib/firmware/b43: Permission denied
lj@LJ-Compaq:~$ sudo ls /lib/firmware/b43
[sudo] password for lj: 
a0g0bsinitvals5.fw   a0g1initvals13.fw      b0g0initvals5.fw    lp0initvals15.fw      ucode14.fw
a0g0bsinitvals9.fw   a0g1initvals5.fw      b0g0initvals9.fw    n0absinitvals11.fw  ucode15.fw
a0g0initvals5.fw     a0g1initvals9.fw      lp0bsinitvals13.fw  n0bsinitvals11.fw   ucode5.fw
a0g0initvals9.fw     b0g0bsinitvals13.fw  lp0bsinitvals14.fw  n0initvals11.fw      ucode9.fw
a0g1bsinitvals13.fw  b0g0bsinitvals5.fw   lp0bsinitvals15.fw  pcm5.fw
a0g1bsinitvals5.fw   b0g0bsinitvals9.fw   lp0initvals13.fw    ucode11.fw
a0g1bsinitvals9.fw   b0g0initvals13.fw      lp0initvals14.fw    ucode13.fw
lj@LJ-Compaq:~$ 

lj@LJ-Compaq:~$ sudo modprobe b43
lj@LJ-Compaq:~$ 

lj@LJ-Compaq:~$ dmesg | grep b43
[ 2450.918803] b43-pci-bridge 0000:02:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2450.949752] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[ 2451.016902] Registered led device: b43-phy0::tx
[ 2451.016950] Registered led device: b43-phy0::rx
[ 2451.016999] Registered led device: b43-phy0::radio
[ 2451.272071] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
lj@LJ-Compaq:~$

---

### Post by chili555 on 2012-06-05
> lj@LJ-Compaq:~$ ls /lib/firmware/b43
ls: cannot open directory /lib/firmware/b43: Permission deniedInteresting!! Let's have a look at: ```
sudo chmod +r /lib/firmware/b43
ls /lib/firmware/b43
```Now do you get a 'permission denied' error?> lj@LJ-Compaq:~$ dmesg | grep b43
[ 2450.918803] b43-pci-bridge 0000:02:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2450.949752] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[ 2451.016902] Registered led device: b43-phy0::tx
[ 2451.016950] Registered led device: b43-phy0::rx
[ 2451.016999] Registered led device: b43-phy0::radio
[ 2451.272071] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)This looks pretty normal. Did it create a wireless interface?```
iwconfig
```Does it see your network?```
sudo iwlist wlan0 scan
```

---

### Post by larryj54 on 2012-06-05
lj@LJ-Compaq:~$ sudo chmod +r /lib/firmware/b43
lj@LJ-Compaq:~$ ls /lib/firmware/b43
ls: cannot access /lib/firmware/b43/a0g1bsinitvals13.fw: Permission denied
ls: cannot access /lib/firmware/b43/ucode14.fw: Permission denied
ls: cannot access /lib/firmware/b43/n0initvals11.fw: Permission denied
ls: cannot access /lib/firmware/b43/lp0bsinitvals14.fw: Permission denied
ls: cannot access /lib/firmware/b43/b0g0bsinitvals5.fw: Permission denied
ls: cannot access /lib/firmware/b43/ucode5.fw: Permission denied
ls: cannot access /lib/firmware/b43/ucode11.fw: Permission denied
ls: cannot access /lib/firmware/b43/lp0initvals13.fw: Permission denied
ls: cannot access /lib/firmware/b43/a0g1bsinitvals9.fw: Permission denied
ls: cannot access /lib/firmware/b43/pcm5.fw: Permission denied
ls: cannot access /lib/firmware/b43/b0g0bsinitvals13.fw: Permission denied
ls: cannot access /lib/firmware/b43/ucode9.fw: Permission denied
ls: cannot access /lib/firmware/b43/a0g0bsinitvals5.fw: Permission denied
ls: cannot access /lib/firmware/b43/n0bsinitvals11.fw: Permission denied
ls: cannot access /lib/firmware/b43/b0g0initvals9.fw: Permission denied
ls: cannot access /lib/firmware/b43/ucode15.fw: Permission denied
ls: cannot access /lib/firmware/b43/lp0bsinitvals15.fw: Permission denied
ls: cannot access /lib/firmware/b43/a0g1initvals13.fw: Permission denied
ls: cannot access /lib/firmware/b43/a0g0initvals5.fw: Permission denied
ls: cannot access /lib/firmware/b43/a0g1initvals5.fw: Permission denied
ls: cannot access /lib/firmware/b43/n0absinitvals11.fw: Permission denied
ls: cannot access /lib/firmware/b43/lp0initvals14.fw: Permission denied
ls: cannot access /lib/firmware/b43/lp0bsinitvals13.fw: Permission denied
ls: cannot access /lib/firmware/b43/a0g0bsinitvals9.fw: Permission denied
ls: cannot access /lib/firmware/b43/a0g0initvals9.fw: Permission denied
ls: cannot access /lib/firmware/b43/lp0initvals15.fw: Permission denied
ls: cannot access /lib/firmware/b43/b0g0bsinitvals9.fw: Permission denied
ls: cannot access /lib/firmware/b43/ucode13.fw: Permission denied
ls: cannot access /lib/firmware/b43/b0g0initvals5.fw: Permission denied
ls: cannot access /lib/firmware/b43/b0g0initvals13.fw: Permission denied
ls: cannot access /lib/firmware/b43/a0g1initvals9.fw: Permission denied
ls: cannot access /lib/firmware/b43/a0g1bsinitvals5.fw: Permission denied
a0g0bsinitvals5.fw   a0g1initvals13.fw    b0g0initvals5.fw    lp0initvals15.fw    ucode14.fw
a0g0bsinitvals9.fw   a0g1initvals5.fw     b0g0initvals9.fw    n0absinitvals11.fw  ucode15.fw
a0g0initvals5.fw     a0g1initvals9.fw     lp0bsinitvals13.fw  n0bsinitvals11.fw   ucode5.fw
a0g0initvals9.fw     b0g0bsinitvals13.fw  lp0bsinitvals14.fw  n0initvals11.fw     ucode9.fw
a0g1bsinitvals13.fw  b0g0bsinitvals5.fw   lp0bsinitvals15.fw  pcm5.fw
a0g1bsinitvals5.fw   b0g0bsinitvals9.fw   lp0initvals13.fw    ucode11.fw
a0g1bsinitvals9.fw   b0g0initvals13.fw    lp0initvals14.fw    ucode13.fw
lj@LJ-Compaq:~$ 


lj@LJ-Compaq:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lj@LJ-Compaq:~$ 


lj@LJ-Compaq:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:83:17:96
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"LJ_belkin54g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005fe182fa177
                    Extra: Last beacon: 116ms ago
                    IE: Unknown: 000C4C4A5F62656C6B696E353467
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

lj@LJ-Compaq:~$ 


The blue light in the wi-fi button is now lit, but still seems to not be connecting to the router.  I unplugged the ethernet cable and it could not make a connection. I am back on wired.  At least the blue light is progress!

---

### Post by chili555 on 2012-06-05
> lj@LJ-Compaq:~$ sudo chmod +r /lib/firmware/b43
lj@LJ-Compaq:~$ ls /lib/firmware/b43
ls: cannot access /lib/firmware/b43/a0g1bsinitvals13.fw: Permission denied
ls: cannot access /lib/firmware/b43/ucode14.fw: Permission denied
ls: cannot access /lib/firmware/b43/n0initvals11.fw: Permission denied
ls: cannot access /lib/firmware/b43/lp0bsinitvals14.fw: Permission deniedLet's try to fix this, even though it may or may not be a hindrance.```
sudo ls -al /lib/firmware | grep b43
```Let's also be sure b43 loads by default on boot:```
sudo su
echo b43 >> /etc/modules
exit
```Thanks.

---

### Post by larryj54 on 2012-06-05
lj@LJ-Compaq:~$ sudo ls -al /lib/firmware | grep b43
drwxr-xr--  2 root root    4096 2012-06-05 15:36 b43
drwxr-x---  2 root root    4096 2012-06-05 15:34 b43legacy
lj@LJ-Compaq:~$ 
lj@LJ-Compaq:~$ sudo su
root@LJ-Compaq:/home/lj# echo b43 >> /etc/modules
root@LJ-Compaq:/home/lj# exit
exit
lj@LJ-Compaq:~$

---

### Post by chili555 on 2012-06-05
Let's try to fix the firmware with brute strength and awkwardness. Are you running Ubuntu 12.04 or some other?```
lsb_release -d
```

EDIT: Oops! I see you are running 11.04. Please do:```
cd /lib/firmware
sudo rm -rf b43
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```Reboot and tell me if there is any improvement.

---

### Post by larryj54 on 2012-06-05
Chilli, while waiting I rebooted, to no avail, then went thru systems/admin/networking and set up router ssid and wep pass phrase.  Didn't seem to do any good, then another reboot and I clicked on the networking icon in to top right icon bar, and it prompted me for the pass phrase, and now its working... I have no idea what exactly you/we did, but its working so Bless you my son.. The Force is strong with you! ;) 

Appreciate the guidance.

LJ

---

### Post by chili555 on 2012-06-05
> I have no idea what exactly you/we did, but its working so Bless you my son.. The Force is strong with you!Never fight the Force. I'm glad it's working by whatever means. Have fun!

Please use thread tools at the top to mark Solved.

---

