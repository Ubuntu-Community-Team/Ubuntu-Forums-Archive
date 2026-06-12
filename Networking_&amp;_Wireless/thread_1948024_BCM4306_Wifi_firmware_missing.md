---
title: "BCM4306: Wifi firmware missing"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by dkrises on 2012-03-27
Hi guys,

Ubuntu newbie here. I have just installed Ubuntu 11.10 alongside Windows XP but i can't seem to connect to my wifi. It comes up with the message 'wifi firmware missing'. I did a hardware scan within Ubuntu in the terminal and my wifi card type was Broadcom BCM4306. Based on the ubuntu forums and ubuntu wiki docs, I installed the b43fw legacy drivers as it was considered the appropriate driver. I followed all the steps including going through  'system- additional hardware' to activate the driver. But it still comes up with the same error message of 'wifi missing'.

My wifi works fine on Windows but this Ubuntu incompatibility is putting me off. Any advice or help would be much appreciated. 

Thanks.

dk

---

### Post by mörgæs on 2012-03-27
Moved to Networking and Wireless. 
Please also read the sticky notes in this forum.

---

### Post by wildmanne39 on 2012-03-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
dmesg | egrep 'b43|firm'
```
Thanks

---

### Post by dkrises on 2012-03-28
wasimquasem@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
wasimquasem@ubuntu:~$ lspci -nnk | grep -iA2 net
03:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12fa]
    Kernel driver in use: b43-pci-bridge
--
03:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3085]
    Kernel driver in use: 8139too
wasimquasem@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wasimquasem@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
wasimquasem@ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  8 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_atiixp             20001  2 
arc4                   12529  2 
b43                   341198  0 
snd_seq_midi           13324  0 
mac80211              310872  1 b43
snd_atiixp_modem       19108  4 
pcmcia                 49378  0 
snd_rawmidi            30547  1 snd_seq_midi
radeon               1015995  3 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_ac97_codec        134826  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12730  1 snd_ac97_codec
yenta_socket           28084  0 
tifm_7xx1              13089  0 
edac_core              53746  0 
cfg80211              199587  2 b43,mac80211
snd_pcm                96755  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_rsrc            18430  1 yenta_socket
k8temp                 13057  0 
edac_mce_amd           23709  0 
tifm_core              15654  1 tifm_7xx1
snd_timer              29991  2 snd_seq,snd_pcm
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73882  0 
snd                    68266  18 snd_atiixp,snd_atiixp_modem,snd_rawmidi,snd_seq,snd_ac97_codec,snd_pcm,snd_seq_device,snd_timer
ttm                    76805  1 radeon
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_atiixp,snd_atiixp_modem,snd_pcm
video                  19412  0 
drm_kms_helper         42558  1 radeon
drm                   236330  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
wmi                    19256  1 hp_wmi
i2c_piix4              13301  0 
shpchp                 37345  0 
sdhci_pci              14032  0 
firewire_ohci          40722  0 
8139too                32177  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
8139cp                 27412  0 
ssb                    52752  1 b43
pata_atiixp            13164  1 
wasimquasem@ubuntu:~$ dmesg | egrep 'b43|firm'
[    2.124643] b43-pci-bridge 0000:03:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 9
[   31.433797] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   31.558618] Registered led device: b43-phy0::tx
[   31.558667] Registered led device: b43-phy0::rx
[   31.558715] Registered led device: b43-phy0::radio
[   66.445387] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   66.445394] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   66.445398] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
wasimquasem@ubuntu:~$

---

### Post by wildmanne39 on 2012-03-28
Hi, yes you still have a firmware issue try this please one line at a time and watch for errors.
```
[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz]("http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz")
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe b43
```
Thanks

---

### Post by roberco on 2012-03-28
Get an Ethernet cable and connect your computer to the Internet. Go to System Settings -> Additional drivers and let your computer does the rest.

---

### Post by dkrises on 2012-03-29
Hi guys,
 
Thanks for your replies
 
wildmanne39 - I will try the firmware file you have sent and update on how i got along.
 
roberco - That is the first thing I did ... connected to the internet via Ethernet and went to System Settings>Additional drivers. It then installs a non-proprietory driver - Smartlink modem driver. After activating .. it still doesn't work.

---

### Post by dkrises on 2012-03-30
Hi guys,
 
I have the solved the problem. I went to App Centre and installed firmware-b43-drivers and it seemed to have the firmware for my Wifi ... so Wifi is working ! However, I am having problems similar to another person on the forum, where the internet is laggy and slow. I am just wondering whether Ubuntu installed within Windows is slow.
 
Thanks for your help so far.
 
dk

---

### Post by wildmanne39 on 2012-03-30
Hi, no the internet is not slow because of wubi please set your settings to match the screenshots then reboot ubuntu.
Thanks

---

### Post by dkrises on 2012-04-01
Thanks for the tips. Internet is working much better and faster than before.

Start of my ubuntu journey !

dk

---

### Post by pratikk on 2012-04-01
Glad it was solved. I had got my Broadcom card working on Lucid with the tool b43-fwcutter from the repos.

---

### Post by wildmanne39 on 2012-04-01
Hi, your welcome! glad to help please use thread tools at the top of the page and mark the thread solved.
Thanks

---

