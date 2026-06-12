---
title: "Solving upstream sound issues with DP55WG Motherboard"
date: 2010-12-07
forum: Multimedia Software
---

### Post by simosx on 2010-12-07
Alsa is the sound subsystem of the Linux kernel.
Many sound cards do not work out of the box and require us to specify a 'model'. What we can do is add information to the Linux kernel (in Alsa) that our sound card follows a specific model. It is quite elemental, and we just need to add a single line to the kernel source.

Let's try out with the sound card of the DP55WG motherboard. 
We will be a bit pedantic so that others may replicate with their own hardware.

[bdudek writes]("http://ubuntuforums.org/showpost.php?p=10195312&postcount=194"): 
```

Ubuntu 10.10 x86_64
Intel DP55WG Motherboard

aplay -l
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0


/etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=6stack-dig

Works fine. You can select either Analog or Digital SPDIF from the Hardware Tab in Sound Preferences.
```

What we know now is that the sound card uses the ALC889 codec, and we already tried and found that the model should be '6stack-dig'.

The relevant file in the Linux kernel is
[http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=sound/pci/hda/patch_realtek.c;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=sound/pci/hda/patch_realtek.c;hb=HEAD)

and we need to add somewhere a line that looks like

```
SND_PCI_QUIRK(0x103c, 0x2a09, "HP", ALC880_5ST),
```

at the proper place. The value for the two hex numbers will come from 'alsa-info.sh'.

bdudek, can you run on your system

```
wget www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash ./alsa-info.sh

```

This extracts your sound card details, along with the PCI/SUBSYSTEM IDs. These are the numbers that we put in that SND_PCI_QUIRK() line above.
The alsa-info.sh command has an option to send the details to alsa-project.org and publish a public URL. You can send the URL here.

Once we have the PCI/SUBSYSTEM IDs, we can make the one-line patch, and test it with the latest Alsa (and removing the model= hint from the alsa configuration file). If sound works fine, we submit the patch.

---

### Post by bdudek on 2010-12-08
I have uploaded the output to [http://www.alsa-project.org/db/?f=797f86ea4acf132fc5e89ac911197f93631b8609](http://www.alsa-project.org/db/?f=797f86ea4acf132fc5e89ac911197f93631b8609) I have 2 minor problems. The first is the levels seem to be too high on the spdif output. I always have to adjust them down a bit. The second is when switching from analogue to spdif both are active for one or two uses of the sound system. An example would be, open gnome file manager and place your mouse over an MP3 file right after changing from analogue to spdif. You will get sound from both the analogue output as well as the spdif output when rhythmbox does it's preview. Move the mouse off the file and then back onto the file again and then the analogue output will turn off. This is repeatable and can take one or two cycles for it to happen. The same happens when going back to analogue from spdif.

---

### Post by simosx on 2010-12-08
> **bdudek said:**
> I have uploaded the output to [http://www.alsa-project.org/db/?f=797f86ea4acf132fc5e89ac911197f93631b8609](http://www.alsa-project.org/db/?f=797f86ea4acf132fc5e89ac911197f93631b8609) I have 2 minor problems. The first is the levels seem to be too high on the spdif output. I always have to adjust them down a bit. The second is when switching from analogue to spdif both are active for one or two uses of the sound system. An example would be, open gnome file manager and place your mouse over an MP3 file right after changing from analogue to spdif. You will get sound from both the analogue output as well as the spdif output when rhythmbox does it's preview. Move the mouse off the file and then back onto the file again and then the analogue output will turn off. This is repeatable and can take one or two cycles for it to happen. The same happens when going back to analogue from spdif.

Regarding the SPDIF output level, could this be an issue with the default output level of the device (i.e. TV or sound system)?
You can dig a bit deeper here if you try the HDA Analyser,
[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)
You give it as input the output of 'alsa-info.sh'. If you run it with 'sudo', then you can change values from the 'pins', such as decibel levels. 

The second issue probably refers to a bug or feature in Pulseaudio or even Nautilus. Pulseaudio is a higher layer over Alsa, and there might be some caching involved within Nautilus (file manager).

Reading the alsa-info.sh output, it shows that you have two main audio cards, the one embedded on the motherboard (Intel) and the one from the NVidia card. I assume you try to get the motherboard sound card to work.
It looks that both your motherboard sound card and the sound card from NVidia have digital outputs. Verify that you use the motherboard digital output.

There is a concern, with '[   14.828401] hda_codec: ALC889: SKU not ready 0x411111f0'. Google shows several recent hits on this. Since your system is working, we can bypass this.

Alsa-info.sh says that your vendor ID for the m/b sound card is '10ec0889'.

Now, when you read
[http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=sound/pci/hda/patch_realtek.c;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=sound/pci/hda/patch_realtek.c;hb=HEAD)
there are references to 10ec0889, and there is a line for
```
    { .id = 0x10ec0889, .name = "ALC889", .patch = patch_alc882 },
```

which means that when you select 'model=auto' (or do not specify a model line), this is the default setting. And is wrong for you.

So, could you please change 'model=6stack-dig' to 'model=auto', reboot, and retrieve a new (the original) alsa-info.sh; This will be useful to compare what's going on.

---

### Post by bdudek on 2010-12-08
I made the change to /etc/modprobe.d/alsa-base.conf. The last line is now "options snd-hda-intel model=auto". Tried a sound file with no success on either analogue or SPDIF. Then I ran the alsa-info.sh command line that you provided and the information you requested is at [http://www.alsa-project.org/db/?f=3b370233db3254e376f8d6da02f88e1c876f184f](http://www.alsa-project.org/db/?f=3b370233db3254e376f8d6da02f88e1c876f184f)

You also mention the NVidia Sound cards. I have a EVGA 01G-P3-1465-AR GeForce GTX 465 (Fermi) 1GB 256-bit GDDR5 PCI Express 2.0 x16 HDCP Ready SLI Support video card. It has 2 DVI-I and one HDMI out. I don't remember off hand what connectors were on the board itself.

I do plan to try the HDA Analyser next. Another side note is that I have not checked to make sure that my BIOS is up to date. If you think that could also be an issue I will pursue.

I checked the output of the alsa-info.sh and found one big difference in the outputs displayed below:

6stack-dig
=============

Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC889 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM


auto
=============

Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM

---

### Post by simosx on 2010-12-09
Regarding the NVidia, the HDMI output carries audio, and Linux uses Alsa to perform the audio output. ATI and NVidia have a feature to support output of audio through the DVI port, when connected to the HDMI input of a device (such as a TV).

Back to the motherboard sound card. The following patch performs the 'model=6stack-dig' setting,

```
diff --git a/alsa-kernel/pci/hda/patch_realtek.c b/alsa-kernel/pci/hda/patch_rea
index cd2d3a5..ad137d7 100644
--- a/alsa-kernel/pci/hda/patch_realtek.c
+++ b/alsa-kernel/pci/hda/patch_realtek.c
@@ -9833,6 +9833,7 @@ static struct snd_pci_quirk alc882_cfg_tbl[] = {
        SND_PCI_QUIRK(0x1071, 0x8227, "Mitac 82801H", ALC883_MITAC),
        SND_PCI_QUIRK(0x1071, 0x8253, "Mitac 8252d", ALC883_MITAC),
        SND_PCI_QUIRK(0x1071, 0x8258, "Evesham Voyaeger", ALC883_LAPTOP_EAPD),
+       SND_PCI_QUIRK(0x10ec, 0x0889, "Intel DP55WG", ALC882_6ST_DIG),
        SND_PCI_QUIRK(0x10f1, 0x2350, "TYAN-S2350", ALC888_6ST_DELL),
        SND_PCI_QUIRK(0x108e, 0x534d, NULL, ALC883_3ST_6ch),
        SND_PCI_QUIRK(0x1458, 0xa002, "Gigabyte P35 DS3R", ALC882_6ST_DIG),
```

What you do,
1. Grab the latest Alsa snapshot from [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-snapshot.tar.bz2](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-snapshot.tar.bz2)
These are daily snapshots.
2. Expand it (tar xvfj ...) and apply the patch above.
You can use 'patch' to apply the patch, or you can find the source file and add the line yourself. This is simple.
3. Compile this Alsa snapshot and install. Use './configure', 'make', and finally 'make install'. You might need to install some development packages. You get a hint as to what is missing from the error messages.
Since your system has Alsa 1.2.23, it is OK to update the 'alsa-driver' only and keep the system alsa-lib and alsa-utils.
4. You need to restore the model (either change to 'model=auto' or just comment out the line).
5. Restart the computer.

Sound should work. In any case, get a fresh alsa-info.sh output for comparisons. If all go well, the final step is to submit to the Linux kernel.

If you want to remove this snapshot Alsa from your system, you can reinstall the kernel package, using Synaptic Package Manager.

---

### Post by bdudek on 2010-12-09
I copied and pasted the patch above into a file named DP55WG.patch. Then tried to apply the patch. I was unable to apply the patch and received this error:

$ patch --verbose < DP55WG.patch
Hmm...  Looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff --git a/alsa-kernel/pci/hda/patch_realtek.c b/alsa-kernel/pci/hda/patch_rea
|index cd2d3a5..ad137d7 100644
|--- a/alsa-kernel/pci/hda/patch_realtek.c
|+++ b/alsa-kernel/pci/hda/patch_realtek.c
--------------------------
Patching file patch_realtek.c using Plan A...
Hunk #1 FAILED at 9833.
1 out of 1 hunk FAILED -- saving rejects to file patch_realtek.c.rej
done



So I applied it manually. Here is what the patch_realtek.c looks like now:

   9834         SND_PCI_QUIRK(0x1071, 0x8253, "Mitac 8252d", ALC883_MITAC),
   9835         SND_PCI_QUIRK(0x1071, 0x8258, "Evesham Voyaeger", ALC883_LAPTOP_EAPD),
   9836         SND_PCI_QUIRK(0x10ec, 0x0889, "Intel DP55WG", ALC882_6ST_DIG),
   9837         SND_PCI_QUIRK(0x10f1, 0x2350, "TYAN-S2350", ALC888_6ST_DELL),
   9838         SND_PCI_QUIRK(0x108e, 0x534d, NULL, ALC883_3ST_6ch),
   9839         SND_PCI_QUIRK(0x1458, 0xa002, "Gigabyte P35 DS3R", ALC882_6ST_DIG),


Did the "./configure" then the "make" 

I get the message: ALSA modules were successfully compiled.

and then "sudo make install" and get this warning:

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.


I commented out the "options snd-hda-intel model=auto" line then rebooted the machine. Now I have no sound cards at all. I run an "aplay -l" for a quick check and here is the output:

$ aplay -l
aplay: device_list:235: no soundcards found...
$

---

### Post by simosx on 2010-12-09
The compilation of Alsa completed successfully and you got the correct messages.

The problem you got when restarting Alsa probably relates to a failure loading the snapshot Alsa kernel driver.
You can see the output of 'dmesg' for any hints of unresolved symbols.
You can force loading Alsa with 'sudo modprobe snd-hda-intel', which should produce immediately any output to show up in 'dmesg'.

Apparently there might be changes in the snapshot Alsa that prevents it from loading.
Your next step is to try out the published 1.0.23 Alsa, alsa-driver-1.0.23.
The file is [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2)
(found from [http://www.alsa-project.org/](http://www.alsa-project.org/) ). Perform the same task to compile and install.

If you need to have sound for work, you can reinstall your currrent kernel package, then perform the compilation when you have more free time.

---

### Post by bdudek on 2010-12-09
The make failed. I have attached the entire make output but here are the last few lines:

/home/bdudek/Desktop/Ubuntu-Sound/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
/home/bdudek/Desktop/Ubuntu-Sound/alsa-driver-1.0.23/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/home/bdudek/Desktop/Ubuntu-Sound/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/home/bdudek/Desktop/Ubuntu-Sound/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/home/bdudek/Desktop/Ubuntu-Sound/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/home/bdudek/Desktop/Ubuntu-Sound/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/home/bdudek/Desktop/Ubuntu-Sound/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [compile] Error 2

---

### Post by simosx on 2010-12-09
Apparently this is an issue with the latest kernel in Ubuntu and the released Alsa 1.0.23 (April 2010),
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg26832.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg26832.html)

Can you go back to the snapshot version of Alsa, and tell me what unresolved symbols you get when you try to load the sound driver?
I think the best course of action is to get this issue solved upstream.
This would help other in a similar situation.

There is the alternative to recompile the whole Linux kernel in Ubuntu, however this would be too much effort for the casual user who would try to replicate the process. Recompiling the whole kernel takes time and disk space.

---

### Post by bdudek on 2010-12-10
OK... I put the snapshot back in and rebooted. Still no sound card so that is repeatable. The output of the dmesg is from the reboot and the manual modprobe that I tried, also I show the alsa-base.conf at the time of this test.

$ sudo modprobe snd-hda-intel
[sudo] password for bdudek: 
FATAL: Error inserting snd (/lib/modules/2.6.35-23-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.35-23-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.35-23-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.35-23-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.35-23-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
$ dmesg | grep snd
[    7.000311] snd: Unknown symbol unregister_sound_special (err 0)
[    7.000440] snd: Unknown symbol unregister_sound_special (err 0)
[    7.000731] snd: Unknown symbol unregister_sound_special (err 0)
[    7.001038] snd: Unknown symbol register_sound_special_device (err 0)
[    7.001399] snd: Unknown symbol register_sound_special_device (err 0)
[    7.001655] snd: Unknown symbol register_sound_special_device (err 0)
[    7.022385] snd_seq_device: Unknown symbol snd_info_register (err 0)
[    7.022440] snd_seq_device: Unknown symbol snd_info_create_module_entry (err 0)
[    7.022495] snd_seq_device: Unknown symbol snd_info_free_entry (err 0)
[    7.022549] snd_seq_device: Unknown symbol snd_seq_root (err 0)
[    7.022610] snd_seq_device: Unknown symbol __snd_printk (err 0)
[    7.022665] snd_seq_device: Unknown symbol snd_iprintf (err 0)
[    7.022750] snd_seq_device: Unknown symbol snd_device_new (err 0)
[    7.054352] snd_timer: Unknown symbol snd_info_register (err 0)
[    7.054410] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)
[    7.054469] snd_timer: Unknown symbol snd_info_register (err 0)
[    7.054533] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)
[    7.054599] snd_timer: Unknown symbol snd_info_free_entry (err 0)
[    7.054718] snd_timer: Unknown symbol snd_info_free_entry (err 0)
[    7.054869] snd_timer: Unknown symbol __snd_printk (err 0)
[    7.054929] snd_timer: Unknown symbol snd_iprintf (err 0)
[    7.054997] snd_timer: Unknown symbol __snd_printk (err 0)
[    7.055057] snd_timer: Unknown symbol snd_iprintf (err 0)
[    7.055129] snd_timer: Unknown symbol snd_ecards_limit (err 0)
[    7.055236] snd_timer: Unknown symbol snd_ecards_limit (err 0)
[    7.055292] snd_timer: Unknown symbol snd_oss_info_register (err 0)
[    7.055359] snd_timer: Unknown symbol snd_unregister_device (err 0)
[    7.055418] snd_timer: Unknown symbol snd_oss_info_register (err 0)
[    7.055479] snd_timer: Unknown symbol snd_unregister_device (err 0)
[    7.055570] snd_timer: Unknown symbol snd_device_new (err 0)
[    7.055634] snd_timer: Unknown symbol snd_device_new (err 0)
[    7.055861] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
[    7.055942] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
[  332.243113] snd: Unknown symbol unregister_sound_special (err 0)
[  332.243379] snd: Unknown symbol register_sound_special_device (err 0)
[  332.245467] snd_timer: Unknown symbol snd_info_register (err 0)
[  332.245631] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)
[  332.245839] snd_timer: Unknown symbol snd_info_free_entry (err 0)
[  332.246210] snd_timer: Unknown symbol __snd_printk (err 0)
[  332.246373] snd_timer: Unknown symbol snd_iprintf (err 0)
[  332.246607] snd_timer: Unknown symbol snd_ecards_limit (err 0)
[  332.246834] snd_timer: Unknown symbol snd_oss_info_register (err 0)
[  332.246997] snd_timer: Unknown symbol snd_unregister_device (err 0)
[  332.247224] snd_timer: Unknown symbol snd_device_new (err 0)
[  332.247625] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
$ tail -2 /etc/modprobe.d/alsa-base.conf
#options snd-hda-intel model=6stack-dig
options snd-hda-intel model=auto
$

Next I tried to change the alsa-base.conf to this:

options snd-hda-intel

and reboot. The module still did not load so I tried a modprobe and got this:

$ sudo modprobe snd-hda-intel
[sudo] password for bdudek: 
WARNING: /etc/modprobe.d/alsa-base.conf line 47: ignoring bad line starting with 'options'
WARNING: /etc/modprobe.d/alsa-base.conf line 47: ignoring bad line starting with 'options'
FATAL: Error inserting snd (/lib/modules/2.6.35-23-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.35-23-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.35-23-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.35-23-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.35-23-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


Line 47 is the last line of the alsa-base.conf

---

### Post by simosx on 2010-12-12
These compilation problems are specific to Ubuntu 10.10,
[http://mailman.alsa-project.org/pipermail/alsa-devel/2010-December/034762.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2010-December/034762.html)

I am looking into what (small) changes are needed to do to Alsa snapshot so that it compiles on Ubuntu 10.10.

---

### Post by simosx on 2010-12-13
> **simosx said:**
> These compilation problems are specific to Ubuntu 10.10,
[http://mailman.alsa-project.org/pipermail/alsa-devel/2010-December/034762.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2010-December/034762.html)

I am looking into what (small) changes are needed to do to Alsa snapshot so that it compiles on Ubuntu 10.10.

Ok, here are the updated instructions.

When you compile Alsa, the first step is normally to run './configure'.
In Ubuntu 10.10, you simply run './configure --with-oss=no' and that's it. 
Of course, you run then 'make' and finally 'sudo make install', as usual. 

I highly recommend to clean up the existing Alsa kernel modules from /lib/modules/.../sound/*
If you still get issues with unknown symbols, it is most probably related to left-over Alsa kernel modules (for example, soundcore.ko was left for some reason).

---

### Post by bdudek on 2010-12-16
Still no sound and the module fails to load. I used the orginal snapshot that you had me download when we first started. I have atatched the process I used to compile, clean and install.

Verify destination

find /lib/modules/2.6.35-23-generic/kernel/sound -name "*.ko" -print

To remove them

sudo find /lib/modules/2.6.35-23-generic/kernel/sound -name "*.ko" -exec rm {} \;

Configure Statement

./configure --with-oss=no

make

sudo make install

Verify the files are back

find /lib/modules/2.6.35-23-generic/kernel/sound -name "*.ko" -print

Edit alsa-base.conf

sudo vi /etc/modprobe.d/alsa-base.conf

make sure that any snd-hda-intel is commented out.

reboot

No sound was the result. Below is from me checking the dmesg and trying a manual load.

$ dmesg | grep -i snd
[   14.752372] snd: Unknown symbol sound_class (err 0)
[   14.752798] snd_timer: Unknown symbol snd_info_register (err 0)
[   14.752878] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)
[   14.752991] snd_timer: Unknown symbol snd_info_free_entry (err 0)
[   14.753186] snd_timer: Unknown symbol __snd_printk (err 0)
[   14.753290] snd_timer: Unknown symbol snd_iprintf (err 0)
[   14.753437] snd_timer: Unknown symbol snd_ecards_limit (err 0)
[   14.753549] snd_timer: Unknown symbol snd_unregister_device (err 0)
[   14.753660] snd_timer: Unknown symbol snd_device_new (err 0)
[   14.753917] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
[   14.764989] snd: Unknown symbol sound_class (err 0)
[   14.765423] snd_seq_device: Unknown symbol snd_info_register (err 0)
[   14.765525] snd_seq_device: Unknown symbol snd_info_create_module_entry (err 0)
[   14.765627] snd_seq_device: Unknown symbol snd_info_free_entry (err 0)
[   14.765726] snd_seq_device: Unknown symbol snd_seq_root (err 0)
[   14.765837] snd_seq_device: Unknown symbol __snd_printk (err 0)
[   14.765943] snd_seq_device: Unknown symbol snd_iprintf (err 0)
[   14.766099] snd_seq_device: Unknown symbol snd_device_new (err 0)
[   15.071050] snd: Unknown symbol sound_class (err 0)
[   15.071603] snd_timer: Unknown symbol snd_info_register (err 0)
[   15.071664] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)
[   15.071735] snd_timer: Unknown symbol snd_info_free_entry (err 0)
[   15.071863] snd_timer: Unknown symbol __snd_printk (err 0)
[   15.071918] snd_timer: Unknown symbol snd_iprintf (err 0)
[   15.071998] snd_timer: Unknown symbol snd_ecards_limit (err 0)
[   15.072067] snd_timer: Unknown symbol snd_unregister_device (err 0)
[   15.072154] snd_timer: Unknown symbol snd_device_new (err 0)
[   15.072305] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
$ sudo modprobe snd-hda-intel
[sudo] password for bdudek: 
FATAL: Error inserting snd (/lib/modules/2.6.35-23-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.35-23-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.35-23-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.35-23-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.35-23-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
$

I tried this configure line and still got the same results

./configure --with-oss=no --with-pcm-oss-plugins=no --with-debug=verbose

---

