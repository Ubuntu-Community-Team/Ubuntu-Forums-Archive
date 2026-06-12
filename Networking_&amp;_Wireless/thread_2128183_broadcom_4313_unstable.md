---
title: "broadcom 4313 unstable"
date: 2013-03-22
forum: Networking &amp; Wireless
---

### Post by bou3lam on 2013-03-22
hi
i have an hp g6 with broadcom bcm4313, ubuntu 12.10, all was working fine before the normal ubuntu updates, now the signal is very weak and cant get connected with broadcom card only after several attempts and for some minutes only, i use now a usb tp-link modem, please someone help, here's my infos :

```
simo@Simo:~$ cat /etc/lsb-release; uname -aDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux Simo 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



```

```

simo@Simo:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1670]
    Kernel driver in use: r8169



```


```


simo@Simo:~$ iwconfig
wlan1     IEEE 802.11bgn  ESSID:"SAGEM_FA54"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 4C:17:EB 
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:29   Missed beacon:0


eth0      no wireless extensions.


eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


lo        no wireless extensions.




```


```

simo@Simo:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no




```


```


simo@Simo:~$ lsmod
Module                  Size  Used by
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
binfmt_misc            17501  1 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_idt      70210  1 
joydev                 17458  0 
lib80211_crypt_tkip    17380  0 
wl                   2573608  0 
arc4                   12530  2 
rt2800usb              22662  0 
rt2800lib              58731  1 rt2800usb
crc_ccitt              12708  1 rt2800lib
coretemp               13401  0 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
rt2x00usb              20665  1 rt2800usb
rt2x00lib              54939  3 rt2800usb,rt2800lib,rt2x00usb
hp_wmi                 18049  0 
sparse_keymap          13891  1 hp_wmi
mac80211              540032  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              206797  2 rt2x00lib,mac80211
ip6t_REJECT            12575  1 
xt_hl                  12522  6 
ip6t_rt                12559  3 
nf_conntrack_ipv6      14055  7 
nf_defrag_ipv6         13203  1 nf_conntrack_ipv6
lib80211               14382  2 lib80211_crypt_tkip,wl
ipt_REJECT             12542  1 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
xt_LOG                 17350  10 
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
xt_limit               12712  13 
xt_tcpudp              12604  18 
snd_rawmidi            30513  1 snd_seq_midi
xt_addrtype            12636  4 
wmi                    19071  1 hp_wmi
snd_seq_midi_event     14900  1 snd_seq_midi
psmouse                95595  0 
xt_state               12579  14 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
microcode              22804  0 
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
ip6table_filter        12816  1 
ip6_tables             27208  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12666  0 
nf_conntrack_broadcast    12590  1 nf_conntrack_netbios_ns
nf_nat_ftp             12650  0 
nf_nat                 25255  1 nf_nat_ftp
nf_conntrack_ipv4      14481  9 nf_nat
nf_defrag_ipv4         12730  1 nf_conntrack_ipv4
nf_conntrack_ftp       13360  1 nf_nat_ftp
uvcvideo               76750  0 
nf_conntrack           82634  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
videobuf2_core         32852  1 uvcvideo
iptable_filter         12811  1 
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
rtsx_pci_ms            13012  0 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13206  0 
memstick               16555  1 rtsx_pci_ms
soundcore              15048  1 snd
ip_tables              26996  1 iptable_filter
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
x_tables               29757  13 ip6t_REJECT,xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
serio_raw              13216  0 
fglrx                5201123  111 
amd_iommu_v2           19098  1 fglrx
i915                  520615  2 
drm_kms_helper         49113  1 i915
lpc_ich                17062  0 
mei                    40691  0 
drm                   288721  3 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
video                  19391  1 i915
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
rtsx_pci_sdmmc         17476  0 
ahci                   25721  2 
libahci                31192  1 ahci
rtsx_pci               28325  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  61651  0 



```

---

### Post by fantab on 2013-03-22
How had you installed the Driver?
[Read Here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access") for more info.

---

### Post by bou3lam on 2013-03-22
thank for your reply, i tried many drivers from the synaptic, all without success, from the link you gave me i see :

```

[COLOR=#333333][FONT=Ubuntu][wl]("http://www.broadcom.com/support/802.11/linux_sta.php") - Proprietary Broadcom STA Wireless driver [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]For Chip ID BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, BCM43227 and BCM43228.
[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT]

[LIST]
[*=left][FONT=inherit]Install either [bcmwl-kernel-source]("https://launchpad.net/ubuntu/+source/bcmwl") (instructions below) **OR** the [broadcom-sta]("https://launchpad.net/ubuntu/+source/broadcom-sta") (instructions at [http://wiki.debian.org/wl](http://wiki.debian.org/wl)) packages.[/FONT]
[/LIST]
[/LIST]

```

and

```

[COLOR=#333333][FONT=Ubuntu][brcmsmac]("http://wireless.kernel.org/en/users/Drivers/brcm80211") (a.k.a brcm80211) - Open source driver from Broadcom (merged into kernel 2.6.37)[FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]For Chip ID BCM4313, BCM43224 and BCM43225.[/FONT]
[/LIST]

```

which one you reccomend to try please ?
thanks

---

### Post by bou3lam on 2013-03-22
tried [broadcom-sta]("https://launchpad.net/ubuntu/+source/broadcom-sta") without success, the card have been missing from the network manager, only tp-link was shown, [bcmwl-kernel-source]("https://launchpad.net/ubuntu/+source/bcmwl") its what i was and using now, it keep trying to connect several times without success, [brcmsmac]("http://wireless.kernel.org/en/users/Drivers/brcm80211") tried to install it from this [http://ubuntuforums.org/showthread.php?t=1617380](http://ubuntuforums.org/showthread.php?t=1617380)  the command [COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000]git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git started downloading a file of 1 gigabyte size, i stopped it, i dont know what to do now[/COLOR][/FONT]

---

### Post by wildmanne39 on 2013-03-22
Hi, please do what this link says.
[http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896](http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896)
Thanks

---

### Post by bou3lam on 2013-03-22
> **Wild Man said:**
> Hi, please do what this link says.
[http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896](http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896)
Thanks
thank you, after doing that the broadcom is not showing in the network manager, only the tp-link

edit :

+ an error :
[[IMG]http://img543.imageshack.us/img543/4838/screenshotfrom201303221.png[/IMG]](http://imageshack.us/photo/my-images/543/screenshotfrom201303221.png/)


Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by bou3lam on 2013-03-22
after updating through ubuntu update tool all seems working fine now ! 
thanks again

---

### Post by bou3lam on 2013-03-22
not for long :( the same as before, [COLOR=#000000] the signal is very weak and cant get connected with broadcom card only after several attempts and for some minutes only, i use now a usb tp-link modem[/COLOR]

---

### Post by bou3lam on 2013-03-22
tried even an older version, no success : [bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb")

maybe the kernel ?

---

### Post by fantab on 2013-03-23
BCM4313 is not supported by open source driver. And there is no closed source driver readily available for Linux, AFAIK. I have the same card on my netbook. 

As a workaround we have to extract the firmware from the card itself with **b43-fwcutter**... [Read Here]("http://linuxwireless.org/en/users/Drivers/b43#Supported_devices") (especially read the section, "If you are using the b43 driver from 3.2 kernel or newer"). Following the instructions had fixed a similar issue for me.
Also revisit the link I posted earlier.

Good Luck.

---

### Post by Hadaka on 2013-03-23
Hi, your card,BCM4313 is just that, card #4313
i could just as easily be BCM8920. The driver is
determined by the 14e4 #  [14e4:4727] 'wl' driver
broadcom-kernel-source.
If possible unplug the usb wireless and from a wired
connection....please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl

```
then rebuild..
```
sudo apt-get install linux-headers-generic
 sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
unplug the wired connection and test.
thanks.

---

### Post by bou3lam on 2013-03-23
> **fantab said:**
> BCM4313 is not supported by open source driver. And there is no closed source driver readily available for Linux, AFAIK. I have the same card on my netbook. 

As a workaround we have to extract the firmware from the card itself with **b43-fwcutter**... [Read Here]("http://linuxwireless.org/en/users/Drivers/b43#Supported_devices") (especially read the section, "If you are using the b43 driver from 3.2 kernel or newer"). Following the instructions had fixed a similar issue for me.
Also revisit the link I posted earlier.

Good Luck.
> **fantab said:**
> BCM4313 is not supported by open source driver. And there is no closed source driver readily available for Linux, AFAIK. I have the same card on my netbook. 


As a workaround we have to extract the firmware from the card itself with b43-fwcutter... Read Here (especially read the section, "If you are using the b43 driver from 3.2 kernel or newer"). Following the instructions had fixed a similar issue for me.
Also revisit the link I posted earlier.


Good Luck.
hi
i have just tried your method, in synaptic i removed everything else than b43-fwcutter, rebooted then did what in the link you gave me, after rebooting, in the network manager there is only the usb one showing


here some infos :
```

/etc/modprobe.d/blacklist.conf  :
#blacklist b43
#blacklist bcma
blacklist ssb
blacklist brcmsmac
#blacklist brcmsmac
#blacklist bcma
baclklist b43legacy

```


```
root@Simo:/home/simo# iwconfig
wlan1     IEEE 802.11bgn  ESSID:"SAGEM_FA54"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 4C:17:EB
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=25/70  Signal level=-85 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:799  Invalid misc:44   Missed beacon:0


eth0      no wireless extensions.


lo        no wireless extensions.

```




```
root@Simo:/home/simo# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux Simo 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



```






```

root@Simo:/home/simo# lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: bcma-pci-bridge
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1670]
    Kernel driver in use: r8169



```




```



root@Simo:/home/simo# iwconfig
wlan1     IEEE 802.11bgn  ESSID:"SAGEM_FA54"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 4C:17:EB   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=27/70  Signal level=-83 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1044  Invalid misc:44   Missed beacon:0


eth0      no wireless extensions.


lo        no wireless extensions.



```


```

root@Simo:/home/simo# rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no





```


```

root@Simo:/home/simo# lsmod
Module                  Size  Used by
parport_pc             32689  0 
ppdev                  17074  0 
rfcomm                 46620  0 
bnep                   18141  2 
bluetooth             209249  10 rfcomm,bnep
binfmt_misc            17501  1 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_idt      70210  1 
fglrx                5201123  89 
joydev                 17458  0 
arc4                   12530  2 
bcma                   35657  0 
amd_iommu_v2           19098  1 fglrx
coretemp               13401  0 
ip6t_REJECT            12575  1 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
snd_hda_intel          33492  3 
rt2800usb              22662  0 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
xt_hl                  12522  6 
snd_hwdep              17699  1 snd_hda_codec
rt2800lib              58731  1 rt2800usb
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
ip6t_rt                12559  3 
crc_ccitt              12708  1 rt2800lib
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rt2x00usb              20665  1 rt2800usb
rt2x00lib              54939  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              540032  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              206797  2 rt2x00lib,mac80211
snd_seq_midi           13325  0 
nf_conntrack_ipv6      14055  7 
nf_defrag_ipv6         13203  1 nf_conntrack_ipv6
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 18049  0 
sparse_keymap          13891  1 hp_wmi
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  520615  2 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
drm_kms_helper         49113  1 i915
ipt_REJECT             12542  1 
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
drm                   288721  3 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
lpc_ich                17062  0 
mei                    40691  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
xt_LOG                 17350  10 
video                  19391  1 i915
xt_limit               12712  13 
wmi                    19071  1 hp_wmi
xt_tcpudp              12604  18 
xt_addrtype            12636  4 
rtsx_pci_ms            13012  0 
xt_state               12579  14 
psmouse                95595  0 
microcode              22804  0 
mac_hid                13206  0 
memstick               16555  1 rtsx_pci_ms
serio_raw              13216  0 
ip6table_filter        12816  1 
ip6_tables             27208  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12666  0 
nf_conntrack_broadcast    12590  1 nf_conntrack_netbios_ns
nf_nat_ftp             12650  0 
nf_nat                 25255  1 nf_nat_ftp
nf_conntrack_ipv4      14481  9 nf_nat
nf_defrag_ipv4         12730  1 nf_conntrack_ipv4
nf_conntrack_ftp       13360  1 nf_nat_ftp
nf_conntrack           82634  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12811  1 
ip_tables              26996  1 iptable_filter
x_tables               29757  13 ip6t_REJECT,xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
rtsx_pci_sdmmc         17476  0 
rtsx_pci               28325  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25721  2 
libahci                31192  1 ahci
r8169                  61651  0

```

---

