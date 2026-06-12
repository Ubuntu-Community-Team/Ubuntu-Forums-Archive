---
title: "Compaq Presario V3410TU Iwl3945 problem"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by rachyl on 2010-03-29
This system comes with a vista installed. Decided to convert it to ubuntu, so I pop in a live cd and install Ubuntu 9.10 formating the whole HDD. Currently the problem with the wireless is the external switch cannot be switch on or off. Below are the outputs for most of the commands. 


lspci | grep 'Wireless'
```
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

ifconfig wlan0
```
wlan0     Link encap:Ethernet HWaddr 00:1b:77:14:4d:7e
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

rfkill list
```
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
```

lshw -C network
```
*-network DISABLED
     description: Wireless interface
     product: PRO/Wireless 3945ABG [Golan] Network Connection
     vendor: Intel Corporation
     physical id: 0
     bus info: pci@0000:05:00.0
     logical name: wlan0
     version: 02
     serial: 00:1b:77:14:4d:7e
     width: 32 bits
     clock: 33MHz
     capabilities: bus_master cap_list ethernet physical wireless
     configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
     resources: irq:28 memory:d4000000-d4000fff
```


Thanks beforehand to any help offered.

---

### Post by rachyl on 2010-04-06
Bump

---

### Post by rachyl on 2010-04-07
Bump

---

### Post by rachyl on 2010-04-07
Bump

---

### Post by rachyl on 2010-04-08
Bump

---

### Post by chili555 on 2010-04-08
> Currently the problem with the wireless is the external switch cannot be switch on or off.Do you mean that the switch itself is defective or do you mean that the switch doesn't seem to change anything? Does it matter if you start the computer with it on? Or start it with it off and switch it on? Learn by trying both combinations and running:```
rfkill list
```May we see:```
lsmod
```Thanks.

---

### Post by rachyl on 2010-04-08
The switch becomes defective. Turning the switch on or off does nothing. Went thru the shortcut keys and did not find anything keys that are of use too. 

lsmod | grep 'iwl'
```
iwl3945               71484  0
iwlcore              114464  1 iwl3945
mac80211             210604  2 iwl3945,iwlcore
led_class              4096  3 iwl3945,iwlcore,sdhci
cfg80211             130696  3 iwl3945,iwlcore,mac80211
```

---

### Post by chili555 on 2010-04-08
> lsmod | grep 'iwl'I would like to see the entirety of lsmod. I am hoping I see some ami or acpi module we might manipulate.

---

### Post by rachyl on 2010-04-08
As requested, below is the whole lsmod. 

lsmod
```
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
cbc                     3516  103 
aes_i586                8124  104 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
dm_crypt               12928  0 
mmc_block              10592  2 
snd_hda_codec_conexant    20060  1 
snd_hda_intel          27016  2 
snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75520  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1660  2 
ecb                     2524  3 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iwl3945                71484  0 
iwlcore               114464  1 iwl3945
mac80211              210604  2 iwl3945,iwlcore
iptable_filter          3100  0 
snd_seq_midi            6464  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
lp                      8964  0 
parport                35340  2 ppdev,lp
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
psmouse                56500  0 
serio_raw               5280  0 
ricoh_mmc               3676  0 
sdhci_pci               7132  0 
sdhci                  17632  1 sdhci_pci
led_class               4096  3 iwl3945,iwlcore,sdhci
cfg80211              130696  3 iwl3945,iwlcore,mac80211
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9252  2 snd_hda_intel,snd_pcm
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
ohci1394               30220  0 
ieee1394               86628  1 ohci1394
e100                   32772  0 
mii                     5212  1 e100
intel_agp              27940  1 
agpgart                35020  2 intel_agp
output                  2780  0 

```

---

### Post by rachyl on 2010-04-08
Anyone else could offer some solutions to this?

---

### Post by rachyl on 2010-04-09
Anyone can offer some help?

---

### Post by chili555 on 2010-04-09
This is a very difficult problem. It is the subject of an unsolved bug report on Lanchpad and a bit of Googling uncovers many people with Presarios with unresponsive wireless buttons in several versions of Linux and several versions of Windows.

Please try:```
rfkill list
sudo su
echo 1 > /sys/class/rfkill/rfkill0/state
exit
rfkill list
```Any change?

Also, please do:```
sudo tail -f /var/log/messages
```Now manipulate the wireless button and see if the kernel is aware of any key presses. If so, jot down the code it records, perhaps something like 0xF4 or some such.

---

### Post by rachyl on 2010-04-09
The first set of command did not change the rfkill list. 
The Hard Blocked is still 'yes'. 

And the log message still did not show any respond from manipulating the wireless button.

---

### Post by chili555 on 2010-04-09
> **rachyl said:**
> The first set of command did not change the rfkill list. 
The Hard Blocked is still 'yes'. 

And the log message still did not show any respond from manipulating the wireless button.I am sorry. I have no ideas left. I am sorry I could not be of more help.

---

### Post by rachyl on 2010-04-09
nvm. 
As expected. Think it is time to get a Wifi USB adapter.

---

