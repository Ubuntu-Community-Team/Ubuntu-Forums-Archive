---
title: "Network Manager connects but cannot browse"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2011-11-15
Hi,

I am running Ubuntu 10.10 on an old laptop (Advent model 7094). Kernel is 2.6.35-30-generic i686. I am trying to connect with Vodafone USB modem model K3806-Z. Network Manager gives me "Connection established" but I cannot browse (Firefox) or send/receive emails (Evolution or Thunderbird).

Any help gratefully received.

---

### Post by rdh61 on 2011-11-15
Here is some info about my system:

  	 	 	 	p { margin-bottom: 0.08in; }  **lspci**
 

 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11) 
 00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) 
 00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25) 
 00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller 
 00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] 
 00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) 
 00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0) 
 00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 
 00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 
 00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller 
 00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91) 
 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter 
 

 

 **lsusb**
 

 Bus 003 Device 002: ID 1241:1166 Belkin MI-2150 Trust Mouse 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 006: ID 19d2:1015 ONDA Communication S.p.A.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 

 

 **ifconfig **
 

 eth0      Link encap:Ethernet  HWaddr 00:16:ec:18:a5:85   
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:19 Base address:0xd800  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:5420 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:5420 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:451794 (451.7 KB)  TX bytes:451794 (451.7 KB) 
  
 usb0      Link encap:Ethernet  HWaddr 02:ac:25:22:19:3f   
           inet addr:109.113.89.119  Bcast:109.113.89.119  Mask:255.255.255.255 
           inet6 addr: fe80::ac:25ff:fe22:193f/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:3978 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:172228 (172.2 KB) 
 

  
 **iwconfig **
 

 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 usb0      no wireless extensions. 
 

 

 **lsmod**
 

 Module                  Size  Used by 
 cdc_ether               4052  0  
 usbnet                 17376  1 cdc_ether 
 cdc_acm                15299  4  
 nls_iso8859_1           3261  1  
 nls_cp437               4931  1  
 vfat                    9201  1  
 fat                    48240  1 vfat 
 usb_storage            40492  1  
 binfmt_misc             6599  1  
 parport_pc             26058  0  
 ppdev                   5556  0  
 joydev                  8767  0  
 snd_intel8x0           25664  2  
 snd_ac97_codec         99227  1 snd_intel8x0 
 ac97_bus                1014  1 snd_ac97_codec 
 snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec 
 snd_seq_midi            4588  0  
 snd_rawmidi            17783  1 snd_seq_midi 
 snd_seq_midi_event      6047  1 snd_seq_midi 
 snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event 
 snd_timer              19067  2 snd_pcm,snd_seq 
 snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq 
 sis_agp                 4123  1  
 snd                    49102  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                59033  0  
 soundcore                880  1 snd 
 shpchp                 29886  0  
 snd_page_alloc          7120  2 snd_intel8x0,snd_pcm 
 agpgart                32011  1 sis_agp 
 serio_raw               4022  0  
 i2c_sis96x              3196  0  
 lp                      7342  0  
 parport                31492  3 parport_pc,ppdev,lp 
 usbhid                 36882  0  
 hid                    67742  1 usbhid 
 sis900                 17316  0  
 mii                     4425  2 usbnet,sis900 
  
 

 **sudo lshw -C network **
 

   *-network                
        description: Ethernet interface 
        product: SiS900 PCI Fast Ethernet 
        vendor: Silicon Integrated Systems [SiS] 
        physical id: 4 
        bus info: pci@0000:00:04.0 
        logical name: eth0 
        version: 91 
        serial: 00:16:ec:18:a5:85 
        size: 10MB/s 
        capacity: 100MB/s 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s 
        resources: irq:19 ioport:d800(size=256) memory:dfffc000-dfffcfff memory:dffc0000-dffdffff 
   *-network 
        description: Ethernet interface 
        physical id: 1 
        logical name: usb0 
        serial: 02:ac:25:22:19:3f 
        capabilities: ethernet physical 
        configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=109.113.89.119 link=yes multicast=yes 
 

 

 **iwlist scan**
 

 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 usb0      Interface doesn't support scanning. 
 

 

 **sudo /etc/init.d/networking restart**
 

 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by alexfish on 2011-11-15
can have a look here

[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490") 

look at reference to 

[LIST]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]**Mozilla Firefox ,**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]**if the browser is not working check the "Work Off line" is unchecked**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][B][URL="http://kb.mozillazine.org/Toolkit.networkmanager.disable"]
[/URL][/B][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]**Tip for the Mozzila Firefox fix ,After opening Firefox, try opening page "about:config"... Filter for "toolkit.networkmanager.disable"**[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]**Change the line to ....." toolkit.networkmanager.disable;true "**[/SIZE][/FONT]
[/LIST]
also could try
```
sudo su
printf "\niface eth111 inet dhcp\n" >> /etc/network/interfaces
```

Also look at

Note the:
{may also apply to Vodafone USB (K 3806-z)not tested (best go to last page)
and
[FONT=Verdana][SIZE=2]VMC and BMC connection manager {re vodafone mobile connect)

[SIZE=1]read from start
the link  version states 10.04 but did post where user installed and worked[/SIZE][B][SIZE=1]
[/SIZE][/B][/SIZE][/FONT]

---

