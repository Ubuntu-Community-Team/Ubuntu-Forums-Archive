---
title: "Lubuntu and Linksys WUSB54Gv2 Wifi USB adapter"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by scy on 2013-04-12
[COLOR=#222222][FONT=Times][SIZE=2][FONT=verdana]Hello everyone!

I am having real trouble trying to get my Wifi adapter to work. I just got it used with no cd's or anything, and I want to get wifi on my lubuntu desktop with it. When I plug it in, though, the power light turns on but it is not recognized as a wifi device and I can't get any wifi on it. Currently I am on an ethernet card.

However, I have no idea how to get it to work and all of the tutorials on how to do it are really confusing. I am a total newbie so can someone hold my hand and walk me thru the steps to set it up?

I am ok using the command line and ndiswrapper if I have to.

Thanks so much!![/FONT][/SIZE][/FONT][/COLOR]

---

### Post by zrdc28 on 2013-04-13
First thing "**sudo lsusb**" and see if it is recognized by the system, it should be close to the bottom.  No ndiswrapper needed 

Next do a "**sudo lsmod**" This is a list of modules loaded at startup, look for rt2500usb or rt2800 ?? and you can tell if it is loaded.
If it is not loaded do a "**sudo modprobe rt2500usb**" and check it again with lsmod!

If the module is loaded do a  "**sudo iwconfig**" If you see a wlan0 with a bunch or info you are nearly home.

Now you can go to networkmanager and put in info and you should be ready to go.

---

### Post by scy on 2013-04-13
Thanks zdrc28!

So far I am stuck at step 4.

I did **lsusb** and got:

```
lsusb
Bus 001 Device 003: ID 13b1:000a Linksys WUSB54G v2 802.11g Adapter [Intersil ISL3887]
Bus 003 Device 002: ID 045e:00e5 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Then I did **lsmod** and got:

```
lsmod
Module                  Size  Used by
snd_emu10k1_synth      13008  0 
snd_emux_synth         33484  1 snd_emu10k1_synth
snd_seq_virmidi        13221  1 snd_emux_synth
snd_seq_midi_emul      13444  1 snd_emux_synth
snd_emu10k1           132518  1 snd_emu10k1_synth
snd_intel8x0           33107  1 
snd_ac97_codec        105652  2 snd_emu10k1,snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
snd_seq_midi           13133  0 
snd_pcm                80235  3 snd_emu10k1,snd_intel8x0,snd_ac97_codec
emu10k1_gp             12542  0 
snd_util_mem           13822  2 snd_emux_synth,snd_emu10k1
gameport               15017  2 emu10k1_gp
snd_rawmidi            25383  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_hwdep              13273  2 snd_emux_synth,snd_emu10k1
snd_seq_midi_event     14476  2 snd_seq_virmidi,snd_seq_midi
snd_seq                51281  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              24412  3 snd_emu10k1,snd_pcm,snd_seq
microcode              18210  0 
snd_seq_device         14138  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62146  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
serio_raw              13032  0 
soundcore              14600  1 snd
snd_page_alloc         14037  3 snd_emu10k1,snd_intel8x0,snd_pcm
lpc_ich                16926  0 
shpchp                 32190  0 
i915                  457241  2 
rfcomm                 37277  0 
bnep                   17708  2 
parport_pc             31969  1 
ppdev                  12818  0 
drm_kms_helper         47304  1 i915
bluetooth             183270  10 rfcomm,bnep
drm                   238811  3 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
mac_hid                13038  0 
video                  18895  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
floppy                 55445  0 
tulip                  52171  0 
```

Then i did **sudo modprobe rt2500usb. **This had no output.

Then I did **lsmod** again and got:
```
lsmod
Module                  Size  Used by
rt2500usb              22384  0 
rt2x00usb              19980  1 rt2500usb
rt2x00lib              48602  2 rt2500usb,rt2x00usb
mac80211              461261  2 rt2x00usb,rt2x00lib
cfg80211              175574  2 rt2x00lib,mac80211
snd_emu10k1_synth      13008  0 
snd_emux_synth         33484  1 snd_emu10k1_synth
snd_seq_virmidi        13221  1 snd_emux_synth
snd_seq_midi_emul      13444  1 snd_emux_synth
snd_emu10k1           132518  1 snd_emu10k1_synth
snd_intel8x0           33107  1 
snd_ac97_codec        105652  2 snd_emu10k1,snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
snd_seq_midi           13133  0 
snd_pcm                80235  3 snd_emu10k1,snd_intel8x0,snd_ac97_codec
emu10k1_gp             12542  0 
snd_util_mem           13822  2 snd_emux_synth,snd_emu10k1
gameport               15017  2 emu10k1_gp
snd_rawmidi            25383  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_hwdep              13273  2 snd_emux_synth,snd_emu10k1
snd_seq_midi_event     14476  2 snd_seq_virmidi,snd_seq_midi
snd_seq                51281  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              24412  3 snd_emu10k1,snd_pcm,snd_seq
microcode              18210  0 
snd_seq_device         14138  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62146  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
serio_raw              13032  0 
soundcore              14600  1 snd
snd_page_alloc         14037  3 snd_emu10k1,snd_intel8x0,snd_pcm
lpc_ich                16926  0 
shpchp                 32190  0 
i915                  457241  2 
rfcomm                 37277  0 
bnep                   17708  2 
parport_pc             31969  1 
ppdev                  12818  0 
drm_kms_helper         47304  1 i915
bluetooth             183270  10 rfcomm,bnep
drm                   238811  3 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
mac_hid                13038  0 
video                  18895  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
floppy                 55445  0 
tulip                  52171  0 

```

But then I did **sudo iwconfig** and got:
```
sudo iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.

```

What should I do now, because there is nothing on wlan0?

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by scy on 2013-04-13
Uh ok. What do these commands do??

---

### Post by scy on 2013-04-13
The output for the first command was
```
sudo lshw -C network
[sudo] password for administrator: 
  *-network DISABLED      
       description: Ethernet interface
       product: LNE100TX [Linksys EtherFast 10/100]
       vendor: Lite-On Communications Inc
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 25
       serial: 00:a0:cc:34:a0:87
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:21 ioport:2000(size=256) memory:c4000000-c40000ff memory:20000000-2000ffff

```

And the second command produced no output.

thanks for your time!

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by scy on 2013-04-13
Thanks for the help, allhallubuntu.

I'll get back in a bit about what you suggested.

Some people were using WPA/WEP or something. After I install the drivers, is there a gui involved in logging into wifi networks? I assume the driver won't log you into my wifi?

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by scy on 2013-04-13
OK. That makes sense :)

---

### Post by scy on 2013-04-14
ahallubuntu, I installed the linux-firmware-nonfree package and it has made no difference. IWCONFIG gives the same results.

---

### Post by scy on 2013-04-14
Well, I went out on a limb and tried:

```
modprobe -r p54usb
sudo modprobe p54usb
lsmod
```

And it's working! No idea how that worked but I'm glad it does!

However, I have 2 things that I want to have happen. Firstly, when I reboot I have to run these commands every time, so if there is a way to have the modprobe stay permanent that would be great. Secondly, can I have my computer automatically log into the network when I log in?

Thanks to everyone who helped me so far because I'm not sure who asked me to do the right commands :D

---

### Post by ahallubuntu on 2013-04-14
~

---

### Post by scy on 2013-04-14
ahallubuntu, lubuntu automatically remembers the network too! My wifi is blazing fast now!!

Thanks so much! :grin:

---

