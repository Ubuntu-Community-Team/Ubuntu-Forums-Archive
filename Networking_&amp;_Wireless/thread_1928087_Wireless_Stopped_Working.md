---
title: "Wireless Stopped Working?"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by bOgNeR17 on 2012-02-19
For some reason I turned on my computer the other day and it would not connect to the wireless router. So I deleted the wireless connection and turn off wireless and networking and turned them back on again and tried to reconnect to the my router but still no luck. The only way I can connect is by disconnecting my Ethernet cable from my xbox 360 and putting it into the Ethernet port on the computer. This is not handy at all because I cannot have both connected to the internet at the same time. I did install an update the other day on lubuntu maybe this might be contributing to the problem. But I also booted up on Ubuntu and the problem is still the same so I take it that its not the updates. Anyone have an idea to why this is happening? Thanks. :KS

---

### Post by wildmanne39 on 2012-02-19
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by seppalta on 2012-02-19
Is your computer a laptop?  Laptops usually have on-off switch for wireless.  Location usually along an edge or behind the keyboard.  Did you perhaps accidentally turn it off?

---

### Post by bOgNeR17 on 2012-02-20
```
diarmuid@bognerdiarmuid1708920806000000000000:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux bognerdiarmuid1708920806000000000000 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
diarmuid@bognerdiarmuid1708920806000000000000:~$ lspci -nnk | grep -iA2 net
00:10.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Packard Bell B.V. Onboard RTL8111 on GA-8SIML Rev1.0 Mainboard [1631:7003]
    Kernel driver in use: 8139too
diarmuid@bognerdiarmuid1708920806000000000000:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
diarmuid@bognerdiarmuid1708920806000000000000:~$ rfkill list all
The program 'rfkill' is currently not installed.  You can install it by typing:
sudo apt-get install rfkill
diarmuid@bognerdiarmuid1708920806000000000000:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
bluetooth             148839  7 bnep
ppdev                  12849  0 
arc4                   12473  2 
binfmt_misc            17292  1 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
ac97_bus               12642  1 snd_ac97_codec
rt2x00usb              20092  1 rt73usb
rt2x00lib              48114  2 rt73usb,rt2x00usb
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
mac80211              272785  2 rt2x00usb,rt2x00lib
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              172392  2 rt2x00lib,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
parport_pc             32114  1 
i2c_sis96x             12743  0 
sis_agp                13165  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
8139too                23283  0 
8139cp                 22636  0 
floppy                 60310  0 
diarmuid@bognerdiarmuid1708920806000000000000:~$ 

```

No im not using a laptop so I that would not be possible. Thanks for the replies. :)

---

### Post by wildmanne39 on 2012-02-20
Hi, please post the output of:
```
lsusb
modinfo rt73usb
```
is the usb adapter the only wireless you are trying to use?

Also please do this:
```
gksudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off

```
Above the exit 0
Then save, close and reboot.
Thanks

---

### Post by bOgNeR17 on 2012-02-21
```
diarmuid@bognerdiarmuid1708920806000000000000:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]
Bus 002 Device 002: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
diarmuid@bognerdiarmuid1708920806000000000000:~$ modinfo rt73usb
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     87FA367B5DFB69C8DA76EC8
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
vermagic:       3.0.0-12-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

Yes the USB adapter is the only wireless I am trying to use there are no other devices attached to the computer for wireless connection.

---

### Post by bOgNeR17 on 2012-02-21
After trying to change the power management of the USB adapter I get this.

```
diarmuid@bognerdiarmuid1708920806000000000000:~$ gksudo gedit /etc/pm/power.d/wireless
diarmuid@bognerdiarmuid1708920806000000000000:~$ #!/bin/sh
diarmuid@bognerdiarmuid1708920806000000000000:~$ /sbin/iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not permitted.
diarmuid@bognerdiarmuid1708920806000000000000:~$ 


```

---

### Post by wildmanne39 on 2012-02-21
Hi, please post the output of:
```
nm-tool
sudo iwlist scan
```
Thanks

---

### Post by bOgNeR17 on 2012-02-21
```
diarmuid@bognerdiarmuid1708920806000000000000:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:0F:EA:A8:2C:DD

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [BTHomeHub2-4NK3] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             connected
  Default:           yes
  HW Address:        00:22:75:FF:80:96

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BTFON:           Infra, 02:24:17:64:25:7B, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    BTOpenzone-H:    Infra, 02:24:17:64:25:7A, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    *BTHomeHub2-4NK3:Infra, 00:24:17:64:25:79, Freq 2462 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.69
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


diarmuid@bognerdiarmuid1708920806000000000000:~$ sudo iwlist scan
[sudo] password for diarmuid: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:17:64:25:79
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-4NK3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001599cfb503
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 000F4254486F6D65487562322D344E4B33
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180204F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 02 - Address: 02:24:17:64:25:7A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone-H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001599c86adb
                    Extra: Last beacon: 528ms ago
                    IE: Unknown: 000C42544F70656E7A6F6E652D48
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180204F0050000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 03 - Address: 02:24:17:64:25:7B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001599c87098
                    Extra: Last beacon: 524ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180204F0050000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00

diarmuid@bognerdiarmuid1708920806000000000000:~$ 

```

I did get the wireless working. I disconnected the USB wireless adapter turned of wireless and networking. I then deleted the saved wireless network. I then plugged the USB adapter back in again and turned on networking and wireless. I connected to the wireless router with no problem. I haven't tried to restart the system yet to see if I have to do the above procedures again every time I reboot but when I do reboot the computer I will let you know. Thanks for your help this far. ;)

---

### Post by wildmanne39 on 2012-02-21
Hi, ok let me know we may add a parameter to the driver to help if needed.
Thanks

---

### Post by bOgNeR17 on 2012-02-22
Restarted my system there now and all I had to do was enable Networking & Wireless and it connected to the wireless router no problem. Will I have to do this everytime I boot up which Is not a problem but if its an easy fix I would be a little handier not having to do that everytime. Thanks for your help [wildmanne39]("http://ubuntuforums.org/member.php?u=508533")

---

### Post by bOgNeR17 on 2012-02-24
Do not have to do the above procedures every time I reboot works 100% thanks.

---

### Post by wildmanne39 on 2012-02-24
Hi, I am glad it is working, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

