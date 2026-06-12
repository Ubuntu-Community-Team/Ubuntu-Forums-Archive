---
title: "Transmission killing network"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by darthpbal on 2011-06-18
For some reason when I'm downloading torrents with transmission, after a certain amount of time the wireless for that machine goes out. I still have the actual connection, but down and up speed goes straight to zero. I know it's not an actual network problem because I have another Ubuntu machine and while one goes out from using transmission, the other can connect perfectly. This problem exists on both Ubuntu 11.04 machines that I have and network only goes out after using transmission on that machine. Any ideas? I ping on the machines to websites and this confirms it's only the local machine being affected and not others on the network or the network itself.

---

### Post by nbound on 2011-06-19
plz post output of **lshw -C network**, and **lsmod**

---

### Post by darthpbal on 2011-06-19
> **nbound said:**
> plz post output of **lshw -C network**, and **lsmod**

Should I do these operations when it does it again? Because I have to restart to get the network back and post here. And I'll have to wait for it to do it again. So far today it hasn't done it again though.

---

### Post by nbound on 2011-06-19
now :)

---

### Post by kerry_s on 2011-06-19
it means your transmission settings are to high, throttle the up/down speed to lower.

---

### Post by nbound on 2011-06-19
Thats more of a workaround than anything. Ive had wireless connections torrent with hundreds of peers. It could be as simple as newer firmware or update compat-wireless (depending on driver module)

---

### Post by darthpbal on 2011-06-20
> **nbound said:**
> now :)

darthpbal@Jarvis:~$ sudo lshw -C network
[sudo] password for darthpbal: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 54:42:49:2a:b4:e7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:6000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 78:dd:08:df:9a:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic-pae firmware=N/A ip=10.0.0.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f3000000-f300ffff

---

### Post by darthpbal on 2011-06-20
> **nbound said:**
> now :)

darthpbal@Jarvis:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
arc4                   12473  2 
snd_hda_intel          24140  2 
ath9k                 103669  0 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               66851  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 ath9k
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
ath9k_common           13611  1 ath9k
videodev               75143  1 uvcvideo
usblp                  17827  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59039  0 
fglrx                2434640  100 
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
soundcore              12600  1 snd
serio_raw              12990  0 
sony_laptop            34432  0 
k10temp                12951  0 
cfg80211              156212  3 ath9k,mac80211,ath
video                  18951  0 
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
sp5100_tco             13456  0 
i2c_piix4              13095  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  2 
uas                    17676  0 
r8169                  46630  0 
ahci                   21591  0 
libahci                25548  1 ahci
pata_atiixp            12968  0

---

### Post by darthpbal on 2011-06-20
Also, sorry for the stupid long time for my reply with the command. Fathers days stuff. Anyway, back to business! :)

---

### Post by darthpbal on 2011-06-21
I can use the work around for now until I fix this. Whats a good limit? I don't really knew the speed that triggers it because my down speed goes all over the place when transmission is on.

---

### Post by chuckyanutsup on 2011-09-27
I've been having the same issue. I've tried throttling to slightly under my max download speed (by about 100-200KB/s), I'll try a stronger throttle. Here are the outputs for lshw -C network and lsmod.

  *-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: c0
       serial: 00:26:9e:42:f1:f8
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:48 memory:c0a00000-c0a3ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 10
       serial: 00:26:b6:30:fb:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.1.135 latency=0 multicast=yes wireless=802.11bg
       resources: irq:17 ioport:6000(size=256) memory:c0e00000-c0e03fff




Module                  Size  Used by
michael_mic            12540  4 
arc4                   12473  2 
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  451068  3 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
r8192se_pci           482548  0 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  1 r8192se_pci
drm_kms_helper         40745  1 i915
soundcore              12600  1 snd
drm                   184164  4 i915,drm_kms_helper
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
psmouse                59039  0 
serio_raw              12990  0 
sparse_keymap          13666  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
sdhci_pci              13623  0 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
ahci                   21591  3 
libahci                25548  1 ahci
atl1c                  36237  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core

EDIT: I tried a stronger throttle and am still having the same issue requiring a restart to reconnect. I was seeding only and had my upload limit set at 150KB/s (my conneciton is capable of about 210KB/s). I've also got my download limit set at 1.4MB/s when my connection is capable of about 2MB/s. Any ideas would be greatly appreciated.

---

### Post by chuckyanutsup on 2011-10-06
I've tried also limiting the number of total peers to 200 (100 per torrent) and am still having the same issue. This is very frustrating as it requires a restart to resolve.

---

### Post by chuckyanutsup on 2011-10-12
Issue also happens over ethernet

---

### Post by Vaphell on 2011-10-12
Looks like your rooter gets flooded with connections and craps out (when it does all traffic is killed, internet and ethernet). Start from very modest download/upload limits and go up from there to see where is the threshold. Limit total number of connections, number of concurrent downloads/uploads.

Have you tried other torrent clients, Deluge for example?

---

### Post by Elysius on 2011-10-12
Also just limit your upload by 1/4 to your download.

---

### Post by chuckyanutsup on 2011-10-13
The issue occured on 2 different modems/routers. I am sceptical that my modem/router's nat table could be getting flooded as there are no issues torrenting on the 2 other machines on the network  (xp and 7) and on the same machine in windows 7 there are no issues (I'm dual booting, I'm new to linux). I've not tried other torrent clients in linux. I'm happy to give it a go to test. I'll be getting a nas soon and from what I understand, it will need to run transmission, so I'd rather get to the bottom of it. I've tried quite conservative limits with both speeds and number of peers, and the issue is still present. 

Strangely I can still see networks on the wifi, but just can't get any throughput. When the ethernet connection dies, I can connect via wifi and vice versa until it crashes as well.

---

### Post by chuckyanutsup on 2011-10-20
Well an upgrade to 11.10 (and changing from 32 to 64 bit) and I've stopped having issues. Thank you for your assistance.

---

### Post by gbrowning on 2011-10-20
Chucky:
    This problem hit me when I went up to Natty from Lucid.  Have just upped to Oenireiriec and have not yet tried BUT.  The solution for Natty was to limit the upload speed.

---

### Post by chuckyanutsup on 2011-10-21
> **gbrowning said:**
> Chucky:
    This problem hit me when I went up to Natty from Lucid.  Have just upped to Oenireiriec and have not yet tried BUT.  The solution for Natty was to limit the upload speed.
I'd tried limiting the upload speed to about half of my network's capability (90KB/s) and the issue did appear to occur less frequently but still did happen.  11.10 and switching to 64 bit and I've been running at full speed for the past week ^_^

---

