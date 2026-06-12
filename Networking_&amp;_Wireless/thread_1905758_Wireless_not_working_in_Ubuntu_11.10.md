---
title: "Wireless not working in Ubuntu 11.10"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by bach22 on 2012-01-07
Hello,
I just installed Ubuntu 11.10 , and when I try to use wireless I get the message "Server not found" (it doesn't load the page). However, it shows that I have wireless connection. I have an Acer Aspire Extensa4420, Broadcom 4312, b43 driver.
I will appreciate any help. Thanks

---

### Post by wildmanne39 on 2012-01-07
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by SuddenlyBees1000 on 2012-01-07
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # and paste the information between the brackets.
Thank you
  
<br> Hi, I'm having the same problem (Windows 7 user, just dl'ed Ubuntu last night and am positively flummoxed.) I am going to follow these same steps and paste my results in the thread... is that alright? Would you be able to help me as well?
Thanks  :KS

---

### Post by wildmanne39 on 2012-01-07
Hi SuddenlyBees1000, start your own thread please and then post the ouput of these commands into it and paste a link here to your thread and I will come and help.
Thanks

---

### Post by bach22 on 2012-01-07
calin@Bach:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Bach 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
calin@Bach:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:0123]
    Kernel driver in use: sky2
--
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e003]
    Kernel driver in use: wl
calin@Bach:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

calin@Bach:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
calin@Bach:~$ lsmod
Thanks

---

### Post by wildmanne39 on 2012-01-07
Hi, please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Watch for errors, when it is done unplug wired connection and reboot.
Thanks

---

### Post by bach22 on 2012-01-07
```

```calin@Bach:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Bach 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
calin@Bach:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:0123]
    Kernel driver in use: sky2
--
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e003]
    Kernel driver in use: wl
calin@Bach:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

calin@Bach:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
calin@Bach:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12759  0 
xt_state               12578  0 
ipt_REJECT             12576  0 
xt_tcpudp              12603  0 
iptable_filter         12810  0 
nf_nat_h323            17002  0 
nf_conntrack_h323      62913  1 nf_nat_h323
nf_nat_pptp            12629  0 
nf_conntrack_pptp      13830  1 nf_nat_pptp
nf_conntrack_proto_gre    13656  1 nf_conntrack_pptp
nf_nat_proto_gre       12767  1 nf_nat_pptp
nf_nat_tftp            12489  0 
nf_conntrack_tftp      12953  1 nf_nat_tftp
nf_nat_sip             17086  0 
nf_conntrack_sip       29730  1 nf_nat_sip
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12704  0 
nf_conntrack_ftp       13452  1 nf_nat_ftp
iptable_nat            13229  0 
nf_nat                 25890  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           82342  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
michael_mic            12612  0 
arc4                   12529  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
joydev                 17693  0 
v4l2_compat_ioctl32    17083  1 videodev
radeon               1016226  3 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
snd_rawmidi            30547  1 snd_seq_midi
lib80211_crypt_tkip    17390  0 
drm                   236290  5 radeon,ttm,drm_kms_helper
acer_wmi               23948  0 
wl                   2568210  0 
pcmcia                 49378  0 
i2c_algo_bit           13423  1 radeon
edac_core              53746  0 
psmouse                73882  0 
serio_raw              13166  0 
shpchp                 37345  0 
yenta_socket           28084  0 
sparse_keymap          13890  1 acer_wmi
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
sp5100_tco             13791  0 
snd_seq_midi_event     14899  1 snd_seq_midi
edac_mce_amd           23709  0 
nsc_ircc               28008  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              13301  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
irda                  201273  1 nsc_ircc
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211               14991  2 lib80211_crypt_tkip,wl
k8temp                 13057  0 
crc_ccitt              12667  1 irda
video                  19412  0 
wmi                    19256  1 acer_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
hid                    95463  1 usbhid
crc_itu_t              12707  1 firewire_core
sdhci                  32166  1 sdhci_pci
ahci                   26002  4 
libahci                26861  1 ahci
pata_atiixp            13164  0 
sky2                   58674  0 
These are the complete results.
Thanks

---

### Post by bach22 on 2012-01-07
It's still not working.....
Thanks anyway.

---

### Post by wildmanne39 on 2012-01-07
Hi, now that you changed drivers please run all the commands from post 2 and paste the output here again so we can see what is what.
Thanks

---

### Post by bach22 on 2012-01-07
Hi,
Here it is:```

```calin@Bach:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Bach 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
calin@Bach:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:0123]
    Kernel driver in use: sky2
--
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e003]
    Kernel driver in use: b43-pci-bridge
calin@Bach:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
calin@Bach:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
calin@Bach:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12759  0 
xt_state               12578  0 
ipt_REJECT             12576  0 
xt_tcpudp              12603  0 
iptable_filter         12810  0 
nf_nat_h323            17002  0 
nf_conntrack_h323      62913  1 nf_nat_h323
nf_nat_pptp            12629  0 
nf_conntrack_pptp      13830  1 nf_nat_pptp
nf_conntrack_proto_gre    13656  1 nf_conntrack_pptp
nf_nat_proto_gre       12767  1 nf_nat_pptp
nf_nat_tftp            12489  0 
nf_conntrack_tftp      12953  1 nf_nat_tftp
nf_nat_sip             17086  0 
nf_conntrack_sip       29730  1 nf_nat_sip
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12704  0 
nf_conntrack_ftp       13452  1 nf_nat_ftp
iptable_nat            13229  0 
nf_nat                 25890  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           82342  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
arc4                   12529  2 
joydev                 17693  0 
b43                   341198  0 
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
mac80211              462092  1 b43
snd_hda_codec_realtek   330769  1 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
pcmcia                 49378  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 b43,mac80211
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
sp5100_tco             13791  0 
psmouse                73882  0 
soundcore              12680  1 snd
edac_core              53746  0 
serio_raw              13166  0 
i2c_piix4              13301  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
k8temp                 13057  0 
edac_mce_amd           23709  0 
nsc_ircc               28008  0 
irda                  201273  1 nsc_ircc
crc_ccitt              12667  1 irda
radeon               1016226  3 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236290  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
video                  19412  0 
shpchp                 37345  0 
wmi                    19256  1 acer_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
hid                    95463  1 usbhid
crc_itu_t              12707  1 firewire_core
sdhci                  32166  1 sdhci_pci
ssb                    52752  1 b43
pata_atiixp            13164  0 
ahci                   26002  4 
libahci                26861  1 ahci
sky2                   58674  0 
Thanks again!

---

### Post by wildmanne39 on 2012-01-07
Hi, you need to change ad-hoc to infrastructure in network manager for it to work by going to the internet icon top right of the screen click on edit connection, wireless and change to infrastructure.
Thanks

---

### Post by bach22 on 2012-01-08
Hi ,
Thanks for the reply.
I did the last changes and still doesn't work...
I can see now the wireless internet icon "streaming", and if I don't disconnect the wired connection it seems to work at least for a while and than it changes automatically to wired connection. Once in a while I am asked for the router wireless password.
Before changing to Ubuntu I was using Fedora 14 and my wireless connection was working fine.
I'm not ready yet to give up using Ubuntu, and will appreciate any other ideas.
Thanks

---

### Post by wildmanne39 on 2012-01-08
Hi, let's blacklist the acer-wmi.
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Please post the output of:
```
ndiswrapper -l
sudo iwlist scan
nm-tool
lsmod | grep b43
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by bach22 on 2012-01-08
Hi,
My problem was solved!!
At the end I changed the editing in the Network connection:
In the IPv4 Settings: Method: Automatic (DHCP) and I unchecked the Require Ipv4 addressing .....box.
Thank you very much for the help!

---

### Post by wildmanne39 on 2012-01-08
Hi, your welcome! that is great, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by L1NUXFR34K on 2012-01-08
I had the same problem. It was with the N-mode. Try this:

<code>
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
</code>

---

### Post by bkratz on 2012-01-08
> **L1NUXFR34K said:**
> I had the same problem. It was with the N-mode. Try this:

<code>
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
</code>



The op (original poster) has a Broadcom card which does not use the same driver you do!

---

### Post by UltimateCat on 2012-01-08
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # and paste the information between the brackets.
Thank you

Sorry to chime in but I have had this same problem for 6 weeks.:(
Just like; bach22 and ;Suddenly Beeslooo have had a connection but found that each time they try to open the internet browser they get the same thing; " Server Not Found"
Can I use these commands for Ubuntu 10.04?
Hoping for solutions for all of us with this prognosis.
Sincerely:D

---

### Post by wildmanne39 on 2012-01-08
Hi UltimateCat, please post the output from the commands in post 2 so we can see where things are at.
Thanks

---

