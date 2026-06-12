---
title: "Intel Corporation PRO/Wireless 2200BG not working in Ubuntu 12.04.1 on Thinkpad T43"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by eestet75 on 2012-11-01
Hello all,

My wireless networking device does not work properly. Here is some information that might be of use to you, if you want to me:

 My computer is a IBM Thinkpad T43 and I'm running the 32-bit version of Ubuntu.
```
johan@johan-ThinkPad-T43:~$ iwconfig && ifconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

eth0      Link encap:Ethernet  HWaddr 00:16:41:12:e2:45  
          inet addr:192.168.1.160  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:41ff:fe12:e245/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:372111 errors:1 dropped:0 overruns:0 frame:3
          TX packets:228464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:512791476 (512.7 MB)  TX bytes:24959545 (24.9 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1152586 (1.1 MB)  TX bytes:1152586 (1.1 MB)

```No wireless interface is up. Only eth0.
Modules:
```
johan@johan-ThinkPad-T43:~$ lsmod | grep ipw2200
ipw2200               146241  0 
libipw                 46701  1 ipw2200
cfg80211              178679  2 ipw2200,libipw
lib80211               14040  2 ipw2200,libipw

```And here is the real error - in kernel boot.
```
johan@johan-ThinkPad-T43:~$ dmesg | grep ipw2200
[   28.076130] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   28.076134] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   28.076255] ipw2200 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   28.076284] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   29.505031] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   29.505037] ipw2200: Unable to load firmware: -2
[   29.505043] ipw2200: failed to register network device
[   29.505086] ipw2200 0000:04:02.0: PCI INT A disabled
[   29.505131] ipw2200: probe of 0000:04:02.0 failed with error -5

```Network configuration:
PCI (sysfs)

It worked fine before I upgraded Ubuntu,

Any ideas of what the problem might be? :-s

---

### Post by chili555 on 2012-11-01
> ipw2200-bss.fw request_firmware failed: Reason -2Does the firmware exist?```
ls -al /lib/firmware/ipw2200-bss.fw
```May we also see:```
dmesg | grep -e 80211 -e ipw
rfkill list all
```

---

### Post by eestet75 on 2012-11-01
> **chili555 said:**
> Does the firmware exist?```
ls -al /lib/firmware/ipw2200-bss.fw
```May we also see:```
dmesg | grep -e 80211 -e ipw
rfkill list all
```

```
ls -al /lib/firmware/ipw2200-bss.fw
```
Doesn't exist; no such file or catalog

```
johan@johan-ThinkPad-T43:~$ dmesg | grep -e 80211 -e ipw
[   28.052249] lib80211: common routines for IEEE802.11 drivers
[   28.052253] lib80211_crypt: registered algorithm 'NULL'
[   28.055646] cfg80211: Calling CRDA to update world regulatory domain
[   28.068727] libipw: 802.11 data/management/control stack, git-1.1.13
[   28.068731] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   28.076130] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   28.076134] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   28.076255] ipw2200 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   28.076284] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   29.502976] cfg80211: World regulatory domain updated:
[   29.502980] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.502984] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.502987] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.502991] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.502994] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.502998] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.505031] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   29.505037] ipw2200: Unable to load firmware: -2
[   29.505043] ipw2200: failed to register network device
[   29.505086] ipw2200 0000:04:02.0: PCI INT A disabled
[   29.505131] ipw2200: probe of 0000:04:02.0 failed with error -5
[15838.860285] Modules linked in: pcmcia joydev snd_intel8x0 snd_ac97_codec ac97_bus thinkpad_acpi snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i915 psmouse yenta_socket snd pcmcia_rsrc nsc_ircc serio_raw soundcore pcmcia_core snd_page_alloc irda nvram bnep ppdev rfcomm bluetooth drm_kms_helper binfmt_misc parport_pc drm crc_ccitt mac_hid i2c_algo_bit video ipw2200 libipw cfg80211 lib80211 lp parport tg3 floppy
[15844.520071] Modules linked in: pcmcia joydev snd_intel8x0 snd_ac97_codec ac97_bus thinkpad_acpi snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i915 psmouse yenta_socket snd pcmcia_rsrc nsc_ircc serio_raw soundcore pcmcia_core snd_page_alloc irda nvram bnep ppdev rfcomm bluetooth drm_kms_helper binfmt_misc parport_pc drm crc_ccitt mac_hid i2c_algo_bit video ipw2200 libipw cfg80211 lib80211 lp parport tg3 floppy

```

Could it be that I'm missing the ipw2200-bss.fw file?

---

### Post by chili555 on 2012-11-01
> Could it be that I'm missing the ipw2200-bss.fw file?I reckon so. Please hook up the ethernet and do:```
sudo apt-get install linux-firmware
sudo modprobe -r ipw2200
sudo modprobe ipw2200
```Now is it working?

---

### Post by eestet75 on 2012-11-02
> **chili555 said:**
> I reckon so. Please hook up the ethernet and do:```
sudo apt-get install linux-firmware
sudo modprobe -r ipw2200
sudo modprobe ipw2200
```Now is it working?

```
johan@johan-ThinkPad-T43:~$ sudo apt-get install linux-firmware
Password: 
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
linux-firmware er i forvejen den nyeste version.
0 opgraderes, 0 nyinstalleres, 0 afinstalleres og 0 opgraderes ikke.
johan@johan-ThinkPad-T43:~$ sudo modprobe -r ipw2200
johan@johan-ThinkPad-T43:~$ sudo modprobe ipw2200

```It does nothing and just tells me that linux-firmware is already the newest version.
Should I try to reinstall linux-firmware?
[I]Tried that, didn't work.

What now?
[/I]

---

### Post by chili555 on 2012-11-02
Please download the attached file to your desktop. Right-click it and select 'Extract Here.' Then, in a terminal, do:```
sudo cp Desktop/2200/* /lib/firmware
```Now reboot with the ethernet detached and tell us if it's working. If not, please post:```
dmesg | grep ipw
```'Desktop' may be named differently in your language. Substitute as necessary.

---

### Post by eestet75 on 2012-11-02
> **chili555 said:**
> Please download the attached file to your desktop. Right-click it and select 'Extract Here.' Then, in a terminal, do:```
sudo cp Desktop/2200/* /lib/firmware
```Now reboot with the ethernet detached and tell us if it's working. If not, please post:```
dmesg | grep ipw
```'Desktop' may be named differently in your language. Substitute as necessary.

Yes, that seems to have worked. Thanks! :)
-----------------------------------------------------------
FYI I'm an experienced Linux user. I've been using it for about 3 years, though without any driver problems.

---

### Post by chili555 on 2012-11-02
Please use thread tools at the top and mark Solved. The searchers will appreciate it.

Glad it's working!

---

### Post by krakenchaos on 2012-11-05
Just want to say Thanks! It helped me. You rocks chili555! :guitar:

---

### Post by bweinel on 2013-08-16
I'm having the same issue with an Intel 2200 BG wireless adapter in Kubuntu 13.04. lshw reports the card is there and being seen by the system but is 'unclaimed'. dmesg reports the kernel is unable to load the ipw2200 firmware (error -5). I have tried all the above suggested steps to remedy the issue, but still no luck. :(

---

### Post by chili555 on 2013-08-16
> **bweinel said:**
> I'm having the same issue with an Intel 2200 BG wireless adapter in Kubuntu 13.04. lshw reports the card is there and being seen by the system but is 'unclaimed'. dmesg reports the kernel is unable to load the ipw2200 firmware (error -5). I have tried all the above suggested steps to remedy the issue, but still no luck. :(Let's see some diagnostics:```
dmesg | grep ipw
ls /lib/firmware | grep ipw
```Thanks.

---

### Post by bweinel on 2013-08-16
> **chili555 said:**
> Let's see some diagnostics:```
dmesg | grep ipw
ls /lib/firmware | grep ipw
```Thanks.

Sounds good...

dmesg | grep ipw

```

[   17.287815] libipw: 802.11 data/management/control stack, git-1.1.13
[   17.287823] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.313396] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   17.313408] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.313626] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.551391] ipw2200: Unable to load ucode: -22
[   17.551429] ipw2200: Unable to load firmware: -22
[   17.552631] ipw2200: probe of 0000:03:06.0 failed with error -5

```

ls /lib/firmware | grep ipw

```

ipw2100-1.3.fw
ipw2100-1.3-i.fw
ipw2100-1.3-p.fw
ipw2200-bss.fw
ipw2200-ibss.fw
ipw2200-sniffer.fw

```


cheers,
Bill

---

### Post by chili555 on 2013-08-16
> [   17.551391] ipw2200: Unable to load ucode: -22
[   17.551429] ipw2200: Unable to load firmware: -22
[   17.552631] ipw2200: probe of 0000:03:06.0 failed with error -5I have seen this several times. In few cases, it was actually solved. Here are my suggestions.

Fully update your system:```
sudo apt-get update && sudo apt-get -y upgrade
```I hope you will get a newer kernel version, known in Ubuntu-land as linux-image. If so, reboot and see if the newer kernel fixes it.

Reset your BIOS to defaults. See if that fixes it.

Unload and reload the driver:```
sudo modprobe -r ipw2200 && sudo modprobe ipw2200
```Any improvement?

Check that the permission of your firmware files are correct:```
ls -al /lib/firmware | grep ipw
```It ought to be:```
-rw-r--r--  1 root root  209190 Nov  8  2012 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 Nov  8  2012 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 Nov  8  2012 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 Nov  8  2012 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 Nov  8  2012 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 Nov  8  2012 ipw2200-sniffer.fw
```...which is to say, readable by all. If not, try to fix it:```
sudo chmod +r /lib/firmware/ipw*
sudo modprobe -r ipw2200 && sudo modprobe ipw2200
```Any improvement?```
dmesg | grep ipw
```Look for later timestamps than above.

Finally, I wonder if the hardware is defective.

---

### Post by bweinel on 2013-08-19
> **chili555 said:**
> I have seen this several times. In few cases, it was actually solved. Here are my suggestions.

Fully update your system:```
sudo apt-get update && sudo apt-get -y upgrade
```I hope you will get a newer kernel version, known in Ubuntu-land as linux-image. If so, reboot and see if the newer kernel fixes it.


Ok. I ran an update/upgrade and didn't get anything newer than what I'm currently running. 

> 
Reset your BIOS to defaults. See if that fixes it.

Unload and reload the driver:```
sudo modprobe -r ipw2200 && sudo modprobe ipw2200
```Any improvement?


Gave this a go to... still no improvement.

> 
Check that the permission of your firmware files are correct:```
ls -al /lib/firmware | grep ipw
```It ought to be:```
-rw-r--r--  1 root root  209190 Nov  8  2012 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 Nov  8  2012 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 Nov  8  2012 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 Nov  8  2012 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 Nov  8  2012 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 Nov  8  2012 ipw2200-sniffer.fw
```...which is to say, readable by all. If not, try to fix it:```
sudo chmod +r /lib/firmware/ipw*
sudo modprobe -r ipw2200 && sudo modprobe ipw2200
```Any improvement?```
dmesg | grep ipw
```Look for later timestamps than above.


All looks good here as well. Permissions are all correct and the timestamps are correct as well.

> Finally, I wonder if the hardware is defective.

Yeah... that's what I'm thinking at this point as well. :( I think I'm going to try for a replacement card and see if that clears it up.

Thanks for your suggestions and help!

cheers,
bill

---

### Post by bweinel on 2013-08-26
Ok ....just a quick update on my 2200BG troubles. On the suspicion that my hardware was bad, I replaced my existing card. I booted up the machine and everything is now working. 
Looks like we nailed it....  :guitar: 

Thanks for all the help and suggestions on this issue.

cheers,
bill

---

### Post by chili555 on 2013-08-26
I'm glad it's working by whatever means. I'm also glad you posted your outcome. I hope it will help some searchers.

---

