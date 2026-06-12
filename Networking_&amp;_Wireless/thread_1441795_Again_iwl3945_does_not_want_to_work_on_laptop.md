---
title: "Again iwl3945 does not want to work on laptop"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by VladimirN on 2010-03-29
I have the same trouble with wi-fi card iwl3945 on laptop with rf kill button as of many ubuntu users, but known workarounds didn't help.
I have laptop Compaq 6720 with Kubuntu 9.10
When starting laptop, wi-fi led becomes blue for a second but then becomes orange and doesn't change after pressing.
option disable_hw_scan=1 isn't helpful, too

See below system information

> ~$ lsb_release -d
Description:    Ubuntu 9.10

>  uname -mr
2.6.31-20-generic i686


> lspci
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

> iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=off
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> dmesg
[243829.020963] iwl3945 0000:10:00.0: PCI INT A disabled
[243893.156618] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[243893.156623] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[243893.156717] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[243893.156738] iwl3945 0000:10:00.0: setting latency timer to 64
[243893.214920] iwl3945 0000:10:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[243893.214925] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
[243893.215083] iwl3945 0000:10:00.0: irq 29 for MSI/MSI-X
[243893.217814] phy1: Selected rate control algorithm 'iwl-3945-rs'

>  sudo lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:3d:bc:63
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:e4000000-e4000fff


> iwlist scan
wlan0     Failed to read scan data : Network is down


>  rfkill list
1: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

Hard blocked: yes 
never changed, I think it's the reason, but do not know how to solve ((

---

### Post by chili555 on 2010-03-29
I believe the wireless light is in a button above the keyboard. Please press the button once; run:```
rfkill list
```Is it still hard blocked? If so press it once more and run:```
rfkill list
```Still blocked? Please post:```
lsmod
```

---

### Post by VladimirN on 2010-03-29
> **chili555 said:**
> I believe the wireless light is in a button above the keyboard. Please press the button once; run:```
rfkill list
```Is it still hard blocked? If so press it once more and run:```
rfkill list
```Still blocked? 

yes, it is always in blocked state regardless of pressing button attempts.

> **chili555 said:**
> Please post:```
lsmod
```

> lsmod      
Module                  Size  Used by
iwl3945                77372  0      
binfmt_misc             8356  1      
ppdev                   6688  0      
vboxnetadp              7520  0      
vboxnetflt             14696  0      
vboxdrv               178152  2 vboxnetadp,vboxnetflt
snd_hda_codec_analog    59292  1                     
arc4                    1660  2                      
snd_hda_intel          26920  4                      
snd_hda_codec          75708  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec                     
snd_pcm_oss            37920  0                                   
snd_mixer_oss          16028  1 snd_pcm_oss                       
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ecb                     2524  2                                        
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6464  0
iwlcore               112796  1 iwl3945
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              181140  2 iwl3945,iwlcore
led_class               4096  2 iwl3945,iwlcore
snd_timer              22276  3 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 10240  0
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd                    59204  18 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
cfg80211               93052  3 iwl3945,iwlcore,mac80211
lp                      8964  0
parport                35340  2 ppdev,lp
psmouse                56500  0
serio_raw               5280  0
fbcon                  36640  72
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0
i915                  226120  2
drm                   160032  2 i915
i2c_algo_bit            5760  1 i915
e1000e                121996  0
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


---

### Post by chili555 on 2010-03-29
Have you installed *linux-backports-modules-karmic-generic*? There is a newer driver for iwl3945 in there. I hope it will help.

---

### Post by VladimirN on 2010-03-30
> **chili555 said:**
> Have you installed *linux-backports-modules-karmic-generic*? There is a newer driver for iwl3945 in there. I hope it will help.

Ok, I've done sudo aptitude inux-backports-modules-karmic-generic then rebooted but nothing changed.
rfkill list still shows 
> 1: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: yes


---

### Post by chili555 on 2010-03-30
> When starting laptop, wi-fi led becomes blue for a second but then becomes orange and doesn't change after pressing.Do you mean in the first few moments that the computer starts? Or later? Can you please confirm that the wireless in enabled in the computer's BIOS?

---

### Post by VladimirN on 2010-03-30
> **chili555 said:**
> Do you mean in the first few moments that the computer starts?
Yes, exactly

> **chili555 said:**
> Can you please confirm that the wireless in enabled in the computer's BIOS?
Enabled, I checked several times.

---

### Post by chili555 on 2010-03-30
I love a mystery, however I hate that your wireless is not working perfectly as my Intel 3945 does. I don't know what you have tried to do to diagnose the problem, so please excuse me if I am asking about the obvious.

Does the wireless switch work in other operating systems? Windows? Have you tried a live CD of an earlier or later version of Ubuntu or any other Linux distribution? I am wondering if the switch itself is defective. My suspicion is raised because you confirmed that the only flicker from the wireless light is in the very first moments of booting. The BIOS and then POST and then CMOS and then GRUB (or a master boot record) are executed before any operating system starts. If you look in *dmesg*, you will see that recognition and initialization of the wireless card comes along quite late.

Let's take a look at *dmesg*. Please do:```
dmesg > dmesg.txt
```Please post the text document as an attachment to your reply.

---

### Post by VladimirN on 2010-03-30
> **chili555 said:**
> I love a mystery,
Pleased to meet you, dr. House! :)

>  however I hate that your wireless is not working perfectly as my Intel 3945 does. I don't know what you have tried to do to diagnose the problem, so please excuse me if I am asking about the obvious.ccc
Anything I've found in google :)

> Does the wireless switch work in other operating systems? Windows? Have you tried a live CD of an earlier or later version of Ubuntu or any other Linux distribution? I am wondering if the switch itself is defective. My suspicion is raised because you confirmed that the only flicker from the wireless light is in the very first moments of booting. The BIOS and then POST and then CMOS and then GRUB (or a master boot record) are executed before any operating system starts. If you look in *dmesg*, you will see that recognition and initialization of the wireless card comes along quite late.
Before Kubuntu on this notebook SLES 10 were installed, under it button worked.

Let's take a look at *dmesg*. Please do:```
dmesg > dmesg.txt
```Please post the text document as an attachment to your reply.[/QUOTE]
Ok, done

---

### Post by chili555 on 2010-03-30
I believe you are running a virtual machine. Is Ubuntu the host or the guest? I noticed this:> [   15.794886] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   15.794890] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   15.794891] vboxdrv: counter framework which can generate NMIs is active. [COLOR="Blue"]You have to prevent[/COLOR]
[   15.794893] vboxdrv: [COLOR="Blue"]the usage of hardware performance counters by[/COLOR]
[   15.794894] vboxdrv:   [COLOR="Blue"]echo 2 > /proc/sys/kernel/perf_counter_paranoid[/COLOR]
[   15.794898] vboxdrv: Found 2 processor cores.
[   15.794978] vboxdrv: fAsync=0 offMin=0x1a7 offMax=0xd80
[   15.795024] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   15.795026] vboxdrv: Successfully loaded version 3.1.4 (interface 0x00100001).I am not a student of virtual machines, so I am not quite sure what that means. I do know that getting a network driver to work correctly from within a virtual machine, rather than bridged to the hosts interface, can be difficult.

If Ubuntu is the host, then this is probably not a factor in your issue.

---

### Post by VladimirN on 2010-03-31
Host for windows v-machine

---

### Post by VladimirN on 2010-03-31
I solved it.
The reason was very interesting option (rather queer, IMHO) in BIOS "enable LAN\WLAN switching", which when enabled prevents rfkill button from work, when wired interface is in connected state. Moreover, this buttons enables at the same time bluetooth (how it is linked with wired connection, only God knows).

---

