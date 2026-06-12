---
title: "No Ethernet, no connection."
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by fanny87 on 2011-11-20
Hello everyone, I have a huge problem.
One week ago I was having problems with my pc (the fan and some other mistakes I don't really know about), so I resetted everything installing another version of ubuntu (I had 10.04 and installed 9.04). Then I found that that cd was damaged and infact I was having more problems and I couldn't connect at all. 
So from another laptop I downloaded via usb (because the cd-door is broken) ubuntu 10.04 and installed it on my problematic pc (that is a hp laptop). But..problems never ends and..neither this one could connect.
I mean, the wireless networks is connected (I have a sitecom router) but the Wired network, meaning ethernet, woulnd't connect no matter what.
 
Now it says wired network: device not managed :confused:
 
Hope someone can really help me, I'm desperate!:(
 
 
(sorry for my bad english, it's not my first language)

---

### Post by bkratz on 2011-11-20
> **fanny87 said:**
> Hello everyone, I have a huge problem.
One week ago I was having problems with my pc (the fan and some other mistakes I don't really know about), so I resetted everything installing another version of ubuntu (I had 10.04 and installed 9.04). Then I found that that cd was damaged and infact I was having more problems and I couldn't connect at all. 
So from another laptop I downloaded via usb (because the cd-door is broken) ubuntu 10.04 and installed it on my problematic pc (that is a hp laptop). But..problems never ends and..neither this one could connect.
I mean, the wireless networks is connected (I have a sitecom router) but the Wired network, meaning ethernet, woulnd't connect no matter what.
 
Now it says wired network: device not managed :confused:
 
Hope someone can really help me, I'm desperate!:(
 
 
(sorry for my bad english, it's not my first language)



It would be helpful to see the output of

```
lspci -nnk | grep -iA2 net
```

and 

```
ifconfig
```

so someone familiar with the devices found can help.

---

### Post by fanny87 on 2011-11-20
Thank you for your answer! Here's the results:
```
 
 
[EMAIL="frank@frank-laptop:~$"]frank@frank-laptop:~$[/EMAIL] lspci -nnk | grep -iA2 net
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express [14e4:16fd] (rev 21)
 Kernel driver in use: tg3
 Kernel modules: tg3
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
 Kernel driver in use: iwl3945
 Kernel modules: iwl3945
[EMAIL="frank@frank-laptop:~$"]frank@frank-laptop:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:a4:cd:9f:69  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:171440 (171.4 KB)  TX bytes:171440 (171.4 KB)
wlan0     Link encap:Ethernet  HWaddr 00:19:d2:38:e6:b9  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe38:e6b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4516 (4.5 KB)

```

---

### Post by praseodym on 2011-11-20
Hi,

did you check the cable? MAC address filter in your router allows new clients? Please show additionally:
```
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/nm-system-settings.conf
dmesg | grep tg3
```

---

### Post by bkratz on 2011-11-20
Referencing the statement


Now it says wired network: [COLOR="Red"]device not managed[/COLOR] 


This may be of some help.

[http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html](http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html)

good luck

---

### Post by fanny87 on 2011-11-20
```
frank@frank-laptop:~$ cat /etc/network/interfaces
# Interfaccia di rete di loopback
auto lo
        iface lo inet loopback
        adress 127.0.0.1
        netmask 255.0.0.0
# Prima interfaccia di rete
auto eth0
       iface eth0 inet static
       address 192.168.0.10
       netmask 255.255.255.0
       network 192.168.0.0
       broadcast 192.168.0.255
       gateway 192.168.0.100
frank@frank-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
frank@frank-laptop:~$ cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true
frank@frank-laptop:~$ cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#
[main]
plugins=ifupdown,keyfile
no-auto-default=00:17:a4:cd:9f:69,
[ifupdown]
managed=false
frank@frank-laptop:~$ dmesg | grep tg3
[    0.987196] tg3.c:v3.102 (September 1, 2009)
[    0.987211] tg3 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.987218] tg3 0000:08:00.0: setting latency timer to 64
[   13.999516] tg3 0000:08:00.0: irq 30 for MSI/MSI-X

```
 
That's it.:confused: Thank you I'll check the site right away.

---

### Post by fanny87 on 2011-11-20
All good till step 5. When I typed 'sudo killall nm-system-settings' I got this answer: nm-system-settings: no process found. I rebooted and typed "sudo killall nm-applet" then "nm-applet & disown".. and now I get a Wired network disconnected, and no more 'device not managed'.
 
:( What to do now?

---

### Post by praseodym on 2011-11-20
Change "false" to "true" in:

```
gksu gedit /var/lib/NetworkManager/Networkmanager.state
```
_and_ in
```
gksu gedit /etc/NetworkManager/nm-system-settings.conf
```
The manual configuration of the /etc/network/interfaces is yours?

---

### Post by fanny87 on 2011-11-20
Yeah I had already changed false to true, following the link [http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html?showComment=1321797226852#c604795683415752949](http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html?showComment=1321797226852#c604795683415752949). anyway with gksu it opens a windows with 'error' but when I change it with sudo it opens the same window, not in error, but completely blank.
 
And now I have in wired connection, ifupdown (eth0) that I can't edit, and was never used. :confused:
 
 
I got helped some days ago into resolve this mess but nothing came out of it.

---

### Post by praseodym on 2011-11-20
If you dont use the manual config with static IP address, remove anything but:
```
auto lo
iface lo inet loopback
```
from the "interfaces" and reboot.

---

### Post by fanny87 on 2011-11-20
I don't get it..I added a new wired connection 'eth1' and on IPv4 I put it to automatic (dhcp) addresses only and writed down DNS server and DHCP client ID.
 
AND STILL NOTHING HAPPENS. :'(

---

### Post by bkratz on 2011-11-20
did you left click on the network icon and select the new eth1 connection?

---

### Post by fanny87 on 2011-11-20
Sorry I read your answer just now, I did everything that you said. So now what? Please help me. So now I just have eth1 on wired connection.
 
 
Yup I did.

---

### Post by fanny87 on 2011-11-20
Someone please!

---

### Post by fanny87 on 2011-11-20
Really? Nobody is able to help me?:(

---

### Post by praseodym on 2011-11-20
In 10.04 checkbox **all** user rights in USERS&GROUPS and login again. After that checkbox "available to all users" and "connect automatically" in the network-manager applet, remove your wired connections in "wired" and "DSL" (if any) and reboot.

---

### Post by fanny87 on 2011-11-20
Hello, thanks for replying. In the end I installed ubuntu 10.10 resetting the previous 10.04. But yeah, of course, I still have the same problems. But now it's fresh new, I put the 'manual' connection for eth0 but still..nothing. I runned "sudo service network-manager restart" but still nothing. I don't know what to do anymore. I'm starting to get sick of ubuntu.:(

---

### Post by praseodym on 2011-11-20
Please show now
```
uname -a
cat /etc/network/interfaces
ifconfig -a
dmesg | grep tg3
lsmod
cat /etc/resolv.conf
```

---

### Post by fanny87 on 2011-11-20
Here it is...is it bad?
 
[EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"]```
 [/EMAIL]
[EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"]frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"] uname -a
Linux frank-HP-Compaq-nw8440-RH418EA-ABZ 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"]frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"] cat /etc/network/interfaces
auto lo
iface lo inet loopback
[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"]frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"] ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:a4:cd:9f:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35712 (35.7 KB)  TX bytes:35712 (35.7 KB)
wlan0     Link encap:Ethernet  HWaddr 00:19:d2:38:e6:b9  
          inet6 addr: fe80::219:d2ff:fe38:e6b9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7797 (7.7 KB)  TX bytes:14573 (14.5 KB)
[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"]frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"] dmesg | grep tg3
[    1.002749] tg3.c:v3.110 (April 9, 2010)
[    1.002777] tg3 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.002791] tg3 0000:08:00.0: setting latency timer to 64
[    1.113974] tg3 0000:08:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4201] (PCI Express) MAC address 00:17:a4:cd:9f:69
[    1.113978] tg3 0000:08:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.113981] tg3 0000:08:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.113984] tg3 0000:08:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   13.723541] tg3 0000:08:00.0: irq 48 for MSI/MSI-X
[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"]frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"] lsmod
Module                  Size  Used by
tpm_infineon            7937  0 
binfmt_misc             6599  1 
snd_hda_codec_si3054     3440  1 
snd_hda_codec_analog    59649  1 
snd_hda_intel          22107  2 
arc4                    1165  2 
snd_hda_codec          87552  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
joydev                  8735  0 
snd_seq_midi            4588  0 
radeon                825934  3 
pcmcia                 35973  0 
iwl3945                85550  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
iwlcore               127415  1 iwl3945
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
snd_timer              19067  2 snd_pcm,snd_seq
mac80211              231541  2 iwl3945,iwlcore
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1               3766  0 
drm                   168054  5 radeon,ttm,drm_kms_helper
video                  18712  0 
i2c_algo_bit            5168  1 radeon
ppdev                   5556  0 
snd                    49006  14 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_wmi                  5191  0 
tifm_core               6089  1 tifm_7xx1
parport_pc             26058  1 
cfg80211              144470  3 iwl3945,iwlcore,mac80211
psmouse                59033  0 
tpm_tis                 7562  0 
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
tpm                    13741  2 tpm_infineon,tpm_tis
intel_agp              26360  0 
hp_accel               12532  0 
lis3lv02d               8524  1 hp_accel
serio_raw               4022  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore                880  1 snd
tpm_bios                5310  1 tpm
output                  1883  1 video
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  3 ttm,drm,intel_agp
input_polldev           3491  1 lis3lv02d
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
firewire_ohci          21106  0 
ahci                   19013  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
led_class               2633  2 hp_accel,sdhci
libahci                21667  3 ahci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
tg3                   123310  0 
[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"]frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$[/EMAIL][EMAIL="frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$"] cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory

```[/EMAIL]

---

### Post by fanny87 on 2011-11-20
When I try to create a new connection in vpn, the wireless icon on the bar just vanish.

---

### Post by praseodym on 2011-11-20
In 10.10 there was a bug in the vpnc-plugin, install this PPA:

```
sudo add-apt-repository ppa:sroecker/ppa
sudo apt-get update
sudo apt-get install --reinstall network-manager network-manager-gnome network-manager-vpnc network-manager-vpnc-gnome
```
Try to add the nameservers:
```
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by fanny87 on 2011-11-21
Sorry for the late reply, here is it :( I can't install or update anything.
 
```
frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$ sudo add-apt repository ppa:sroeckeer/ppa
sudo: add-apt: command not found
frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$ sudo apt-get update
Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick Release.gpg
  Impossibile risolvere "extras.ubuntu.com"
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
  Impossibile risolvere "extras.ubuntu.com"
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-it
  Impossibile risolvere "extras.ubuntu.com"
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security Release.gpg
  Impossibile risolvere "security.ubuntu.com"
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
  Impossibile risolvere "security.ubuntu.com"
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-it
  Impossibile risolvere "security.ubuntu.com"
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
  Impossibile risolvere "security.ubuntu.com"
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-it
  Impossibile risolvere "security.ubuntu.com"
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Impossibile risolvere "security.ubuntu.com"
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-it
  Impossibile risolvere "security.ubuntu.com"
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Impossibile risolvere "security.ubuntu.com"
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-it
  Impossibile risolvere "security.ubuntu.com"
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg
  Impossibile risolvere "ppa.launchpad.net"
Err [http://ppa.launchpad.net/sroecker/ppa/ubuntu/](http://ppa.launchpad.net/sroecker/ppa/ubuntu/) maverick/main Translation-en
  Impossibile risolvere "ppa.launchpad.net"
Err [http://ppa.launchpad.net/sroecker/ppa/ubuntu/](http://ppa.launchpad.net/sroecker/ppa/ubuntu/) maverick/main Translation-it
  Impossibile risolvere "ppa.launchpad.net"
Err [http://it.archive.ubuntu.com]("http://it.archive.ubuntu.com/") maverick Release.gpg
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/main Translation-it
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-it
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-it
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick/universe Translation-it
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com]("http://it.archive.ubuntu.com/") maverick-updates Release.gpg
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-it
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-it
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-it
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Impossibile risolvere "it.archive.ubuntu.com"
Err [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-it
  Impossibile risolvere "it.archive.ubuntu.com"
Lettura elenco dei pacchetti... Fatto
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://it.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-it.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-it.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-it.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-it.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-it.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-it.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-it.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-it.bz2)  Impossibile risolvere "it.archive.ubuntu.com"
W: Impossibile recuperare [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Impossibile risolvere "extras.ubuntu.com"
W: Impossibile recuperare [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Impossibile risolvere "extras.ubuntu.com"
W: Impossibile recuperare [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-it.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-it.bz2)  Impossibile risolvere "extras.ubuntu.com"
W: Impossibile recuperare [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Impossibile risolvere "security.ubuntu.com"
W: Impossibile recuperare [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Impossibile risolvere "security.ubuntu.com"
W: Impossibile recuperare [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-it.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-it.bz2)  Impossibile risolvere "security.ubuntu.com"
W: Impossibile recuperare [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Impossibile risolvere "security.ubuntu.com"
W: Impossibile recuperare [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-it.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-it.bz2)  Impossibile risolvere "security.ubuntu.com"
W: Impossibile recuperare [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Impossibile risolvere "security.ubuntu.com"
W: Impossibile recuperare [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-it.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-it.bz2)  Impossibile risolvere "security.ubuntu.com"
W: Impossibile recuperare [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Impossibile risolvere "security.ubuntu.com"
W: Impossibile recuperare [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-it.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-it.bz2)  Impossibile risolvere "security.ubuntu.com"
W: Impossibile recuperare [http://ppa.launchpad.net/sroecker/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/sroecker/ppa/ubuntu/dists/maverick/Release.gpg)  Impossibile risolvere "ppa.launchpad.net"
W: Impossibile recuperare [http://ppa.launchpad.net/sroecker/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/sroecker/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Impossibile risolvere "ppa.launchpad.net"
W: Impossibile recuperare [http://ppa.launchpad.net/sroecker/ppa/ubuntu/dists/maverick/main/i18n/Translation-it.bz2](http://ppa.launchpad.net/sroecker/ppa/ubuntu/dists/maverick/main/i18n/Translation-it.bz2)  Impossibile risolvere "ppa.launchpad.net"
W: Impossibile scaricare alcuni file di indice: saranno ignorati o verranno usati quelli vecchi.
frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$ sudo apt-get install --reinstall network-manager network-manager-gnome network-manager-vpnc network-manager-vpnc-gnome
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
E: Impossibile trovare il pacchetto network-manager-vpnc
E: Impossibile trovare il pacchetto network-manager-vpnc-gnome
frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$ echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
nameserver 8.8.8.8
frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$ echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
nameserver 8.8.4.4
frank@frank-HP-Compaq-nw8440-RH418EA-ABZ:~$ sudo service network-manager restart
network-manager start/running, process 1849

```

---

### Post by fanny87 on 2011-11-21
Is there any way to have a connession with Ubuntu? Even rebooting or restart everything would do (even through I already tried that). I tried 9.04, 10.4 and 10.10 and none of those would let me connect. And I don't think it's the ethernet cable or wifi problem, seeing the other laptop with windows connecting automatically. :( 
Please, I'm thinking of returning to windows..and it's scary XD

---

