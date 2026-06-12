---
title: "Compaq Presario C500 wifi problem"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by xxwikkixx on 2011-08-02
i install ubuntu on my old compaq presario and it works great better than windows....but when i installed it the first time my wifi didnt work so i did some research and it work fine until today i updated ubuntu through the update manager and it installed linux kernel 2.38.0.10 i believe some thing like that....and now my wifi wont turn on again. in the additional drivers it say it is installed and successfully in use but the wifi light wont come on and nothing....right now i m using my sprint 3g card to post on this forum............................can some one please help me [-o<[-o<[-o<

---

### Post by wildmanne39 on 2011-08-02
Hi, run these commands in a terminal please.
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsmod
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

### Post by xxwikkixx on 2011-08-02
never mind i got it to work.....i uninstalled all broadcom divers from ubuntu software center and also from the synaptic manager, then i installed the broadcom sta driver from the ubuntu softwasre center and restarted my laptop and it works fine now. :KS:KS:KS

---

### Post by wildmanne39 on 2011-08-02
Hi, ok would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by techshack on 2012-02-18
> **wildmanne39 said:**
> Hi, run these commands in a terminal please.
```
sudo lshw -C network
``````
lspci -nn | grep 0280
``````
lsmod
``````
iwconfig
``````
rfkill list all
```and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you
# flynn@flynn-Presario-C500-RZ820PA-ACJ:~$ sudo lshw -C network
[sudo] password for flynn: 
12345Sorry, try again.
[sudo] password for flynn: 
12345sysfs)  
^[[C^[[C  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:20000000-20003fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:e5:c3:c9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:50:c5:00:47:b5
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=MOSCHIP usb-ethernet driver driverversion=22-Aug-2005 duplex=full firmware=MOSCHIP 7830/7832/7730 usb-NET ausb-0000:00:1d.7-6 ip=192.168.1.2 link=yes multicast=yes port=MII speed=100Mbit/s
flynn@flynn-Presario-C500-RZ820PA-ACJ:~$ 12345
12345: command not found
flynn@flynn-Presario-C500-RZ820PA-ACJ:~$ 12345\sudo lshw -C network
12345sudo: command not found
flynn@flynn-Presario-C500-RZ820PA-ACJ:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
flynn@flynn-Presario-C500-RZ820PA-ACJ:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  8 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
mcs7830                13525  0 
snd_seq_midi           13132  0 
usbnet                 25214  1 mcs7830
snd_rawmidi            25241  1 snd_seq_midi
wl                   2646601  0 
psmouse                73673  0 
binfmt_misc            17292  1 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  509519  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 hp_wmi
lib80211               14570  1 wl
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
8139too                23283  0 
8139cp                 22636  0 
flynn@flynn-Presario-C500-RZ820PA-ACJ:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

flynn@flynn-Presario-C500-RZ820PA-ACJ:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
flynn@flynn-Presario-C500-RZ820PA-ACJ:~$

---

### Post by techshack on 2012-02-18
> **xxwikkixx said:**
> never mind i got it to work.....i uninstalled all broadcom divers from ubuntu software center and also from the synaptic manager, then i installed the broadcom sta driver from the ubuntu softwasre center and restarted my laptop and it works fine now. :KS:KS:KS
...i have done the same...but mine is not working.......................and  y would anybody will uninstall synaptics..which is a touchpad driver......

---

### Post by techshack on 2012-02-18
its silly to mention..but i have to.....Am having wireless networking problem...in my COMPAQ PRESARIO C500 ...the additional driver tab shows..that Broadcom Sta Wireless is activated n rrunning...but my wireless button do not shw any light...or nothing.....Plzzz help....i love Ubuntu environment..but i Didn't expected such things....................(sob)..(sob)......:confused::confused::o:o

---

### Post by bkratz on 2012-02-18
> **techshack said:**
> its silly to mention..but i have to.....Am having wireless networking problem...in my COMPAQ PRESARIO C500 ...the additional driver tab shows..that Broadcom Sta Wireless is activated n rrunning...but my wireless button do not shw any light...or nothing.....Plzzz help....i love Ubuntu environment..but i Didn't expected such things....................(sob)..(sob)......:confused::confused::o:o




The sta driver is not the right one for either 11.04 or 11.10. Here is the directions for the BCM4311 for either.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)



Also the hardblocked message indicates that the wireless switch is "off"

---

