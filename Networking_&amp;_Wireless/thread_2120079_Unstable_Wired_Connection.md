---
title: "Unstable Wired Connection"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by whyaname on 2013-02-25
Hey all,

I have a dual boot Ubuntu 12.10 and Windows 7 system. I have a problem with the wired connection in Ubuntu. The wired connection works perfectly in Windows 7 but when I use Ubuntu it changes between Connected and Disconnected every 3 seconds or so. My wireless connection works perfectly in both Ubuntu and Windows but since I only have a wired connection at home, I am eager to resolve this issue. My laptop is HP Elitebook 8560w.

Any help would be greatly appreciated. Thanks.

---

### Post by praseodym on 2013-02-25
Please open a terminal with CTRL+ALT+T and show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by whyaname on 2013-02-25
anavajain@anavajain-HP-EliteBook-8560w-XX058AV:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1631]
    Kernel driver in use: e1000e
--
25:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 3e)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1111]
    Kernel driver in use: iwlwifi
anavajain@anavajain-HP-EliteBook-8560w-XX058AV:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1631]
    Kernel driver in use: e1000e
--
25:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 3e)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1111]
    Kernel driver in use: iwlwifi
anavajain@anavajain-HP-EliteBook-8560w-XX058AV:~$ lsmod
Module                  Size  Used by
rndis_host             13856  0 
cdc_ether              13495  1 rndis_host
usbnet                 26160  2 rndis_host,cdc_ether
vesafb                 13798  1 
joydev                 17458  0 
bnep                   18141  2 
rfcomm                 46620  12 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_idt      70210  1 
tpm_infineon           17537  0 
coretemp               13401  0 
arc4                   12530  2 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
ppdev                  17074  0 
hp_wmi                 18049  0 
sparse_keymap          13891  1 hp_wmi
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_hda_intel          33492  5 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
parport_pc             32689  1 
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19391  0 
tpm_tis                18681  0 
snd_timer              29426  2 snd_seq,snd_pcm
hp_accel               25977  0 
lis3lv02d              19830  1 hp_accel
input_polldev          13897  1 lis3lv02d
wmi                    19071  1 hp_wmi
iwlwifi               386799  0 
snd                    78921  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_rawmidi,snd_hda_intel,snd_seq,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
mac80211              540032  1 iwlwifi
microcode              22804  0 
radeon                895730  0 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
lpc_ich                17062  0 
btusb                  22475  0 
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
bluetooth             209249  22 bnep,rfcomm,btusb
ttm                    83596  1 radeon
drm_kms_helper         49113  1 radeon
cfg80211              206797  2 iwlwifi,mac80211
drm                   288721  3 radeon,ttm,drm_kms_helper
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13414  1 radeon
mac_hid                13206  0 
mei                    40691  0 
lp                     17760  0 
parport                46346  3 ppdev,parport_pc,lp
psmouse                95595  0 
serio_raw              13216  0 
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci
crc_itu_t              12708  1 firewire_core
e1000e                199273  0 
anavajain@anavajain-HP-EliteBook-8560w-XX058AV:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:9c:02:8e:cf:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5000 (5.0 KB)  TX bytes:11009 (11.0 KB)
          Interrupt:20 Memory:d4500000-d4520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30175 (30.1 KB)  TX bytes:30175 (30.1 KB)

usb0      Link encap:Ethernet  HWaddr 02:5c:63:6e:67:37  
          inet addr:192.168.42.176  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::5c:63ff:fe6e:6737/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:944 errors:3 dropped:0 overruns:0 frame:3
          TX packets:1028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:730233 (730.2 KB)  TX bytes:202651 (202.6 KB)

wlan0     Link encap:Ethernet  HWaddr 24:77:03:91:37:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

anavajain@anavajain-HP-EliteBook-8560w-XX058AV:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
anavajain@anavajain-HP-EliteBook-8560w-XX058AV:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

---

### Post by praseodym on 2013-02-25
Uninstall the package "resolvconf" and reboot.

---

### Post by whyaname on 2013-02-25
> **praseodym said:**
> Uninstall the package "resolvconf" and reboot.
How do I uninstall it? sudo apt-get remove resolvconf?

---

### Post by whyaname on 2013-02-26
> **praseodym said:**
> Uninstall the package "resolvconf" and reboot.

Uninstalling the package did not rectify the situation.

---

### Post by praseodym on 2013-02-26
Please show the outputs from above again.

---

### Post by whyaname on 2013-02-26
> **praseodym said:**
> Please show the outputs from above again.

lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:1631]
    Kernel driver in use: e1000e
--
25:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 3e)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1111]
    Kernel driver in use: iwlwifi

lsmod

Module                  Size  Used by
vesafb                 13798  1 
joydev                 17458  0 
rfcomm                 46620  12 
bnep                   18141  2 
tpm_infineon           17537  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_idt      70210  1 
coretemp               13401  0 
arc4                   12530  2 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
ppdev                  17074  0 
hp_wmi                 18049  0 
sparse_keymap          13891  1 hp_wmi
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq_midi_event     14900  1 snd_seq_midi
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
tpm_tis                18681  0 
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78921  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15048  1 snd
lpc_ich                17062  0 
microcode              22804  0 
parport_pc             32689  1 
video                  19391  0 
hp_accel               25977  0 
lis3lv02d              19830  1 hp_accel
input_polldev          13897  1 lis3lv02d
wmi                    19071  1 hp_wmi
iwlwifi               386799  0 
mac80211              540032  1 iwlwifi
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
radeon                895730  0 
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
mac_hid                13206  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
ttm                    83596  1 radeon
drm_kms_helper         49113  1 radeon
drm                   288721  3 radeon,ttm,drm_kms_helper
i2c_algo_bit           13414  1 radeon
btusb                  22475  0 
psmouse                95595  0 
cfg80211              206797  2 iwlwifi,mac80211
bluetooth             209249  22 rfcomm,bnep,btusb
lp                     17760  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
parport                46346  3 ppdev,parport_pc,lp
mei                    40691  0 
serio_raw              13216  0 
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
firewire_ohci          40402  0 
sdhci_pci              18617  0 
firewire_core          64369  1 firewire_ohci
sdhci                  32646  1 sdhci_pci
crc_itu_t              12708  1 firewire_core
e1000e                199273  0 

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:9c:02:8e:cf:9a  
          inet addr:88.159.88.55  Bcast:88.159.89.255  Mask:255.255.254.0
          inet6 addr: fe80::29c:2ff:fe8e:cf9a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68586 (68.5 KB)  TX bytes:101360 (101.3 KB)
          Interrupt:20 Memory:d4500000-d4520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95026 (95.0 KB)  TX bytes:95026 (95.0 KB)

wlan0     Link encap:Ethernet  HWaddr 24:77:03:91:37:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

cat /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

/cat/etc/resolve.conf

cat: /etc/resolve.conf: No such file or directory

---

### Post by squigish on 2013-02-26
I think this is unlikely to solve your problem, but there's a chance that the situation will be improved by COMPLETELY removing resolveconf.

When you remove a package using synaptic, or apt-get remove, some residual configuration files are left over.  By running
```
sudo apt-get purge resolveconf

```
you will remove those config files as well.

I'm not a networking expert, and I'll let someone else look through the log files you posted.

---

### Post by praseodym on 2013-02-26
The file is named  /etc/resolv.conf and the package resolvconf, both without "e"

---

### Post by whyaname on 2013-02-26
> **praseodym said:**
> The file is named  /etc/resolv.conf and the package resolvconf, both without "e"

Yes, I'm sorry but while running the /etc/resolv.conf command, I mistakenly typed resolve.conf. The package was already removed correctly and here is the result of /etc/resolv.conf :

# Generated by NetworkManager
nameserver 127.0.1.1

---

### Post by praseodym on 2013-02-27
Check:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
```

---

### Post by whyaname on 2013-02-27
> **praseodym said:**
> Check:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
```

I tried this, still no change. Another problem that has come up is that after deleting the resolv.conf package I can no longer connect to my University's wpa network. I can still connect to unsecured networks and my mobile data tethered to my laptop but the university networks do not connect at all. With the wired connection, it connects for 2 seconds and then disconnects for 5 seconds or so.

---

### Post by praseodym on 2013-02-27
In that case reinstall the package by double-click and reboot.:

[http://de.archive.ubuntu.com/ubuntu/pool/main/r/resolvconf/resolvconf_1.67ubuntu2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/r/resolvconf/resolvconf_1.67ubuntu2_all.deb)

---

### Post by whyaname on 2013-03-01
> **praseodym said:**
> In that case reinstall the package by double-click and reboot.:

[http://de.archive.ubuntu.com/ubuntu/pool/main/r/resolvconf/resolvconf_1.67ubuntu2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/r/resolvconf/resolvconf_1.67ubuntu2_all.deb)

I installed the package again and now the wifi works for wpa connection. I also tried a different distro (Linux Mint) and it has the same problem for the wired connection. Is this a Linux specific issue then because again, Windows 7 and 8 work with the wired connection.

---

