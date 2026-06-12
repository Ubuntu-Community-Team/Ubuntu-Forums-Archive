---
title: "No sound, cannot fix, help please :("
date: 2010-08-27
forum: Multimedia Software
---

### Post by northerndude81 on 2010-08-27
Hi, I cannot get sounds of any kind to play on my machine. I tried the Comprehensive Sound Guide, but did not get very far. (I'm not very proficient with these things.) I did lspci -v and got:

```
 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: Micro-Star International Co., Ltd. Device 4570
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

...but I cannot find my sound card on the ASLA site. I tried to follow the Sound Guide instructions after that, but I got lost. Can anyone help?

Thanks.

---

### Post by northerndude81 on 2010-08-28
Anyone? I'm in 10.04. It's no fun without sound! :(

---

### Post by cchhrriiss121212 on 2010-08-28
Does aplay -l give you anything?

---

### Post by northerndude81 on 2010-08-28
It gives me this:

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

...but I have no idea what it means. :( Can you help?

---

### Post by northerndude81 on 2010-08-28
Ok, I typed:

```
sudo modprobe snd-
```

into the terminal and I got:

```
snd-ac97-codec           snd-hdsp                 snd-seq-midi-emul
snd-ad1816a              snd-hdspm                snd-seq-midi-event
snd-ad1848               snd-hifier               snd-seq-oss
snd-ad1889               snd-hrtimer              snd-seq-virmidi
snd-adlib                snd-hwdep                snd-serial-u16550
snd-ak4114               snd-i2c                  snd-sgalaxy
snd-ak4117               snd-ice1712              snd-sis7019
snd-ak4xxx-adda          snd-ice1724              snd-soc-ad1836
snd-ali5451              snd-ice17xx-ak4xxx       snd-soc-ad1938
snd-als100               snd-indigo               snd-soc-ad73311
snd-als300               snd-indigodj             snd-soc-ak4104
snd-als4000              snd-indigodjx            snd-soc-ak4535
snd-atiixp               snd-indigoio             snd-soc-ak4642
snd-atiixp-modem         snd-indigoiox            snd-soc-core
snd-au8810               snd-intel8x0             snd-soc-cs4270
snd-au8820               snd-intel8x0m            snd-soc-l3
snd-au8830               snd-interwave            snd-soc-max9877
snd-aw2                  snd-interwave-stb        snd-soc-pcm3008
snd-azt2320              snd-korg1212             snd-soc-spdif
snd-azt3328              snd-layla20              snd-soc-ssm2602
snd-bt87x                snd-layla24              snd-soc-tlv320aic23
snd-ca0106               snd-lx6464es             snd-soc-tlv320aic26
snd-cmi8330              snd-maestro3             snd-soc-tlv320aic3x
snd-cmipci               snd-mia                  snd-soc-twl4030
snd-cs4231               snd-miro                 snd-soc-uda134x
snd-cs4236               snd-mixart               snd-soc-uda1380
snd-cs4281               snd-mixer-oss            snd-soc-wm8350
snd-cs46xx               snd-mona                 snd-soc-wm8400
snd-cs5530               snd-mpu401               snd-soc-wm8510
snd-cs5535audio          snd-mpu401-uart          snd-soc-wm8523
snd-cs8427               snd-msnd-classic         snd-soc-wm8580
snd-ctxfi                snd-msnd-lib             snd-soc-wm8728
snd-darla20              snd-msnd-pinnacle        snd-soc-wm8731
snd-darla24              snd-mtpav                snd-soc-wm8750
snd-dt019x               snd-mts64                snd-soc-wm8753
snd-dummy                snd-nm256                snd-soc-wm8776
snd-echo3g               snd-opl3-lib             snd-soc-wm8900
snd-emu10k1              snd-opl3sa2              snd-soc-wm8903
snd-emu10k1-synth        snd-opl3-synth           snd-soc-wm8940
snd-emu10k1x             snd-opl4-lib             snd-soc-wm8960
snd-emu8000-synth        snd-opl4-synth           snd-soc-wm8961
snd-emux-synth           snd-opti92x-ad1848       snd-soc-wm8971
snd-ens1370              snd-opti92x-cs4231       snd-soc-wm8974
snd-ens1371              snd-opti93x              snd-soc-wm8988
snd-es1688               snd-oxygen               snd-soc-wm8990
snd-es1688-lib           snd-oxygen-lib           snd-soc-wm8993
snd-es18xx               snd-page-alloc           snd-soc-wm9081
snd-es1938               snd-pcm                  snd-soc-wm-hubs
snd-es1968               snd-pcm-oss              snd-sonicvibes
snd-es968                snd-pcsp                 snd-sscape
snd-fm801                snd-pcxhr                snd-tea575x-tuner
snd-gina20               snd-pdaudiocf            snd-tea6330t
snd-gina24               snd-portman2x4           snd-timer
snd-gusclassic           snd-pt2258               snd-trident
snd-gusextreme           snd-rawmidi              snd-usb-audio
snd-gus-lib              snd-riptide              snd-usb-caiaq
snd-gusmax               snd-rme32                snd-usb-lib
snd-hda-codec            snd-rme96                snd-usb-us122l
snd-hda-codec-analog     snd-rme9652              snd-usb-usx2y
snd-hda-codec-atihdmi    snd-sb16                 snd-util-mem
snd-hda-codec-ca0110     snd-sb16-csp             snd-via82xx
snd-hda-codec-cirrus     snd-sb16-dsp             snd-via82xx-modem
snd-hda-codec-cmedia     snd-sb8                  snd-virmidi
snd-hda-codec-conexant   snd-sb8-dsp              snd-virtuoso
snd-hda-codec-idt        snd-sbawe                snd-vx222
snd-hda-codec-intelhdmi  snd-sb-common            snd-vx-lib
snd-hda-codec-nvhdmi     snd-sc6000               snd-vxpocket
snd-hda-codec-realtek    snd-seq                  snd-wavefront
snd-hda-codec-si3054     snd-seq-device           snd-wss-lib
snd-hda-codec-via        snd-seq-dummy            snd-ymfpci
snd-hda-intel            snd-seq-midi 
```

...But I'm not sure which one of those matches my sound card, if any of them even do. To be honest, I don't really understand the information on the ALSA website.

Can anyone tell me what to do from here?

---

### Post by genuine-pia on 2010-08-28
Have you tried the preferences, when you right click on the sound icon,mine was playing sound but it set so low I could not hear it. Also you can down load codes for audio from the software cent or package manager.
Your driver set for your hardware is also an option install as third party driver.

---

### Post by northerndude81 on 2010-08-28
Yes, I've checked all that, but thank you. All the settings are correct and I've downloaded the restricted drivers and whatnot from the package manager.

Still not able to get any sound at all. :(

Anyone else have any ideas?

---

### Post by jmfal on 2010-08-28
Welcome to ubuntu

Your sound module is at the bottom of the list>snd-hda-intel<
you can try this in terminal:

  ```
  sudo modprobe snd-hda-intel
```

play some music, if no joy, there is a thread in this section of the forum by markbuntu:snd-hda intel options database.

this may help as you may have to edit/add to the alsa conf.  file

---

### Post by lidex on 2010-08-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by northerndude81 on 2010-08-28
Ok, I have no idea what that did, but here's the link:

[http://www.alsa-project.org/db/?f=606ab69fcd96c676bfa0a75b9eef892d1b6fcb90]("http://www.alsa-project.org/db/?f=606ab69fcd96c676bfa0a75b9eef892d1b6fcb90")

Please let me know what to do next. Thanks for your help!

---

### Post by northerndude81 on 2010-08-28
> **jmfal said:**
> Welcome to ubuntu

Your sound module is at the bottom of the list>snd-hda-intel<
you can try this in terminal:

  ```
  sudo modprobe snd-hda-intel
```

play some music, if no joy, there is a thread in this section of the forum by markbuntu:snd-hda intel options database.

this may help as you may have to edit/add to the alsa conf.  file

I tried your command but it didn't work for me. :(

Again, the link from lidex's suggestion is:

[http://www.alsa-project.org/db/?f=606ab69fcd96c676bfa0a75b9eef892d1b6fcb90]("http://www.alsa-project.org/db/?f=606ab69fcd96c676bfa0a75b9eef892d1b6fcb90")

:confused:

---

### Post by lidex on 2010-08-28
Try an alsa upgrade. Use the link in my sig.

---

### Post by northerndude81 on 2010-08-28
I followed all of the upgrade instructions, but the sound STILL doesn't work! :confused:

What can I do at this point? Any suggestions?

---

### Post by MasterNetra on 2010-08-28
Well probably not the same sound card in question you could try what is suggested in post #6 in this thread: [http://ubuntuforums.org/showthread.php?t=1388295](http://ubuntuforums.org/showthread.php?t=1388295) only for the package in step 3 you'll want to switch karmic to lucid. But maybe one or more of those three things will help.

You may need to restart for one or more of those changes to take effect.

---

### Post by lidex on 2010-08-28
Next do this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=targa 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

If that doesn't work, try another model. Select from these:
```
targa-dig
targa-2ch-dig
3stack-dig
```

Don't install backports at this stage.

---

### Post by northerndude81 on 2010-08-28
MasterNerta,

Thanks, I tried steps 1 and 2 suggested in that post, but they didn't do anything.

I would like to try step 3, but I do not know how to install the "linux-backports-modules-alsa-lucid-generic" package. Can I do it from Synaptic or do I need a command line?

Edit: I'm going to try lidex's suggestions now...

---

### Post by northerndude81 on 2010-08-28
Wow, lidex, the step you provided worked! After all that, feels great to have it working. :D

Thanks to all who helped me! I will mark this thread "solved."

---

