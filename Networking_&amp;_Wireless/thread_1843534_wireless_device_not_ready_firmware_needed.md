---
title: "wireless device not ready firmware needed"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by andar12345 on 2011-09-13
I just installed ubuntu 11.04 onto my Dell inpsiron 5100 laptop that was running windows xp. I used the wubi (?) that allowed me to keep windows because I wanted to test it out. Im glad I did because everything works fine except for my wireless internet connection. It works for windows but ubuntu cant find any connections. When I click the wireless button at top right it doesnt even let me click the wireless network stuff. I have the wireless enabled. It says something like : device not ready needs firmware. I have read through just about every single thread on this site, installed every freaking thing that everyone was saying to install and nothing works. I am not currently on the computer in question but will be soon and the ethernet connection works so I can post the lspci //seems like thats what everyone asks for .
Let me know anything else you need to see to help me please. I am just learning my way around linux systems and want to get rid of windows.

Thank you everybody

---

### Post by praseodym on 2011-09-13
Hi,

please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
```

---

### Post by andar12345 on 2011-09-14
Here are the results. Sorry it took so long. Thank you for helping me.




lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
    Subsystem: Device [4401:1028]
    Kernel driver in use: b44
--
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
    Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card [1028:0001]
    Kernel driver in use: b43-pci-bridge


lsmod
Module                  Size  Used by
parport_pc             32111  0 
binfmt_misc            13213  1 
ppdev                  12849  0 
snd_intel8x0           33213  2 
radeon                896428  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
b43legacy             127415  0 
snd_rawmidi            25269  1 snd_seq_midi
ttm                    65184  1 radeon
mac80211              257001  1 b43legacy
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
dcdbas                 14054  0 
drm                   180037  4 radeon,ttm,drm_kms_helper
cfg80211              156212  2 b43legacy,mac80211
yenta_socket           27230  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
shpchp                 32345  0 
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
b44                    35301  0 
firewire_ohci          31504  0 
ssb                    45942  2 b43legacy,b44
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

 rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
//smiling faces? i did not do that. ...

---

### Post by praseodym on 2011-09-15
Mark your text and klick on the # Button in Advanced Mode to convert into code-tags.

You only need to install the firmware via

```
sudo apt-get install b43-fwcutter firmware-b43legacy-installer
```

---

### Post by andar12345 on 2011-09-16
Did not seem to work

s```
udo apt-get install b43-fwcutter firmware-b43legacy-installer
[sudo] password for administrator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43legacy-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up firmware-b43legacy-installer (4.178.10.4-5) ...
Not supported card here (PCI id 14e4:4401
14e4:4320)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43legacy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by praseodym on 2011-09-16
```
sudo apt-get remove --purge firmware-b43legacy-installer
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```should do the trick.

---

### Post by andar12345 on 2011-09-19
Still does not work. I restarted computer after typing in the lines you gave me. It did however change the look of the desktop. The toolbar at the top of the screen used to be black now it is gray and the icons have the same function but have changed appearance. When I click the network icon it still will not let me click on wireless networks. Underneath it still says device not ready(firmware missing)  Im sorry for being a pain in the ***. Unless you have any other suggestions I do not think it was meant to be. Thank you for helping me. let me know if you have any other ideas.

---

### Post by praseodym on 2011-09-19
Take the firmware from here:

```
wget http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz 
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

