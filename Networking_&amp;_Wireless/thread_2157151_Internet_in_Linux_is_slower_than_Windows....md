---
title: "Internet in Linux is slower than Windows..."
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by lavini557 on 2013-06-24
Hello, Ubuntu forums! First time here, and I need help. Bad :( My internet is slower on Linux than on Windows.
Now, the internet is fine in my basement and on the first floor, but the internet is really slow on the 2nd floor (where my room is). This is only with Linux, though. I was fine when using Windows in my room.
From a bit of research, I assume the issue is partially because of distance (my router is in the basement, so more wall and stuff to go through). But if this is so, why was the internet running fine when using Windows? o.o The only time the internet lagged on Windows is when my brother is playing LoL, but my internet is slow even if he hasn't turned on his computer.
I have posted iwconfig:
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"WLAN-DC5B"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:22:2D:7B: DC:5D   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:183   Missed beacon:0
Any help is appreciated :)

---

### Post by praseodym on 2013-06-24
Hi,

please show also these outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
cat /etc/resolv.conf
sudo iwlist scan
route -n
```

---

### Post by lavini557 on 2013-06-24
**lspci -nnk | grep -iA2 net**
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:1805]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1629]
    Kernel driver in use: rtl8192ce
**lsusb**
Bus 002 Device 002: ID 064e:d281 Suyin Corp. 
Bus 004 Device 002: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
[B]
lsmod[/B]
[QUOTE]
Module                  Size  Used by
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
joydev                 17377  0 
snd_hda_codec_idt      70256  1 
snd_hda_codec_hdmi     36913  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
kvm                   443165  0 
videodev              129260  2 uvcvideo,videobuf2_core
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
arc4                   12615  2 
rtsx_pci_ms            13011  0 
memstick               16554  1 rtsx_pci_ms
video                  19390  0 
snd_hda_intel          39619  1 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
hp_accel               26012  0 
snd_rawmidi            30180  1 snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
lis3lv02d              20111  1 hp_accel
wmi                    19070  1 hp_wmi
rtl8192ce              53594  0 
input_polldev          13896  1 lis3lv02d
rtlwifi                79673  1 rtl8192ce
radeon                942029  2 
rtl8192c_common        48779  1 rtl8192ce
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
mac80211              606457  3 rtlwifi,rtl8192c_common,rtl8192ce
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
ttm                    83187  1 radeon
snd                    68876  12 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         49394  1 radeon
cfg80211              510937  2 mac80211,rtlwifi
microcode              22881  0 
k10temp                13126  0 
psmouse                95870  0 
serio_raw              13215  0 
soundcore              12680  1 snd
drm                   286028  4 ttm,drm_kms_helper,radeon
i2c_piix4              13266  0 
lp                     17759  0 
i2c_algo_bit           13413  1 radeon
parport                46345  1 lp
pata_acpi              13038  0 
rtsx_pci_sdmmc         17475  0 
sdhci_pci              18590  0 
sdhci                  32522  1 sdhci_pci
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
pata_atiixp            13242  0 
ahci                   25731  2 
libahci                31364  1 ahci
r8169                  67446  0 

**ifconfig -a**

eth0      Link encap:Ethernet  HWaddr 08:2e:5f:98:ba:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38229 (38.2 KB)  TX bytes:38229 (38.2 KB)


wlan0     Link encap:Ethernet  HWaddr 20:10:7a:4a:96:26  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3220544 (3.2 MB)  TX bytes:252093 (252.0 KB)
**cat /etc/resolv.conf**
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

**sudo iwlist scan**
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:22:2D:7B: DC:5D
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key: on
                    ESSID:"WLAN-DC5B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000155c7636cda
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 0009574C414E2D44433542
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 06:07:70:A9:02:99
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key: on
                    ESSID:"KT_WLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000155c5ce9f84
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00074B545F574C414E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 03 - Address: 00:22:2D:7B:BB: D5
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key: on
                    ESSID:"WLAN-BBBD3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000061dbd7181b7
                    Extra: Last beacon: 952ms ago
                    IE: Unknown: 000A574C414E2D4242424433
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030108
                    IE: Unknown: 050C000200000000000000000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 00:13:F7:FA:17:B4
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key: on
                    ESSID:"SUE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f3a75781c5
                    Extra: Last beacon: 848ms ago
                    IE: Unknown: 0003535545
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030102
                    IE: Unknown: 050C000201000000000000000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 05 - Address: 00:1C: DF:21:33:2B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key: on
                    ESSID:"FORKEUTIS33478"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f7e04b10c
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000E464F524B45555449533333343738
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DDA50050F204104A00011010440001021041000100103B0001031047001000000000000000011000001CDF21332B1021001242656C6B696E20436F72706F726174696F6E102300114E20576972656C65737320526F7574657210240007332E30312E31301042000E31323734353832333330333037341054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
          Cell 06 - Address: 00:22:3F: D6:37:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key: on
                    ESSID:"WLAN-ABE42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000021d5cfead24
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000A574C414E2D4142453432
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
[B]
route -n[/B]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

---

### Post by praseodym on 2013-06-24
Try using a fixed channel and WPA2-AES encryption instead of (unsecure) WEP.

---

### Post by lavini557 on 2013-06-24
Um...I don't understand. o.o Could you elaborate? Like what do you mean by a 'fixed channel'? And how would I change my encryption? And why do you think I need to change the encryption? o.o

---

### Post by praseodym on 2013-06-24
Mixed encryptions are normally slower in Ubuntu. See the router manual for setting the channel and changing the encryption

---

### Post by lavini557 on 2013-06-24
Tried changing channel and switching to WPA-PSK...doesn't change anything :( Anything else that you would recommend?

---

### Post by praseodym on 2013-06-25
Try to update the driver:
```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r) linux-headers-generic
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Reboot.

---

### Post by lavini557 on 2013-06-27
It worked! XD Thank you. Just wondering, but will this work if I try to update drivers on another Linux computer? Or do I have to use another set of command lines? Oh, and how do I change the title to mark it as solved?
[EDIT] It only worked for a short time - after that it got really slow. I think it got even worse than before, because the internet is also a bit slower than usual when I used my laptop on the 1st floor :(. I posted Terminal results of updating the driver in case it helps.

eric@HP-Pavilion-dv6-6c35dx:~$ sudo apt-get install --reinstall build-essential linux-headers-$(uname -r) linux-headers-generic
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  guile-1.8-libs
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  binutils dpkg-dev fakeroot g++ g++-4.7 gcc gcc-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libc-dev-bin libc6-dev
  libdpkg-perl libfile-fcntllock-perl libgcc-4.7-dev libitm1
  libstdc++6-4.7-dev linux-libc-dev make manpages-dev
Suggested packages:
  binutils-doc debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc
  libstdc++6-4.7-dbg gcc-multilib autoconf automake1.9 libtool flex bison gdb
  gcc-doc gcc-4.7-multilib libmudflap0-4.7-dev gcc-4.7-locales libgcc1-dbg
  libgomp1-dbg libitm1-dbg libquadmath0-dbg libmudflap0-dbg binutils-gold
  glibc-doc libstdc++6-4.7-doc make-doc
The following NEW packages will be installed:
  binutils build-essential dpkg-dev fakeroot g++ g++-4.7 gcc gcc-4.7
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libc-dev-bin libc6-dev libdpkg-perl libfile-fcntllock-perl libgcc-4.7-dev
  libitm1 libstdc++6-4.7-dev linux-libc-dev make manpages-dev
0 upgraded, 21 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 27.7 MB/28.7 MB of archives.
After this operation, 76.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libitm1 amd64 4.7.3-1ubuntu1 [36.2 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main binutils amd64 2.23.2-2ubuntu1 [2,393 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libc-dev-bin amd64 2.17-0ubuntu5 [81.4 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates/main linux-libc-dev amd64 3.8.0-25.37 [921 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libc6-dev amd64 2.17-0ubuntu5 [3,088 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libgcc-4.7-dev amd64 4.7.3-1ubuntu1 [2,464 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main gcc-4.7 amd64 4.7.3-1ubuntu1 [6,088 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main gcc amd64 4:4.7.3-1ubuntu10 [5,120 B]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libstdc++6-4.7-dev amd64 4.7.3-1ubuntu1 [1,704 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main g++-4.7 amd64 4.7.3-1ubuntu1 [7,993 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main g++ amd64 4:4.7.3-1ubuntu10 [1,448 B]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main make amd64 3.81-8.2ubuntu2 [120 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libdpkg-perl all 1.16.10ubuntu1 [186 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main dpkg-dev all 1.16.10ubuntu1 [712 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main build-essential amd64 11.6ubuntu4 [5,672 B]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main fakeroot amd64 1.18.4-2ubuntu1 [89.1 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libalgorithm-diff-perl all 1.19.02-3 [50.0 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libalgorithm-diff-xs-perl amd64 0.04-2build3 [12.5 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main libfile-fcntllock-perl amd64 0.14-2 [15.8 kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main manpages-dev all 3.44-0ubuntu1 [1,738 kB]
Fetched 27.7 MB in 19s (1,441 kB/s)                                            
Selecting previously unselected package libitm1:amd64.
(Reading database ... 134926 files and directories currently installed.)
Unpacking libitm1:amd64 (from .../libitm1_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package binutils.
Unpacking binutils (from .../binutils_2.23.2-2ubuntu1_amd64.deb) ...
Selecting previously unselected package libc-dev-bin.
Unpacking libc-dev-bin (from .../libc-dev-bin_2.17-0ubuntu5_amd64.deb) ...
Selecting previously unselected package linux-libc-dev:amd64.
Unpacking linux-libc-dev:amd64 (from .../linux-libc-dev_3.8.0-25.37_amd64.deb) ...
Selecting previously unselected package libc6-dev:amd64.
Unpacking libc6-dev:amd64 (from .../libc6-dev_2.17-0ubuntu5_amd64.deb) ...
Selecting previously unselected package libgcc-4.7-dev:amd64.
Unpacking libgcc-4.7-dev:amd64 (from .../libgcc-4.7-dev_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package gcc-4.7.
Unpacking gcc-4.7 (from .../gcc-4.7_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.7.3-1ubuntu10_amd64.deb) ...
Selecting previously unselected package libstdc++6-4.7-dev:amd64.
Unpacking libstdc++6-4.7-dev:amd64 (from .../libstdc++6-4.7-dev_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.7.
Unpacking g++-4.7 (from .../g++-4.7_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.7.3-1ubuntu10_amd64.deb) ...
Selecting previously unselected package make.
Unpacking make (from .../make_3.81-8.2ubuntu2_amd64.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.10ubuntu1_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.10ubuntu1_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.6ubuntu4_amd64.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2ubuntu1_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-3_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package libfile-fcntllock-perl.
Unpacking libfile-fcntllock-perl (from .../libfile-fcntllock-perl_0.14-2_amd64.deb) ...
Preparing to replace linux-headers-3.8.0-25-generic 3.8.0-25.37 (using .../linux-headers-3.8.0-25-generic_3.8.0-25.37_amd64.deb) ...
Unpacking replacement linux-headers-3.8.0-25-generic ...
Preparing to replace linux-headers-generic 3.8.0.25.43 (using .../linux-headers-generic_3.8.0.25.43_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Selecting previously unselected package manpages-dev.
Unpacking manpages-dev (from .../manpages-dev_3.44-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up libitm1:amd64 (4.7.3-1ubuntu1) ...
Setting up binutils (2.23.2-2ubuntu1) ...
Setting up libc-dev-bin (2.17-0ubuntu5) ...
Setting up linux-libc-dev:amd64 (3.8.0-25.37) ...
Setting up libc6-dev:amd64 (2.17-0ubuntu5) ...
Setting up libgcc-4.7-dev:amd64 (4.7.3-1ubuntu1) ...
Setting up gcc-4.7 (4.7.3-1ubuntu1) ...
Setting up gcc (4:4.7.3-1ubuntu10) ...
Setting up libstdc++6-4.7-dev:amd64 (4.7.3-1ubuntu1) ...
Setting up g++-4.7 (4.7.3-1ubuntu1) ...
Setting up g++ (4:4.7.3-1ubuntu10) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up make (3.81-8.2ubuntu2) ...
Setting up libdpkg-perl (1.16.10ubuntu1) ...
Setting up dpkg-dev (1.16.10ubuntu1) ...
Setting up build-essential (11.6ubuntu4) ...
Setting up fakeroot (1.18.4-2ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libalgorithm-diff-perl (1.19.02-3) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build3) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libfile-fcntllock-perl (0.14-2) ...
Setting up linux-headers-3.8.0-25-generic (3.8.0-25.37) ...
Setting up linux-headers-generic (3.8.0.25.43) ...
Setting up manpages-dev (3.44-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
eric@HP-Pavilion-dv6-6c35dx:~$ wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
--2013-06-27 18:13:20--  [http://media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz)
Resolving media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)... 213.95.41.13, 2001:780:0:25:206:5bff:fe04:8bcb
Connecting to media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 714676 (698K) [application/octet-stream]
Saving to: &#8216;5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz&#8217;


100%[======================================>] 714,676      568KB/s   in 1.2s   


2013-06-27 18:13:22 (568 KB/s) - &#8216;5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz&#8217; saved [714676/714676]


eric@HP-Pavilion-dv6-6c35dx:~$ tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/rtl8192de/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/rtl8723e/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/rtl8192ce/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/rtl8188ee/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/rtl8192se/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/rtl8192de/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/rtl8723e/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/rtl8192ce/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/rtl8192se/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/wireless/rtlwifi/rtl8192de/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/wireless/rtlwifi/rtl8192ce/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/wireless/rtlwifi/rtl8192se/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/Kconfig
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/Kconfig
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/wireless/rtlwifi/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/wireless/rtlwifi/Kconfig
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/scripts/unload.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/scripts/driver-select
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/scripts/wlunload.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/scripts/unload.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/scripts/driver-select
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/scripts/wlunload.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/scripts/unload.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/scripts/driver-select
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/scripts/wlunload.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/config.mk
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/config.mk
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/config.mk
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/script/compat-uninstall.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/script/compat-install-mesh.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/script/copyfile.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/script/restore.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/script/compat-install.sh
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/Realtek-Firmware-License.txt
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/rtl8192defw_12.bin
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/rtl8192cfw.bin
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/rtl8192cfwU.bin
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/rtl8188efw.bin
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/rtl8192sefw.old.bin
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/rtl8192sefw.bin
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/rtl8192cfwU_B.bin
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/rtl8723fw.bin
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/rtl8192defw.bin
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/rtl8723fw_B.bin
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/led.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/hw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/phy.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/reg.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/hw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/trx.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/sw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/dm.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/def.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/fw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/trx.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/rf.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/fw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/dm.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/rf.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/led.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/table.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/table.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/sw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/phy.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/led.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/hw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/phy.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/reg.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/hw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/trx.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/sw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/dm.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/def.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/fw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/trx.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/rf.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/fw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/dm.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/rf.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/led.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/table.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/table.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/sw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/phy.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/led.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/hw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/phy.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/reg.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/hw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/trx.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/sw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/dm.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/def.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/fw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/trx.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/rf.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/fw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/dm.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/rf.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/led.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/table.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/table.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/sw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/phy.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/led.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/hw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/phy.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/reg.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/hw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/pwrseqcmd.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/trx.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/sw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/dm.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/pwrseqcmd.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/btc.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/def.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/fw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/trx.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/pwrseq.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/rf.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/hal_bt_coexist.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/fw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/dm.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/hal_bt_coexist.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/hal_btc.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/pwrseq.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/rf.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/led.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/table.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/hal_btc.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/table.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/sw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/phy.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/led.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/hw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/phy.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/reg.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/hw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/pwrseqcmd.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/trx.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/sw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/dm.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/pwrseqcmd.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/def.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/fw.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/trx.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/pwrseq.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/rf.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/fw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/dm.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/pwrseq.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/rf.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/led.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/table.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/table.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/sw.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/phy.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/Makefile
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/Kconfig
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/readme
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/release_note
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/cam.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/core.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/debug.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/efuse.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/ps.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rc.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/regd.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/stats.c
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/cam.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/core.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/debug.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/efuse.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/ps.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rc.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/regd.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/stats.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/wifi.h
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/rtl8192de/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/rtl8723e/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/rtl8192ce/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/rtl8188ee/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/rtl8192se/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/rtl8192de/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/rtl8723e/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/rtl8192ce/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/rtl8192se/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/wireless/rtlwifi/rtl8192de/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/wireless/rtlwifi/rtl8192ce/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/wireless/rtlwifi/rtl8192se/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/rtlwifi/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/rtlwifi/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/wireless/rtlwifi/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/wireless/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/wireless/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/wireless/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/net/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/net/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/net/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/drivers/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/scripts/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/drivers/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/scripts/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/drivers/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/scripts/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.2.5-1/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/3.0-2/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/2.6.39-1/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/script/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/rtlwifi/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/compat/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/firmware/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee/
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/
eric@HP-Pavilion-dv6-6c35dx:~$ cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/
eric@HP-Pavilion-dv6-6c35dx:~/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ make
make -C /lib/modules/3.8.0-25-generic/build M=/home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
  CC [M]  /home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
make[2]: *** [/home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
make: *** [all] Error 2
eric@HP-Pavilion-dv6-6c35dx:~/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ sudo make install
make -C /lib/modules/3.8.0-25-generic/build M=/home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
  CC [M]  /home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
make[2]: *** [/home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/eric/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
make: *** [all] Error 2
eric@HP-Pavilion-dv6-6c35dx:~/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ sudo depmod -a
eric@HP-Pavilion-dv6-6c35dx:~/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.8.0-25-generic
eric@HP-Pavilion-dv6-6c35dx:~/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ sudo cp -r firmware/* /lib/firmware
eric@HP-Pavilion-dv6-6c35dx:~/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ 

What should I do? :(

---

### Post by lavini557 on 2013-06-28
Bump

---

### Post by lavini557 on 2013-06-30
Ok, this isn't a bump...it's just a (possible) solution that I'm trying to do right now, but there's a problem...
So I saw from [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI) that my pci card (8188CE) doesn't work out of the box -_- . So, I am trying to install the driver by compiling from file using [http://ubuntuforums.org/showthread.php?t=1580036](http://ubuntuforums.org/showthread.php?t=1580036), but there is one issue...
I can get the make command working (after jumping through some hoops o.o), but when I try to use 'make install', this appears:

root@HP-Pavilion-dv6-6c35dx:/home/eric/Desktop/rtl8192ce_linux# make install
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
make[1]: Entering directory `/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192'
make: *** [install] Error 2

Heck, the "No rule to make target" also appears when I tried to use 'make clean':

root@HP-Pavilion-dv6-6c35dx:/home/eric/Desktop/rtl8192ce_linux# make clean
make[1]: Entering directory `/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Entering directory `/'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192'
make: *** [clean] Error 2

Can anyone help? I was going to put this in another thread (because no one seemed to be reading this thread) but I am putting it here first, just in case someone finally responds to this thread -_- .

---

### Post by kurt18947 on 2013-06-30
When you build your own drivers and install an updated/different image, you'll need to repeat the steps to rebuild the drivers.  So keep the original download where you can find it.

---

### Post by lavini557 on 2013-06-30
I don't understand o.o (sorry I'm such a noob), but what do you want me to do? I don't know what you mean by keeping the download where I can find it. Do you want me to NOT build the driver? Please elaborate on your statement.

---

### Post by kurt18947 on 2013-06-30
> **lavini557 said:**
> I don't understand o.o (sorry I'm such a noob), but what do you want me to do? I don't know what you mean by keeping the download where I can find it. Do you want me to NOT build the driver? Please elaborate on your statement.

Sorry, I may have confused you.  I'm not knowledgeable  in compiling and installing drivers so I can't help there.  I was just saying that once manually compiled and installed drivers are working, the device will likely cease to function if  new image/kernel is installed.  You will need to duplicate your steps to rebuild and reinstall the software.  Praseodym is an expert here, he should be able to help you.

---

### Post by lavini557 on 2013-06-30
I just sent a message to praseodym about it. Hope he replies

---

### Post by wildmanne39 on 2013-06-30
Hi, you said your issue was solved by installing the driver with the commands praseodym gave you so why are you trying to compile it another way?

If  this is another computer if so you need to start a new thread for that computer.
Thanks

---

### Post by lavini557 on 2013-07-01
Good sir, did you read my edited post? You should have -_-
> 
[COLOR=#000000]It worked! XD Thank you. Just wondering, but will this work if I try to update drivers on another Linux computer? Or do I have to use another set of command lines? Oh, and how do I change the title to mark it as solved?[/COLOR]
**[COLOR=#000000][EDIT] It only worked for a short time - after that it got really slow. I think it got even worse than before, because the internet is also a bit slower than usual when I used my laptop on the 1st floor [/COLOR][IMG]http://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]**[COLOR=#000000]**. I posted Terminal results of updating the driver in case it helps.**

That's from post #10, FYI[/COLOR]

---

### Post by praseodym on 2013-07-01
Try to install the driver as root-user:
```

make clean
sudo su
make
make install
exit
```

---

### Post by lavini557 on 2013-07-01
Doesn't work, unfortunately.
> 
eric@HP-Pavilion-dv6-6c35dx:~$ cd Desktop/rtl8192ce_linux
eric@HP-Pavilion-dv6-6c35dx:~/Desktop/rtl8192ce_linux$ make clean
make[1]: Entering directory `/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Entering directory `/'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192'
make: *** [clean] Error 2
eric@HP-Pavilion-dv6-6c35dx:~/Desktop/rtl8192ce_linux$ sudo su
[sudo] password for eric: 
root@HP-Pavilion-dv6-6c35dx:/home/eric/Desktop/rtl8192ce_linux# make
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Stop.
make[1]: *** [_module_/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
make: *** [all] Error 2
root@HP-Pavilion-dv6-6c35dx:/home/eric/Desktop/rtl8192ce_linux# make install
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Stop.
make[1]: *** [_module_/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
make: *** [all] Error 2
root@HP-Pavilion-dv6-6c35dx:/home/eric/Desktop/rtl8192ce_linux# exit
exit

:(

---

### Post by praseodym on 2013-07-01
Which driver version is shipped with 13.04?
```

modinfo rtl8192ce | grep versi
```
Hre with mainline-kernel 3.9 its this one:

```
modinfo rtl8192ce | grep versi
srcversion:     81B219B74DCBA4399568D61
vermagic:       3.9.0-030900-generic SMP mod_unload modversions 686 

```

---

### Post by lavini557 on 2013-07-01
Here's what I have:
> 
eric@HP-Pavilion-dv6-6c35dx:~$ modinfo rtl8192ce | grep versi
srcversion:     B41EC2D43683C181DF50FB6
vermagic:       3.8.0-25-generic SMP mod_unload modversions 


---

### Post by praseodym on 2013-07-02
So try the mainline-kernel 3.9:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/)

Download for 32bit all packages with i386.deb and all.deb, for 64bit amd64.deb and all.deb and save them in "Doanloads". Installation via
```

sudo apt-get install --reinstall build-essential dkms
sudo dpkg -i ~/Downloads/linux-*.deb
```
Reboot.

---

### Post by lavini557 on 2013-07-02
ehh...I don't think it did much. Here's my terminal output after restarting (I did the grep versi thing just to check before I started):
> 
eric@HP-Pavilion-dv6-6c35dx:~$ modinfo rtl8192ce | grep versi
srcversion:     81B219B74DCBA4399568D61
vermagic:       3.9.0-030900-generic SMP mod_unload modversions 
eric@HP-Pavilion-dv6-6c35dx:~$ cd ~/Desktop/rtl8192ce_linux
eric@HP-Pavilion-dv6-6c35dx:~/Desktop/rtl8192ce_linux$ make clean
gcc: error: /lib/modules/3.9.0-030900-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
make[1]: Entering directory `/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Entering directory `/'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192'
make: *** [clean] Error 2
eric@HP-Pavilion-dv6-6c35dx:~/Desktop/rtl8192ce_linux$ sudo su
[sudo] password for eric: 
root@HP-Pavilion-dv6-6c35dx:/home/eric/Desktop/rtl8192ce_linux# make
make[1]: Entering directory `/usr/src/linux-headers-3.9.0-030900-generic'
gcc: error: /lib/modules/3.9.0-030900-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Stop.
make[1]: *** [_module_/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.9.0-030900-generic'
make: *** [all] Error 2
root@HP-Pavilion-dv6-6c35dx:/home/eric/Desktop/rtl8192ce_linux# make install
make[1]: Entering directory `/usr/src/linux-headers-3.9.0-030900-generic'
gcc: error: /lib/modules/3.9.0-030900-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Stop.
make[1]: *** [_module_/home/eric/Desktop/rtl8192ce_linux/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.9.0-030900-generic'
make: *** [all] Error 2
root@HP-Pavilion-dv6-6c35dx:/home/eric/Desktop/rtl8192ce_linux# exit
exit


---

### Post by praseodym on 2013-07-03
You dont need to compile the driver. Check with the native one
```

dmesg | grep rtl8
iwconfig
sudo iwlist scan
iwconfig
cat /etc/resolv.conf
route -n
```

---

### Post by lavini557 on 2013-07-03
Um...I'm not sure what you were trying to do with the commands...but I'm assuming you want me to post the Terminal output.
> 
eric@HP-Pavilion-dv6-6c35dx:~$ dmesg | grep rtl8
[   13.051823] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   19.037026] rtl8192ce 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   19.037035] rtl8192ce 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   19.037038] rtl8192ce 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
eric@HP-Pavilion-dv6-6c35dx:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"WLAN-DC5B"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:22:2D:7B: DC:5D   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0


eric@HP-Pavilion-dv6-6c35dx:~$ sudo iwlist scan
[sudo] password for eric: 
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:22:2D:7B: DC:5D
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key: on
                    ESSID:"WLAN-DC5B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010aa8421b6
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0009574C414E2D44433542
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 00:1C: DF:21:33:2B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key: on
                    ESSID:"FORKEUTIS33478"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009503755d86
                    Extra: Last beacon: 24256ms ago
                    IE: Unknown: 000E464F524B45555449533333343738
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
          Cell 03 - Address: 00:13:F7:FA:17:B4
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key: on
                    ESSID:"SUE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b4e6f1ec7f
                    Extra: Last beacon: 23888ms ago
                    IE: Unknown: 0003535545
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 06:07:70:A9:02:99
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key: on
                    ESSID:"KT_WLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001761f1b331
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 00074B545F574C414E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 05 - Address: 00:07:70:A9:02:99
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key: on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001761f4b181
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010020FF7F
          Cell 06 - Address: 00:22:3F: D6:37:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key: on
                    ESSID:"WLAN-ABE42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003cec261181
                    Extra: Last beacon: 23936ms ago
                    IE: Unknown: 000A574C414E2D4142453432
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C


eric@HP-Pavilion-dv6-6c35dx:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"WLAN-DC5B"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:22:2D:7B: DC:5D   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0


eric@HP-Pavilion-dv6-6c35dx:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
eric@HP-Pavilion-dv6-6c35dx:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


---

### Post by lavini557 on 2013-07-04
bump

---

### Post by silv3rm00n on 2013-07-04
Do this and it should fix the speed

sudo ethtool -s eth0 duplex full speed 10 autoneg off

---

### Post by lavini557 on 2013-07-05
Nope. It did nothing -_- but thanks anyway :). And just an FYI, but I'm using Wifi, not ethernet. The command you told me uses eth0, not wlan0, so just saying...is there a command like that for wifi?
Oh, and just to show that I'm using wifi:
> 
eric@HP-Pavilion-dv6-6c35dx:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"WLAN-DC5B"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:22:2D:7B: DC:5D   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2760   Missed beacon:0

*squee :)

---

### Post by praseodym on 2013-07-06
I found a solution here for kernel 3.9:

[http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-unstabile-verbindung-18mb-se/2/#post-5756187](http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-unstabile-verbindung-18mb-se/2/#post-5756187)

```

echo "options rtl8192ce swlps=0" | sudo tee -a /etc/modprobe.d/rtl8192ce.conf
echo "options rtl8192ce ips=0" | sudo tee -a /etc/modprobe.d/rtl8192ce.conf
```
Reboot.

---

### Post by lavini557 on 2013-07-06
[IMG]http://media.tumblr.com/tumblr_lq2gvvXaum1qc27gg.jpg[/IMG]

But seriously you are awesome :)

---

