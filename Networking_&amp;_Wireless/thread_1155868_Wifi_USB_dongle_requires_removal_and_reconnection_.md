---
title: "Wifi USB dongle requires removal and reconnection after the PC is suspended"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by glubbdrubb on 2009-05-11
I am using an Intel based desktop to connect to my local Wifi network.

I use the "Suspend" feature quite a lot when I am not  using my PC for any significant length of time. However, after typing in my password when bringing it out of "suspension", it will not reconnect to the network automatically or manually. 

I have to unplug and re-plug the USB wifi dongle. It then connects automatically.

I am using a Canyon 802.11 g model with the ubuntu provided drivers.

I am glad that it is just a USB dongle or else I would need to get into the guts to fiddle with the PCI card :)

---

### Post by eldragon on 2009-05-11
im not quite sure what does ubuntu uses to suspend, so this might not apply but its worth trying.

first, identify your wireless kernel module (google a bit, use lsusb, etc)

once you have identified the module, create a file called 12modules under /etc/pm/sleep.d and paste this text inside: 
```

#!/bin/bash

	case "$1" in
		hibernate|suspend)
                        rmmod <your module> #insert your module's name
			;;
		thaw|resume)
			modprobe <your module> #insert your module's name
			sleep 1
			;;
		*)
			;;
	esac

```
modify it to include your wireless module.

then you have to make it executable for it to work

i had to do something like this in order to be able to suspend since the config line in pm-suspend used to ignore modules does not work for me.

what this script does, is remove the included modules before suspend, and inserts them later. during resume. hope it helps.


if this does not help, simply delete the file created.

---

### Post by glubbdrubb on 2009-05-11
Well... it did not work but I suspect I did not do it correctly. 
I am battling to figure out what the kernel mode is called. I used lsusb and lsmod but did not find it or recognize it. So I tried to disable the usb kernel module, and that did not correct the problem either. 

Any thoughts?

Should I file a bug perhaps? These are the sorts of things that will keep the Masses away from linux in general. They may be relatively easy to fix but until Ubuntu works perfectly "out of the box", we wont be reaching 5% for a while.

</rant>

---

### Post by cottfcfan on 2009-05-11
ive just solved the exact same problem after weeks.
If you could post what wireless card you are using or what the driver is I might be able to help.

---

### Post by glubbdrubb on 2009-05-11
It is a Ralink USB Wireless Adapter. How would I figure out what drivers it uses? I seem to remember that when I installed it, it work almost immediately (I think). I am using the "Restricted Drivers" that Ubuntu installed when I plugged in my nVidia card. I think it just downloaded more drivers for the wfi dongle.

---

### Post by cottfcfan on 2009-05-11
Go into a terminal, Type lsmod and paste the output here.
 Or give the exact model and number of your wireless adaptor.

---

### Post by glubbdrubb on 2009-05-11
Here you go:

Module                  Size  Used by
isofs                  40228  0 
udf                    88484  0 
aes_i586               15744  2 
aes_generic            35880  1 aes_i586
binfmt_misc            16904  1 
rfcomm                 44560  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
vboxnetflt             92296  0 
vboxdrv               119080  1 vboxnetflt
ipv6                  263972  18 
ppdev                  15748  0 
af_packet              25728  4 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  4 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
container              11520  0 
pci_slot               12680  0 
video                  25232  0 
output                 11008  1 video
sbshc                  13440  1 sbs
wmi                    14504  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
parport_pc             39332  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_hda_intel         384176  7 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
rt73usb                30464  0 
crc_itu_t              10112  2 udf,rt73usb
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
rt2500usb              27904  0 
rt2x00usb              18816  2 rt73usb,rt2500usb
rt2x00lib              36224  3 rt73usb,rt2500usb,rt2x00usb
rfkill                 17176  1 rt2x00lib
snd_rawmidi            29824  1 snd_seq_midi
led_class              12164  1 rt2x00lib
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
mac80211              216820  2 rt2x00usb,rt2x00lib
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               32392  2 rt2x00lib,mac80211
nvidia               7082420  44 
snd                    63268  22 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               31892  1 nvidia
intel_agp              33724  0 
soundcore              15328  1 snd
serio_raw              13444  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
evdev                  17696  6 
iTCO_wdt               18596  0 
psmouse                45200  0 
pcspkr                 10624  0 
shpchp                 38036  0 
iTCO_vendor_support    11652  1 iTCO_wdt
pci_hotplug            34976  1 shpchp
button                 14224  0 
agpgart                42184  2 nvidia,intel_agp
ext3                  133256  2 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  6 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
pata_jmicron           11136  0 
ata_piix               24708  4 
ohci1394               37936  0 
libata                178208  4 pata_acpi,ata_generic,pata_jmicron,ata_piix
iee


Edit: sorry it did not come out nicely..

---

### Post by cottfcfan on 2009-05-11
OK looks like were in business, its the same driver as mine. rt73usb.
 Open a terminal type "sudo gedit" followed by your password.
 An unsaved document comes up.
Paste in this line- SUSPEND_MODULES=rt73usb
 Click "file" at the top. "save as", then "file system" on the left.
 Then in the main box double click "etc", "pm" and "config.d".
In the name at the top call it "madwifi" and finally click save.
 That should be it.
Suspend and resume and see what happens.
 Let me know if there is a problem.

---

### Post by glubbdrubb on 2009-05-11
IT WORKED!

Thanks for the help. That is now my second last annoyance fixed.

I am quite surprised that the networking modules aren't suspended when you put the PC into suspension anyway.

I am surprised that the monitor switches off with out my intervention. :o

I guess it must be a driver issue..

---

### Post by cottfcfan on 2009-05-12
Glad it worked.
Hoped my post was clear enough.
Ive been wrestling with this for weeks, and I know many others are having the same problem.
Workarounds are so simple, when they work!!

---

### Post by intangodelta on 2009-07-28
Hi, I just wanted to add that this worked for me on my Advent 4214 netbook, in case anyone is searching for a solution like I've been doing for many hours!

Thanks!

---

### Post by gearond on 2009-12-29
Thank you very much for the executabgle script solution. It seemed like the best one to try off the bat, and it worked great, once I remebered to make it executable :-) I'm a developer, and I really need the ablilty to hibernate and have my files all whre I was when I stopeed. (Stupid Bluefish editor wonj'[t remeber where it was,. Gotta switch to JAVA based Eclipse soon).

Again, THANK YOU.

---

### Post by mehturt on 2010-02-03
Guys, can you connect to a WPA2 network after suspend/resume?  Because that's my problem with rt73usb device.

---

### Post by glubbdrubb on 2010-02-04
Follow the advise that was given to me earlier in the thread. That will solve your problem as it solved mine.

---

### Post by mehturt on 2010-02-04
I think I tried this before but it did not work for me.. but I'll try again tonight.

---

### Post by glubbdrubb on 2010-02-04
> **cottfcfan said:**
> OK looks like were in business, its the same driver as mine. rt73usb.
 Open a terminal type "sudo gedit" followed by your password.
 An unsaved document comes up.
Paste in this line- SUSPEND_MODULES=rt73usb
 Click "file" at the top. "save as", then "file system" on the left.
 Then in the main box double click "etc", "pm" and "config.d".
In the name at the top call it "madwifi" and finally click save.
 That should be it.
Suspend and resume and see what happens.
 Let me know if there is a problem.

That should do it

---

### Post by mehturt on 2010-02-04
yes, it seems to work now - thanks!

---

### Post by manicmoddin on 2010-04-14
:P Woop!

you seem to have cured my problem too in Karmic with an Archos 10

Many thanks

Jimmy

---

### Post by spicysomtam on 2012-09-18
The fix in #2 works for me on ub 12.04 with a rubbish Belkin wireless N router and a atheros wifi adapter (kernel module ath9k). Thanks for the help!

---

### Post by overdrank on 2012-09-18
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

