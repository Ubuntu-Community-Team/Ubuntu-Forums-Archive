---
title: "sound doesn't work after upgrading"
date: 2010-05-24
forum: Multimedia Software
---

### Post by CHNdonny on 2010-05-24
Hi,Friends in ubuntu:

    I am encountered with the problem that sound doesn't work after the distribution upgrade from 8.04 to 10.04

    I checked the sound panel,it seems that the sound device couldn't be identified. please see the pic 1,2,3 for details:

    [IMG]http://donny.blog.ubuntu.org.cn/files/2010/05/sound1.png[/IMG]

    [IMG]http://donny.blog.ubuntu.org.cn/files/2010/05/sound2.png[/IMG]

    [IMG]http://donny.blog.ubuntu.org.cn/files/2010/05/sound3.png[/IMG]

    afterwards, I checked the sound related sofeware I have installed,please see the pic 4,5 for details:

    I reinstalled these softwares,but it turned out to be in vain

    [IMG]http://donny.blog.ubuntu.org.cn/files/2010/05/software1.png[/IMG]

    [IMG]http://donny.blog.ubuntu.org.cn/files/2010/05/software2.png[/IMG]

    Then I taped the command to check if the sound modules had been reloaded:
>     lsmod | grep snd
snd_intel8x0           25588  0 
snd_usb_audio          75765  0 
snd_usb_lib            15658  1 snd_usb_audio
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_hwdep               5412  1 snd_usb_audio
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_dummy           1338  0 
snd_pcm                70662  4 snd_intel8x0,snd_usb_audio,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  12 snd_intel8x0,snd_usb_audio,snd_ac97_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm

snd_intel8x0 seems to be not working? 

> lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
05:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

```
uname -a
Linux desktop 2.6.32-22-generic #35-Ubuntu SMP Tue Jun 1 14:17:36 UTC 2010 i686 GNU/Linux

```


```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

```
head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

```
MY PC: CPU: AMD SEMPRON64 3000+   MAIN BOARD: EP0X 8NPAJ nVidia nForce4 4x Chipset
```

How can I resolve this Problem, your great assistance is appreciated , Thank you!

---

### Post by mojo2012 on 2010-05-24
I had a similar problem. Pulseaudio simply hanged and didn't load my config. Something in my ~/.pulse* config files were currupt. I deleted the whole folder from another account, then logged in and then all worked fine again.

---

### Post by Bucky Ball on 2010-05-24
Applications->Sound and Video->Pulseaudio Device Chooser. When the icon appears in the toolbar, left click and choose Volume manager.

What devices have you got in there?

Also, run this in a terminal and post the result:

```
lspci
```

---

### Post by CHNdonny on 2010-05-24
> **mojo2012 said:**
> I had a similar problem. Pulseaudio simply hanged and didn't load my config. Something in my ~/.pulse* config files were currupt. I deleted the whole folder from another account, then logged in and then all worked fine again.


Thank you for your reply! but I have tried that, but it's ineffective

---

### Post by CHNdonny on 2010-05-24
> **Bucky Ball said:**
> Applications->Sound and Video->Pulseaudio Device Chooser. When the icon appears in the toolbar, left click and choose Volume manager.

What devices have you got in there?

Also, run this in a terminal and post the result:

```
lspci
```

thank you for your reply!

I can't find Pulseaudio Device Chooser

and i add pci information into  floor #1 it seems to be all right

---

### Post by CHNdonny on 2010-05-25
does anyone know the answer?

---

### Post by wasabishot on 2010-06-05
Same problem here..
reinstalling pulseaudio solved it just until next restart.

happened since updating the system yesterday.

help?!

---

### Post by CHNdonny on 2010-06-05
> **wasabishot said:**
> Same problem here..
reinstalling pulseaudio solved it just until next restart.

happened since updating the system yesterday.

help?!
thank you very much,I did the complete removal,and reinstalled them according to your means.but it's strange that the problem remains

---

### Post by lidex on 2010-06-05
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by CHNdonny on 2010-06-06
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

HI,
thank you for reply,I have posted the outcome at deck #1, please take a look.

---

### Post by lidex on 2010-06-06
I'm seeing a lot of issues with nvidia chipsets in lucid. One solution was switching to x32 from x64. Another was uninstalling proprietary video driver and using open-source. Have you upgraded to latest alsa - 1.0.23?

---

### Post by CHNdonny on 2010-06-07
> **lidex said:**
> I'm seeing a lot of issues with nvidia chipsets in lucid. One solution was switching to x32 from x64. Another was uninstalling proprietary video driver and using open-source. Have you upgraded to latest alsa - 1.0.23?

I installed x86 version though My cpu is amd64,by the way,another lucid was installed on the other hard drive and it's working properly.

---

### Post by lidex on 2010-06-07
> **CHNdonny said:**
> I installed x86 version though My cpu is amd64,by the way,another lucid was installed on the other hard drive and it's working properly.

Interesting. Are they both of the same type - sata/pata?

---

### Post by CHNdonny on 2010-06-08
> **lidex said:**
> Interesting. Are they both of the same type - sata/pata?

yes,I feel it is quite strange as well.both of my hard disk are pata.

---

