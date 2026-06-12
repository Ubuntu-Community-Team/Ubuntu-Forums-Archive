---
title: "Ubuntu 12.04.1 wireless problem"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by ken poy on 2012-11-13
hello,  i just updated my system to Ubuntu 12.04.1 from 10.04.1.  my major problem is no Wireless connections.  10.04.1 worked fine.  each time Fn+F2 was hit the wireless light and wireless connections would toggle on and off.  now in 12.04.1 Fn+F2 does not toggle wireless.  i know my wireless modem is working as i have another wireless application.
i have read problems relation to the wireless driver.

BroadCom  STA wireless driver is activated and in use. 

there are problems written about wireless drivers  not sure if they apply??

following is info requested for wireless problems:    thanks for your help   ken

1. Machine Dell Inspiron 1501 Laptop


2. ken@ken-Inspiron-1501:~$ lspci -nn | grep -i bcm
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
ken@ken-Inspiron-1501:~$ 

3.  ken@ken-Inspiron-1501:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:ac:b1:cc  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:feac:b1cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3228883 (3.2 MB)  TX bytes:281044 (281.0 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20608 (20.6 KB)  TX bytes:20608 (20.6 KB)

4. ken@ken-Inspiron-1501:~$ lsmod
Module                  Size  Used by
usblp                  17885  0 
usb_storage            39646  0 
uas                    17828  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13516  1 
b44                    31364  0 
ssb                    50691  1 b44
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
wl                   2646601  0 
snd_hda_codec_idt      60251  1 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                737789  1 
psmouse                72919  0 
sp5100_tco             13495  0 
soundcore              14635  1 snd
serio_raw              13027  0 
k8temp                 12905  0 
joydev                 17393  0 
i2c_piix4              13093  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lib80211               14040  1 wl
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
shpchp                 32325  0 
ati_agp                13242  0 
wmi                    18744  1 dell_wmi
lp                     17455  0 
video                  19068  0 
parport                40930  3 parport_pc,ppdev,lp
mac_hid                13077  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
pata_atiixp            12999  0 
usbhid                 41906  0 
hid                    77367  1 usbhid
ken@ken-Inspiron-1501:~$ 


5.  lots of msgs  need to narrow down

6.  ken@ken-Inspiron-1501:~$ sudo lshw -C network
[sudo] password for ken: 
PCI (sysfs) 


7.  ken@ken-Inspiron-1501:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


8.  ken@ken-Inspiron-1501:~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS


9.  ken@ken-Inspiron-1501:~$ uname -mr
3.2.0-29-generic-pae i686


10.  ken@ken-Inspiron-1501:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/NetworkManager.conf.
**** I had set managed to true as i did in 10.04.1 and wireless worked fine.
                                                                         [ OK ]

---

### Post by chili555 on 2012-11-13
Please check here. Notice your device is the same: 14e4:4311.> Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="Red"]14e4:4311[/COLOR]]The fix is the same.

[http://ubuntuforums.org/showthread.php?t=1997880](http://ubuntuforums.org/showthread.php?t=1997880)

---

### Post by ken poy on 2012-11-13
i applied the correction and it did fix my wireless problem..
many thanks      ken

---

### Post by chili555 on 2012-11-13
Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

