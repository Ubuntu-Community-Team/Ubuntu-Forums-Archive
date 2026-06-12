---
title: "Sound not working after fresh 12.04 install"
date: 2012-05-05
forum: Multimedia Software
---

### Post by olliepa on 2012-05-05
I have recently installed 12.04, but the sound is not working from both internal speakers, and from headphones when I connect them.

I have followed the instructions at [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) to no avail and submitted a bug report. I've also tried running alsamixer and unmuting a few more things, but that didn't work.

I've tried to upgrade alsa sound drivers by running:

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
however on the last command:

```
$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-alsa-driver-modules-3.2.0-24-generic-pae
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.2.0-24-generic-pae'
```
What should I do to try get sound functioning?

It might be worth noting that 10.04 previously ran on this machine with no sound problems.

Thanks for any help.

EDIT: [same question on the ask ubuntu stackexchange]("http://askubuntu.com/questions/130809/sound-not-working-after-12-04-install#comment159603_130809")

---

### Post by Rodney9 on 2012-05-05
sudo apt-get install pavucontrol

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.


Rodney

---

### Post by Curtis6767 on 2012-05-05
Maybe all you need to do is type alsamixer in a terminal then make adjustments to the volume levels. Use your cursor keys to move around and adjust volumes. If something has an M at the bottom of the column then that means it's muted. Click on the M to highlight it and then use your 'm' key to unmute it.

If that doesn't work, then, as Rodney says, install Pulse Audio Volume Control, which you can get through the software center. 

You might also find this interesting: [http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html](http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html)

Hope this helps

---

### Post by olliepa on 2012-05-08
I installed PulseAudio and tried adjusting settings there, however that didn't help either :(

---

### Post by ayanstein on 2012-05-08
same problem here, at first I had 12.04 beta and did an update and the sound/audio no longer work, so I tried a fresh install and the audio doesnt work either, tried the troubleshooting instructions still no luck.

please help 
thanks :)

below are my lsmod and lspci outputs


lsmod output:
Module                  Size  Used by
dm_crypt               22528  1 
bnep                   17830  2 
rfcomm                 38139  12 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
uvcvideo               67203  0 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
videodev               86588  1 uvcvideo
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25424  1 snd_seq_midi
btusb                  17912  2 
snd_seq_midi_event     14475  1 snd_seq_midi
bluetooth             158438  23 bnep,rfcomm,btusb
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath5k                 145127  0 
psmouse                72919  0 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
samsung_laptop         13353  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19387  1 ath5k
mac_hid                13077  0 
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  414603  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
sky2                   53628  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915


lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

---

### Post by Tech226 on 2012-05-08
It might be beneficial if you posted the outputs of lsmod & lspci.

---

### Post by ayanstein on 2012-05-08
> **Tech226 said:**
> It might be beneficial if you posted the outputs of lsmod & lspci.

thank you, edited post :)

---

### Post by Tech226 on 2012-05-08
In System Settings -> Sound -> Output tab, what is selected in "Play sound through"?

---

### Post by olliepa on 2012-05-08
Here's my lsmod and lspci output

lsmod:

Module                  Size  Used by
parport_pc             32114  0 
rfcomm                 38139  12 
ppdev                  12849  0 
bnep                   17830  2 
vesafb                 13516  1 
arc4                   12473  2 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
joydev                 17393  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10962290  42 
ath9k                 117326  0 
mac80211              436455  1 ath9k
snd_timer              28931  2 snd_pcm,snd_seq
usbhid                 41906  0 
btusb                  17912  2 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
hid                    77367  1 usbhid
mac_hid                13077  0 
sony_laptop            39681  0 
ath9k_common           13781  1 ath9k
uvcvideo               67203  0 
bluetooth             158438  23 rfcomm,bnep,btusb
ath9k_hw              391523  2 ath9k,ath9k_common
serio_raw              13027  0 
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
r592                   17808  0 
videodev               86588  1 uvcvideo
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               15857  1 r592
cfg80211              178679  3 ath9k,mac80211,ath
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36570  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e1000e                140005  0 

lspci:

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
03:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

---

### Post by ayanstein on 2012-05-08
> **Tech226 said:**
> In System Settings -> Sound -> Output tab, what is selected in "Play sound through"?

there is only one option,
Speakers
*Built in Audio*

---

### Post by olliepa on 2012-05-08
> **Tech226 said:**
> In System Settings -> Sound -> Output tab, what is selected in "Play sound through"?

Speakers, but all of the output selections fail to result in sound.

---

### Post by Tech226 on 2012-05-09
Have you tried the following command?

```
ubuntu-bug audio
```

---

### Post by beaucoder on 2012-05-09
Hi Guyz,

Fresh 12.04 install on an Intel HDA motherboard with Intel processor.  AND NO SOUND!!!???!!!

If you have an intel HDA chip (Realtek ALC8887) which you can see in the gnome-alsa-mixer installed from the Ubuntu Software Center. Just run the app and look in the tabs.

From the Webupd8.org folks: Fix HDA Intel ALC887 no sound issue in Ubuntu 10.10 Maverick Meerkat:

sudo gedit /etc/modprobe.d/alsa-base.conf

then add this line at bottom: options snd-hda-intel model=generic

Save the file. Reboot and try your sound. Make sure your alsa-mixer sound settings are ON. 

Shazzam!!!  Tunes!!!!! 

HTH,

Kenneth "beaucoder"
 in Sugar Creek where life is sweet, mostly.

---

### Post by ayanstein on 2012-05-09
> **beaucoder said:**
> Hi Guyz,

Fresh 12.04 install on an Intel HDA motherboard with Intel processor.  AND NO SOUND!!!???!!!

If you have an intel HDA chip (Realtek ALC8887) which you can see in the gnome-alsa-mixer installed from the Ubuntu Software Center. Just run the app and look in the tabs.

From the Webupd8.org folks: Fix HDA Intel ALC887 no sound issue in Ubuntu 10.10 Maverick Meerkat:

sudo gedit /etc/modprobe.d/alsa-base.conf

then add this line at bottom: options snd-hda-intel model=generic

Save the file. Reboot and try your sound. Make sure your alsa-mixer sound settings are ON. 

Shazzam!!!  Tunes!!!!! 

HTH,

Kenneth "beaucoder"
 in Sugar Creek where life is sweet, mostly.

I tried doing these instructions but audio still won't work sir, is audio an issue on 12.04?

Thank you for the help and reply sir

---

### Post by olliepa on 2012-05-12
> **beaucoder said:**
> Hi Guyz,

Fresh 12.04 install on an Intel HDA motherboard with Intel processor.  AND NO SOUND!!!???!!!

If you have an intel HDA chip (Realtek ALC8887) which you can see in the gnome-alsa-mixer installed from the Ubuntu Software Center. Just run the app and look in the tabs.

From the Webupd8.org folks: Fix HDA Intel ALC887 no sound issue in Ubuntu 10.10 Maverick Meerkat:

sudo gedit /etc/modprobe.d/alsa-base.conf

then add this line at bottom: options snd-hda-intel model=generic

Save the file. Reboot and try your sound. Make sure your alsa-mixer sound settings are ON. 

Shazzam!!!  Tunes!!!!! 

HTH,

Kenneth "beaucoder"
 in Sugar Creek where life is sweet, mostly.

Man from sugar creek - Thankyou. This problem was on my parents computer at their house so it took me a few days to get over and try it. It's mother's day and mum's the only one that needs sound so a lovely present.

If you have an ask ubuntu account, go here [http://askubuntu.com/questions/130809/sound-not-working-after-12-04-install](http://askubuntu.com/questions/130809/sound-not-working-after-12-04-install) and claim the bounty I set on the question by answering there.

---

### Post by Heaphy on 2012-05-15
Hi, I too have just freshly installed 12.04 and had an issue with making sound work.
Spent the last day looking through the internet to find people  having the same experiences and seeing if they could fix it. Thus  finding this post.

I went into alsamixer via terminal and un-muted a few things but had no luck with that (though it could have helped with my end result)

Then I saw this:
> **Tech226 said:**
> In System Settings -> Sound -> Output tab, what is selected in "Play sound through"?

I also found that there was only one option: the built in audio.
Since I was in the sound settings, I decided to have a peek around and play with some settings to try and fix the problem.

In system settings -> sound -> Hardware Tab I went to 'settings  for the selected device' and changed it from Analog Stereo Duplex, to  Analog Stereo Input. (I actually just flicked through each setting to  see if there were any changes)
Setting it to Analog Stereo Input made it immediately work perfectly.

It all almost seemed too easy.
I hope this helps you too if you have not fixed it already :)

---

### Post by h8theman on 2013-03-06
Beaucoder! Dude!!! You are the best. Worked like a charm. Thank you so much!

---

### Post by h8theman on 2013-03-06
Beaucoder! Dude!!! You are the best. Worked like a charm. Thank you so much!

---

