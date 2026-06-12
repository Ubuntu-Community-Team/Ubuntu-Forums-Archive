---
title: "Ibm t40, 2wire router, bad password on wireless connection"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by Zarny on 2011-07-17
Hi all,

I'm new to ubuntu so bear with me, please. I got an IBM T40 laptop with 10.04 ubuntu and 2wire router. I can see the wireless network in network manager, try to connect, but get back msg that my password is bad. All other devices connect with same password (10 digit password written on routers label). Wired connection has no problems at all.

P.S. I read the forums and tried some solutions, but I think I messed up more than helped the problem.

1.
prem@prem-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
prem@prem-laptop:~$ 

2.
prem@prem-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
prem@prem-laptop:~$ 

3.
prem@prem-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:60:37:27:cb  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fe37:27cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2710220 (2.7 MB)  TX bytes:284165 (284.1 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:8a:ba:5a:f3  
          inet6 addr: fe80::202:8aff:feba:5af3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:604 dropped:0 overruns:0 frame:604
          TX packets:37 errors:37 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2494 (2.4 KB)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

prem@prem-laptop:~$ 

4.
prem@prem-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-93 dBm
          Rx invalid nwid:1912  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7595   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-93 dBm
          Rx invalid nwid:1912  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7595   Missed beacon:0

prem@prem-laptop:~$ 


5.
prem@prem-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
pcmcia                 30784  0 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
joydev                  8740  0 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
thinkpad_acpi          68083  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                677684  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
yenta_socket           20408  2 
snd                    54244  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,thinkpad_acpi,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29329  1 radeon
airo                   67901  0 
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
nsc_ircc               18220  0 
video                  17375  0 
ppdev                   5259  0 
psmouse                63245  0 
intel_agp              24375  1 
led_class               2864  1 thinkpad_acpi
drm                   162377  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
soundcore               6620  1 snd
output                  1871  1 video
irda                  186844  1 nsc_ircc
crc_ccitt               1339  1 irda
serio_raw               3978  0 
parport_pc             25962  1 
nvram                   6203  1 thinkpad_acpi
agpgart                31724  3 ttm,intel_agp,drm
shpchp                 28835  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
e100                   28211  0 
mii                     4381  1 e100
prem@prem-laptop:~$ 


6.
dmesg gives so much info that I cant see the beginning of it in terminal window

7.
prem@prem-laptop:~$ sudo lshw -C network
[sudo] password for prem: 
  *-network:0 DISABLED    
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:ba:5a:f3
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0200000-c0203fff memory:c0400000-c07fffff memory:c0800000-c09fffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:37:27:cb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.71 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:c0204000-c0204fff ioport:8400(size=64)
prem@prem-laptop:~$


8.
prem@prem-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:3F:29:6D:F9
                    ESSID:"DontMessWithIt"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-31 dBm  Noise level:-93 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

wifi0     Scan completed :
          Cell 01 - Address: 00:18:3F:29:6D:F9
                    ESSID:"DontMessWithIt"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-31 dBm  Noise level:-93 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

prem@prem-laptop:~$ 


9.
prem@prem-laptop:~$ lsb_release -d
Description:    Ubuntu 10.04.2 LTS
prem@prem-laptop:~$ 


10.
prem@prem-laptop:~$ uname -mr
2.6.32-32-generic i686
prem@prem-laptop:~$

---

### Post by bkratz on 2011-07-17
eth1 Scan completed :
Cell 01 - Address: 00:18:3F:29:6D:F9
ESSID:"DontMessWithIt"
[COLOR="Red"]Mode:Master[/COLOR]
Frequency:2.437 GHz (Channel 6)
Quality=100/100 Signal level=-31 dBm Noise level:-93 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Extra:bcn_int=100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK


Perhaps you meant to use master mode ( I doubt it though! it is used to make an AP (access point).  Perhaps it is something you changed during your efforts.
Anyway, I believe you should start with [COLOR="Red"]managed[/COLOR] mode and go from there.

sudo iwconfig eth1 mode Managed

to get back to a starting point

See the section in terminal using man iwconfig which stands for manual iwconfig for details.

man iwconfig

---

### Post by Zarny on 2011-07-17
changed it to "managed", but problem persists

---

### Post by tgalati4 on 2011-07-17
Many times connections problems are with "Shared" or "Restricted" key versus "Open" key.

Try in a terminal:

sudo iwconfig eth1 key restricted

Then try logging in again.

---

### Post by bkratz on 2011-07-18
> **Zarny said:**
> changed it to "managed", but problem persists



You might also want to look at

sudo iwlist eth1 auth  

 -tells about encryption capabilities

---

### Post by Zarny on 2011-07-18
> **tgalati4 said:**
> Many times connections problems are with "Shared" or "Restricted" key versus "Open" key.

Try in a terminal:

sudo iwconfig eth1 key restricted

Then try logging in again.


still no cigar

---

### Post by Zarny on 2011-07-18
> **bkratz said:**
> You might also want to look at

sudo iwlist eth1 auth  

 -tells about encryption capabilities


prem@prem-laptop:~$ sudo iwlist eth1 auth 
eth1      unknown authentication information.



prem@prem-laptop:~$

---

### Post by Zarny on 2011-07-19
please someone help me. this is so  frustrating...no wireless

---

