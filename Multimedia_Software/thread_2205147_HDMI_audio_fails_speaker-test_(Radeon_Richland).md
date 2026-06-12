---
title: "HDMI audio fails speaker-test (Radeon Richland)"
date: 2014-02-12
forum: Multimedia Software
---

### Post by Jugdish on 2014-02-12
[SIZE=3][FONT=arial]Hi guys, I'm a first-time Ubuntu user, and just finished installing Saucy to my new machine. Everything seems to be running fine except I cannot get HDMI audio to work no matter what I try.

My system has an integrated AMD Radeon Richland APU. The Onboard audio is working fine (tested with headphones). The HDMI audio is enabled in BIOS, and it's listed in aplay -l and in the Sound Settings dialog. But it's not making a peep, and when I run a speaker-test I get the following error:

```

$ speaker-test -l 4 -c 2 -r 48000 -D hw:0,3

speaker-test 1.0.27.1

Playback device is hw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Home directory not accessible: Permission denied
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
[B]Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Input/output error[/B]

```

I've read many suggestions for possible fixes, but none have worked for me. Here's a rundown of what I've tried:
[/FONT][/SIZE]
[LIST]
[*][SIZE=3][FONT=arial]Ensure HDMI is unmuted in alsamixer
[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]Update alsa to latest daily build. I'm now running oem-audio-hda-daily-dkms - 0.201402110705~ubuntu13.10.1 downloaded from launchpad
[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]Update video driver from radeon to fglrx (catalyst 13.12). Initially HDMI audio was not listed among outputs under Sound Settings (although it was shown in aplay -l), but after installing fglrx driver, now HDMI audio is listed in Sound Settings.
[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]Checked volume and settings in PulseAudio Volume Control - set HDMI audio to be the fallback output.
[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]Updated grub as per this thread: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)[/FONT][/SIZE]
[/LIST]
[SIZE=3][FONT=arial]
Here are details about my system. Happy to provide further output if it's helpful, just let me know. Thanks very much for any help you can provide!

```

$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
[/FONT][/SIZE]```
$ dmesg | grep HDMI

[   11.201380] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input5
```[FONT=arial]
[/FONT]```
$ cat /proc/asound/cards


 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xff744000 irq 52
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xff740000 irq 16
```

[SIZE=3][FONT=arial]```
$ cat /proc/asound/version 

Advanced Linux Sound Architecture Driver Version k3.11.0-15-generic
```
[/FONT][/SIZE]```
$ lsmod | grep snd

snd_hda_codec_realtek    57495  1
snd_hda_codec_generic    68274  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     46433  1
snd_seq_midi           13324  0
snd_hda_intel          52306  5
snd_hda_codec         137465  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
```
[FONT=arial]```
$ lspci -nn | grep VGA[/FONT]

[FONT=arial]00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Richland [1002:999c][/FONT]
```
[SIZE=3][FONT=arial]```
$ sudo lshw -c video

  *-display
       description: VGA compatible controller
       product: Richland
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:53 memory:c0000000-cfffffff ioport:f000(size=256) memory:ff700000-ff73ffff
```
```
$ cat /etc/X11/xorg.conf

Section "Device"
 Identifier "ATI radeon 8650"
 Driver "fglrx"
EndSection
```

[/FONT][/SIZE]

---

### Post by zenisekc on 2014-02-15
I had/have the same problem with the AMD Richland A10 APU, which includes the AMD Radeon HD 8670, part of the "sea islands" family.

First, I installed the [AMD Catalyst drivers]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD"). I got audio over HDMI, but then hardware acceleration was not working in Google Chrome. (You can check at chrome://gpu.) After investigating that further, I knew I had to switch back to the open source driver. However, performance is [greatly enhanced]("http://www.phoronix.com/scan.php?page=article&item=amd_gallium3d_hd8670d&num=4") by the proprietary drivers.

You can enable audio over HDMI in the open source "[radeon]("http://xorg.freedesktop.org/wiki/RadeonFeature/#22")" driver for AMD cards by making the following Grub edit:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"
```
[http://askubuntu.com/questions/364135/no-hdmi-audio-on-radeon-6770-connected-via-hdmi-to-my-tv](http://askubuntu.com/questions/364135/no-hdmi-audio-on-radeon-6770-connected-via-hdmi-to-my-tv)
This is an easy edit, and it would be great if it worked for Richland, but for me, it did not produce the desired result. Although I can't find the link now, I read a page that said HDMI audio was not supported for the "sea islands" family on the open source radeon driver, even with the Grub edit. I assume we might just need to wait for updates.

---

### Post by Jugdish on 2014-02-15
Thanks for the reply. I'm running the A10-6700T APU which I *think* has Radeon HD 8650D, although Linux identifies it as "[COLOR=#000000][FONT=arial][AMD/ATI] Richland [1002:999c]" in lspci.
[/FONT][/COLOR]
I've tried rolling back to the open source radeon driver and doing the grub update, but this didn't fix anything.

It would be great if you could find the link that definitively says the radeon driver does not support HDMI audio with Radeon HD 8000 series. But even so, I would expect the latest catalyst driver to support it!

---

### Post by Jugdish on 2014-02-17
Turns out the problem was in the kernel. After upgrading the kernel to 3.13, I now have working HDMI audio! Video playback was a bit jerky with the open source radeon driver, so I installed the Catalyst 14.1 beta driver, and all is good now.

If you want to get a fix for HDMI audio with your Radeon HD 8000 graphics, you can upgrade your kernel to 3.13 now or wait for Trusty in April.

---

### Post by tho.tran1809 on 2014-02-19
> **Jugdish said:**
> Turns out the problem was in the kernel. After upgrading the kernel to 3.13, I now have working HDMI audio! Video playback was a bit jerky with the open source radeon driver, so I installed the Catalyst 14.1 beta driver, and all is good now.

If you want to get a fix for HDMI audio with your Radeon HD 8000 graphics, you can upgrade your kernel to 3.13 now or wait for Trusty in April.


Can you tell me how to upgrade to kernel 3.13? I'm using Ubuntu 13.10 with kernel 3.11.
And also, I'm using Catalyst 13, but do not know how to uninstall it.

I've to install Catalyst 14 after upgrade to kernel 3.13, right? Pls help me details instruction.

Thanks!

---

### Post by Jugdish on 2014-02-19
> **tho.tran1809 said:**
> Can you tell me how to upgrade to kernel 3.13? I'm using Ubuntu 13.10 with kernel 3.11.
And also, I'm using Catalyst 13, but do not know how to uninstall it.

I've to install Catalyst 14 after upgrade to kernel 3.13, right? Pls help me details instruction.

Thanks!

Instructions for removing Catalyst 13: [http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx)

To upgrade to kernel 3.13, go here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.3-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.3-trusty/)
Download 3 debs: (1) linux-headers-*_all.deb, plus the (2) linux-headers-*-generic and (3) linux-image-*-generic corresponding to your arch (i386/amd64)
Install the 3 debs by:
```

cd /path/where/you/downloaded/the/debs
sudo dpkg -i *.deb

```
and reboot.

Instructions for installing Catalyst 14 beta: [http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

---

