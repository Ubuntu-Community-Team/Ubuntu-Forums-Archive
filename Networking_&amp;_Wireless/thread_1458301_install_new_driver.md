---
title: "install new driver"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by roundhead on 2010-04-19
I have been searching off and on for weeks. I am using 9.10 Karma and have the broadcom b43 card. when I go to the Hardware Drivers, it shows the Broadcom STA wireless driver is activated and currently in use. BUT under the wireless network driver tab (System, Admin, Windows wireless drivers) there is nothing showing up. Everyone says to look for the Network Admin icon on the top right screen but there is nothing there. there is no wireless icon. there used to be, but it never worked. I have tried downloading the driver and I have extracted it. but I dont know how to install it. Or is it already installed. I am new to Linux and have really tried to find a solution...no avail. thanks so much for any suggestions

---

### Post by bkratz on 2010-04-19
> **roundhead said:**
> I have been searching off and on for weeks. I am using 9.10 Karma and have the broadcom b43 card. when I go to the Hardware Drivers, it shows the Broadcom STA wireless driver is activated and currently in use. BUT under the wireless network driver tab (System, Admin, Windows wireless drivers) there is nothing showing up. Everyone says to look for the Network Admin icon on the top right screen but there is nothing there. there is no wireless icon. there used to be, but it never worked. I have tried downloading the driver and I have extracted it. but I dont know how to install it. Or is it already installed. I am new to Linux and have really tried to find a solution...no avail. thanks so much for any suggestions

First I think we need to determine which wireless card you have so we know whether b43 or sta is appropriate.
Go to the termina (Application>>Accessories>>Terminal) and enter in 

```
lspci | grep Network
```

that is LSPCI in lowercase N in upper, and copy/paste the output back here or simply report back it should be BCM43xx xx is what we need to know.

---

### Post by roundhead on 2010-04-19
BCM 4312 802.11a/b/g
shouldnt I be able to cut and paste? doesnt seem to work

---

### Post by bkratz on 2010-04-19
> **roundhead said:**
> BCM 4312 802.11a/b/g
shouldnt I be able to cut and paste? doesnt seem to work

Well the sta driver is the correct one; however, did you try to use ndiswrapper at some point?  That's the only way I know to get the Windows wireless driver entry in System>>Administration, by downloading ndisgtk. If so, we will probably have to remove it or blacklist it  and then try (just save this for later)

I have a good thread about that, just need some time to find it.


[B](here is the thread, just in case we need it and I lose it again!)
[http://ubuntuforums.org/showthread.php?t=507378](http://ubuntuforums.org/showthread.php?t=507378)
just for reference--don't do unless we need to![/B]

```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

```




could you also post the output of 

```
lsmod
```

(that is LSMOD in lowercase). How are you trying to do the copy/paste?

---

### Post by roundhead on 2010-04-20
E: The method driver /usr/lib/apt/methods/attp could not be found.
E: The method driver /usr/lib/apt/methods/attp could not be found.
stewart@dell1501:~$ lsmod
Module                  Size  Used by
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
xt_TCPMSS               3868  1 
xt_limit                2176  8 
xt_tcpudp               2780  11 
nf_nat_irc              2012  0 
nf_nat_ftp              2652  0 
ipt_LOG                 5344  8 
ipt_MASQUERADE          2204  1 
xt_DSCP                 2844  0 
ipt_REJECT              2812  1 
nf_conntrack_irc        4992  1 nf_nat_irc
nf_conntrack_ftp        6880  1 nf_nat_ftp
xt_state                1820  8 
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
iptable_nat             5500  1 
nf_nat                 18096  4 nf_nat_irc,nf_nat_ftp,ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13352  11 iptable_nat,nf_nat
nf_conntrack           67484  9 nf_nat_irc,nf_nat_ftp,ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
iptable_mangle          3452  0 
snd_hda_codec_idt      59876  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  1 
b44                    28652  0 
ssb                    35524  1 b44
mii                     5212  1 b44
lib80211_crypt_tkip     8636  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
dell_wmi                2564  0 
ip_tables              11692  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16544  10 xt_TCPMSS,xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
wl                   1272936  0 
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
psmouse                56500  0 
serio_raw               5280  0 
ricoh_mmc               3676  0 
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  1 sdhci
lib80211                6432  2 lib80211_crypt_tkip,wl
k8temp                  4188  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_piix4               9932  0 
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp

sorry I was trying ctrl C instead of highlighting and copying/paste...I asked Chilli about that install bcmwl since nothing was happening. I will post the output.
thanks for your help!

---

### Post by roundhead on 2010-04-20
also as you can see, when I did the get update it said driver could not be found. I know that I did blacklist B43 as suggested in another thread. and I am sure that I tried the ndiscwrapper as well. any suggestions would be greatly appreciated
Stewart

---

### Post by bkratz on 2010-04-20
> **roundhead said:**
> also as you can see, when I did the get update it said driver could not be found. I know that I did blacklist B43 as suggested in another thread. and I am sure that I tried the ndiscwrapper as well. any suggestions would be greatly appreciated
Stewart

Well I don't see ndiswrapper in your modules so you must have already removed it. I do see several interesting things though, the b44 and ssb drivers which are probably used by your ethernet controller, so they can't be removed or blacklisted. I do see WL so the STA driver is there which is good.

I also see several modules that are indicative of a dell laptop. Is it? If so you might want to read the following:

[http://ubuntuforums.org/showpost.php?p=9031581&postcount=2](http://ubuntuforums.org/showpost.php?p=9031581&postcount=2)


Here is another thread by probably the best Broadcom person: Ayuthia which looks suspiciously just like yours you could probably find answers there ( it is very specifically documented)

[http://www.uluga.ubuntuforums.org/showthread.php?t=1308533](http://www.uluga.ubuntuforums.org/showthread.php?t=1308533)

it should get you working.


By the way if the first link works we will have to make it permanent, so post back.

---

### Post by roundhead on 2010-04-20
yes it is a dell...I tried sudo rmmod -f dell-laptop and this is the message
ERROR: Removing 'dell_laptop': No such file or directory

---

### Post by roundhead on 2010-04-20
I followed Ayuthia's instructions and here is the result

ERROR: Removing 'dell_laptop': No such file or directory
stewart@dell1501:~$ sudo modprobe -r b43 wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
stewart@dell1501:~$ sudo modprobe -r b43 ssb wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ssb is in use.
stewart@dell1501:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
stewart@dell1501:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:1C:10:8A:52:4C
                    ESSID:"BBC"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-36 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:12:0E:89:43:98
                    ESSID:"08FX02046909"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-71 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

eth0      Interface doesn't support scanning.

stewart@dell1501:~$ 
Ayuthia's instructions....here is the result

---

### Post by roundhead on 2010-04-20
the ndiswrapper shows up in the system/admin/synaptic package manager

---

### Post by bkratz on 2010-04-20
> **roundhead said:**
> I followed Ayuthia's instructions and here is the result

ERROR: Removing 'dell_laptop': No such file or directory
stewart@dell1501:~$ sudo modprobe -r b43 wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
stewart@dell1501:~$ sudo modprobe -r b43 ssb wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ssb is in use.
stewart@dell1501:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
stewart@dell1501:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:1C:10:8A:52:4C
                    ESSID:"BBC"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-36 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:12:0E:89:43:98
                    ESSID:"08FX02046909"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-71 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

eth0      Interface doesn't support scanning.

stewart@dell1501:~$ 
Ayuthia's instructions....here is the result

Told you not to remove ssb!, just kidding. All the rest of the warnings you can ignore-- they don't mean anything. It looks like you have a working interface. Can you temporarily remove encryption just to make sure you can connect? I never did get tkip/aes working as a combination, but I did get Wpa2 with aes (only) working quite well. Congratulations, you are about there. The Dell_laptop module shows up in the modules shown, but if it doesn't matter, don't worry. I did notice that the original post shows a dash rather than an underscore after the word Dell (that is the way I copied from the original). If it still doesn't connect try removing Dell_laptop rather than Dell-laptop, but if it works don't mess with it. You could remove the windows wireless drivers using synaptic by removing ndisgtk, but why bother, just ignore it. Hopefully you are set if not post back.

---

### Post by roundhead on 2010-04-21
> **bkratz said:**
> Told you not to remove ssb!, just kidding. All the rest of the warnings you can ignore-- they don't mean anything. It looks like you have a working interface. Can you temporarily remove encryption just to make sure you can connect? I never did get tkip/aes working as a combination, but I did get Wpa2 with aes (only) working quite well. Congratulations, you are about there. The Dell_laptop module shows up in the modules shown, but if it doesn't matter, don't worry. I did notice that the original post shows a dash rather than an underscore after the word Dell (that is the way I copied from the original). If it still doesn't connect try removing Dell_laptop rather than Dell-laptop, but if it works don't mess with it. You could remove the windows wireless drivers using synaptic by removing ndisgtk, but why bother, just ignore it. Hopefully you are set if not post back.
dear Bkratz, 
I am actually illiterate with linux and am very slow with everything else. I have been learning as I go for a few weeks. I really want to use Ubuntu but it may be something more difficult, not having any background in computers. do I need to disconnect the ethernet to get wifi to work? for some reason, it just will not show up. I have been messing around following some advice on other threads but I am afraid it may be too much to ask. my options are A) spend an inhumanly amount of time trying to fix this, B) pay someone to fix this (not really an option) or C) let Bill Gates win. I may need to start over with your advice. If Ayuthia can help, that would be great. I dont have 75 beans so I cant ask him or her.  let me reprint the new stuff

---

### Post by roundhead on 2010-04-21
will try later...I can nolonger connect with the laptop using the cable.

---

