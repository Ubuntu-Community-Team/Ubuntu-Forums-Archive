---
title: "No internet after re-install"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by andydunne on 2011-07-24
Hello Ubuntu Community,

As a recent convertee to Ubuntu/Linux I haven't had to use the forum as everything that I wanted worked. Wireless etc. But as I got comfortable I started messing about with the settings and preferences and ended up re-installing Ubuntu.(Due to my windows upbringing). Since then I've been unable to connect to my home network. Not hardware as I'm logged into windows and on internet  to type this. I've had a look through the forum but didn't really see anything that matched my problem. I've run Iwconfig and Ifconfig and below are the results.

boss@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:"dunnes"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
           Tx-Power=17 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
 

 boss@ubuntu:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 20:cf:30:56:e3:7a   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:46  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:224 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:224 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:17264 (17.2 KB)  TX bytes:17264 (17.2 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:1f:77:09   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 
Thanks in advance for any help and apologies for the lengthy post

---

### Post by wildmanne39 on 2011-07-24
Hi, I will see if I can help you please run these commands in a terminal
```
lsmod
```
```
lspci -nn 
```
```
rfkill list all
```
and post the results here.

---

### Post by andydunne on 2011-07-25
Thanks Wildmanne,

boss@ubuntu:~$ lsmod  
 Module                  Size  Used by  
 binfmt_misc            17565  1  
 parport_pc             36959  0  
 ppdev                  17113  0  
 snd_hda_codec_realtek   336693  1  
 snd_hda_intel          33211  2  
 arc4                   12529  2  
 snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13604  1 snd_hda_codec  
 snd_pcm                96625  2 snd_hda_intel,snd_hda_codec  
 ath9k                 118238  0  
 i915                  514985  3  
 snd_seq_midi           13324  0  
 snd_rawmidi            30486  1 snd_seq_midi  
 mac80211              294370  1 ath9k  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event  
 drm_kms_helper         42136  1 i915  
 eeepc_wmi              19323  0  
 snd_timer              29602  2 snd_pcm,snd_seq  
 joydev                 17606  0  
 sparse_keymap          13898  1 eeepc_wmi  
 snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq  
 ath9k_common           13851  1 ath9k  
 ath9k_hw              323077  2 ath9k,ath9k_common  
 uvcvideo               72195  0  
 ath                    23773  2 ath9k,ath9k_hw  
 drm                   227495  4 i915,drm_kms_helper  
 cfg80211              178528  3 ath9k,mac80211,ath  
 videodev               82052  1 uvcvideo  
 snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                73535  0  
 v4l2_compat_ioctl32    17078  1 videodev  
 serio_raw              13166  0  
 i2c_algo_bit           13400  1 i915  
 soundcore              12680  1 snd  
 video                  19438  1 i915  
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm  
 lp                     17825  0  
 parport                46458  3 parport_pc,ppdev,lp  
 usb_storage            53538  0  
 uas                    17996  0  
 ahci                   25951  1  
 libahci                26642  1 ahci  
 atl1c                  41171  0  
 boss@ubuntu:~$ lspci -nn  
 00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]  
 00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]  
 00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]  
 00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)  
 00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)  
 00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)  
 00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)  
 00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)  
 00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)  
 00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)  
 00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)  
 00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)  
 00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)  
 00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02) 
 00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)  
 01:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)  
 02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)  
 boss@ubuntu:~$ rfkill list all  
 0: eeepc-wlan: Wireless LAN  
 	Soft blocked: no  
 	Hard blocked: no  
 1: phy0: Wireless LAN  
 	Soft blocked: no  
 	Hard blocked: no  
 boss@ubuntu:~$

---

### Post by wildmanne39 on 2011-07-25
Hi, where did this connection come from?
> wlan0 IEEE 802.11bgn ESSID:"dunnes"
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=17 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff 
Thank you

---

### Post by andydunne on 2011-07-26
Thats our home router. It sees it but won't connect to the internet or collect email. I'm puzzled 'cos it connected no problem the first time I installed ubuntu 10.10 and am currently online using windows. I have the WEP key and previously connected two laptops and the wii without any major problems to the router.

---

### Post by wildmanne39 on 2011-07-26
Hi, would you please run these commands in a terminal please.
```
modinfo ath9k
```
```
dmesg | grep ath

```
and post the results here.
thank you

---

### Post by andydunne on 2011-07-27
boss@ubuntu:~$ modinfo ath9k  
 filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
 license:        Dual BSD/GPL  
 description:    Support for Atheros 802.11n wireless LAN cards.  
 author:         Atheros Communications  
 srcversion:     01818FC37C72588C93B13E4 
 alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*  
 alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*  
 alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*  
 alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*  
 alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*  
 alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*  
 alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*  
 alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*  
 alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*  
 alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*  
 alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*  
 depends:        ath9k_hw,mac80211,cfg80211,ath9k_common,ath  
 vermagic:       2.6.38-8-generic SMP mod_unload modversions  
 parm:           debug:Debugging mask (uint)  
 parm:           nohwcrypt:Disable hardware encryption (int)  
 parm:           blink:Enable LED blink on activity (int)  
 parm:           btcoex_enable:Enable wifi-BT coexistence (int)  
 

 boss@ubuntu:~$ dmesg i grep ath  
 Usage: dmesg [-c] [-n level] [-r] [-s bufsize]  
 boss@ubuntu:~$ dmesg l grep ath  
 Usage: dmesg [-c] [-n level] [-r] [-s bufsize]  
 boss@ubuntu:~$ dmesg 1 grep ath  
 Usage: dmesg [-c] [-n level] [-r] [-s bufsize]

---

### Post by wildmanne39 on 2011-07-27
Hi, is your isp BT Hub?

```
dmesg | grep ath
```
copy and paste this command and see post the results here, the response in the last post is not what I expected.
Thank you

---

### Post by andydunne on 2011-07-28
ISP is local company Imagine.
Apologies for the last post, I wasn't sure whether it was a number or letter or what so I thought I'd tried them all. See now the one I missed. Thanks again for your time

 [COLOR=#000000][FONT=Calibri][SIZE=2]boss@ubuntu:~$ dmesg | grep ath [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][    1.091322] device-mapper: multipath: version 1.2.0 loaded [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][    1.091332] device-mapper: multipath round-robin: version 1.0.0 loaded [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   16.723370] ath9k 0000:02:00.0: enabling device (0000 -> 0002) [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   16.723395] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   16.723423] ath9k 0000:02:00.0: setting latency timer to 64 [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   16.776939] ath: EEPROM regdomain: 0x60 [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   16.776949] ath: EEPROM indicates we should expect a direct regpair map [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   16.776959] ath: Country alpha2 being used: 00 [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   16.776964] ath: Regpair used: 0x60 [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   16.998170] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control' [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   17.000216] Registered led device: ath9k-phy0::radio [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   17.000319] Registered led device: ath9k-phy0::assoc [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   17.000426] Registered led device: ath9k-phy0::tx [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2][   17.000517] Registered led device: ath9k-phy0::rx [/SIZE][/FONT][/COLOR]

---

### Post by wildmanne39 on 2011-07-28
Hi, run these commands please
```
dmesg | grep wlan0
```
```
dmesg | grep firmware
```
```
sudo iwlist scan
```
and post the results here.
Thank you

---

### Post by andydunne on 2011-07-28
Here we go again


boss@ubuntu:~$ dmesg | grep wlan0  
 [   20.845495] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [   36.270081] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [   36.272146] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 [   47.452793] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [   47.458020] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 [   58.651950] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [   58.654485] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 [   69.845325] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [   69.847559] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 [   81.024977] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [   81.026934] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 [   92.235609] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [   92.237537] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 [  103.134151] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [  103.138165] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 [  114.339714] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [  114.341935] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 [  125.561416] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [  125.563534] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 [  136.768667] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [  136.772501] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 [  147.974450] wlan0: authenticate with 00:17:3f:e3:a7:ab (try 1)  
 [  147.976453] wlan0: 00:17:3f:e3:a7:ab denied authentication (status 13)  
 boss@ubuntu:~$ dmesg | grep firmware  
 boss@ubuntu:~$ sudo iwlist scan  
 [sudo] password for boss:  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 wlan0     Scan completed :  
           Cell 01 - Address: 00:17:3F:E3:A7:AB  
                     Channel:1  
                     Frequency:2.412 GHz (Channel 1)  
                     Quality=33/70  Signal level=-77 dBm   
                     Encryption key:on  
                     ESSID:"dunnes" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s  
                               12 Mb/s; 24 Mb/s; 36 Mb/s  
                     Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s  
                     Mode:Master  
                     Extra:tsf=0000004bd052cf1d  
                     Extra: Last beacon: 990ms ago  
                     IE: Unknown: 000664756E6E6573  
                     IE: Unknown: 010882848B960C183048  
                     IE: Unknown: 030101 
                     IE: Unknown: 07064E4C20010D14  
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32041224606C  
                     IE: Unknown: DD0900037F01010008FF7F  
                     IE: Unknown: DD1A00037F030100000000173FE3A7AB02173FE3A7AB64002C010808  
           Cell 02 - Address: 00:0F:CC:D9:51:D4  
                     Channel:9  
                     Frequency:2.452 GHz (Channel 9)  
                     Quality=20/70  Signal level=-90 dBm   
                     Encryption key:on  
                     ESSID:"Unimatrix0" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s  
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s  
                               36 Mb/s; 48 Mb/s; 54 Mb/s  
                     Mode:Master  
                     Extra:tsf=000000c0cde2c1b6  
                     Extra: Last beacon: 500ms ago  
                     IE: Unknown: 000A556E696D617472697830  
                     IE: Unknown: 010582848B962C  
                     IE: Unknown: 030109 
                     IE: Unknown: 2A0104 
                     IE: IEEE 802.11i/WPA2 Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (1) : CCMP  
                         Authentication Suites (1) : PSK  
                     IE: Unknown: 32080C1218243048606C  
                     IE: WPA Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (1) : TKIP  
                         Authentication Suites (1) : PSK  
           Cell 03 - Address: 00:23:F8:D7:0C:B0  
                     Channel:11  
                     Frequency:2.462 GHz (Channel 11)  
                     Quality=29/70  Signal level=-81 dBm   
                     Encryption key:on  
                     ESSID:"eircom07980083"  
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s  
                               11 Mb/s; 12 Mb/s; 18 Mb/s  
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s  
                     Mode:Master  
                     Extra:tsf=000002cd57e48184  
                     Extra: Last beacon: 330ms ago  
                     IE: Unknown: 000E656972636F6D3037393830303833  
                     IE: Unknown: 010882848B0C12961824  
                     IE: Unknown: 03010B 
                     IE: Unknown: 0706474220010D14  
                     IE: Unknown: 200100 
                     IE: WPA Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (1) : TKIP  
                         Authentication Suites (1) : PSK  
                     IE: Unknown: 2A0102 
                     IE: Unknown: 32043048606C  
           Cell 04 - Address: 00:16:01:B1:19:9B  
                     Channel:7  
                     Frequency:2.442 GHz (Channel 7)  
                     Quality=21/70  Signal level=-89 dBm   
                     Encryption key:off  
                     ESSID:""  
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s  
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s  
                               36 Mb/s; 48 Mb/s; 54 Mb/s  
                     Mode:Master  
                     Extra:tsf=000000062a08925c  
                     Extra: Last beacon: 660ms ago  
                     IE: Unknown: 0000  
                     IE: Unknown: 010482840B16  
                     IE: Unknown: 030107 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 32080C1218243048606C  
                     IE: Unknown: 050400030000

---

### Post by wildmanne39 on 2011-07-28
Hi, have a look at this link I believe it is post 17 where I give instructions on what may fix this problem. Try what the post says and let me know if it fixes your problem.
[http://ubuntuforums.org/showthread.php?p=11093299#post11093299](http://ubuntuforums.org/showthread.php?p=11093299#post11093299)
Thank you

---

### Post by andydunne on 2011-07-29
Hi wildmanne,
that link just brought me to the forum home page. Some additional info, I brought the netbook to work and connected via ethernet fine, i connected via ethernet direct from modem fine but would not connect via ethernet through the router

---

### Post by wildmanne39 on 2011-07-29
Hi, ok that link was correct but there must have been a glitch when I put it in the thread, but I took it out and put it back in and now it works, so you can click on the link in my previous post.

I am sorry about the glitch.

---

### Post by bkratz on 2011-07-29
> **wildmanne39 said:**
> Hi, ok that link was correct but there must have been a glitch when I put it in the thread, but I took it out and put it back in and now it works, so you can click on the link in my previous post.

I am sorry about the glitch.


@Wildmanne39, I believe i noticed in the post 11 that all his/her AP's are listed as mode:master rather than managed.

---

### Post by wildmanne39 on 2011-07-29
@bkratz
Hi, you are right thank you!!! I missed that.

@andydunne
Before you do anything else to get your internet working you need to change mode master to managed by entering these commands.
```
sudo ifconfig wlan0 down
```
```
sudo iwconfig wlan0 mode Managed
```
```
sudo ifconfig wlan0 up
```

---

### Post by andydunne on 2011-08-07
Sorry Wildmanne, been away from home for a few days. New development, haven't had a chance to try your last post yet but was in my parents and connected to their WPA router no problem

---

### Post by wildmanne39 on 2011-08-07
Hi, I believe this will fix your problem.

Set wpa/wpa2 to just wpa2.

Run this command.
```
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
```
Thank you

---

### Post by andydunne on 2011-08-07
Hi Wildmanne

I'm home again and back trying to connect to my WEP encrypted Belkin router
Here's the results from your last post

andy@ubuntu:~$ sudo rmmod-f ath9k  
 [sudo] password for andy:  
 sudo: rmmod-f: command not found  
 andy@ubuntu:~$ sudo modprobe ath9k nohwcrypt=1  
 andy@ubuntu:~$

---

### Post by wildmanne39 on 2011-08-07
Hi, just copy and paste the commands, the first command needs a space between the d and the -f.

---

### Post by andydunne on 2011-08-08
@ wildmanne

No joy with those. Still the same result. Will try to install WICD again later

---

### Post by wildmanne39 on 2011-08-08
Hi, did you change your wep to just wpa2?
Thank you

---

### Post by andydunne on 2011-08-08
@Wildmanne

Yes sorted. Thanks very much. Who'd have thought it would be something so simple. Now how do I mark it as solved

---

### Post by wildmanne39 on 2011-08-08
Hi, your welcome! I am glad it is working now, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by airper on 2011-08-12
Hi wildmanne39, 

I've got a very similar problem with my wireless connection on a Toshiba Satellite R830-145. Same Wireless card. I've followed your instructions numerous times, but I don't seem to be able to get out of master mode.

Up to post 15 just about everything is the same, but if I run the code in post 16 and then run sudo iwlist scan, the card is still in Mode: Master. I've posted the code from iwlist scan below. Could you give any advice. I've struggled with this for a couple of weeks now and here I though I'd found a solution.

```

wayne@wayne-SATELLITE-R830:~$ sudo iwconfig wlan0 power off
wayne@wayne-SATELLITE-R830:~$ sudo ifconfig wlan0 down
wayne@wayne-SATELLITE-R830:~$ sudo iwconfig wlan0 mode Managed
wayne@wayne-SATELLITE-R830:~$ sudo ifconfig wlan0 up
wayne@wayne-SATELLITE-R830:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:8B:5D:9C:E6:5A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-R22X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000056024052fb6
                    Extra: Last beacon: 830ms ago
                    IE: Unknown: 000F4254486F6D65487562322D52323258
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:26:44:20:03:AB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"PlusnetWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000052a90ab3f
                    Extra: Last beacon: 590ms ago
                    IE: Unknown: 000F506C75736E6574576972656C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD870050F204104A0001101044000102103B00010310470010931C1243B5D35E1FA5FF38EF865479561021000754484F4D534F4E1023000A54686F6D736F6E20544710240006353835207637104200093130303153464752501054000800060050F20400011011001054686F6D736F6E20544735383520763710080002008410570001001041000100
                    IE: Unknown: DD060010180201F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```

---

