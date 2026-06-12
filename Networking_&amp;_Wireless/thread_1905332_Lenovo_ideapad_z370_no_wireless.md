---
title: "Lenovo ideapad z370 no wireless"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by blibben on 2012-01-06
Hi,

I got a problem with my Lenovo thinkpad. When I first installed Oneiric Ocelot - 11.10, I had no problem with my Wireless. I re-installed the same system a few days ago and since then I can't turn on my Wireless. The computer doesn't even find it. I've already installed STA ([http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)). It also seems to work properly in additional drivers. When I write "sudo rfkill list" I get the message:

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Can someone please help me? Thank you!

---

### Post by wildmanne39 on 2012-01-06
Hi, it says it is hard blocked which ususally means the actual switch is off on the computer try turning it on with the switch or a key press like f12 or fn f12, you may have to look at your documentation to see what turns it on.

Also please post:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
lsmod
```
Thanks

---

### Post by blibben on 2012-01-06
Hi.

I already tried to the two different 2 buttons for wireless but nothing changes.... I wrote your command and here's the answer:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux nicolas 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
nicolas@nicolas:~$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: wl
nicolas@nicolas:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated  
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

Thanks for the fast reply!

---

### Post by wildmanne39 on 2012-01-06
Hi, please post output of:
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by blibben on 2012-01-06
!

---

### Post by blibben on 2012-01-06
```
Module                  Size  Used by
parport_pc             32114  0
ppdev                  12849  0
snd_hda_codec_hdmi     31426  1
snd_hda_codec_realtek   254125  1
joydev                 17393  0
rfcomm                 38408  0
bnep                   17923  2
bluetooth             148839  10 rfcomm,bnep
binfmt_misc            17292  1
lib80211_crypt_tkip    17240  0
wl                   2646601  0
snd_hda_intel          24262  2
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rts5139               279514  0
uvcvideo               67271  0
videodev               85626  1 uvcvideo
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
psmouse                73673  0
serio_raw              12990  0
mei                    36466  0
nouveau               663211  0
ttm                    65224  1 nouveau
i915                  505159  3
drm_kms_helper         32889  2 nouveau,i915
drm                   192194  6 nouveau,ttm,i915,drm_kms_helper
i2c_algo_bit           13199  2 nouveau,i915
mxm_wmi                12859  1 nouveau
ideapad_laptop         13575  0
sparse_keymap          13658  1 ideapad_laptop
video                  18908  2 nouveau,i915
wmi                    18744  1 mxm_wmi
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0
ahci                   21634  2
libahci                25727  1 ahci
```

---

### Post by wildmanne39 on 2012-01-06
Hi, please try:
```
sudo rfkill unblock all
```
Thanks

---

### Post by blibben on 2012-01-06
Hi again.

Already tried but it's not working...

---

### Post by wildmanne39 on 2012-01-06
Hi, please try:
```
sudo rmmod -f mxm_wmi
```
Thanks

---

### Post by blibben on 2012-01-06
Hi. I get the message:
```
ERROR: Removing 'mxm_wmi': Resource temporarily unavailable 
```

Thanks

---

### Post by wildmanne39 on 2012-01-06
Hi, please show:
```
cat /var/lib/NetworkManager/NetworkManager.state
```
Thanks

---

### Post by blibben on 2012-01-06
Hi

I just get the message that the Archive doesn't exist.  

Thanks

---

### Post by wildmanne39 on 2012-01-06
Hi, did you copy and paste the command? you should have seen a small file.

Try it one more time please.
Thanks

---

### Post by wildmanne39 on 2012-01-06
Hi, I have to leave to go to the store I will be back in a little while.
Thanks

---

### Post by blibben on 2012-01-06
Hi..

Incredible enough I fixed it... After reading some threads from people with the same issue, though using windows, I entered BIOS and choosed "Restore to default values". Then I just saved and exited and everything's working perfectely well... I have no clue how come. Maybe the bug is in BIOS? Thank you for all your efforts! I never got an answer so quick before!

---

### Post by wildmanne39 on 2012-01-06
Hi, your welcome that is strange, please use thread tools to mark as solved.
Thanks

---

### Post by kushlendramishra on 2012-04-01
Hi, I am having the same problem with the same machine. Initially, I had installed Ubuntu 11.10 but could not get the wireless working. I installed Ubuntu 10.10 hoping since it is the more stable version, it might solve the problem, but it created more problems than it solved. I upgraded to Ubuntu 11.04 but still cant get the wireless working.

---

### Post by wildmanne39 on 2012-04-01
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by parovelb on 2012-04-07
Hello!
I have an issue too. I am using the 12.04beta xubuntu with lenovo s205. My wireless seems inexistent although the switch is on and in the wireless is bios enabled. Below is what I get from the list of commands mentioned earlier.

```
parovelb@lenchi:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
parovelb@lenchi:~$ 
parovelb@lenchi:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux lenchi 3.2.0-21-generic #34-Ubuntu SMP Fri Mar 30 04:25:35 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
parovelb@lenchi:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Lenovo Device [17aa:397b]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Lenovo Device [17aa:f101]
	Kernel modules: rt2800pci
parovelb@lenchi:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5986:0292 Acer, Inc 
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 0489:e00d Foxconn / Hon Hai 
parovelb@lenchi:~$ iwconfig
pan1      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

parovelb@lenchi:~$ rfkill list all
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
parovelb@lenchi:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12759  1 
iptable_filter         12810  1 
iptable_nat            13229  1 
nf_nat                 25891  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           81926  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  4 ipt_MASQUERADE,iptable_filter,iptable_nat,ip_tables
bridge                 91179  0 
stp                    12931  1 bridge
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
rfcomm                 47604  4 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_conexant    62128  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_intel          33773  6 
snd_hda_codec         127706  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17693  0 
btusb                  18288  1 
snd_seq_midi           13324  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
rts5139               351143  0 
bluetooth             180104  13 bnep,rfcomm,btusb
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
v4l2_compat_ioctl32    17128  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
radeon                804319  3 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  22 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87603  0 
serio_raw              13211  0 
sp5100_tco             13791  0 
ttm                    76949  1 radeon
k10temp                13166  0 
i2c_piix4              13301  0 
soundcore              15091  1 snd
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
mac_hid                13253  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 radeon
video                  19411  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62098  0 

```

Where is the catch?

---

### Post by wildmanne39 on 2012-04-07
Hi, does it connect and work then disconnect? please explain.
Thanks

---

### Post by parovelb on 2012-04-07
No, it does not connect however it shows the previously used connections. I have the network-manager installed. Btw, if I turn off the switch the bluetooth goes off therefore the hard switch is working.

---

### Post by wildmanne39 on 2012-04-07
Hi, try this if it works we will make it permanent:
```
sudo ifconfig wlan0 down
sudo rmmod -f rt2800pci
sudo modprobe rt2800pci nohwcrypt=1
sudo ifconfig wlan0 up
```
Thanks

---

### Post by parovelb on 2012-04-09
@wildmanne39
Thank you Wildmanne39 for your effort. @moteprime had the same problem and found the solution in another tread ([http://ubuntuforums.org/showthread.php?t=1849602&page=2](http://ubuntuforums.org/showthread.php?t=1849602&page=2), answer n.20). 
I think it is a matter of driver version. For me the solution was installing an older driver ([http://ubuntuforums.org/showthread.php?p=11830109](http://ubuntuforums.org/showthread.php?p=11830109),  answer n.5).

---

### Post by wildmanne39 on 2012-04-15
Hi, I am glad you got it working.
Enjoy

---

### Post by vinloop on 2012-07-07
the problem in this case is that phy0 switch is dependent on the lenovo energy management software for windows. your wifi card power wont turn on until that switch is on. so what you need to do is install windows and the energy management driver for windows. your wifi will start working(check the Fn+f5 function is also turned on). done this, when you start your ubuntu, wifi will be working. have fun !!

---

