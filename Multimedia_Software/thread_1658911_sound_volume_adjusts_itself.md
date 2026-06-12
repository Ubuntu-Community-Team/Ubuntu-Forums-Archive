---
title: "sound volume adjusts itself"
date: 2011-01-03
forum: Multimedia Software
---

### Post by bmwheaven on 2011-01-03
Hi,

Since a few days my audio volume adjusts itself while listening music (rythmbox) or watching a movie (vlc). Anyone else have these problems? It's really really annoying. 

My system:
Ubuntu 10.04, 64 bit on intel i5
sound card: VIA VT1828S (onboard Asus P7P55D-E mainboard)

Thanks

---

### Post by lidex on 2011-01-03
Try resetting your pulseaudio configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

Any updates just prior to this happening?

---

### Post by bmwheaven on 2011-01-04
I think the system has updated to the latest version:
Ubuntu 10.04.1 LTS
Kernel 2.6.32-27-generic

As for the code: 2x[COLOR=Red] "No such file or directory"[/COLOR]
I did install ALSA Mixer, that might be the reason your code isn't working?

---

### Post by lidex on 2011-01-04
So no help then?

---

### Post by bmwheaven on 2011-01-04
No help? I could use some, sound is still going up and down in volume (right now even on internetradio)

---

### Post by sevenenemy on 2011-01-04
> **bmwheaven said:**
> I think the system has updated to the latest version:
Ubuntu 10.04.1 LTS
Kernel 2.6.32-27-generic

As for the code: 2x[COLOR=Red] "No such file or directory"[/COLOR]
I did install ALSA Mixer, that might be the reason your code isn't working?

Try upgrading to 10.10. 

solved all my problems from 10.04

---

### Post by lidex on 2011-01-04
Quik way to get newest alsa modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by bmwheaven on 2011-01-04
Ok, updated to 10.10 and installed latest version of alsamixer (0.9.7)

So far: still the same problem.
In alsamixer F6, F3, F4, etc don't work...

Is there any other way to setup alsamixer correctly?

---

### Post by lidex on 2011-01-04
Next let's try this.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-digout  
```
Save. Close. Reboot. 
Check your levels in alsamixer.
If you can't figure out alsamixer try gnome-alsamixer.
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```
If that doesn't help use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by bmwheaven on 2011-01-05
Here is the link:

[http://www.alsa-project.org/db/?f=9f42de7d3c9e2f192b4793cb483de46b028cc1d4](http://www.alsa-project.org/db/?f=9f42de7d3c9e2f192b4793cb483de46b028cc1d4)


Thanks for your help!

---

### Post by lidex on 2011-01-05
OK. Now remove the edit to alsa-base.conf that we made earlier. Reboot and then post this output please:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

I think you're on to something with the codec confusion. HDMI and default soundcard are using the same module.

---

### Post by bmwheaven on 2011-01-05
this is what I get:
```
[   12.344242]   alloc kstat_irqs on node -1
[   12.344248] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.344408]   alloc irq_desc for 53 on node -1
[   12.344410]   alloc kstat_irqs on node -1
[   12.344417] HDA Intel 0000:00:1b.0: irq 53 for MSI/MSI-X
[   12.344435] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.344439] ALSA hda_intel.c:2561: chipset global capabilities = 0x4401
[   12.419886] ALSA hda_intel.c:914: codec_mask = 0x1
[   12.420023] ALSA hda_intel.c:1354: codec #0 probed OK
[   12.443646] ALSA hda_codec.c:4630: autoconfig: line_outs=4 (0x24/0x25/0x26/0x27/0x0)
[   12.443649] ALSA hda_codec.c:4634:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.443652] ALSA hda_codec.c:4638:    hp_outs=1 (0x28/0x0/0x0/0x0/0x0)
[   12.443654] ALSA hda_codec.c:4639:    mono: mono_out=0x0
[   12.443655] ALSA hda_codec.c:4642:    dig-out=0x2d/0x2e
[   12.443657] ALSA hda_codec.c:4643:    inputs:
[   12.443659] ALSA hda_codec.c:4647:  Front Mic=0x29
[   12.443661] ALSA hda_codec.c:4647:  Rear Mic=0x2b
[   12.443662] ALSA hda_codec.c:4647:  Line=0x2a
[   12.443664] ALSA hda_codec.c:4647:  CD=0x2c
[   12.443665] ALSA hda_codec.c:4649: 
[   12.447524] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.447671]   alloc irq_desc for 54 on node -1
[   12.447672]   alloc kstat_irqs on node -1
[   12.447680] HDA Intel 0000:01:00.1: irq 54 for MSI/MSI-X
[   12.447698] HDA Intel 0000:01:00.1: setting latency timer to 64
[   12.447701] ALSA hda_intel.c:2561: chipset global capabilities = 0x1001
[   12.479535] ALSA hda_intel.c:914: codec_mask = 0x1
[   12.479783] ALSA hda_intel.c:1354: codec #0 probed OK
[   12.482705] HDMI: sink_present = 0, eld_valid = 1
[   12.510506] usb 3-2: new SuperSpeed USB device using xhci_hcd and address 2
--
[   13.418563] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   13.488548] ALSA hda_intel.c:707: azx_get_response timeout, polling the codec once: last cmd=0x002f0d00
[   13.538984] scsi 9:0:0:0: Direct-Access     ADATA    NH01             0000 PQ: 0 ANSI: 2
--
[   17.921948] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   18.011587] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.011628] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[   18.031341] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.031363] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[   18.031961] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   18.032114] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   18.033738] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   18.033786] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[   18.033797] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   18.033813] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x1, channel=0, format=0x4011
[   18.040820] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.040824] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.040826] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.040829] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.040831] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.041016] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.041019] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.041021] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.041023] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.041026] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.041268] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.041272] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.041275] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.041278] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.041281] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.041585] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.041589] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.041591] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.041593] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.041595] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.041793] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.041796] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.041798] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.041800] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.041803] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.041993] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.041995] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.041997] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.041999] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.042001] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.042205] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.042207] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.042210] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.042212] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.042214] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.042469] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.042471] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.042473] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.042475] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.042477] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.042663] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.042666] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.042668] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.042670] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.042672] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.042823] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.042825] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.042827] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.042829] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.042831] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.043034] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.043037] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.043039] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.043041] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.043043] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.043298] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.043301] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.043303] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.043305] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.043307] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.043492] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.043495] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.043497] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.043499] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.043501] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.043683] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.043685] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.043687] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.043689] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.043691] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.043895] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.043897] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.043899] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.043902] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.043904] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.044173] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.044176] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.044179] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.044181] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.044183] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.044370] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.044372] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.044374] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.044376] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.044378] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.044558] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.044561] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.044563] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.044565] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.044568] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.044774] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.044777] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.044779] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.044782] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.044784] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.045061] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.045064] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.045066] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.045069] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.045071] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.045498] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.045507] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x5, channel=0, format=0x4011
[   18.061513] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4011
[   18.081504] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4011
[   18.101468] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=0, format=0x4011
[   18.121433] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=0, format=0x4011
[   18.140838] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4011
[   18.160762] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.160779] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x5, channel=0, format=0x4011
[   18.160787] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4011
[   18.160792] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4011
[   18.160798] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=0, format=0x4011
[   18.160804] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=0, format=0x4011
[   18.160809] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4011
[   18.161042] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.161252] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.161510] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.161780] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.162201] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.162208] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   18.180723] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.180731] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   18.180756] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.180766] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.181247] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.200981] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.220966] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.222870] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   18.240956] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.260618] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.280587] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   18.300687] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.300691] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.300694] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.300696] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.300698] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.301198] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x6e80, format=0x4013
[   18.301206] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   18.301208] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4013
[   18.320482] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4013
[   18.340453] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=2, format=0x4013
[   18.360483] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=0, format=0x4013
[   18.381017] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4013
[   18.401005] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x6e80, format=0x4013
[   18.401014] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   18.401016] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4013
[   18.401019] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4013
[   18.401021] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=2, format=0x4013
[   18.401023] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=0, format=0x4013
[   18.401026] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4013
[   18.401248] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.401437] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.401663] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.401961] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.402323] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.402330] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   18.402342] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.402348] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   18.402359] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.402366] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.402767] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.421307] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.441273] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.461207] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.481179] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.501167] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.501171] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.501174] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.501179] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.501182] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.501721] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   18.501729] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   18.501732] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4015
[   18.520181] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4015
[   18.540549] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=2, format=0x4015
[   18.560428] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=4, format=0x4015
[   18.580704] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4015
[   18.600688] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   18.600695] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   18.600698] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4015
[   18.600700] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4015
[   18.600702] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=2, format=0x4015
[   18.600704] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=4, format=0x4015
[   18.600706] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4015
[   18.600914] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.601122] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.601343] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.601590] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.601930] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.601936] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   18.601948] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.601954] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   18.601963] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.601969] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.602314] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.620659] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.640281] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.660864] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.680847] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.700829] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.700833] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.700836] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.700838] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.700840] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.701415] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   18.701423] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   18.701426] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4015
[   18.720739] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4015
[   18.740740] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=2, format=0x4015
[   18.760297] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=4, format=0x4015
[   18.780338] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4015
[   18.800393] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   18.800401] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   18.800404] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4015
[   18.800406] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4015
[   18.800409] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=2, format=0x4015
[   18.800411] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=4, format=0x4015
[   18.800413] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4015
[   18.800651] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.800840] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.801058] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.801338] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.801703] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.801710] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   18.801722] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   18.801728] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   18.801737] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.801744] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   18.802150] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.820223] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.840224] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.860193] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.880167] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.900173] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   18.900177] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   18.900179] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   18.900181] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   18.900184] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   18.900724] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   18.900732] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   18.900735] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4015
[   18.920072] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4015
[   18.940022] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=2, format=0x4015
[   18.959936] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=4, format=0x4015
[   18.979935] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4015
[   18.999926] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xa500, format=0x4015
[   18.999937] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   18.999944] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4015
[   18.999950] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4015
[   18.999955] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=2, format=0x4015
[   18.999961] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=4, format=0x4015
[   18.999967] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4015
[   19.000372] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.000687] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.001012] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.001309] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.001676] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.001682] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   19.001694] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.001699] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   19.001709] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.001715] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.002068] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   19.019900] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   19.039843] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   19.059829] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   19.079702] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   19.100013] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   19.100016] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   19.100018] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   19.100020] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   19.100022] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   19.100623] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xdc80, format=0x4017
[   19.100631] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   19.100633] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4017
[   19.119617] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4017
[   19.139647] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=2, format=0x4017
[   19.159619] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=4, format=0x4017
[   19.179536] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=6, format=0x4017
[   19.199538] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0xdc80, format=0x4017
[   19.199602] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   19.199609] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4017
[   19.199614] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4017
[   19.199620] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=2, format=0x4017
[   19.199626] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=4, format=0x4017
[   19.199631] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=6, format=0x4017
[   19.199946] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.200277] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.200616] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.200913] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.201362] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.201369] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   19.201381] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.201387] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   19.201397] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.201436] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.201833] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   19.217195] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   19.219445] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   19.248796] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   19.268753] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   19.288694] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   19.308865] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   19.308868] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   19.308870] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   19.308873] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   19.308875] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   19.309340] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.309348] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x8, channel=0, format=0x4011
[   19.338634] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xf, stream=0x8, channel=0, format=0x4011
[   19.358569] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.358581] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x8, channel=0, format=0x4011
[   19.358587] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xf, stream=0x8, channel=0, format=0x4011
[   19.358858] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.359050] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.359257] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.359521] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.359876] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.359883] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   19.359895] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.359900] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   19.359908] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.359914] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.360272] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.360274] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.360442] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.360444] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.360681] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.360684] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.360899] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.360901] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.361150] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.361152] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.361452] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.361454] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.361674] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.361676] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.361890] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.361892] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.362141] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.362143] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.362442] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.362444] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.362664] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.362666] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.362881] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.362883] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.363132] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.363134] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.363432] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.363435] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.363654] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.363656] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.363871] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.363873] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.364170] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.364173] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.364573] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.364575] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.364796] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.364798] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.365016] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.365018] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.365267] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.365269] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.365568] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xe
[   19.365570] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0xf
[   19.366581] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.366769] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.366984] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.367246] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.367609] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.367616] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   19.367628] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   19.367634] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   19.367643] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.367651] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   19.368924] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   19.368934] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x5, channel=0, format=0x4011
[   19.369001] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4011
[   19.389373] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4011
[   19.409396] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=0, format=0x4011
[   19.429292] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=0, format=0x4011
[   19.458297] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4011
[   19.468933] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   19.468943] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x5, channel=0, format=0x4011
[   19.468946] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4011
[   19.468949] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4011
[   19.468951] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=0, format=0x4011
[   19.468953] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=0, format=0x4011
[   19.468956] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4011
[   19.476678] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   19.476686] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   19.476698] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   19.476704] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x1, channel=0, format=0x4011
[   19.957971] UDF-fs: Partition marked readonly; forcing readonly mount
[   20.016515] UDF-fs INFO UDF: Mounting volume 'Naamloos', timestamp 2005/11/21 08:25 (103c)
[   24.507873] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   24.507886] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   24.508783] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   24.508808] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   32.607621] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   32.622116] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   32.642075] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   32.662004] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   32.681988] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[   32.701967] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[   32.722198] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[   32.722201] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[   32.722203] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[   32.722205] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[   32.722207] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[  106.553013] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  106.553029] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x5, channel=0, format=0x4011
[  106.564118] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4011
[  106.584122] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4011
[  106.604049] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=0, format=0x4011
[  106.624064] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=0, format=0x4011
[  106.644028] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4011
[  106.664017] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  106.664030] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x5, channel=0, format=0x4011
[  106.664037] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x5, channel=0, format=0x4011
[  106.664043] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x5, channel=0, format=0x4011
[  106.664049] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x5, channel=0, format=0x4011
[  106.664054] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x5, channel=0, format=0x4011
[  106.664060] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x5, channel=0, format=0x4011
[  113.074124] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[  113.093989] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[  113.113995] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[  113.134032] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[  113.154001] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
[  113.173971] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xe, stream=0x0, channel=0, format=0x0
[  113.194129] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x8, stream=0x0, channel=0, format=0x0
[  113.194137] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x0, channel=0, format=0x0
[  113.194143] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xa, stream=0x0, channel=0, format=0x0
[  113.194149] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xb, stream=0x0, channel=0, format=0x0
[  113.194155] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0xc, stream=0x0, channel=0, format=0x0
```

---

### Post by bmwheaven on 2011-03-06
I thought: lets just wait and see if the problem solves itself: it doesn't.
I still have the same problem, can someone help me out?

---

