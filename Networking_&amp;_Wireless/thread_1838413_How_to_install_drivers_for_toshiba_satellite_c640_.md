---
title: "How to install drivers for toshiba satellite c640 laptop??"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by lalitha niharika on 2011-09-03
I dual booted my laptop with windows 7 and ubuntu 10.10.I installed all windows 7 drivers from toshiba official website, all hardware are working nicely in windows.In ubuntu, auto etho connection establishes immediately after connecting it to airtel broadband, but after sometime, it doesn't work.None of the other hardwares is working.(webcam, wifi, wired connection).I think, bluetooth is working because I could see bluetooth icon.Ubuntu is not recognizing graphic card, I am unable to use compiz.So I would request you to tell me the names of drivers which are needed to be installed and also please mention how to install, where to download them.Thanks in advance.I would like to mention onemore thing.If you suggest me to add wireless connection, I cant do that because I don't know any of the details of our wifi.

---

### Post by josephmills on 2011-09-03
Hi there lets start by looking at some of you hardware please open your terminal and type in 

```
lspci -nn 
``````
lsusb
``````
rfkill list all 
``````
lsmod
``````
cat /etc/modprobe.d/blacklist.conf
``` then paste here thanks

---

### Post by lalitha niharika on 2011-09-03
lalitha@lalitha-Satellite-C640:~$ lspci -nn
 00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0104] (rev 09)
 00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0116] (rev 09)
 00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
 00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
 00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 04)
 00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b4)
 00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b4)
 00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
 00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c49] (rev 04)
 00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 04)
 00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 04)
 01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
 02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
 lalitha@lalitha-Satellite-C640:~$ lsusb
 Bus 002 Device 003: ID 0930:0215 Toshiba Corp.  
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 001 Device 004: ID 10f1:1a34   
 Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp.  
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 lalitha@lalitha-Satellite-C640:~$ rfkill list all
 0: hci0: Bluetooth
 	Soft blocked: no
 	Hard blocked: no
 1: phy0: Wireless LAN
 	Soft blocked: no
 	Hard blocked: yes
 lalitha@lalitha-Satellite-C640:~$ lsmod
 Module                  Size  Used by
 binfmt_misc             6599  1  
 sco                     7998  2  
 bnep                    9542  2  
 l2cap                  37008  3 bnep
 parport_pc             26058  0  
 ppdev                   5556  0  
 joydev                  8767  0  
 snd_hda_intel          22235  2  
 snd_hda_codec          87552  1 snd_hda_intel
 snd_hwdep               5040  1 snd_hda_codec
 snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
 snd_seq_midi            4588  0  
 snd_rawmidi            17783  1 snd_seq_midi
 arc4                    1165  2  
 snd_seq_midi_event      6047  1 snd_seq_midi
 snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
 ath9k                  88916  0  
 i915                  295819  3  
 ath9k_common            5982  1 ath9k
 ath9k_hw              292329  2 ath9k,ath9k_common
 ath                     8153  2 ath9k,ath9k_hw
 mac80211              231927  2 ath9k,ath9k_common
 snd_timer              19067  2 snd_pcm,snd_seq
 snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
 uvcvideo               55911  0  
 videodev               43098  1 uvcvideo
 v4l1_compat            13359  2 uvcvideo,videodev
 toshiba_bluetooth       1723  0  
 btusb                  11001  0  
 drm_kms_helper         30136  1 i915
 drm                   168092  3 i915,drm_kms_helper
 snd                    49102  12 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
 bluetooth              50500  6 sco,bnep,l2cap,btusb
 cfg80211              144822  4 ath9k,ath9k_common,ath,mac80211
 led_class               2633  1 ath9k
 psmouse                59033  0  
 i2c_algo_bit            5168  1 i915
 intel_agp              26566  2 i915
 video                  18712  1 i915
 soundcore                880  1 snd
 serio_raw               4022  0  
 snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
 output                  1883  1 video
 agpgart                32011  2 drm,intel_agp
 lp                      7342  0  
 parport                31492  3 parport_pc,ppdev,lp
 usb_storage            40492  0  
 ahci                   19326  2  
 atl1c                  29949  0  
 libahci                21728  1 ahci
 lalitha@lalitha-Satellite-C640:~$ cat /etc/modprobe.d/blacklist.conf
 # This file lists those modules which we don't want to be loaded by
 # alias expansion, usually so some other driver will be loaded for the
 # device instead.
 

 # evbug is a debug tool that should be loaded explicitly
 blacklist evbug
 

 # these drivers are very simple, the HID drivers are usually preferred
 blacklist usbmouse
 blacklist usbkbd
 

 # replaced by e100
 blacklist eepro100
 

 # replaced by tulip
 blacklist de4x5
 

 # causes no end of confusion by creating unexpected network interfaces
 blacklist eth1394
 

 # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
 # hardware on its own (Ubuntu bug #2011, #6810)
 blacklist snd_intel8x0m
 

 # Conflicts with dvb driver (which is better for handling this device)
 blacklist snd_aw2
 

 # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
 blacklist i2c_i801
 

 # replaced by p54pci
 blacklist prism54
 

 # replaced by b43 and ssb.
 blacklist bcm43xx
 

 # most apps now use garmin usb driver directly (Ubuntu: #114565)
 blacklist garmin_gps
 

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

---

### Post by josephmills on 2011-09-03
[COLOR=Red]02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01[/COLOR])
 
 1: phy0: Wireless LAN
     Soft blocked: no
   [COLOR=Red]  Hard blocked: yes[/COLOR]
 
 [COLOR=Red]ath9k                  88916  0[/COLOR]  
   
 [COLOR=Red]ath9k_common            5982  1 ath9k
 ath9k_hw              292329  2 ath9k,ath9k_common
 ath                     8153  2 ath9k,ath9k_hw[/COLOR]
 [COLOR=Red]mac80211              231927  2 ath9k,ath9k_common[/COLOR]
 
 [COLOR=Red]cfg80211              144822  4 ath9k,ath9k_common,ath,mac80211[/COLOR]
 [COLOR=Red]led_class               2633  1 ath9k[/COLOR]
 



ok this is what I see you ave a [COLOR=Red] Atheros [COLOR=Black]wireless card 
which needs the ath9k and it dependece which it has 

here is the real trouble 
[/COLOR][/COLOR]
 1: phy0: Wireless LAN
     Soft blocked: no
   [COLOR=Red]  Hard blocked: yes[/COLOR]
 


that shows us that the wireless switch is tuned  off
you need to find the wireless switch and turn it in and you wireless should work.  :popcorn:

---

### Post by lalitha niharika on 2011-09-04
but I am not finding any switch here:(..why my autoetho is disconnecting everytime after using it for some time?

---

### Post by fdrake on 2011-09-04
i think the switch key is Fn+F8 button. Test it in windows first to double check. Then if it is right run it in ubuntu few times and type:
rfkill list all . try this untill u see

> 1: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]**_Hard blocked: no_**[/COLOR]

also since you have so many issues have you tried other versions of ubuntu with a live cd?
i also suggest you to enable all your repositories and get all the available updates.
to enable the repositories : [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

to get updates:
```

sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) linux-backports-modules-wireless-$(less /etc/lsb-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f 2)-$(uname -r | cut -d "-" -f 3)
sudo aptitude update
sudo aptitude upgrade

```
and reboot. check if something else is working.

---

### Post by lalitha niharika on 2011-09-04
yes!!I got hard block:no by clicking f8,fn...thanks a lot!!:Pbut please help me to solve wired network problem...it shows that autoetho connection established, but I am unable to browse!firefox shows server not found message:confused:

---

### Post by fdrake on 2011-09-04
> **lalitha niharika said:**
> yes!!I got hard block:no by clicking f8,fn...thanks a lot!!:Pbut please help me to solve wired network problem...it shows that autoetho connection established, but I am unable to browse!firefox shows server not found message:confused:

i am assuming the wif is working now, so i will leave that on the side for now.

can you please post the results for :
(while connected with the wire and disconnected with the wifi)
```

nm-tool
ifconfig
lshw -c network

```

---

### Post by lalitha niharika on 2011-09-04
Even I have to assume that wifi is working.I can really test it tomorrow as i dont have wifi at home.

lalitha@lalitha-Satellite-C640:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        00:26:6C:D2:C0:BB

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        E0:CA:94:2F:D9:3C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


lalitha@lalitha-Satellite-C640:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:6c:d2:c0:bb  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fed2:c0bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1530 errors:3 dropped:0 overruns:0 frame:1
          TX packets:1526 errors:0 dropped:0 overruns:0 carrier:1
          collisions:14 txqueuelen:1000 
          RX bytes:1559538 (1.5 MB)  TX bytes:264554 (264.5 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:820 (820.0 B)  TX bytes:820 (820.0 B)

lalitha@lalitha-Satellite-C640:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:d2:c0:bb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.1.4 latency=0 multicast=yes
       resources: irq:45 memory:90500000-9053ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: e0:ca:94:2f:d9:3c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-30-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90400000-9040ffff
lalitha@lalitha-Satellite-C640:~$

---

### Post by lalitha niharika on 2011-09-04
just now I found something.My problem is with server, not network.i am unable to install many softwares in ubuntu center.no I tried changing server.It is showing updating catche, but nothing is moving.It is not downloading anything.What should I do?I tried three times to change different servers.none of the server is allowing download.

---

### Post by fdrake on 2011-09-04
> **lalitha niharika said:**
> just now I found something.My problem is with server, not network.i am unable to install many softwares in ubuntu center.no I tried changing server.It is showing updating catche, but nothing is moving.It is not downloading anything.What should I do?I tried three times to change different servers.none of the server is allowing download.

phee....  as a matter of fact I locked several times to your posts but i could not find any errors with the wired connection! 
And i don't know what you mean by "Ubuntu Center", you mean synaptic ?

Ps: your wifi network shows DISABLED! let's leave that for the end.

---

### Post by lalitha niharika on 2011-09-04
i am unable to update or upgrade!!

---

### Post by lalitha niharika on 2011-09-04
ubuntu centre means ubuntu software centre.I think wired connection is all right, but it is not working because of server

---

### Post by fdrake on 2011-09-04
> **lalitha niharika said:**
> i am unable to update or upgrade!!

so you are online with fireofx but you cannot connect to the ubuntu servers?

can ypu post the results for:

```
sudo aptitude autoclean
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by lalitha niharika on 2011-09-04
lalitha@lalitha-Satellite-C640:~$ sudo aptitude autoclean
[sudo] password for lalitha: 
sudo: aptitude: command not found
lalitha@lalitha-Satellite-C640:~$ sudp aptitude clean
No command 'sudp' found, did you mean:
 Command 'sup' from package 'sup' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'sfdp' from package 'graphviz' (main)
sudp: command not found
lalitha@lalitha-Satellite-C640:~$ sudp aptitude update
No command 'sudp' found, did you mean:
 Command 'sup' from package 'sup' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'sfdp' from package 'graphviz' (main)
sudp: command not found
lalitha@lalitha-Satellite-C640:~$ sudp aptitude upgrade
No command 'sudp' found, did you mean:
 Command 'sup' from package 'sup' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'sfdp' from package 'graphviz' (main)
sudp: command not found

---

### Post by lalitha niharika on 2011-09-04
now I am online.but sometimes even network problem occurs with mozilla.it shows server not found message.then I can again get network by restarting.I don't know why.I had no problems when I used ubuntu on my desktop.

---

### Post by fdrake on 2011-09-04
> **lalitha niharika said:**
> now I am online.but sometimes even network problem occurs with mozilla.it shows server not found message.then I can again get network by restarting.I don't know why.I had no problems when I used ubuntu on my desktop.

i am sorry i mistakenly typed sudp instead of sudo:

these are the right commands:

```
sudo aptitude autoclean
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by lalitha niharika on 2011-09-25
I just installed ubuntu again.Thanks for the help

---

