---
title: "Atheros AR9285"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by cluelesswonder on 2013-06-17
I'm having problems connecting to wireless today. It has been fine for the past few days and suddenly a few hours ago it just stopped working. I have rebooted my  computer twice with no fix yet. I'm also running ubuntu 12.04 LTS
The same codes yield:

lo        no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
       eth0      no wireless extensions.

lsmod |grep -e wl -e brcmsma

wl                   2906597  0 
lib80211               14040  1 wl
cfg80211              178877  4 wl,ath9k,mac80211,ath

lspci -nn |grep 0280

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285  Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

If I need to provide any more information, please let me know.

---

### Post by Hadaka on 2013-06-17
Hi, you have a broadcom driver loaded,
you dont have a broadcom card. soooo.
please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rfv wl
sudo modprobe -rf ath9k
sudo modprobe ath9k
```
got wireless now??

---

### Post by cluelesswonder on 2013-06-17
hmmm. nope.
Now I have this
```
enigma@Peanut:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for enigma: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,656 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 602630 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-48-generic-pae
enigma@Peanut:~$ sudo modprobe -rfv wl
FATAL: Module wl not found.
enigma@Peanut:~$ sudo modprobe -rfv wl
FATAL: Module wl not found.


```

which doesn't sound good. . .:S

---

### Post by Hadaka on 2013-06-17
Hi,actually it sounds great! It means the first
command removed the module wl,which again
is a broadcom module and you still dont have a 
broadcom card. so finish running the rest of the commands
and report back.
thanks.

---

### Post by cluelesswonder on 2013-06-17
I ran the commands but still no wireless.
Also. the network settings won't allow me to turn the wireless on, saying it's unavailable and I can't 'enable wireless' in the connection information either.
I don't think I did anything between when it was working and when it stopped besides watch a movie. . .which shouldn't have interfered. . .

---

### Post by Hadaka on 2013-06-17
ok, please post the output of..
```
uname -r
lsb_release -a
lsmod
rfkill list all
```
thanks.

---

### Post by cluelesswonder on 2013-06-17
```
enigma@Peanut:~$ uname -r
3.2.0-48-generic-pae
enigma@Peanut:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
enigma@Peanut:~$ lsmod
Module                  Size  Used by
ath9k                 117356  0 
mac80211              436493  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              391626  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
ipheth                 13278  0 
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  12 
bnep                   17830  2 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
wl                   2906597  0 
lib80211               14040  1 wl
snd_hda_intel          32719  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
sony_laptop            39681  0 
mac_hid                13077  0 
psmouse                86520  0 
serio_raw              13027  0 
snd                    62218  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  428056  8 
drm_kms_helper         45466  1 i915
uvcvideo               67203  0 
drm                   197641  4 i915,drm_kms_helper
btusb                  17948  2 
i2c_algo_bit           13199  1 i915
bluetooth             158479  23 rfcomm,bnep,btusb
mei                    36570  0 
videodev               86588  1 uvcvideo
video                  19115  1 i915
intel_ips              17822  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cfg80211              178877  4 ath9k,mac80211,ath,wl
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   53628  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
enigma@Peanut:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: sony-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```

---

### Post by Hadaka on 2013-06-17
Hi, you still have the wl module in there.
please do..
```
sudo modprobe -rf wl
sudo modprobe ath9k
```
thanks.

---

### Post by cluelesswonder on 2013-06-17
That didn't seem to work.
Still no wireless networks available, no wireless networks found in wicd either.

```
enigma@Peanut:~$ sudo modprobe -rf wl
[sudo] password for enigma: 
FATAL: Module wl not found.
enigma@Peanut:~$ sudo modprobe ath9k
```
nothing happened when I ran either of those commands. . .

---

### Post by Hadaka on 2013-06-17
hi, it looks like your wireless is also off by 
a hard switch. so press the switch or the
key combo to turn it on.
also do..
```
rfkill unblock all
```
thanks.

---

### Post by cluelesswonder on 2013-06-17
ok, that worked!
Thanks very much for your help :)

---

### Post by cluelesswonder on 2013-06-17
Another issue: after I did that the first time, my computer froze (hopefully unrelated issue?) and I had to hold down the power key to reboot.
When it started up again, same issue with the wireless. The fix you described solved this, again but will I need to do this every time I restart my computer. . .?

---

### Post by Hadaka on 2013-06-17
Hi, restart your computer and find out.
if all is well..then please mark this thread solved

how to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

*edit the FIRST post to mark solved
thanks.

---

