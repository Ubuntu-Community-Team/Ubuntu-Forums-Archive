---
title: "D-Link &quot;DWA-547&quot; Will only work on 1Mb/s"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by towoha on 2008-12-25
Hi everyone. 
I'm rely new to the Linux and Ubuntu world so please bear with me! 
I've installed the latest Ubuntu version on my desktop computer to day. Everything works just great except that my wlan card only connects on 1mb/s and that's just to poor! I've gone over the list on how to post a thread and it's a bit long since I'm not sure off all the media I'm getting with the commands. So I just cross my fingers and hope that someone will bear with me and give me some hints on what I can do... 

1 ) Machine Brand and Model (PC/Laptop):
Code:
Packard Bell IStart F3215

2 ) Wireless Brand, Model and Wireless Chipset:
Code:

$ lspci 02:02.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
$ lsusb Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 045e:00f1 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


3 ) check interface:
Code:
$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:b1:cb:9c  
          inet addr:192.168.0.192  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:b9ff:feb1:cb9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11152053 (11.1 MB)  TX bytes:1559075 (1.5 MB)
          Interrupt:20 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:5b:08:e8:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3665 (3.6 KB)  TX bytes:5795 (5.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-5B-08-E8-44-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"virusbasen"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


4 ) Check for modules:
Code:
$ lsmod
Module                  Size  Used by
ipv6                  263972  14 
aes_i586               15744  0 
aes_generic            35880  1 aes_i586
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 

cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container              11520  0 
pci_slot               12552  0 
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
arc4                    9984  2 
snd_seq_oss            38528  0 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
ath9k                 274232  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              216820  1 ath9k
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                 10624  0 
i2c_piix4              16144  0 
cfg80211               32392  1 mac80211
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
evdev                  17696  7 
nvidia               6900560  36 
i2c_core               31892  2 i2c_piix4,nvidia
shpchp                 37908  0 
button                 14224  0 
pci_hotplug            35236  1 shpchp
ati_agp                14988  0 
agpgart                42184  2 nvidia,ati_agp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
usbhid                 35840  0 
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
hid                    50560  1 usbhid
pata_atiixp            12800  0 
8139too                31616  0 
sg                     39732  0 
pata_acpi              12160  0 
8139cp                 27520  0 
mii                    13440  2 8139too,8139cp
ata_generic            12932  0 
ehci_hcd               43276  0 
ahci                   37132  2 
ohci_hcd               31888  0 
libata                177312  4 pata_atiixp,pata_acpi,ata_generic,ahci
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
usbcore               148848  4 usbhid,ehci_hcd,ohci_hcd
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

(hint) search for the Wireless module
Code:
$ lsmod | grep "wlan_module_name"
I don't know what my wlan_module_name are...


5 ) Kernel boot messages
Code:
$ dmesg
To long to write here. If someone can help me with my wlan_module_name I can cut it from the text!

6 ) Network configuration
Code:
$ sudo lshw -C network
 *-network:0             
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wmaster0
       version: 01
       serial: 00:19:5b:08:e8:44
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:1b:b9:b1:cb:9c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.192 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:9a:f6:8c:77:22
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


7 ) Scan for networks:
Code:
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:F0:71:0C:14
                    ESSID:"virusbasen"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/100  Signal level:-59 dBm  Noise level=-95 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A4E101FFFFF000000000000000000000000000004000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001a73e7d180
                    Extra: Last beacon: 92ms ago

pan0      Interface doesn't support scanning.


8 ) Ubuntu Version:
Code:
$ lsb_release -d
Description:	Ubuntu 8.10


9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:
$ uname -mr
2.6.27-7-generic i686


10 ) Restarting the network:
Code:
$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... 
Ignoring unknown interface eth0=eth0


PLEASE HELP ME! SOMEONE...

Regards
Torbjørn
Norway
PS: Please excuse my English for any misspellings.

---

### Post by towoha on 2008-12-26
Please, anyone out there that can help me???

---

### Post by towoha on 2008-12-27
Is there no one that can help me with this???

---

### Post by Gizmonty on 2008-12-27
I can't offer a lot of help other than to say that you're not the only one. I have a DWA-556 which uses the same AR5008 chipset and I have the same 1 Mbps connection.

As far as I've been able to tell it is a fault with the current Ath9k driver and should be corrected in the future as it has been reported. Some people have reported success with other techniques such as madwifi or ndiswrapper but I don't really know what these are.

Sorry I can't be more helpful.

---

### Post by Gizmonty on 2008-12-28
OK, I found a solution that sort-of works for me at [http://probing.wikidot.com/ubuntu-intrepid-8-10-replacing-ath9k-by-madwifi](http://probing.wikidot.com/ubuntu-intrepid-8-10-replacing-ath9k-by-madwifi). This replaces the Ath9k drivers with the madwifi ones. The performance is better although still not good enough for my purposes.

I have made a few modifications as there were a few errors and omissions in the instructions but I now have iwconfig reporting 36 Mb/s.

Open a terminal and type
```
sudo nano /etc/modprobe.d/blacklist
```

and add the following lines to the file

```
blacklist ath9k
blacklist mac80211
blacklist cfg80211

```

Save the file and then enter the following in the terminal

```
sudo apt-get install linux-headers-generic
sudo apt-get install subversion
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk madwifi
cd madwifi/scripts
sudo sh madwifi-unload
sudo sh find-madwifi-modules.sh -r `uname -r`
cd ..
sudo make
sudo make install

```

Then reboot and things should be a bit better.

It sounds like Ubuntu let a dud Ath9k driver through and won't be fixing this until 9.04 is released. I suspect that will be the best solution once it is out.

I'm no Ubuntu/linux expert and don't completely understand what all of this does/did so use at your own risk.

---

### Post by towoha on 2008-12-28
> **Gizmonty said:**
> OK, I found a solution that sort-of works for me at [http://probing.wikidot.com/ubuntu-intrepid-8-10-replacing-ath9k-by-madwifi](http://probing.wikidot.com/ubuntu-intrepid-8-10-replacing-ath9k-by-madwifi). This replaces the Ath9k drivers with the madwifi ones. The performance is better although still not good enough for my purposes.

I have made a few modifications as there were a few errors and omissions in the instructions but I now have iwconfig reporting 36 Mb/s.

Open a terminal and type
```
sudo nano /etc/modprobe.d/blacklist
```

and add the following lines to the file

```
blacklist ath9k
blacklist mac80211
blacklist cfg80211

```

Save the file and then enter the following in the terminal

```
sudo apt-get install linux-headers-generic
sudo apt-get install subversion
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk madwifi
cd madwifi/scripts
sudo sh madwifi-unload
sudo sh find-madwifi-modules.sh -r `uname -r`
cd ..
sudo make
sudo make install

```

Then reboot and things should be a bit better.

It sounds like Ubuntu let a dud Ath9k driver through and won't be fixing this until 9.04 is released. I suspect that will be the best solution once it is out.

I'm no Ubuntu/linux expert and don't completely understand what all of this does/did so use at your own risk.

Well, export ore not. It works =) Still not the best speed (36Mb/s) But still it's 36 times better than what I had. Now I can browse the web wireless =) I will try to get some other solutions to see if I can improve the speed a bit more, but if this ends up to be the best solution I will use it! 
Thanks for the great input!

---

