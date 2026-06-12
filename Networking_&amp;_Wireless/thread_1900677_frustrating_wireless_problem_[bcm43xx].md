---
title: "frustrating wireless problem [bcm43xx]"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by cham423 on 2011-12-26
hey guys, 

my frustrating problem is with my wireless card (obviously since i'm posting in this forum)

the card is a broadcom 4318

01:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

And the problem is that the wireless works, after configuring it with ndisgtk (windows wireless drivers app), but after rebooting, the device comes up as unclaimed. 

after rebooting, ndiswrapper says the device is installed, but it doesn't work, I can't connect to or view any wireless networks.

I have spent hours searching for the solution, and have installed ndiswrapper, as well as numerous drivers, including the new oneric ocelot fix for broadcom drivers that has recently been posted in the forums.

If anyone could help me, that would be awesome.

some additional information: my blacklist file is empty, and my additional drivers module says "no proprietary drivers are in use on this system"

thank you in advance if anyone helps me!!

---

### Post by wildmanne39 on 2011-12-26
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by cham423 on 2011-12-27
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
[Thanks


ok! 
cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux millie-pc 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

lspci -nnk | grep -iA2 net

01:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: COMPAL Electronics Inc Device [14c0:0012]
    Kernel driver in use: 8139too
--
01:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)
    Subsystem: Broadcom Corporation Device [14e4:044a]
    Kernel driver in use: ndiswrapper

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:CF:30:88:49:B0   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

note: this is after configuring with ndisgtk....it won't have wlan0 after I reboot. (should I post that code too?)

rfkill list all
it returned nothing. I tried sudo-ing it as well. it just gives me another user@userpc line

lsmod

wl                   2646601  0 
lib80211               14570  1 wl
ndiswrapper           193669  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 39822  0 
psmouse                73673  0 
serio_raw              12990  0 
i915                  505159  3 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
drm_kms_helper         32889  1 i915
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
8139too                23283  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
8139cp                 22636  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


once again, this is with a working wireless connection. after rebooting, it will act like it doesn't have a wireless adapter at all.

If you want, I can post the results from those commands after rebooting as well

---

### Post by wildmanne39 on 2011-12-27
Hi, ndiswrapper is not needed and you also have another driver installed for your card that is not needed so let's get rid of both of them and install the correct driver and it should work.

One these codes one line at a time.
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a

```
Then do:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
watch for error and it is done disconnect your wired connection and reboot.
Thanks

---

### Post by cham423 on 2011-12-27
ok, thanks!

Ran all of those commands, and did exactly what you said, and I still can't get on wireless. there is no wlan0 connection on the laptop and I can't see or connect to any networks. both of those packages installed without errors, and the commands all ran without errors, except it couldn't remove the ndiswrapper.conf because it said it didn't exist. 

what should I do now?

---

### Post by collisionystm on 2011-12-27
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by wildmanne39 on 2011-12-27
Hi, please post:
```
ndiswrapper -l
```
```
lsmod | grep b43
```
when you ran the remove ndiswrapper command did you just copy and paste each one? 

There are five lines to run of that command one at a time because you have ndisdwrapper installed and it should have removed it and that is a problem you can not get it working until it and the other driver is gone.
Thanks

---

### Post by dave2012 on 2011-12-27
I have a similar problem and I have unistalled ndiswrapper but still cannot get wireless connection. Any other tips?

---

### Post by dave2012 on 2011-12-27
I have a similar problem and I have unistalled ndiswrapper but still cannot get wireless connection. Any other tips? I have an AMD computer but I'm not sure how to check the specs in ubuntu 11.10.

---

### Post by wildmanne39 on 2011-12-27
Hi, please start your own thread so you can get the help you need and so can the original poster of this thread, you can post the first set of commands from this thread in your thread and post a link here and I will take a look.
Thanks

---

### Post by dave2012 on 2011-12-27
> **wildmanne39 said:**
> Hi, please start your own thread so you can get the help you need and so can the original poster of this thread, you can post the first set of commands from this thread in your thread and post a link here and I will take a look.
Thanks
My apologies, I'm new to ubuntu and forums in general so I don't know how to create a new thread. I tried but it seems I do not have permissions yet.

---

### Post by wildmanne39 on 2011-12-27
Hi, I am including a screenshot, it should be a matter of just clicking on the new thread icon, if it does not work run the commands I gave in the first post and post them here.

Sometimes you have to try more then once because of an error but it happens very rarely.
Thanks

---

### Post by dave2012 on 2011-12-27
> **wildmanne39 said:**
> Hi, I am including a screenshot, it should be a matter of just clicking on the new thread icon, if it does not work run the commands I gave in the first post and post them here.

Sometimes you have to try more then once because of an error but it happens very rarely.
Thanks

Thanks! I created a new thread [http://ubuntuforums.org/showthread.php?p=11569090#post11569090](http://ubuntuforums.org/showthread.php?p=11569090#post11569090)

---

### Post by cham423 on 2011-12-28
> **wildmanne39 said:**
> Hi, please post:
```
ndiswrapper -l
``````
lsmod | grep b43
```when you ran the remove ndiswrapper command did you just copy and paste each one? 

There are five lines to run of that command one at a time because you have ndisdwrapper installed and it should have removed it and that is a problem you can not get it working until it and the other driver is gone.
Thanks

ndiswrapper -l

The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

lsmod | grep b43

there was no output. does that mean the drivers didn't install right?

---

### Post by wildmanne39 on 2011-12-28
Hi please try:
```
sudo modprobe b43
```

It is possible that the driver did not install correctly or it just did not load.

If the command above does not turn it on please post.
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by bkratz on 2011-12-28
@wildmanne39, sorry to interrupt but I notice that the op also has the sta driver installed (wl in lsmod) besides ndiswrapper, if that helps (blacklist issues?).

---

### Post by wildmanne39 on 2011-12-28
Hi bkratz, I noticed that too, I thought I had posted the command to remove it but I was working with another person with the same problem and I must have only posted it in that thread and not here, thank you I appreciate the help.

@cham423 please run this command:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
If it does not come on then post the output of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

