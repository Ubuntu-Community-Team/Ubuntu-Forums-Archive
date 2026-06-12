---
title: "Rfkill hard block in 9.10 with bcm4301"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by viherpeukalo on 2010-01-04
I can't get wireless working with Lucid Lynx or even Karmic Koala. On occasions I can get it on for a moment, but it'll be soon stopped by rfkill hard block switch. Pushing the wireless on/off button on the laptop does nothing.

Wireless works with 9.04


```
epssi@paska:~$ lspci -nn | grep Network
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)
epssi@paska:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
epssi@paska:~$ lspci -nn | grep Network
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)
epssi@paska:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:10:42:48  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

epssi@paska:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"hippiparatiisi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

epssi@paska:~$ lsmod
Module                  Size  Used by
aes_i586                8124  0 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
joydev                 10240  0 
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
arc4                    1660  2 
snd_seq_dummy           2656  0 
ecb                     2524  2 
snd_seq_oss            28576  0 
b43legacy             117752  0 
snd_seq_midi            6432  0 
mac80211              181140  1 b43legacy
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               93052  2 b43legacy,mac80211
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
led_class               4096  1 b43legacy
i2c_sis96x              3904  0 
pcmcia                 36808  0 
psmouse                56500  0 
x_tables               16544  1 ip_tables
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
irda                  189564  0 
serio_raw               5280  0 
yenta_socket           24296  2 
rsrc_nonstatic         11644  1 yenta_socket
shpchp                 32272  0 
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
ppdev                   6688  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
parport_pc             31940  1 
crc_ccitt               1852  1 irda
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
b44                    28684  0 
ohci1394               29900  0 
radeon                636000  2 
ttm                    36212  1 radeon
ssb                    35364  2 b43legacy,b44
video                  19380  0 
output                  2780  1 video
sis900                 19932  0 
mii                     5212  2 b44,sis900
ieee1394               86596  1 ohci1394
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
sis_agp                 6972  1 
agpgart                34988  3 ttm,drm,sis_agp
epssi@paska:~$ dmesg | grep b43legacy
[   21.859233] b43legacy-phy0: Broadcom 4301 WLAN found
[   21.881021] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   21.881046] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[   21.907124] b43legacy-phy0 debug: Radio initialized
[   28.740068] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   29.055997] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   29.145146] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   29.304029] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   29.369613] b43legacy-phy0 debug: Chip initialized
[   29.370480] b43legacy-phy0 debug: 30-bit DMA initialized
[   29.370688] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x44
[   29.370694] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x46
[   29.370698] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x12
[   29.370702] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x4D
[   29.370733] b43legacy-phy0 debug: Wireless interface started
[   29.370767] b43legacy-phy0 debug: Adding Interface type 2
[   40.876457] b43legacy-phy0 debug: Removing Interface type 2
[   40.888202] b43legacy-phy0 debug: Wireless interface stopped
[   40.888410] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[   40.888496] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 3/64
[   40.888582] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   40.896071] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   40.904074] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   40.915578] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   40.920121] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 2/128
[   40.928061] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   40.936080] b43legacy-phy0 debug: Radio initialized
[   40.936103] b43legacy-phy0 debug: Radio initialized
[   41.097052] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   41.153940] b43legacy-phy0 debug: Chip initialized
[   41.154349] b43legacy-phy0 debug: 30-bit DMA initialized
[   41.154573] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x44
[   41.154580] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x46
[   41.154585] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x12
[   41.154590] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x4D
[   41.154621] b43legacy-phy0 debug: Wireless interface started
[   41.154632] b43legacy-phy0 debug: Adding Interface type 2
[   44.822224] b43legacy-phy0: Radio hardware status changed to DISABLED
[   44.822243] b43legacy-phy0 debug: Radio initialized
[   44.860080] b43legacy-phy0: Radio turned on by software
[   44.860097] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   44.908096] b43legacy-phy0 debug: Removing Interface type 2
[   44.924217] b43legacy-phy0 debug: Wireless interface stopped
[   44.924415] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[   44.924496] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[   44.924581] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   44.933009] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   44.940074] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   44.952094] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   44.960091] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 4/128
[   44.968483] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   44.976082] b43legacy-phy0 debug: Radio initialized
[   44.976105] b43legacy-phy0 debug: Radio initialized
epssi@paska:~$ sudo lshw -C network
[sudo] password for epssi: 
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:10:42:48
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:e800(size=256) memory:dfffc000-dfffcfff memory:dffc0000-dffdffff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:dfffe000-dfffffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:1c:fb:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
epssi@paska:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

epssi@paska:~$ lsb_release -d
Description:	Ubuntu 9.10
epssi@paska:~$ uname -mr
2.6.31-17-generic i686
epssi@paska:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                           
 [ OK ]
epssi@paska:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

---

### Post by imayoda on 2010-01-19
Same sad problem here, I have a zv5000 series hp notebook.. rf_kill is hardware blocked.

I installed in karmic koala the rfkill packet directly from debian sid, but nothing, the unlock all function doesn't do the magic..

Any suggestions anybody? Please i'm running mad with this wireless b43legacy ](*,)

---

### Post by eldragon on 2010-01-19
blacklist the rfkill kernel module

---

### Post by imayoda on 2010-01-19
> **eldragon said:**
> blacklist the rfkill kernel module

It says I have none module named rfkill in /proc/modules 

:(

(i'm looking around and see that many have problems with this issue/button )

---

### Post by bkratz on 2010-01-19
Maybe something useful here??

[http://ubuntuforums.org/showthread.php?t=1334195&highlight=rfkill](http://ubuntuforums.org/showthread.php?t=1334195&highlight=rfkill)

---

### Post by imayoda on 2010-01-19
This is what happens just after loading b43legacy module:

[PHP]imayoda@Kubuntu-studio:~$ sudo rfkill list
0: phy0: Wireless LAN                     
        Soft blocked: no                 
        Hard blocked: no                  
imayoda@Kubuntu-studio:~$ sudo ifconfig wlan0 up
imayoda@Kubuntu-studio:~$ sudo rfkill list
0: phy0: Wireless LAN                     
        Soft blocked: no                  
        Hard blocked: yes                 
imayoda@Kubuntu-studio:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu   
...cut...                                                                                                               
[   30.246262] type=1505 audit(1263908187.343:13): operation="profile_replace" pid=1042 name=/usr/sbin/cupsd          
[   30.253481] type=1505 audit(1263908187.351:14): operation="profile_replace" pid=1043 name=/usr/sbin/mysqld-akonadi 
[   30.259745] type=1505 audit(1263908187.355:15): operation="profile_replace" pid=1045 name=/usr/sbin/tcpdump        
[   30.269120] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 5 (level, low) -> IRQ 5                         
[   30.600254] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.                                    
[   30.601754] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7         
[   30.602403] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.                                    
[   30.602885] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07                     
[   30.603577] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.                                    
[   30.858234] ondemand governor failed, too long transition latency of HW, fallback to performance governor          
[   30.860939] ondemand governor failed, too long transition latency of HW, fallback to performance governor          
[   31.680381] ata1.00: configured for UDMA/100                                                                       
[   31.680392] ata1: EH complete                                                                                      
[   32.117201] floppy0: no floppy controllers found                                                                   
[   32.210816] CPU0 attaching NULL sched-domain.                                                                      
[   32.210824] CPU1 attaching NULL sched-domain.                                                                      
[   32.224215] CPU0 attaching sched-domain:                                                                           
[   32.224224]  domain 0: span 0-1 level SIBLING                                                                      
[   32.224230]   groups: 0 1                                                                                          
[   32.224241] CPU1 attaching sched-domain:                                                                           
[   32.224246]  domain 0: span 0-1 level SIBLING                                                                      
[   32.224250]   groups: 1 0                                                                                          
[   32.554593] agpgart-ati 0000:00:00.0: AGP 3.0 bridge                                                               
[   32.554616] agpgart-ati 0000:00:00.0: putting AGP V3 device into 8x mode                                           
[   32.554642] pci 0000:01:05.0: putting AGP V3 device into 8x mode                                                   
[   32.672077] [drm] Setting GART location based on new memory map                                                    
[   32.672087] [drm] Loading R200 Microcode                                                                           
[   32.672134] [drm] writeback test succeeded in 1 usecs                                                              
[   40.272075] ondemand governor failed, too long transition latency of HW, fallback to performance governor          
[   40.325013] eth0: no IPv6 routers present                                                                          
[   40.375414] CPU0 attaching NULL sched-domain.                                                                      
[   40.375424] CPU1 attaching NULL sched-domain.                                                                      
[   40.388135] CPU0 attaching sched-domain:                                                                           
[   40.388144]  domain 0: span 0-1 level SIBLING                                                                      
[   40.388154]   groups: 0 1                                                                                          
[   40.388166] CPU1 attaching sched-domain:                                                                           
[   40.388170]  domain 0: span 0-1 level SIBLING                                                                      
[   40.388174]   groups: 1 0                                                                                          
[   92.460633] ondemand governor failed, too long transition latency of HW, fallback to performance governor          
[   92.460696] ondemand governor failed, too long transition latency of HW, fallback to performance governor          
[ 1066.872112] cfg80211: Calling CRDA to update world regulatory domain                                               
[ 1066.987504] cfg80211: World regulatory domain updated:                                                             
[ 1066.987513]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)                                     
[ 1066.987520]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                          
[ 1066.987526]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                                          
[ 1066.987531]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                                          
[ 1066.987537]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                          
[ 1066.987542]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                                          
[ 1067.091196] b43legacy-phy0: Broadcom 4301 WLAN found                                                               
[ 1067.112026] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4                                          
[ 1067.112050] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2                             
[ 1067.136029] b43legacy-phy0 debug: Radio initialized                                                                
[ 1067.243997] phy0: Selected rate control algorithm 'minstrel'                                                       
[ 1067.247336] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]                               
[ 1102.045949] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw                                             
[ 1102.116303] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw                                               
[ 1102.124358] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[ 1102.232034] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[ 1102.332293] b43legacy-phy0 debug: Chip initialized
[ 1102.332574] b43legacy-phy0 debug: 30-bit DMA initialized
[ 1102.332781] Registered led device: b43legacy-phy0::tx
[ 1102.332816] Registered led device: b43legacy-phy0::rx
[ 1102.332851] Registered led device: b43legacy-phy0::radio
[ 1102.332894] b43legacy-phy0 debug: Wireless interface started
[ 1102.332911] b43legacy-phy0 debug: Adding Interface type 2
[ 1102.332961] b43legacy-phy0: Radio hardware status changed to DISABLED
[ 1102.332971] b43legacy-phy0 debug: Radio initialized
[ 1102.397317] b43legacy-phy0: Radio turned on by software
[ 1102.397327] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 1102.397687] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1102.440733] b43legacy-phy0 debug: Removing Interface type 2
[ 1102.452383] b43legacy-phy0 debug: Wireless interface stopped
[ 1102.452703] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[ 1102.452778] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[ 1102.452849] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[ 1102.461438] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[ 1102.468062] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[ 1102.476048] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[ 1102.484022] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[ 1102.492022] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[ 1102.500022] b43legacy-phy0 debug: Radio initialized
[ 1102.500036] b43legacy-phy0 debug: Radio initialized
imayoda@Kubuntu-studio:~$ damn!
[/PHP]

Can't do anything i guess.. bad status :(

---

### Post by imayoda on 2010-01-19
Definite.. we need a linux guru to fix this.. i have tried anything suggested here and there, but no luck..

thanks to anyone responded, and those that will..

---

### Post by imayoda on 2010-01-22
Things are working with Ndiswrapper and some loose of time banning b44, ssb and b43legacy modules.. (update-initramfs -u after that)
Yeah! even the beautiful rf button is working good with led too..

now..
Does anybody know please if there is a way to access WPA protected networks with this config?

I'm stuck only with WEP support by now..

Kind regards :confused:

---

### Post by viherpeukalo on 2010-09-14
Bump! Cannot use 10.04, 9.10 because of this - stuck with 9.04.

---

### Post by cracker89 on 2010-11-03
> **imayoda said:**
> Things are working with Ndiswrapper and some loose of time banning b44, ssb and b43legacy modules.. (update-initramfs -u after that)
Yeah! even the beautiful rf button is working good with led too..
 
now..
Does anybody know please if there is a way to access WPA protected networks with this config?
 
I'm stuck only with WEP support by now..
 
Kind regards :confused:
 
Hey. Am having similar problem in ubuntu 10.4... just one question:
do you need xp installed parallel to use ndiswrapper?

---

### Post by imayoda on 2010-11-03
> **cracker89 said:**
> Hey. Am having similar problem in ubuntu 10.4... just one question:
do you need xp installed parallel to use ndiswrapper?

no.. ndiswrapper only needs to load the .inf file located in driver folder downloaded from ...errr.. i don't remeber where.. do a search..

it work but only nosecurity and wep , no wpa or better..

new hope comes from broadcom open release of drivers for wireless chipsets: maybe in 11.04 we would get rid of workarounds :)

---

### Post by cracker89 on 2010-11-03
ok.. I had the problem with 10.4 and reps to P4man for this;

if ```
rfkill list
```
shows a hard block, then try running these, depending on your wifi card type, or something similar;

```
sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k
```

hope you get some direection here... :)

---

### Post by cracker89 on 2010-11-04
[http://lovinglinux.ubuntuforums.org/showthread.php?t=780692&page=3](http://lovinglinux.ubuntuforums.org/showthread.php?t=780692&page=3)

something here?

---

### Post by pkadetiloye on 2010-11-13
> **imayoda said:**
> Definite.. we need a linux guru to fix this.. i have tried anything suggested here and there, but no luck..

thanks to anyone responded, and those that will..

Hey, I fixed it. Check this [http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

:guitar:

---

### Post by imayoda on 2010-11-13
> **pkadetiloye said:**
> Hey, I fixed it. Check this [http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

:guitar:

Nice.. :popcorn:

unfortunately this wasn't possible in my case cause after all there was no longer a dev rfkill in the system... quite strange ahah:)

---

### Post by pkadetiloye on 2010-11-13
> **imayoda said:**
> Nice.. :popcorn:

unfortunately this wasn't possible in my case cause after all there was no longer a dev rfkill in the system... quite strange ahah:)

That's right. Install the package
   $sudo apt-get install rfkill

Then follow the blog [http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

Hope that helps!

:guitar:

---

### Post by valenluis on 2011-05-02
> **cracker89 said:**
> ok.. I had the problem with 10.4 and reps to P4man for this;

if ```
rfkill list
```
shows a hard block, then try running these, depending on your wifi card type, or something similar;

```
sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k
```

hope you get some direection here... :)

Thanks, it worked! :)

---

