---
title: "need help compiling compat-wireless"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by GiladGressel on 2011-07-15
Hi,

so I'm asking for help compiling compat-wireless

running 11.04 on an asus 1201n
wireless has not been great, cuts in and out.

other folks have said they are using a driver from compat-wireless, was trying to do the same, but so far have failed.

i downloaded [ompat-wireless-3.0-rc4-1.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-3.0-stable/v3.0/compat-wireless-3.0-rc4-1.tar.bz2")
followed the instructions from that site -- everything seemed to work except after reboot no wifi.  still use rtl8192se_pci which i believe is the default with natty and is also not good.

output of 

```
gilad@maya:~$ lspci -nn | grep 0280
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
gilad@maya:~$ 
```hope you can help thanks
-gilad

EDIT -- I think i just found my problem.  newbie mistake i think.
i updated my ubuntu in the same sesion i installed the drivers from compat.  the result is that my ubuntu now loads a newer kernel header than I installed the driver went from.  so i guess i just have to reinstall it in this version? will try

still curious what your hunch is chilli

---

### Post by chili555 on 2011-07-15
> still use rtl8192se_pci which i believe is the default with natty and is also not good.I think the underlying issue is firmware. Let's have a look at:```
modinfo rtl8192se-pci
ls /lib/firmware/rtlwifi
```I am not sure 3.0-rc4 is best, I think it's designed for kernel 3.0-rc4. If you are running Natty, you probably have 2.6.38.

---

### Post by GiladGressel on 2011-07-15
ok 
so i did successfully make the compat driver run.however once it ran i couldn't connect at all
so i ran make uninstall

it's true that 3.0 seems geared to a higher kernel than mine, i only tried it because other people reported it working from the r8192se thread.  and in thejpsters post it listed his kernel as lower so i thought it may work

here is the output from your request
```

gilad@maya:~$ modinfo r8192se_pci
filename:       /lib/modules/2.6.38-10-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
license:        GPL
version:        0017.0507.2010
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     15A8DFA339847552659BE80
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        cfg80211
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)
gilad@maya:~$ ls /lib/firmware/rtlwifi
rtl8192cfw.bin  rtl8192cufw.bin  rtl8192defw.bin  rtl8192sefw.bin  rtl8712u.bin
gilad@maya:~$ 
```

---

### Post by chili555 on 2011-07-15
It gets weirder by the moment. You have the stock version which does not require firmware...but you have the firmware! Before we break out the toolbox, please tell me what about the current driver is not working as expected.

---

### Post by GiladGressel on 2011-07-15
ok

so, i load my computer.   i connect to the available wirless network (currently in a hotel so it's called attwifi -- no password just a click on "agree to terms and services" and not every time either)

it works for awhile.  roughly 2-3 minutes then it stops working.

then i get annoyed and force to reload the wifi by clicking on the network again.  it goes through a process where it either loads it or doesn't.  often it automatically reverts to an ad-hoc network i use.

i have taken to running modprobe r8192se_pci in order to force it back on track.

when i was home connecting to a password encrypted network i would simply lose connection.  It won't show that it loses connection -- the internet just stops moving.

can hold a connection for even up to an hour I think.  not really sure how long
currently it's been connected for about 15 minutes which seems long to me

hope that helps sorry i rambled
i have to leave for awhile now will be back in a few hours
if you leave me a list of commands etc to run I'm very happy to post them

-gilad

---

### Post by chili555 on 2011-07-15
Let's go ahead and try compat-wireless. Please go here: [http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball](http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball)

Download the file to your desktop. Right-click it and select Extract Here. Now do:```
cd Desktop/compat
```Press Tab and the rest will fill in automatically. Next do:```
./scripts/driver-select rtlwifi
make
sudo make install
```The new module is called rtl8192se. The one referenced above is r8192se_pci.> make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  INSTALL /home/chili/test2/compat-wireless-2011-07-15/compat/compat.ko
  INSTALL /home/chili/test2/compat-wireless-2011-07-15/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  INSTALL /home/chili/test2/compat-wireless-2011-07-15/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  INSTALL /home/chili/test2/compat-wireless-2011-07-15/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  INSTALL /home/chili/test2/compat-wireless-2011-07-15/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  INSTALL /home/chili/test2/compat-wireless-2011-07-15/drivers/net/wireless/rtlwifi/rtl8192se/[COLOR="Red"]rtl8192se[/COLOR].ko
  INSTALL /home/chili/test2/compat-wireless-2011-07-15/drivers/net/wireless/rtlwifi/rtlwifi.ko
Just so there is no difficulty, let's blacklist r8192se_pci:```
sudo su
echo "blacklist r8192se_pci" >> /etc/modprobe.d/blacklist.conf
echo rtl8192se >> /etc/modules
exit
```Reboot and let us have your report.

---

### Post by GiladGressel on 2011-07-15
So I followed all instructions to the t
Upon loading it worked beautifully for about 30 seconds and then stopped altogether I have been trying to coax it back to no avail

I am sure the correct module is running because I checked with lsmod it's listed under rtlwifi as rtl8192se

Any other ideas ?
This driver has been a pain for ubuntu for awhile I used to run ndiswrapper in 10.10 but that driver gets weak signals and slow speeds for me
In 10.04 there was a ppa by Matt price but that is also no longer good

That's about all I can say 
Thanks for helping I'm ready to try more things

---

### Post by nm_geo on 2011-07-16
> **GiladGressel said:**
> So I followed all instructions to the t
Upon loading it worked beautifully for about 30 seconds and then stopped altogether I have been trying to coax it back to no avail

I am sure the correct module is running because I checked with lsmod it's listed under rtlwifi as rtl8192se

Any other ideas ?
This driver has been a pain for ubuntu for awhile I used to run ndiswrapper in 10.10 but that driver gets weak signals and slow speeds for me
In 10.04 there was a ppa by Matt price but that is also no longer good

That's about all I can say 
Thanks for helping I'm ready to try more things

Could you show us the 

```
lsmod
```

and 

```
rfkill list all 

```

You have Chili working here with you and it does not get any better I am just curious..

---

### Post by chili555 on 2011-07-16
Let's also see:```
dmesg | grep -e wlan -e 819
sudo cat /var/log/syslog | grep etwork | tail -n20
```If the second command is sparse, try syslog.1. Thanks.

---

### Post by GiladGressel on 2011-07-16
Ok quick question before I run the codes
Do you want those logs running the installed compat driver or with the native natty driver?
Currently I ran sudo make uninstall and reversed the blacklist and module entries you had me make (was on auto pilot cleanup mode)
Given what others have posted I'm inclined to think the compat driver is more effective than the native driver so should we be focused on getting that to work?
Thanks for the help!
Gilad

---

### Post by chili555 on 2011-07-16
> Do you want those logs running the installed compat driverYes, because:> Given what others have posted I'm inclined to think the compat driver is more effective than the native driver Please reboot so we are starting with a clean slate. I will be away for about an hour. Even driver genies need exercise! See you soon.

---

### Post by GiladGressel on 2011-07-16
EDIT -- just read your response after i posted this
ok will remake compat driver and post codes in rebooted state

BELOW CODES ARE FOR NATIVE LINUX DRIVER



lsmod

```
gilad@maya:~$ lsmod
Module                  Size  Used by
rfcomm                 38125  10 
binfmt_misc            13213  1 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
vboxnetadp             13348  0 
vboxnetflt             27855  0 
vboxdrv               238410  2 vboxnetadp,vboxnetflt
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
joydev                 17322  0 
nvidia               9766978  86 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
eeepc_wmi              18771  0 
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
sparse_keymap          13666  1 eeepc_wmi
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
r8192se_pci           482505  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
btusb                  18160  2 
uvcvideo               66851  0 
snd_timer              28659  2 snd_pcm,snd_seq
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  1 r8192se_pci
psmouse                73312  0 
videodev               75143  1 uvcvideo
serio_raw              12990  0 
video                  18951  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2            12906  0 
shpchp                 32345  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  3 
libahci                25548  1 ahci
atl1c                  36237  0 
gilad@maya:~$ 

```rfkill list all

```
gilad@maya:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: eeepc-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
gilad@maya:~$

```dmesg | grep -e wlan -e 819

```
gilad@maya:~$ dmesg | grep -e wlan -e 819
[    0.478198] pci 0000:05:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    1.623361] ata1: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76100 irq 40
[   14.622859] Linux kernel driver for RTL8192 based WLAN cards
[   14.623691] rtl819xSE 0000:07:00.0: PCI INT A -> Link[LN4A] -> GSI 18 (level, low) -> IRQ 18
[   14.623712] rtl819xSE 0000:07:00.0: setting latency timer to 64
[   14.651399] rtl8192: wireless switch is on
[   23.070316] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   23.070431] =====>rtl8192_set_chan()====ch:2
[   23.071057] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.180068] =====>rtl8192_set_chan()====ch:3
[   23.288102] =====>rtl8192_set_chan()====ch:4
[   23.396040] =====>rtl8192_set_chan()====ch:5
[   23.452871] =====>rtl8192_set_chan()====ch:1
[   23.564042] =====>rtl8192_set_chan()====ch:2
[   23.676053] =====>rtl8192_set_chan()====ch:3
[   23.788043] =====>rtl8192_set_chan()====ch:4
[   23.900037] =====>rtl8192_set_chan()====ch:5
[   24.012041] =====>rtl8192_set_chan()====ch:6
[   24.124141] =====>rtl8192_set_chan()====ch:7
[   24.236034] =====>rtl8192_set_chan()====ch:8
[   24.348033] =====>rtl8192_set_chan()====ch:9
[   24.460034] =====>rtl8192_set_chan()====ch:10
[   24.572028] =====>rtl8192_set_chan()====ch:11
[   24.684035] =====>rtl8192_set_chan()====ch:12
[   24.796048] =====>rtl8192_set_chan()====ch:13
[   24.939923] =====>rtl8192_set_chan()====ch:1
[   25.052074] =====>rtl8192_set_chan()====ch:2
[   25.164036] =====>rtl8192_set_chan()====ch:3
[   25.276038] =====>rtl8192_set_chan()====ch:4
[   25.388026] =====>rtl8192_set_chan()====ch:5
[   25.500031] =====>rtl8192_set_chan()====ch:6
[   25.612028] =====>rtl8192_set_chan()====ch:7
[   25.724029] =====>rtl8192_set_chan()====ch:8
[   25.836032] =====>rtl8192_set_chan()====ch:9
[   25.948073] =====>rtl8192_set_chan()====ch:10
[   26.060037] =====>rtl8192_set_chan()====ch:11
[   26.172041] =====>rtl8192_set_chan()====ch:12
[   26.284072] =====>rtl8192_set_chan()====ch:13
[   44.137686] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   44.138346] =====>rtl8192_set_chan()====ch:1
[   44.252088] =====>rtl8192_set_chan()====ch:2
[   44.364094] =====>rtl8192_set_chan()====ch:3
[   44.476101] =====>rtl8192_set_chan()====ch:4
[   44.588121] =====>rtl8192_set_chan()====ch:5
[   44.700102] =====>rtl8192_set_chan()====ch:6
[   44.812074] =====>rtl8192_set_chan()====ch:7
[   44.924083] =====>rtl8192_set_chan()====ch:8
[   45.036075] =====>rtl8192_set_chan()====ch:9
[   45.148075] =====>rtl8192_set_chan()====ch:10
[   45.260094] =====>rtl8192_set_chan()====ch:11
[   45.372091] =====>rtl8192_set_chan()====ch:12
[   45.484104] =====>rtl8192_set_chan()====ch:13
[   51.666103] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   51.666592] =====>rtl8192_set_chan()====ch:1
[   51.780087] =====>rtl8192_set_chan()====ch:2
[   51.892074] =====>rtl8192_set_chan()====ch:3
[   52.004069] =====>rtl8192_set_chan()====ch:4
[   52.116218] =====>rtl8192_set_chan()====ch:5
[   52.228066] =====>rtl8192_set_chan()====ch:6
[   52.340091] =====>rtl8192_set_chan()====ch:7
[   52.452082] =====>rtl8192_set_chan()====ch:8
[   52.564095] =====>rtl8192_set_chan()====ch:9
[   52.676046] =====>rtl8192_set_chan()====ch:10
[   52.788099] =====>rtl8192_set_chan()====ch:11
[   52.900061] =====>rtl8192_set_chan()====ch:12
[   53.012546] =====>rtl8192_set_chan()====ch:13
[   53.127665] =====>rtl8192_set_chan()====ch:6
[   53.138183] =====>rtl8192_set_chan()====ch:11
[   53.148504] rtl819xSE:rtl8192_tx: ERR!! Nic is disabled! Can't tx packet len=30 qidx=6!!!
[   53.148664] =====>rtl8192_set_chan()====ch:11
[   53.293138] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   63.169059] =====>rtl8192_set_chan()====ch:1
[   63.280087] =====>rtl8192_set_chan()====ch:2
[   63.392049] =====>rtl8192_set_chan()====ch:3
[   63.504092] =====>rtl8192_set_chan()====ch:4
[   63.616080] =====>rtl8192_set_chan()====ch:5
[   63.728051] =====>rtl8192_set_chan()====ch:6
[   63.840191] =====>rtl8192_set_chan()====ch:7
[   63.952043] =====>rtl8192_set_chan()====ch:8
[   64.064065] =====>rtl8192_set_chan()====ch:9
[   64.176110] =====>rtl8192_set_chan()====ch:10
[   64.288070] =====>rtl8192_set_chan()====ch:11
[   64.400060] =====>rtl8192_set_chan()====ch:12
[   64.512066] =====>rtl8192_set_chan()====ch:13
[   64.626478] =====>rtl8192_set_chan()====ch:11
[   64.639462] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   64.642420] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   64.642428] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[   64.644430] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   74.004729] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   74.060470] =====>rtl8192_set_chan()====ch:1
[   74.172046] =====>rtl8192_set_chan()====ch:2
[   74.284035] =====>rtl8192_set_chan()====ch:3
[   74.396042] =====>rtl8192_set_chan()====ch:4
[   74.508043] =====>rtl8192_set_chan()====ch:5
[   74.620049] =====>rtl8192_set_chan()====ch:6
[   74.732038] =====>rtl8192_set_chan()====ch:7
[   74.844040] =====>rtl8192_set_chan()====ch:8
[   74.956041] =====>rtl8192_set_chan()====ch:9
[   75.048030] wlan0: no IPv6 routers present
[   75.068046] =====>rtl8192_set_chan()====ch:10
[   75.180036] =====>rtl8192_set_chan()====ch:11
[   75.292033] =====>rtl8192_set_chan()====ch:12
[   75.404045] =====>rtl8192_set_chan()====ch:13
[   75.516045] =====>rtl8192_set_chan()====ch:11
[   75.527972] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   75.527985] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[   75.536894] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   75.537337] =====>rtl8192_set_chan()====ch:12
[   75.548577] =====>rtl8192_set_chan()====ch:1
[   75.561807] =====>rtl8192_set_chan()====ch:1
[   75.575338] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   75.582143] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[   75.582152] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[   75.582158] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[   75.582163] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[   75.582199] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   75.582207] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[   86.918199] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   86.936228] =====>rtl8192_set_chan()====ch:1
[   86.948740] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   86.956974] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[   86.956987] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[   86.956995] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[   86.957004] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[   86.957055] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   86.957066] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[   90.383216] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   90.400103] =====>rtl8192_set_chan()====ch:1
[   90.412652] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   90.421246] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[   90.421254] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[   90.421260] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[   90.421266] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[   90.421302] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   90.421310] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[   94.805476] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   94.824079] =====>rtl8192_set_chan()====ch:1
[   94.836821] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   94.844383] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[   94.844391] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[   94.844396] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[   94.844401] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[   94.844436] ===>rtl8192se_link_change():ieee->iw_mode is 2
[   94.844444] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  114.003469] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  114.056563] =====>rtl8192_set_chan()====ch:1
[  114.168039] =====>rtl8192_set_chan()====ch:2
[  114.280048] =====>rtl8192_set_chan()====ch:3
[  114.392042] =====>rtl8192_set_chan()====ch:4
[  114.504053] =====>rtl8192_set_chan()====ch:5
[  114.616057] =====>rtl8192_set_chan()====ch:6
[  114.728042] =====>rtl8192_set_chan()====ch:7
[  114.840038] =====>rtl8192_set_chan()====ch:8
[  114.952050] =====>rtl8192_set_chan()====ch:9
[  115.064055] =====>rtl8192_set_chan()====ch:10
[  115.176046] =====>rtl8192_set_chan()====ch:11
[  115.288051] =====>rtl8192_set_chan()====ch:12
[  115.400040] =====>rtl8192_set_chan()====ch:13
[  115.512055] =====>rtl8192_set_chan()====ch:1
[  115.522839] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  115.522849] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  115.528700] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  115.548820] =====>rtl8192_set_chan()====ch:1
[  115.563501] =====>rtl8192_set_chan()====ch:1
[  115.576768] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  115.586898] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[  115.586909] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[  115.586918] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[  115.586925] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[  115.586974] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  115.586984] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  129.165035] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  129.184078] =====>rtl8192_set_chan()====ch:1
[  129.196506] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  129.201674] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[  129.201685] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[  129.201693] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[  129.201701] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[  129.201749] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  129.201759] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  135.427044] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  135.444074] =====>rtl8192_set_chan()====ch:1
[  135.459145] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  135.476051] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[  135.476060] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[  135.476066] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[  135.476071] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[  135.476110] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  135.476118] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  138.225574] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  138.244684] =====>rtl8192_set_chan()====ch:1
[  138.345491] =====>rtl8192_set_chan()====ch:1
[  138.372196] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  138.397767] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[  138.397775] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[  138.397781] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[  138.397786] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[  138.397822] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  138.397829] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  142.159743] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  142.176151] =====>rtl8192_set_chan()====ch:1
[  142.188995] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  142.196085] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[  142.196094] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[  142.196099] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[  142.196105] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[  142.196141] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  142.196148] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  146.692725] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  146.712120] =====>rtl8192_set_chan()====ch:1
[  146.724130] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  146.734219] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[  146.734227] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[  146.734232] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[  146.734237] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[  146.734273] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  146.734280] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  160.195455] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  160.212652] =====>rtl8192_set_chan()====ch:1
[  160.225516] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  160.241820] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[  160.241832] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[  160.241840] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[  160.241846] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[  160.241898] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  160.241908] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  169.919415] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  169.936083] =====>rtl8192_set_chan()====ch:1
[  169.948737] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  169.955709] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[  169.955717] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[  169.955723] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[  169.955728] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[  169.955764] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  169.955771] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  174.003082] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  174.056280] =====>rtl8192_set_chan()====ch:1
[  174.168047] =====>rtl8192_set_chan()====ch:2
[  174.280037] =====>rtl8192_set_chan()====ch:3
[  174.392063] =====>rtl8192_set_chan()====ch:4
[  174.504042] =====>rtl8192_set_chan()====ch:5
[  174.616058] =====>rtl8192_set_chan()====ch:6
[  174.728046] =====>rtl8192_set_chan()====ch:7
[  174.840064] =====>rtl8192_set_chan()====ch:8
[  174.952053] =====>rtl8192_set_chan()====ch:9
[  175.064079] =====>rtl8192_set_chan()====ch:10
[  175.176087] =====>rtl8192_set_chan()====ch:11
[  175.288081] =====>rtl8192_set_chan()====ch:12
[  175.400091] =====>rtl8192_set_chan()====ch:13
[  175.512084] =====>rtl8192_set_chan()====ch:1
[  175.522925] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  175.522940] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  175.529184] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  175.529332] =====>rtl8192_set_chan()====ch:2
[  175.551055] =====>rtl8192_set_chan()====ch:11
[  175.966468] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  175.968542] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  175.968553] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  254.004890] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  254.060519] =====>rtl8192_set_chan()====ch:1
[  254.172038] =====>rtl8192_set_chan()====ch:2
[  254.284056] =====>rtl8192_set_chan()====ch:3
[  254.396042] =====>rtl8192_set_chan()====ch:4
[  254.508055] =====>rtl8192_set_chan()====ch:5
[  254.620045] =====>rtl8192_set_chan()====ch:6
[  254.732054] =====>rtl8192_set_chan()====ch:7
[  254.844040] =====>rtl8192_set_chan()====ch:8
[  254.956058] =====>rtl8192_set_chan()====ch:9
[  255.068046] =====>rtl8192_set_chan()====ch:10
[  255.180053] =====>rtl8192_set_chan()====ch:11
[  255.292050] =====>rtl8192_set_chan()====ch:12
[  255.404045] =====>rtl8192_set_chan()====ch:13
[  255.516066] =====>rtl8192_set_chan()====ch:11
[  255.526897] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  255.526908] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  255.538399] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  255.538974] =====>rtl8192_set_chan()====ch:1
[  258.052091] =====>rtl8192_set_chan()====ch:1
[  260.564089] =====>rtl8192_set_chan()====ch:1
[  263.076090] =====>rtl8192_set_chan()====ch:1
[  265.538574] =====>rtl8192_set_chan()====ch:1
[  265.652089] =====>rtl8192_set_chan()====ch:1
[  265.667517] =====>rtl8192_set_chan()====ch:6
[  265.719704] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  265.724939] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a425
[  265.724947] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a449
[  265.724953] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e431c
[  265.724958] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f321c
[  265.724995] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  265.725003] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  354.002653] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  354.056515] =====>rtl8192_set_chan()====ch:1
[  354.168046] =====>rtl8192_set_chan()====ch:2
[  354.280058] =====>rtl8192_set_chan()====ch:3
[  354.392046] =====>rtl8192_set_chan()====ch:4
[  354.504041] =====>rtl8192_set_chan()====ch:5
[  354.616046] =====>rtl8192_set_chan()====ch:6
[  354.728042] =====>rtl8192_set_chan()====ch:7
[  354.840044] =====>rtl8192_set_chan()====ch:8
[  354.952041] =====>rtl8192_set_chan()====ch:9
[  355.068052] =====>rtl8192_set_chan()====ch:10
[  355.180039] =====>rtl8192_set_chan()====ch:11
[  355.292050] =====>rtl8192_set_chan()====ch:12
[  355.404041] =====>rtl8192_set_chan()====ch:13
[  355.516054] =====>rtl8192_set_chan()====ch:6
[  355.527310] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  355.527321] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
gilad@maya:~$ 
```sudo cat /var/log/syslog | grep etwork | tail -n20

```
gilad@maya:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for gilad: 
Jul 16 09:46:56 maya NetworkManager[853]: <info> (wlan0): roamed from BSSID 00:0F:F7:51:80:10 (attwifi) to 04:21:B0:6A:BD:2B (attwifi)
Jul 16 09:46:57 maya kernel: [  258.052064] Linking with attwifi,channel:1, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Jul 16 09:46:59 maya kernel: [  260.564059] Linking with attwifi,channel:1, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Jul 16 09:47:02 maya kernel: [  263.076062] Linking with attwifi,channel:1, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Jul 16 09:47:04 maya NetworkManager[853]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jul 16 09:47:04 maya kernel: [  265.588049] Linking with attwifi,channel:1, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Jul 16 09:47:04 maya NetworkManager[853]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jul 16 09:47:04 maya kernel: [  265.666918] Linking with attwifi,channel:1, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Jul 16 09:47:04 maya kernel: [  265.667079] Linking with attwifi,channel:6, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Jul 16 09:47:04 maya kernel: [  265.667107] Linking with attwifi,channel:6, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Jul 16 09:47:04 maya NetworkManager[853]: <info> (wlan0): supplicant connection state:  associating -> associated
Jul 16 09:47:04 maya NetworkManager[853]: <info> (wlan0): supplicant connection state:  associated -> completed
Jul 16 09:47:08 maya NetworkManager[853]: <info> (wlan0): roamed from BSSID 04:21:B0:6A:BD:2B (attwifi) to 00:0F:8F:79:B5:B0 (attwifi)
Jul 16 09:50:34 maya kernel: [  475.527541] Linking with attwifi,channel:11, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Jul 16 09:50:34 maya kernel: [  475.527575] Linking with attwifi,channel:11, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Jul 16 09:50:34 maya NetworkManager[853]: <info> (wlan0): supplicant connection state:  completed -> associating
Jul 16 09:50:34 maya NetworkManager[853]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jul 16 09:50:34 maya NetworkManager[853]: <info> (wlan0): supplicant connection state:  disconnected -> associated
Jul 16 09:50:34 maya NetworkManager[853]: <info> (wlan0): supplicant connection state:  associated -> completed
Jul 16 09:50:38 maya NetworkManager[853]: <info> (wlan0): roamed from BSSID 00:0F:8F:79:B5:B0 (attwifi) to 00:0F:F7:51:80:10 (attwifi)
```ok this is with the native natty driver r8192se_pci

let me know if that was a mistake to uninstall the compat

thanks a lot
-gilad



-gilad

---

### Post by GiladGressel on 2011-07-16
ok here are log files with compat driver.  and currently i am connect to internet (posting through it) with compat, been about 3 minutes...(edit: one minute after typing that, but before posting this it dropped connection and reconnected)

lsmod

```
gilad@maya:~$ lsmod
Module                  Size  Used by
rfcomm                 38125  10 
sco                    17827  2 
binfmt_misc            13213  1 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
vboxnetadp             13348  0 
vboxnetflt             27855  0 
vboxdrv               238410  2 vboxnetadp,vboxnetflt
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rtl8192se              92452  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
rtlwifi                94463  1 rtl8192se
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              265583  2 rtl8192se,rtlwifi
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              165898  2 rtlwifi,mac80211
eeepc_wmi              18771  0 
lp                     13349  0 
uvcvideo               66851  0 
sparse_keymap          13666  1 eeepc_wmi
btusb                  18160  2 
joydev                 17322  0 
video                  18951  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
soundcore              12600  1 snd
videodev               75143  1 uvcvideo
nvidia               9766978  86 
psmouse                73312  0 
serio_raw              12990  0 
i2c_nforce2            12906  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
shpchp                 32345  0 
parport                36746  3 parport_pc,ppdev,lp
atl1c                  36237  0 
ahci                   21591  3 
libahci                25548  1 ahci
gilad@maya:~$ 
```

rfkill list all

```
gilad@maya:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: eeepc-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
gilad@maya:~$ 
```

dmesg | grep -e wlan -e 819

```
gilad@maya:~$ dmesg | grep -e wlan -e 819
[    0.488192] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.588819] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.638199] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.782819] isapnp: Scanning for PnP cards...
[    1.627106] ata1: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76100 irq 40
[   17.960819] nvidia 0000:05:00.0: PCI INT A -> Link[SGRU] -> GSI 23 (level, low) -> IRQ 23
[   18.592038] r8192se_pci: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   18.592049] r8192se_pci: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   18.592414] r8192se_pci: disagrees about version of symbol wiphy_register
[   18.592420] r8192se_pci: Unknown symbol wiphy_register (err -22)
[   18.592852] r8192se_pci: disagrees about version of symbol wiphy_new
[   18.592858] r8192se_pci: Unknown symbol wiphy_new (err -22)
[   18.594236] r8192se_pci: disagrees about version of symbol wiphy_rfkill_stop_polling
[   18.594242] r8192se_pci: Unknown symbol wiphy_rfkill_stop_polling (err -22)
[   18.595973] r8192se_pci: disagrees about version of symbol wiphy_unregister
[   18.595979] r8192se_pci: Unknown symbol wiphy_unregister (err -22)
[   18.597768] r8192se_pci: disagrees about version of symbol wiphy_rfkill_start_polling
[   18.597775] r8192se_pci: Unknown symbol wiphy_rfkill_start_polling (err -22)
[   18.599191] r8192se_pci: disagrees about version of symbol cfg80211_inform_bss_frame
[   18.599197] r8192se_pci: Unknown symbol cfg80211_inform_bss_frame (err -22)
[   18.600283] r8192se_pci: disagrees about version of symbol wiphy_free
[   18.600290] r8192se_pci: Unknown symbol wiphy_free (err -22)
[   19.120465] rtl8192se 0000:07:00.0: PCI INT A -> Link[LN4A] -> GSI 18 (level, low) -> IRQ 18
[   19.120480] rtl8192se 0000:07:00.0: setting latency timer to 64
[   19.132856] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   19.132861]            Loading firmware rtlwifi/rtl8192sefw.bin
[   23.891885] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   61.497184] wlan0: authenticate with 00:0f:f7:51:80:10 (try 1)
[   61.499192] wlan0: authenticated
[   61.499257] wlan0: associate with 00:0f:f7:51:80:10 (try 1)
[   61.501771] wlan0: RX AssocResp from 00:0f:f7:51:80:10 (capab=0x401 status=0 aid=36)
[   61.501784] wlan0: associated
[   61.503853] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   72.144050] wlan0: no IPv6 routers present
[   74.929057] wlan0: deauthenticating from 00:0f:f7:51:80:10 by local choice (reason=3)
[   74.981433] wlan0: authenticate with 00:0f:f7:57:9f:70 (try 1)
[   74.985225] wlan0: authenticated
[   74.985316] wlan0: associate with 00:0f:f7:57:9f:70 (try 1)
[   74.992937] wlan0: RX AssocResp from 00:0f:f7:57:9f:70 (capab=0x401 status=0 aid=102)
[   74.992949] wlan0: associated
[  115.335108] wlan0: deauthenticating from 00:0f:f7:57:9f:70 by local choice (reason=3)
[  115.403378] wlan0: authenticate with 00:0f:f7:51:80:10 (try 1)
[  115.406774] wlan0: authenticated
[  115.406876] wlan0: associate with 00:0f:f7:51:80:10 (try 1)
[  115.408640] wlan0: RX AssocResp from 00:0f:f7:51:80:10 (capab=0x401 status=0 aid=38)
[  115.408652] wlan0: associated
[  174.931668] wlan0: deauthenticating from 00:0f:f7:51:80:10 by local choice (reason=3)
[  175.008985] wlan0: authenticate with 00:0f:f7:57:9f:70 (try 1)
[  175.013948] wlan0: authenticated
[  175.014040] wlan0: associate with 00:0f:f7:57:9f:70 (try 1)
[  175.026498] wlan0: RX AssocResp from 00:0f:f7:57:9f:70 (capab=0x401 status=0 aid=103)
[  175.026510] wlan0: associated
[  254.915382] wlan0: deauthenticating from 00:0f:f7:57:9f:70 by local choice (reason=3)
[  254.975438] wlan0: authenticate with 00:0f:f7:51:80:10 (try 1)
[  254.980166] wlan0: authenticated
[  254.980254] wlan0: associate with 00:0f:f7:51:80:10 (try 1)
[  254.981987] wlan0: RX AssocResp from 00:0f:f7:51:80:10 (capab=0x401 status=0 aid=39)
[  254.981995] wlan0: associated
gilad@maya:~$ 
```

sudo cat /var/log/syslog | grep etwork | tail -n20

```
gilad@maya:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for gilad: 
Jul 16 10:15:53 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  completed -> associating
Jul 16 10:15:53 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jul 16 10:15:53 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  disconnected -> associated
Jul 16 10:15:53 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  associated -> completed
Jul 16 10:15:56 maya NetworkManager[830]: <info> (wlan0): roamed from BSSID 00:0F:F7:51:80:10 (attwifi) to 00:0F:F7:57:9F:70 (attwifi)
Jul 16 10:16:33 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  completed -> associating
Jul 16 10:16:33 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jul 16 10:16:33 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  disconnected -> associated
Jul 16 10:16:33 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  associated -> completed
Jul 16 10:16:38 maya NetworkManager[830]: <info> (wlan0): roamed from BSSID 00:0F:F7:57:9F:70 (attwifi) to 00:0F:F7:51:80:10 (attwifi)
Jul 16 10:17:33 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  completed -> associating
Jul 16 10:17:33 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jul 16 10:17:33 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  disconnected -> associated
Jul 16 10:17:33 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  associated -> completed
Jul 16 10:17:38 maya NetworkManager[830]: <info> (wlan0): roamed from BSSID 00:0F:F7:51:80:10 (attwifi) to 00:0F:F7:57:9F:70 (attwifi)
Jul 16 10:18:53 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  completed -> associating
Jul 16 10:18:53 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jul 16 10:18:53 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  disconnected -> associated
Jul 16 10:18:53 maya NetworkManager[830]: <info> (wlan0): supplicant connection state:  associated -> completed
Jul 16 10:18:56 maya NetworkManager[830]: <info> (wlan0): roamed from BSSID 00:0F:F7:57:9F:70 (attwifi) to 00:0F:F7:51:80:10 (attwifi)
gilad@maya:~$ 
```

thanks again for all the help!
-gilad

---

### Post by GiladGressel on 2011-07-16
just an update
i've been using the compat driver for 30 minutes now
it connects regularly now but does disconnect and reconnect every 8-10 minutes

the signal strength and speed are decent, youtube loads videos, but not completely although that could be the network strength (tested on my ipod touch, they also needed some time to load)

so the results today with compat are better than yesterday , although it is disconecting for no apparently reason, it does reconnect within a minute

-gilad

---

### Post by chili555 on 2011-07-16
> **GiladGressel said:**
> just an update
i've been using the compat driver for 30 minutes now
it connects regularly now but does disconnect and reconnect every 8-10 minutes

the signal strength and speed are decent, youtube loads videos, but not completely although that could be the network strength (tested on my ipod touch, they also needed some time to load)

so the results today with compat are better than yesterday , although it is disconecting for no apparently reason, it does reconnect within a minute

-giladIt disconnects and reconnects for a very apparent reason:> roamed from BSSID [COLOR="Red"]00:0F:F7:57:9F:70[/COLOR] (attwifi) to [COLOR="RoyalBlue"]00:0F:F7:51:80:10[/COLOR] (attwifi)
gilad@maya:~$There are at least two access points with the same SSID, attwifi and Network Manager is roaming from one to the other as it decides which is more suitable. You might do:```
sudo iwlist wlan0 scan
```Find out which of the several has the best quality, for example:> wlan0     Scan completed :
          Cell 01 - Address: 99:24:56:22:D7:99
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    [COLOR="Red"]Quality=70/70[/COLOR]  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"GBR1"Then Edit Connections in Network Manager and put its MAC address in BSSID; save and close. Please see attached. Please try both upper- and lower-case; e.g. 00:0F:F7:57:9F:70 or 00:0f:f7:57:9f:70. What we are trying to do is lock NM to a specific access point.

If that doesn't work, we can dig deeper. Notice the behavior is present in both driver versions. That suggests to me that the fault is not the driver but roaming in NM. NM is not yet perfect!

---

### Post by GiladGressel on 2011-07-16
ok i actually had about 6 "attwifi" to choose from.  I picked the highest quality (56/70) 

even if NM doesn't lock-down as you hope, it's good enough for me that it generally stays connected

i'm only in this hotel for a few more days.  I generally travel about 6months of the year so this is very helpful for me if I am in this situation again (quite possible).

I will have to wait until I need to use an encrypted network (home).  Previously the native driver did not sustain a connection when using a wpa or wpa2 password.

however, i won't be home till january so will have to find out then 

thanks again for all the help.  i'll mark this solved

-gilad

---

### Post by GiladGressel on 2011-07-16
ok so just kidding about being done with my questions

so i entered in the address (tried both upper and lower case now -- neither has solved the problem below)

it connects and then disconnects and reconnects etc (more frequently now every 30-60seconds)

when i open "edit connections" i see two entries for "auto attwifi"  one of them has the manual adress and the other has nothing entered.  it appears NM is re-creating attwifi in order to stay roaming?

suggestions?

also is there a command i can run to see what address i am currently connected to? 

-gilad

edit -- when i enter lowercase and save -- it automatically reopens when uppercase.
i tried deleting the autoattwifi that is being creating by NM, but it just comes back.

---

### Post by chili555 on 2011-07-16
> also is there a command i can run to see what address i am currently connected to?*iwconfig* will show, for example:> wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  [COLOR="Red"]Access Point: 99:24:56:22:D7:99   [/COLOR]
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
> when i open "edit connections" i see two entries for "auto attwifi" one of them has the manual adress and the other has nothing entered. Please try checking Connect Automatically on the one where you entered the BSSID. Make sure it is unchecked on the other. Does that help?

I am Googling roaming and Network Manager; you might do so as well.

---

### Post by GiladGressel on 2011-07-16
unchecking "connect automatically"  leaves NM connecting to nothing.

it see's attwifi available but will not connect.  

for whatever reason the attwifi I have designated an address for does not seem to appear as an option in the NM applet.

am also googling
thanks for the help
gilad

---

