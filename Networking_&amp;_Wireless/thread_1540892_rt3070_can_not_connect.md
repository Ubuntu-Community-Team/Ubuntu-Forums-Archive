---
title: "rt3070 can not connect"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by xXx8004 on 2010-07-28
Hi
I'm new at Ubuntu i have rt3070 usb wireless network 
i have black list it and i can see the my network but I cant  connect  just asking me for password and trying to connect but get back to same  window asking for password.
can anybody help me please??
 i tried for 4 hours now without any results

Thanks

---

### Post by xXx8004 on 2010-07-28
hi
i get new driver and i tried to install it but something get wrong

i went to the folder by terminal and i wrote make and i get 

CC      /home/naz/Skrivbord/temp/os/linux/rt3070sta.mod.o 
  LD [M]  /home/naz/Skrivbord/temp/os/linux/rt3070sta.ko 
make[2]: warning:  Clock skew detected.  Your build may be incomplete. 
make[1]: warning:  Clock skew detected.  Your build may be incomplete. 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic' 
cp -f /home/naz/Skrivbord/temp/os/linux/rt3070sta.ko /tftpboot 
cp: cannot remove `/tftpboot': Permission denied 
make: *** [LINUX] Error 1



Thanks

---

### Post by xXx8004 on 2010-07-28
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"11n-AP"  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.422 GHz  Access Point: 00:1E:58:00:1C:FE   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-63 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by xXx8004 on 2010-07-28
naz@naz-desktop:~$ sudo modprobe rt2800usb
[sudo] password for naz: 
naz@naz-desktop:~$ sudo modprobe rt30700usb
FATAL: Module rt30700usb not found.
naz@naz-desktop:~$ sudo modprobe rt3070usb
FATAL: Module rt3070usb not found.
naz@naz-desktop:~$ sudo modprobe rt2800usb
naz@naz-desktop:~$ dmesg | tail 
[  177.530643] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=3)
[  187.540060] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 419
[  187.540321] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=3)
[  197.549371] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 419
[  197.549722] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=3)
[  207.559907] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 419
[  207.560267] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=3)
[  217.570743] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 419
[  217.571103] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=3)
[  227.580967] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 419




naz@naz-desktop:~$ lsmod | grep rt2
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126485  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
rt2870sta             461811  1 


naz@naz-desktop:~$ dmesg | grep rt2
[   10.920636] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   10.973928] usbcore: registered new interface driver rt2870
[   11.131122] Error: Driver 'rt2870' is already registered, aborting...
[   11.131171] usbcore: error -16 registering interface     driver rt2870
[  151.736006] usbcore: registered new interface driver rt2800usb

i hope someone can help me

---

### Post by flash63 on 2010-07-29
Hello,
block rt2800usb:
```
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Restart. The module rt2870sta supports this chipset, the module rt3070sta don't exist.

---

### Post by xXx8004 on 2010-07-29
**Re: rt3070** 
The config file look like:
 
# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist ndiswrapper
 
its blacklisted

---

### Post by flash63 on 2010-07-29
Only rt2870sta present?
```
lsmod | grep rt2
```

---

### Post by xXx8004 on 2010-07-29
naz@naz-desktop:~$ lsmod | grep rt2
rt2870sta 461811 1
 
What is going on? i cant very much!!
 
Thanks

---

### Post by flash63 on 2010-07-29
OK, test it
```
iwconfig
iwlist chan
sudo iwlist scan
```
Does the scan work show your own network.

Some problems with the Network-Manager are:
 * same chanel than other Accesspoints near by
 * mixed Encryption WPA1/2 (switch your Router to WPA2-AES (CCMP))

---

### Post by xXx8004 on 2010-07-29
[FONT=Batang][SIZE=3][/SIZE][/FONT] 
[FONT=Batang][SIZE=3]Hi[/SIZE][/FONT]
[FONT=Batang][SIZE=3]my network is avnb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]i can see it but i can not connect to im writing my password to the router and it is trying to connect but going back to the same window asking for password[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT] 
[FONT=Batang][SIZE=3][/SIZE][/FONT] 
[FONT=Batang][SIZE=3]naz@naz-desktop:~$ iwconfig[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3]lo        no wireless extensions.[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]eth0      no wireless extensions.[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Mode:Auto  Frequency=2.422 GHz  Access Point: 00:1E:58:00:1C:FE   [/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Bit Rate=1 Mb/s   [/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          RTS thr:off   Fragment thr:off[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Link Quality=10/100  Signal level:-55 dBm  Noise level:-97 dBm[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]naz@naz-desktop:~$ iwlist chan[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3]lo        no frequency information.[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]eth0      no frequency information.[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]wlan0     11 channels in total; available frequencies :[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 01 : 2.412 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 02 : 2.417 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 03 : 2.422 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 04 : 2.427 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 05 : 2.432 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 06 : 2.437 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 07 : 2.442 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 08 : 2.447 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 09 : 2.452 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 10 : 2.457 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Channel 11 : 2.462 GHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Current Frequency:2.422 GHz (Channel 3)[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]naz@naz-desktop:~$ sudo iwlist scan[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3][sudo] password for naz: [/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3]lo        Interface doesn't support scanning.[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]eth0      Interface doesn't support scanning.[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]wlan0     Scan completed :[/SIZE][/FONT]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Cell 01 - Address: 00:1E:58:00:1C:FE[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Protocol:802.11b/g/n[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    ESSID:"avnb"[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Mode:Managed[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Channel:3[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Quality:89/100  Signal level:-55 dBm  Noise level:-97 dBm[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Encryption key:on[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Bit Rates:11 Mb/s[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    IE: WPA Version 1[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                        Group Cipher : TKIP[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                        Pairwise Ciphers (2) : TKIP CCMP[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                        Authentication Suites (1) : PSK[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    IE: IEEE 802.11i/WPA2 Version 1[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                        Group Cipher : TKIP[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                        Pairwise Ciphers (2) : TKIP CCMP[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                        Authentication Suites (1) : PSK[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Cell 02 - Address: 00:24:17:C3:1E:9F[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Protocol:802.11b/g[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    ESSID:"TN_private_7017BC"[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Mode:Managed[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Channel:6[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Quality:26/100  Signal level:-79 dBm  Noise level:-97 dBm[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Encryption key:on[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Bit Rates:54 Mb/s[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    IE: WPA Version 1[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                        Group Cipher : TKIP[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                        Pairwise Ciphers (1) : TKIP[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                        Authentication Suites (1) : PSK[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]          Cell 03 - Address: 00:25:68:B9:2D:86[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Protocol:802.11b/g[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    ESSID:"Omeree"[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Mode:Managed[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Channel:11[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Quality:57/100  Signal level:-67 dBm  Noise level:-97 dBm[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Encryption key:on[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]                    Bit Rates:54 Mb/s[/FONT][/SIZE]

---

### Post by flash63 on 2010-07-29
As i said your Router works with mixed Encryption WPA1/2
```
Cell 01 - Address: 00:1E:58:00:1C:FE
Protocol:802.11b/g/n
ESSID:"avnb"
Mode:Managed
Channel:3
Quality:89/100 Signal level:-55 dBm Noise level:-97 dBm
Encryption keyn
Bit Rates:11 Mb/s
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK

```Connect over LAN-Kabel to your Router, start a browser (firefox) login over the Web-Interface (configuration page) an switch to Chanel 1 an pure WPA2-AES Encryption and the connection by the Network-Manager should work.

---

### Post by blehxor on 2010-07-29
I've had this same problem and have exhaustively searched these forums for an answer. 

Using Ubuntu 10.04 clean install. I have a generic 802.11b/g/n usb dongle with the RT3070 chipset. I downloaded the latest RT3070STA drivers from ralink.com TODAY. Installed RT3070sta, and blacklisted rt2800usb. Reinstalled network-manager.

Still have the issue described above: I can scan all the networks in my building, they have great signal. I have verified they are WPA2-AES only, not mixed. Still unable to authenticate with them. 

Reading through the install tutorials for this driver, every single one had some step to modify the RT3070STA module to be renamed RT2870STA in some way. I assumed they were outdated as the latest version of the RT3070 drivers I have does create a RT3070STA.ko and the /etc/Wireless/RT3070STA/ folder (in contrast to what these tutorials describe).  Am I incorrect, should I still be installing and using the RT2870STA module?

I had tried to install a different wireless dongle on a separate clean install of ubuntu 10.04 and gotten the exact same issue, no authentication with the WPA2.  Is there something I'm missing in the ubuntu configuration here?

Thanks in advance!

---

### Post by flash63 on 2010-07-29
> **blehxor said:**
> I've had this same problem and have exhaustively searched these forums for an answer. 

Using Ubuntu 10.04 clean install. I have a generic 802.11b/g/n usb dongle with the RT3070 chipset. I downloaded the latest RT3070STA drivers from ralink.com TODAY. Installed RT3070sta, and blacklisted rt2800usb. Reinstalled network-manager.
Loaded Modules?
```
lsmod | grep sta
```
In this case i think you must blacklist rt2870sta (or rt370sta to try which Driver works) too.

---

### Post by blehxor on 2010-08-02
Thanks for the reply,  I went on to read how much easier karmic should be, wiped my drive and created a fresh install of 9.10. Things are connecting fine now. The project I'm using this wireless device for is in the early stages of development, at some point I'll revisit 10.04 and give an update to this thread if I make any progress. Appreciate your help Flash.

Edit: oops wrong codename

---

