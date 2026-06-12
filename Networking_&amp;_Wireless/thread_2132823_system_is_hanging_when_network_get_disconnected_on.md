---
title: "system is hanging when network get disconnected on my laptop"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by manopj1 on 2013-04-06
I use ubuntu 11.04 client with autofs configured nfs mount.I have conneted this client to ldap server and getting sucessfull authenication.I configured offline configuration also as my lap top network conntion through wifi.Now I am facing two issues.

My client gui hangs when wifi network disconnected.

I have upgraded the kernel to 3.1.0-030100rc10-generic but still the problem exits.

---

### Post by praseodym on 2013-04-06
You know that 11.04 is outdated? I recommend a fresh installation of 12.04. Please check the outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by manopj1 on 2013-04-08
here it shows the output 

oot@p61:~# lspci -nnk|grep -iA2 net
01:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
    Kernel driver in use: iwlagn
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: QUANTA Computer Inc Device [152d:0772]
    Kernel driver in use: r8169
root@p61:~# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@p61:~# lsmod
Module                  Size  Used by
binfmt_misc            17292  1 
parport_pc             32114  0 
ppdev                  12849  0 
nfs                   302874  1 
lockd                  78804  1 nfs
fscache                50674  1 nfs
auth_rpcgss            39629  1 nfs
nfs_acl                12771  1 nfs
sunrpc                205179  13 nfs,lockd,auth_rpcgss,nfs_acl
dm_crypt               22559  0 
autofs4                27924  2 
arc4                   12473  2 
iwlagn                278442  0 
snd_hda_codec_realtek   240069  1 
mac80211              411961  1 iwlagn
snd_hda_intel          24262  2 
snd_hda_codec          93296  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25187  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
cfg80211              172813  2 iwlagn,mac80211
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
psmouse                69362  0 
lp                     17455  0 
serio_raw              12990  0 
parport                40930  3 parport_pc,ppdev,lp
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  2 dm_mirror,dm_region_hash
btrfs                 606516  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
i915                  519054  3 
drm_kms_helper         32889  1 i915
drm                   196543  4 i915,drm_kms_helper
r8169                  47492  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
root@p61:~# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@p61:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth6      Interface doesn't support scanning.

wlan6     Scan completed :
          Cell 01 - Address: 1C:AF:F7:81:AD:58
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"CSE-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000ce6c97
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 00054353452D32
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706474220010D0B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 02 - Address: 1C:AF:F7:81:AD:59
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"CSEstaff"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000cfcd80
                    Extra: Last beacon: 5216ms ago
                    IE: Unknown: 00084353457374616666
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706474220010D0B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 03 - Address: 1C:AF:F7:81:AD:88
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"CSE-1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002714b393b9
                    Extra: Last beacon: 4800ms ago
                    IE: Unknown: 00054353452D31
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 0706474220010D0B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407080800000000000000000000000000000000000000
                    IE: Unknown: 3D1607080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 04 - Address: 58:93:96:08:3F:79
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d5d7b454
                    Extra: Last beacon: 4608ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: DD1A00904C340B080000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD080013920100018500
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 58:93:96:C8:3F:79
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"AJCE CENTRAL WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d5d7bd58
                    Extra: Last beacon: 4608ms ago
                    IE: Unknown: 0011414A43452043454E5452414C2057694669
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F20201018F0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: DD1A00904C340B080000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD080013920100018500
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 58:93:96:88:3F:79
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:off
                    ESSID:"AJCE-Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d5d7b8f0
                    Extra: Last beacon: 4608ms ago
                    IE: Unknown: 000B414A43452D4D6F62696C65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: DD1A00904C340B080000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD080013920100018500

root@p61:~#

---

### Post by praseodym on 2013-04-08
There is a bug with the N-mode of the driver. Deactivate it via:
```

echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```

---

### Post by manopj1 on 2013-04-09
thanks for your reply.but still my problem exits.I think it is the issue with ldap authetication or nfs in gui mode.I use pam

terminal its working fine.only thing in gui i am not able to logout and restart.

---

