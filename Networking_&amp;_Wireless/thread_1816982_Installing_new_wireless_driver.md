---
title: "Installing new wireless driver"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by amirfoad on 2011-08-02
Hi!
I have a netbook (HP Mini 110) which the default OS was Windows 7 Starter!
I change the OS to Ubuntu! every thing is ok, but the problem is wireless network!
my wireless card model is: [B]Ralink rt3090
[/B]I know that ubuntu have basically problem with Ralink Cards! and can't verify the right model!
the problem is in weak signal and lots of disconnects and many so! 
I checked the Fedora 15 and also SUSE 11.4 and in SUSE it was great! but I have some other problems with SUSE!

I searched a lot and finally in French forums I found the answer:

[http://translate.google.com/translate?hl=en&rurl=translate.google.com&sl=fr&tl=en&u=http://forum.ubuntu-fr.org/viewtopic.php%3Fid%3D442993](http://translate.google.com/translate?hl=en&rurl=translate.google.com&sl=fr&tl=en&u=http://forum.ubuntu-fr.org/viewtopic.php%3Fid%3D442993)

as you see the problem is driver which is not correct and in this link you can find the correct driver:

[http://translate.googleusercontent.com/translate_c?hl=en&rurl=translate.google.com&sl=fr&tl=en&twu=1&u=http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/pool/main/r/rt3090/&usg=ALkJrhhTzlyWc7rj3oIFWdZ98Zv0olC8qw](http://translate.googleusercontent.com/translate_c?hl=en&rurl=translate.google.com&sl=fr&tl=en&twu=1&u=http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/pool/main/r/rt3090/&usg=ALkJrhhTzlyWc7rj3oIFWdZ98Zv0olC8qw)

But now my problem is that I don't know how to install new driver? :D
I read the readme file in package but I don't understand it!

someone who is professional in ubuntu please give me the step by step manual of how to install this new driver!
I really need it!
Thanks a lot!

---

### Post by wildmanne39 on 2011-08-02
Hi, run these commands in the terminal please:
```
sudo lshw -C network
```
```
lsmod
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by amirfoad on 2011-08-02
hi. tnx for reply.
here is the result:
```
 To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

amirfoad@amirfoad-HP-Mini-110-3000:~$ sudo lshw -C network
[sudo] password for amirfoad: 
                                        
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 04
       serial: 00:21:cc:47:84:2b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:90004000-90004fff memory:90000000-90003fff
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:f0:6d:4c:37:1a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-10-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:92000000-9200ffff
amirfoad@amirfoad-HP-Mini-110-3000:~$ 
amirfoad@amirfoad-HP-Mini-110-3000:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
rfcomm                 38125  8 
sco                    17827  2 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rt2860sta             494649  0 
snd_timer              28659  2 snd_pcm,snd_seq
i915                  450934  3 
arc4                   12473  2 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
rt2800pci              18119  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  2 rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
rts_pstor             348243  0 
cfg80211              156212  2 rt2x00lib,mac80211
btusb                  18160  2 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
drm                   180037  4 i915,drm_kms_helper
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
psmouse                73312  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
i2c_algo_bit           13184  1 i915
eeprom_93cx6           12653  1 rt2800pci
video                  18951  1 i915
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  42534  0 
amirfoad@amirfoad-HP-Mini-110-3000:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
amirfoad@amirfoad-HP-Mini-110-3000:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
amirfoad@amirfoad-HP-Mini-110-3000:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
amirfoad@amirfoad-HP-Mini-110-3000:~$ 
 
```

---

### Post by wildmanne39 on 2011-08-02
Hi, run this command and see if it fixes it.
```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by amirfoad on 2011-08-02
I do it! and even a restart after done! but nothing changed!
did you read the link in first post?
i think i should install the new driver first and then blacklist the old driver! right?
and my problem is how to compile the new driver?!
also tnx for help! :D

---

### Post by wildmanne39 on 2011-08-02
Hi, I am researching your issue because I am not sure that changing drivers is the best solution.

---

### Post by wildmanne39 on 2011-08-02
Hi, your card can use that driver, it looks like we need to black list some more drivers that are conflicting with it.
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Add these lines at the end:
```
blacklist rt2800pci
blacklist rt2x00pci

```
Then restart and see if it is working bettrer.

---

### Post by amirfoad on 2011-08-03
Yes!
Thats right!
I blacklist those drivers and also install new driver from here:

[https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages](https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages)
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb)

and now every thing is ok and perfect.

thanks so much for your help my friend.
have nice.

---

### Post by wildmanne39 on 2011-08-03
Hi, your welcome! glad you fixed it,would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

