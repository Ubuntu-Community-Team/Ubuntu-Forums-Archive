---
title: "FATAL: Error inserting iwl3945"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by biancarei on 2009-03-29
I can't connect to WiFi after an update. Before, it was working fine. I'm using iwl3945. Here are the details:

root@AcerAspire4710:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

/** wlan0 is not here.
-----
root@AcerAspire4710:~# ifconfig wlan0
wlan0: error fetching interface information: Device not found
-----
root@AcerAspire4710:~# lshw -C Network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:5d:a2:24
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5787m-v3.23 ip=192.168.0.101 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
 [B] *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0[/B]
-----
root@AcerAspire4710:~# lspci | grep -i network
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
-----
root@AcerAspire4710:~# dmesg | grep -i iwl3945
[   32.372726] iwl3945: disagrees about version of symbol __wake_up
[   32.372731] iwl3945: Unknown symbol __wake_up
-----
root@AcerAspire4710:~# lsmod | grep -i iwl
iwlwifi_mac80211      221284  0 
cfg80211               15368  1 iwlwifi_mac80211
-----
root@AcerAspire4710:~# modprobe iwl3945
FATAL: Error inserting iwl3945 (/lib/modules/2.6.24-24-rt/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
-----

i really can't figure out what seems to be the problem.. I can connect fine, WIRED. But, how can i connect when I'm away from home.. 

Can someone please help me?
As you can see, I'm using Acer Aspire 4710 and Ubuntu Hardy Heron, with Intel PRO/Wireless 3945ABG..

---

### Post by Concussion on 2009-03-31
I have the same issue. I've been banging my head against a wall trying to get this thing working.

---

### Post by chili555 on 2009-03-31
I would try installing *linux-backports-modules-hardy-generic*. There is apparently a newer version of *iwl3945* in there. If that doesn't fix it, I'd try rebooting into an earlier kernel by interrupting the boot process with the Esc key. Arrow down to an earlier kernel and press Enter. Does wlan0 spring to life?

If so, then open Synaptic and look for *linux-image-2.6.24-24-rt* and mark it for reinstallation. Press Apply. Reboot into your latest kernel. Is the problem fixed?

@Concussion - Substitute your details here if you aren't running Hardy.

---

### Post by biancarei on 2009-03-31
Thank you for your help. What I did was upgrade to Ibex (8.10). It fixed all bugs. It's working nicely now. Even the Wifi Light on my laptop is working..^__^

---

### Post by Concussion on 2009-03-31
I am running Intrepid
 2.6.27-7-generic
I just reinstalled the whole thing so that I could start from the beginning.
I have not done any of the updates which would bring me to 
2.6.27.11

lsmod reports
 ```
binfmt_misc            18700  1 
rfcomm                 51104  0 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,bnep,sco,l2cap
ppdev                  16904  0 
acpi_cpufreq           16400  0 
cpufreq_conservative    16392  0 
cpufreq_ondemand       16400  2 
cpufreq_powersave      10368  0 
cpufreq_userspace      12420  0 
cpufreq_stats          14468  0 
freq_table             13568  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
wmi                    15808  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
af_packet              29568  2 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
sbp2                   32652  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
loop                   26380  0 
ipv6                  314312  10 
joydev                 20736  0 
pcmcia                 48408  0 
snd_hda_intel         489264  2 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
arc4                   10368  2 
ecb                    11520  2 
crypto_blkcipher       27780  1 ecb
snd_seq_oss            42368  0 
yenta_socket           35084  1 
sdhci_pci              17024  0 
sdhci                  27396  1 sdhci_pci
snd_seq_midi           15872  0 
rsrc_nonstatic         19328  1 yenta_socket
iwl3945               112116  0 
evdev                  20512  9 
mmc_core               67168  1 sdhci
psmouse                51612  0 
iTCO_wdt               21072  0 
serio_raw              14596  0 
pcspkr                 11136  0 
irda                  218732  0 
iTCO_vendor_support    12420  1 iTCO_wdt
snd_rawmidi            34176  1 snd_seq_midi
tifm_7xx1              15104  0 
rfkill                 19364  2 iwl3945
tifm_core              17864  1 tifm_7xx1
pcmcia_core            48804  3 pcmcia,yenta_socket,rsrc_nonstatic
crc_ccitt              10496  1 irda
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
mac80211              253440  1 iwl3945
snd_seq                67168  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
container              12288  0 
video                  28948  5 
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class              13192  1 iwl3945
output                 11776  1 video
nvidia               7815240  28 
cfg80211               37136  2 iwl3945,mac80211
snd                    79432  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               36128  1 nvidia
battery                21128  0 
ac                     13448  0 
button                 15904  0 
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
intel_agp              39280  0 
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
ata_piix               29444  2 
pata_acpi              13568  0 
ata_generic            14212  0 
libata                200160  3 ata_piix,pata_acpi,ata_generic
scsi_mod              183160  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
ohci1394               41524  0 
r8169                  40196  0 
ieee1394              110592  2 sbp2,ohci1394
ehci_hcd               48908  0 
uhci_hcd               34336  0 
usbcore               175376  3 ehci_hcd,uhci_hcd
thermal                27424  0 
processor              47800  4 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 
```


my wireless indicator was isn't on when I boot, and I get the same thing after activating it when I run this. 
```
concussion@portable:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

```

---

### Post by Concussion on 2009-03-31
I rebooted into Winxp and enabled my wireless.
Rebooted and ran

```
concussion@portable:~$ dmesg | grep -i iwl
[   14.959301] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.959307] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   15.180246] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.180265] iwl3945 0000:02:00.0: setting latency timer to 64
[   15.180295] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   15.273541] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.274312] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   15.587777] iwl3945 0000:02:00.0: PCI INT A disabled

```

Says that it is disabled.

---

### Post by Concussion on 2009-03-31
I've been following some of your posts and it seems that I'm missing something. 

```
concussion@portable:~$ cat /etc/modprobe.d/iwl3945
cat: /etc/modprobe.d/iwl3945: No such file or directory
```

---

### Post by chili555 on 2009-04-02
> **Concussion said:**
> I've been following some of your posts and it seems that I'm missing something. 

```
concussion@portable:~$ cat /etc/modprobe.d/iwl3945
cat: /etc/modprobe.d/iwl3945: No such file or directory
```Well, you don't need it unless you have a particular need for it. Let's check. Please do these terminal commands:```
sudo ifdown wlan0
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo dhclient wlan0
```Did you connect?

If so, let's make it permanent:```
sudo gedit /etc/modprobe.d/iwl3945
```Add two lines:```
alias wlan0 iwl3945 
options iwl3945 disable_hw_scan=1
```Proofread, save and close. If you are still having problems, please post back.

---

### Post by tallis on 2010-08-12
> **chili555 said:**
> Well, you don't need it unless you have a particular need for it. Let's check. Please do these terminal commands:```
sudo ifdown wlan0
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo dhclient wlan0
```Did you connect?

If so, let's make it permanent:```
sudo gedit /etc/modprobe.d/iwl3945
```Add two lines:```
alias wlan0 iwl3945 
options iwl3945 disable_hw_scan=1
```Proofread, save and close. If you are still having problems, please post back.

If I try to "sudo modprobe iwl3945 disable_hw_scan=1" I get 

apostolos@apostolos-laptop:/etc$ sudo modprobe iwl3945 disable_hw_scan=1
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting iwl3945 (/lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Can anybody help?

I'm using lucid 10.04

---

