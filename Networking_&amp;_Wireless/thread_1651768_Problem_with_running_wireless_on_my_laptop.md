---
title: "Problem with running wireless on my laptop"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by JackomoLight on 2010-12-23
Hello everybody,

yesterday I installed Ubuntu 10.10 and I am a bit stuck with running the wireless on my HP Compaq 6715b I've been doing some research for the last 4-5 hours but nothing helped. Here is the info I gathered:

*Note I am a newbie to ubuntu

command: lspci
etc...
Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)


command: lshw -C network

*-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:5f:db:ca
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.09 ip=192.168.1.3      latency=0 multicast=yes
       resources: irq:43 memory:d0000000-d000ffff


So the driver is installed.

command: rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

and no matter what I do

command: iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.


Any help will be appreciated and Merry Christmas

---

### Post by JackomoLight on 2010-12-23
Just to add something to the info I provided

lsmod

shows

usbhid                 42062  0 
hid                    84710  1 usbhid
tpm_infineon            9441  0 
snd_hda_codec_analog    80317  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
radeon                909450  3 
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
ttm                    68212  1 radeon
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         32836  1 radeon
pcmcia                 40944  0 
joydev                 11395  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6804  0 
hp_wmi                  6467  0 
tpm_tis                 9894  0 
video                  22176  0 
drm                   206230  3 radeon,ttm,drm_kms_helper
i2c_algo_bit            6208  1 radeon
snd                    64181  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           24279  0 
pcmcia_rsrc            10357  1 yenta_socket
tpm                    16013  2 tpm_infineon,tpm_tis
hp_accel               14304  0 
lis3lv02d              10384  1 hp_accel
input_polldev           4527  1 lis3lv02d
parport_pc             30086  1 
pcmcia_core            17677  3 pcmcia,yenta_socket,pcmcia_rsrc
tpm_bios                6426  1 tpm
output                  2527  1 video
edac_core              46822  0 
soundcore               1240  1 snd
psmouse                62080  0 
serio_raw               4910  0 
led_class               3393  1 hp_accel
k8temp                  4128  0 
i2c_piix4              10047  0 
edac_mce_amd            9387  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
shpchp                 34910  0 
lp                     10201  0 
parport                37032  3 ppdev,parport_pc,lp
firewire_ohci          24615  0 
ahci                   22210  1 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
libahci                26052  1 ahci
pata_atiixp             4405  0 
tg3                   135768  0


so the driver(tg3) is loaded but its not used

---

### Post by bkratz on 2010-12-23
> **JackomoLight said:**
> Hello everybody,

yesterday I installed Ubuntu 10.10 and I am a bit stuck with running the wireless on my HP Compaq 6715b I've been doing some research for the last 4-5 hours but nothing helped. Here is the info I gathered:

*Note I am a newbie to ubuntu

command: lspci
etc...
[COLOR="DarkRed"]Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
[/COLOR]

command: lshw -C network

*-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:5f:db:ca
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.09 ip=192.168.1.3      latency=0 multicast=yes
       resources: irq:43 memory:d0000000-d000ffff



Any help will be appreciated and Merry Christmas

The controller above is your ethernet controller not the wireless. It would say something like Network or wireless in the description rather than ethernet.

Can you post the entire output of 

```
lspci -nn

```


If it is a usb device (sometime they are even though they are internal) try

lsusb

---

### Post by JackomoLight on 2010-12-26
Thanks for the reply but I already solved and figured out that it was the ethernet controller :D

---

