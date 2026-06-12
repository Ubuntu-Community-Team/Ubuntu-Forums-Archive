---
title: "Hercules Wireless USB WiFi N150 Pico (HWNUp-150) - No Drivers"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by kafedzou on 2010-10-24
Hi everybody, 

I recently bought a Hercules Wireless USB WiFi N150 Pico (HWNUp-150). I'm currently using Ubuntu 10.04 LTS. Unfortunately, Ubuntu does not recognise the USB WiFi stick and there were no Linux drivers included. 

Information: 
**1 ) Machine Brand and Model (PC/Laptop)**:
```
NO BRAND

```[B]
2 ) Wireless Brand, Model and Wireless Chipset:[/B]
 ```
$ lsusb

Bus 001 Device 002: ID 06f8:e033 Guillemot Corp.
```[B]
3 ) check interface:[/B]
```
$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0b:6a:af:08:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24538 (24.5 KB)  TX bytes:24538 (24.5 KB)


``````
$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

```[B]

4 ) Check for modules:[/B]
     ```
$ lsmod 

Module                  Size  Used by
binfmt_misc             6587  1 
nfsd                  238967  11 
lockd                  64849  1 nfsd
nfs_acl                 2245  1 nfsd
auth_rpcgss            33735  1 nfsd
sunrpc                193085  10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3437  1 nfsd
snd_via82xx            20058  2 
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
vga16fb                11385  0 
snd_mpu401_uart         5617  1 snd_via82xx
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                674824  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
snd                    54148  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
drm_kms_helper         29297  1 radeon
via_agp                 5310  1 
drm                   162377  5 radeon,ttm,drm_kms_helper
agpgart                31724  3 ttm,via_agp,drm
i2c_algo_bit            5028  1 radeon
ns558                   3056  0 
gameport                9089  3 snd_via82xx,ns558
shpchp                 28820  0 
i2c_viapro              5573  0 
ppdev                   5259  0 
parport_pc             25962  1 
psmouse                63245  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
via_rhine              19154  0 
pata_via                7272  2 
mii                     4381  1 via_rhine
sata_via                6945  0 
```[B]
5 ) Kernel boot messages[/B]
     ```
$ dmesg 

Too much output, with grep, no output
```**6 ) Network configuration**
     ```
$ sudo lshw -C network 

       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:0b:6a:af:08:53
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:d400(size=256) memory:ffeffc00-ffeffcff
```[B]
7 ) Scan for networks:[/B]
     ```
$ iwlist scan 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```**8 ) Ubuntu Version: **
     ```
$ lsb_release -d

Description:    Ubuntu 10.04.1 LTS
```[B]
9 ) Kernel/architecture (including 32 vs. 64 bit): [/B]
     ```
$ uname -mr

2.6.32-24-generic i686
```**10 ) Restarting the network:**
     ```
$ sudo /etc/init.d/networking restart

* Reconfiguring network interfaces...                                                                                                                [ OK ]
```If someone knows how to fix this or knows where I can find the correct drivers, please let me know. 

Thanks in advance,
K.

---

### Post by Der Ritter on 2010-10-24
Hercules devices can apparently work with ndiswrapper. Try following [these instructions]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Hercules_HWGum-54"). Use [this exe]("http://ts.hercules.com/download/wifi/drivers/HWNUp-150/HWNUp-150_v6.0.exe") instead of the one linked from the instructions. You will need access to a Windows XP computer and some sort of removable media to copy the required files.

---

### Post by kafedzou on 2010-10-25
Thanks for your reply Der Ritter, 

But I have one problem: I don't have access to a Windows XP computer and I don't have LAN access as well. 

Is there a possibility to do this without Windows? I have an installation CD-ROM with drivers for Windows. Perhaps I can do something with that? 

Content of CD: 
```
.:
totaal 688
dr-x------ 1 xxxxxx xxxxxx   2048 2010-05-28 17:25 .
drwxr-xr-x 3 root   root     4096 2010-10-25 13:41 ..
-r-------- 1 xxxxxx xxxxxx 557294 2010-05-26 17:29 autorun.ico
-r-------- 1 xxxxxx xxxxxx     45 2004-11-19 11:47 autorun.inf
dr-x------ 1 xxxxxx xxxxxx   2048 2010-05-28 17:25 Bin
-r-------- 1 xxxxxx xxxxxx 136744 2007-03-07 14:54 Setup.exe
-r-------- 1 xxxxxx xxxxxx    372 2010-03-24 18:03 Setup.ini

./Bin:
totaal 392403
dr-x------ 1 xxxxxx xxxxxx      2048 2010-05-28 17:25 .
dr-x------ 1 xxxxxx xxxxxx      2048 2010-05-28 17:25 ..
-r-------- 1 xxxxxx xxxxxx  24756800 2007-12-07 14:58 AdbeRdr810_de_DE.exe
-r-------- 1 xxxxxx xxxxxx  23787520 2007-12-07 15:01 AdbeRdr810_es_ES.exe
-r-------- 1 xxxxxx xxxxxx  24536608 2007-12-07 14:57 AdbeRdr810_fr_FR.exe
-r-------- 1 xxxxxx xxxxxx  24024440 2007-12-07 15:03 AdbeRdr810_it_IT.exe
-r-------- 1 xxxxxx xxxxxx  24219056 2007-12-07 14:59 AdbeRdr810_nl_NL.exe
-r-------- 1 xxxxxx xxxxxx  24698760 2008-02-20 12:00 AdbeRdr810_ru_RU.exe
-r-------- 1 xxxxxx xxxxxx  23405072 2007-12-07 14:53 AdbeRdr811_en_US.exe
-r-------- 1 xxxxxx xxxxxx  22936416 2008-02-20 12:01 AdbeRdr812_pt_BR.exe
-r-------- 1 xxxxxx xxxxxx    528384 2004-10-22 04:37 demo32.exe
-r-------- 1 xxxxxx xxxxxx   1645320 2004-05-04 22:53 gdiplus.dll
-r-------- 1 xxxxxx xxxxxx 180456176 2010-05-28 14:45 setup.exe
-r-------- 1 xxxxxx xxxxxx   3657480 2010-05-28 16:53 User manualDEU.pdf
-r-------- 1 xxxxxx xxxxxx   3279951 2010-05-28 16:36 User manualENU.pdf
-r-------- 1 xxxxxx xxxxxx   3340302 2010-05-28 17:20 User manualESP.pdf
-r-------- 1 xxxxxx xxxxxx   3052878 2010-05-28 16:25 User manualFRA.pdf
-r-------- 1 xxxxxx xxxxxx   3312928 2010-05-28 17:19 User manualITA.pdf
-r-------- 1 xxxxxx xxxxxx   3445461 2010-05-28 16:54 User manualNLD.pdf
-r-------- 1 xxxxxx xxxxxx   2958261 2010-05-28 17:20 User manualPTG.pdf
-r-------- 1 xxxxxx xxxxxx   3324996 2010-05-28 17:21 User manualRUS.pdf
-r-------- 1 xxxxxx xxxxxx    436099 2010-05-18 18:35 WiFiLauncher.dbd
-r-------- 1 xxxxxx xxxxxx      7836 2010-05-20 12:49 Wifilauncher.txt
```Regards, 
K

---

### Post by fixeon on 2010-10-30
it might be a long shot but did you try that (RTL8192SU seems to be the chipset used in your key):
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by danadn on 2011-02-02
Did you finally manage to install it?

I have the same problem. I've made contact to the tech support and they told me that the chipset was _Realtek RTL8192CU_. So I went to realtek web and downloaded it, compiled it and voila! It started to show wifi's **BUT** the WPA one's had the name disabled, I couldn't select them so - the drivers doesn't work?

In the readme it puts that it works on 32bits kernel, and my ubuntu was 64bits **so** right now I'm gonna install the 32bits version, do all again and pray the penguin god.

---

### Post by danadn on 2011-02-03
Ok, so I got it working.

I had to reinstall ubuntu but the _32bits_ version. It's sad that Realtek doesn't release drivers for 64bits ¬¬

However the speed I get is slower than the speed I get on Windows 7... this is crazy

---

