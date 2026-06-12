---
title: "wireless is disable by hardware switch on 11.10"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by skyhookpro on 2011-10-19
greeting, After update from 11.04-to-11.10 two days ago, everything runs fine but yesterday my wirelesscard stop working and a message "wireless is disable by hardware switch, to be honest dont know if i touch someting. the device is recognized but try click on the device is in "gray" type. so i do some diag and this is what i found run my cmd line and tis info is what i get:
0:[B] hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no[/B]
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: [B]phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes[/B]
Can someone help me out on this doing the correct steps...

Thank in advance

---

### Post by vangop on 2011-10-19
Click the network manager tray icon - is the "Enable wireless" checked?
Check your hardware wireless switch/button.

---

### Post by takai on 2011-10-20
I am having the same issue. Fresh 11.10 installation. Wireless enabled in the bios, and hardware switches enabled.

Even occurs with external USB wireless devices. Occurs on 4 different laptops.

---

### Post by takai on 2011-10-20
For what its worth, its this bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701259)

Still unsolved.

---

### Post by praseodym on 2011-10-20
Please show:

```
lspci -nnk | grep -iA2 net
lsmod
```
Check any switches/keys/key combinations, and your BIOS settings. Maybe resetting the BIOS to default?

---

### Post by takai on 2011-10-20
> **praseodym said:**
> Please show:

```
lspci -nnk | grep -iA2 net
lsmod
```
Check any switches/keys/key combinations, and your BIOS settings. Maybe resetting the BIOS to default?

Removing the dell_laptop kernel module unlocks the wireless. This is with both the stock Linux Broadcom drivers, and the Broadcom B43 and STA drivers. 

Its a well documented bug, which has been reported in January, yet nothing has been done about it in either of the 11.x releases.

---

### Post by bkratz on 2011-10-20
> **takai said:**
> Removing the dell_laptop kernel module unlocks the wireless. This is with both the stock Linux Broadcom drivers, and the Broadcom B43 and STA drivers. 

Its a well documented bug, which has been reported in January, yet nothing has been done about it in either of the 11.x releases.


From the post 1

0:[B] hp-wifi: Wireless LAN

[/B]I doubt the user has a dell laptop.

---

### Post by skyhookpro on 2011-10-21
Sorry for late respond(study/work) my free try to figure out why wireless doesnot work here is me step-by-step diagnosis.
1. chk my network panel find wireless setting and was off try to switch back on, wont allow me, just return to off, also on the botton i saw another switch " ariplane mode" so decide turn off it can turn off, try to switch back wireless back on again doesnot allow mw to do that. 
2. went to ubuntu help..wireless diagnosis...here what i found.
a. initial chk so..nm-tool:

 Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             unavailable
  Default:           no
  HW Address:        00:12:F0:88:7C:20

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
Then: *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:88:7c:20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:b0107000-b0107fff
Also:libipw                 46701  1 ipw2200

Also too:eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Note: Wireless  was working before make the update i just get to a point to make a fresh installation but really i dont want to.
Thanks guys for take time for help me out of this.

somewhat frustration comming up..jejeje; nonetheless i have faith that this issue have a solution...cheer an have a good day to all of awesome people.

---

### Post by skyhookpro on 2011-10-21
working in bios right now...08:30(EST)

---

### Post by skyhookpro on 2011-10-21
went to Bios, wireless enable. rechk again network panel switch can't switch back on. and the F*** airplane mode in on, put back to off position again. try to switch on wireless doesnot work. yet. have another option?

---

### Post by skyhookpro on 2011-10-21
06:06.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:12f5]
    Kernel driver in use: ipw2200
AND

Module                  Size  Used by
nls_utf8               12493  1 
nls_iso8859_1          12617  0 
isofs                  39549  1 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  9 
parport_pc             32114  0 
ppdev                  12849  0 
snd_intel8x0           33318  0 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
binfmt_misc            17292  1 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
btusb                  18160  3 
i915                  505108  4 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146148  0 
mmc_block              22393  0 
bluetooth             148839  15 bnep,rfcomm,btusb
libipw                 46701  1 ipw2200
drm_kms_helper         32889  1 i915
hp_wmi                 13652  0 
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
tifm_sd                17566  0 
pcmcia                 39822  0 
psmouse                73673  0 
tifm_7xx1              12937  0 
snd                    55902  7 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
cfg80211              172392  2 ipw2200,libipw
drm                   192226  5 i915,drm_kms_helper
tifm_core              15040  2 tifm_sd,tifm_7xx1
soundcore              12600  1 snd
yenta_socket           27428  0 
wmi                    18744  1 hp_wmi
pcmcia_rsrc            18367  1 yenta_socket
lib80211               14570  2 ipw2200,libipw
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
8139too                23283  0 
firewire_ohci          35854  0 
8139cp                 22636  0 
firewire_core          56937  1 firewire_ohci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
nbd                    17427  0

---

### Post by Mr Zero on 2011-10-21
try ifconfig eth1 up
or ifconfig eth0 up
or ifconfig wlan up

---

### Post by praseodym on 2011-10-21
We just had this in the German forum:

Download the firmware for the module ipw2200 Version 3 from here:

[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)

and unpack it to /lib/firmware. Reboot after that

---

### Post by skyhookpro on 2011-10-21
ok I got it...I let you know..

---

### Post by skyhookpro on 2012-01-30
Hi ladys and gentleman, my apologies not answer or follow up my laptop issues back on October...lost my job for low business and really have more important thing to do at that time. But thing going better and now I write my feedback on how I did correct the issue.
Remeber a message display :  "wireless is disable by hardware switch" and after some of you guys trying to help me out on this ( thank you very much) BUT the driver wont help.
so I grab some of my tool do some basic(visual inspect)  check my wireless card i mean physical connection was good. Yes this laptop has external push button chk with my multimeter and the switch work fine. So my next step was FORMAT and try fresh intallation with window XP sp3 and return the laptop to "factory condition" and guess what...work!!! well ok that good, also went to HP site thy got all driver for my wireless card and intalled. step one successfully achieve. Now install UBUNTU 11.10 as a second boot at the same HD. Installation again success, now let test the wireless..guess what NOT work , get really mad and frustrated, but have a little hope... so again I did my basics on wireless diagnosis.
and found this linux command "sudo rfkill list" and I saw soft key off and hard key also off.
at the end of terminal line have few command block, unblock etc. so i type unblock and the number and word that belong to wireless setting. ITS ALIVEEEEEEE my wireless work again happynees couldnt be better...so thank all the people that try to help me out back on October thank you..

BTW. right now studying MCITP...SERVER ADMI...PLUS ADVANCE IN ELECTRONICS...VERY HAPPY!!!!!

---

### Post by psicopato on 2012-03-04
> **skyhookpro said:**
> Hi ladys and gentleman, my apologies not answer or follow up my laptop issues back on October...lost my job for low business and really have more important thing to do at that time. But thing going better and now I write my feedback on how I did correct the issue.
Remeber a message display :  "wireless is disable by hardware switch" and after some of you guys trying to help me out on this ( thank you very much) BUT the driver wont help.
so I grab some of my tool do some basic(visual inspect)  check my wireless card i mean physical connection was good. Yes this laptop has external push button chk with my multimeter and the switch work fine. So my next step was FORMAT and try fresh intallation with window XP sp3 and return the laptop to "factory condition" and guess what...work!!! well ok that good, also went to HP site thy got all driver for my wireless card and intalled. step one successfully achieve. Now install UBUNTU 11.10 as a second boot at the same HD. Installation again success, now let test the wireless..guess what NOT work , get really mad and frustrated, but have a little hope... so again I did my basics on wireless diagnosis.
and found this linux command "sudo rfkill list" and I saw soft key off and hard key also off.
at the end of terminal line have few command block, unblock etc. so i type unblock and the number and word that belong to wireless setting. ITS ALIVEEEEEEE my wireless work again happynees couldnt be better...so thank all the people that try to help me out back on October thank you..

BTW. right now studying MCITP...SERVER ADMI...PLUS ADVANCE IN ELECTRONICS...VERY HAPPY!!!!!


:popcorn:

Many, many & many thanks !!!

Since the last update to version 11.10 my laptop HP DV1359ea has lost wifi communication though the Intel pro 2200bg built in network card :(

I've tried dozens of ways to fix the bug since I'm not a linux expert. Dozens of hours later I see this posts and with the rfkill method  I also could fix my laptop but.
MANY THANKS:P

---

