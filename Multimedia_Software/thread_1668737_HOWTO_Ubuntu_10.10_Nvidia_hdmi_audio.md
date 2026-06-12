---
title: "HOWTO: Ubuntu 10.10 Nvidia hdmi audio"
date: 2011-01-16
forum: Multimedia Software
---

### Post by tjones00 on 2011-01-16
Although this information is present in this forum in bits and pieces a new nvidia hdmi audio thread pops up every couple days. 

So for simplicity sake here's my attempt and a very simple howto instead of editing re-editing and reposting old information.

First make sure you have nvidia proprietary drivers installed. hdmi audio does not work with nouveau/opensource. Open a terminal. Applications -> Accessories ->Terminal.

Now type:

```
cat /proc/driver/nvidia/version
```You should see something like this.
```

NVRM version: NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
GCC version:  gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 
```If not go install the nvidia proprietary driver via System -> Administration -> Additional Drivers.




**NVIDIA HDMI AUDIO Ubuntu 10.10**

Begin by reading this (it's ok if you don't understand it but you should be aware of this post): [http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)

**Step 1)** To start confirm that your system can see your nvidia hdmi audio card. Type aplay -l in a terminal. You should see something like this.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```If you do not see a nvidia sound device you need to upgrade to a properly patched alsa 1.0.23 or 2.6.35+ kernel. For the fact that it is often not required nowdays I'll leave that out of this howto. Follow this link to upgrade alsa [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)


**Step 2)** Confirm which device is responsible for hdmi audio.

Open a terminal and type:

```
grep eld_valid /proc/asound/NVidia/eld*
```You'll see an output like this:

```
/proc/asound/NVidia/eld#0.0:eld_valid        0
/proc/asound/NVidia/eld#1.0:eld_valid        0
/proc/asound/NVidia/eld#2.0:eld_valid        0
/proc/asound/NVidia/eld#3.0:eld_valid        1
```The line that returns eld_valid 1 is the device responsible for hdmi audio on your nvidia card and has recognized that there is a connection. 

If you don't receive a 1 for one of the devices you need to return to  Step 1) and ensure you have a properly patched alsa 1.0.23 or 2.6.35+  kernel. This may also be the fault of the system not acquiring EDID data  from your hdmi connection. Inability to acquire an EDID will also  result in resolution issues so you should move onto resolving this issue  before setting up hdmi audio. You can confirm your system has acquired  an EDID from the connection by checking your /var/log/Xorg.0.log file.

**UPDATE:** [http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)
According to the above:

> 13.5. Verify Your ELD Is Valid
To validate that the ALSA driver is aware of your monitor, check the eld files. Recall that older chipsets (ION and earlier) don’t support ELD reporting, and hence the ELD files will not exist. In this case, ALSA always assumes that all audio features are available


Therefore if you don't receive any eld information you may just have an older card that doesn't support reporting. You will then have to manually test each device with aplay to determine which device is responsible for audio.

eg. 
```
aplay -D plughw:NVidia,3 /usr/share/sounds/alsa/Front_Center.wav
aplay -D plughw:NVidia,7 /usr/share/sounds/alsa/Front_Center.wav
aplay -D plughw:NVidia,8 /usr/share/sounds/alsa/Front_Center.wav
aplay -D plughw:NVidia,9 /usr/share/sounds/alsa/Front_Center.wav
```

**Step 3)** Use a probemask to enable the proper codec for hdmi:NVidia.

eld#0.0=device 3       probe_mask=0x101
eld#1.0=device 7       probe_mask=0x102
eld#2.0=device 8       probe_mask=0x104
eld#3.0=device 9       probe_mask=0x108

Edit or create a /etc/modprobe.d/sound.conf file. Type the following in a terminal:

```
gksudo gedit /etc/modprobe.d/sound.conf
```add the proper options snd-hda-intel probe_mask line to this file (this example uses device 9)

```
options snd-hda-intel probe_mask=0x108
```Save the file and update the initramfs to make sure this change will be used upon reboot.

```
sudo update-initramfs -u
```[B]

**UPDATE:** see this post for more information on probe_masks.
[http://ubuntuforums.org/showpost.php?p=10465858&postcount=21](http://ubuntuforums.org/showpost.php?p=10465858&postcount=21)


Step 4)[/B] Edit your pulseaudio default.pa file. **Note if you do not have pulseaudio installed just add pcm.!default hdmi:NVidia to your /etc/asound.conf file remove any .asoundrc file and reboot as in this post [http://ubuntuforums.org/showpost.php?p=10381472&postcount=11](http://ubuntuforums.org/showpost.php?p=10381472&postcount=11)

If you have pulseaudio installed continue with the following edit.

```
gksudo gedit /etc/pulse/default.pa
```Find the static alsa sink line:

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
```Add load-module module-alsa-sink device=hdmi:NVidia to the end of the section:

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
load-module module-alsa-sink device=hdmi:NVidia

```Remove any local pulseaudio/alsa settings to ensure this new default.pa systemwide setting will be used. Type the following in a terminal.

```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie
```[B]

Step 5)[/B] Reboot the computer and you should now be able to use the standard hdmi audio connection or the hdmi device via hdmi:NVidia. 

If not try unmuting the device in alsamixer then test it again.

```
alsamixer
```MM denotes muted 00 is unmuted, m is the toggle, f6 to switch cards.

To test the probemask after the reboot do the following:

```
aplay -Dhdmi:NVidia /usr/share/sounds/alsa/Front_Center.wav
```If you receive audio with the aplay command but not at your desktop your pulseaudio or local settings are probably incorrect.



If you have problems with this probemask method you will have to resort to editing default.pa and possibly asound.conf listing the explicit card# and device # for your hdmi audio eg. hw:1,9 or hw:NVidia,9

If anybody sees something wrong with this process let me know and I'll correct it asap.

---

### Post by swapnil_bhartiya on 2011-01-20
I tried your howto and now no devices shown in Sound Preferences. Please suggest.

---

### Post by tjones00 on 2011-01-20
These forums have been having issues today.

To test the probemask directly do the following. First run alsamixer and make sure the device is unmuted. Then type this in a terminal.

```
aplay -Dhdmi:NVidia /usr/share/sounds/alsa/Front_Center.wav
```

If that works the probemask is good and it's just pulseaudio settings. These should have been auto repopulated after the wipeout but to make sure do the following.

```
gksudo gedit /etc/asound.conf
```

add

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

Then reboot.

If you still don't see any devices try killing and relaunching pulseaudio.

```
sudo killall pulseaudio

sudo pulseaudio -D
```

If aplay -Dhdmi:NVidia didn't work the then the nvidia suggested probemask is most likely incompatible with your card.

Do the following.

1) Remove the /etc/modeprobe.d/sound.conf file you created or remove the probemask line if you just added it to the file and update initramfs again.

2) Edit the the default.pa file replacing hdmi:NVidia with an explict plughw: call to your card,device eg if the card was 1 and the device 9 plughw:1,9.

load-module module-alsa-sink device=plughw:1,9

You can keep the asound.conf pointing to pulse.

If that still doesn't work then you'll most likely have to use a hw: definition in default.pa and setup the asound.conf to work properly with your card with the dmix/hw setup people have been using. It's an ok method but not as dynamic as hdmi:NVidia or plughw:*,* would be for people with different setups.

Pretty much all the stuff in the last half of this post that was originally posted 6 months ago and is just a mess.
[http://ubuntuforums.org/showpost.php?p=9732345&postcount=8](http://ubuntuforums.org/showpost.php?p=9732345&postcount=8)

---

### Post by tjones00 on 2011-01-20
multipost forum error nothing to see here.

---

### Post by tjones00 on 2011-01-20
multipost forum error nothing to see here.

---

### Post by tjones00 on 2011-01-20
multipost forum error nothing to see here.

---

### Post by tjones00 on 2011-01-20
multipost forum error nothing to see here.

---

### Post by tjones00 on 2011-01-20
multipost forum error nothing to see here.

---

### Post by tjones00 on 2011-01-20
multipost forum error nothing to see here.

---

### Post by gomike on 2011-01-20
So I am stuck at step 4

I have no "pulseaudio default.pa" file.

OK I figured out I had to install pulseaudio and finally got it working.

---

### Post by tjones00 on 2011-01-20
There is no file at /etc/pulse/default.pa?

This should be created if pulseaudio was installed.

Confirm pulseaudio is installed just open synaptic package manager and type pulseaudio.

If it's installed right click on it select properties look at installed files and find the default.pa file location.

Or from a terminal type.

```
sudo find / -name default.pa
```

If pulseaudio is not installed (you don't need it) and you are only using alsa edit the /etc/asound.conf to point to hdmi:NVidia

First test the probemask.

```
aplay -Dhdmi:NVidia /usr/share/sounds/alsa/Front_Center.wav
```

If you hear sound then do the following asound.conf edit.

```
gksudo gedit /etc/asound.conf
```

add the following.

```
pcm.!default hdmi:NVidia
```

and reboot.

---

### Post by efflandt on 2011-01-21
After using 2 different nvidia cards GT 220 and GT 430 I settled on a somewhat different method than suggested here, which has worked for others including GTX cards.

After tjones00 Step 1 to verify if HDA NVidia devices show up in **aplay -l**,  run **alsamixer**, use F6 to pick HDA Nvidia, then unmute all the S/PDIF devices (press **m** for any that are MM so they become 00).

Then find out which one works for following, also trying 1,7 1,8 or 1,9 in place of 1,3 (use your nvidia card number in place of the 1):

```
aplay -D plughw:1,3 /usr/share/sounds/Front_Center.wav
```Then using **gksu gedit** (or **sudo nano** ) edit **/etc/pulse/default.pa** and add a line after the commented out line for alsa-sink for the card and device that worked for that aplay sound.  In my case it was 1,9, so I added the bolded line below:

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```Then reboot, play music in Rythmbox or other audio player, and see if one of the devices in the **Output** tab of **Sound Preferences** works for HDMI sound.  In my case I ended up with an extra device and the one that worked for HDMI was an HDA NVidia device that did not say HDMI.

---

### Post by mikebutler on 2011-01-26
What an excellent thread!

Unfortunately, I'm still stumped. :-(

Is the driver installed? Yup:
```

htpc@htpc:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
GCC version:  gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5)

```

Do I have an HDMI audio device? Yup:
```

htpc@htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Not sure why this is required or what it means:
```
grep 'eld_valid' /proc/asound/NVidia/eld*
```
```
/proc/asound/NVidia/eld#0.0:eld_valid        0
/proc/asound/NVidia/eld#1.0:eld_valid        0
/proc/asound/NVidia/eld#2.0:eld_valid        0
/proc/asound/NVidia/eld#3.0:eld_valid        1
```

I don't seem to have those files or that flag:
```

htpc@htpc:~$ ls /proc/asound/NVidia/
codec#0  codec#3  id  pcm0c  pcm0p  pcm3p
htpc@htpc:~$ grep -r eld_valid /proc/asound/NVidia/
htpc@htpc:~$

```

Is that a problem? There's certainly some EDID going on according to Xorg.0.log:
```

[    27.820] (WW) NVIDIA(0): The EDID for LG Electronics LG TV (DFP-0) contradicts itself:
[    27.820] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    27.820] (WW) NVIDIA(0):     EDID's valid HorizSync range (31.000-82.000 kHz) would
[    27.820] (WW) NVIDIA(0):     exclude this mode's HorizSync (27.0 kHz); ignoring
[    27.820] (WW) NVIDIA(0):     HorizSync check for mode "1920x1080".

```
Though, it doesn't seem very happy.

Anyways, I can do a this and it seems to happily spend some time spitting out the audio, but I can't hear it!
```

htpc@htpc:~$ aplay -D plughw:0,3 /usr/share/sounds/alsa/Noise.wav
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
htpc@htpc:~$

```

Also, if I use plughw:0,0, I can hear the noise through the analog out:
```

htpc@htpc:~$ aplay -D plughw:0,3 /usr/share/sounds/alsa/Noise.wav
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
htpc@htpc:~$

```

I've tried unmuting the S/PDIF out from alsamixer, but that doesn't seem to be the issue.

So, I'm pretty much out of ideas. Got any suggestions? I had this working in the same hardware setup in 10.04, but that was with xbmclive with a bunch of config that was already done for me. :-(

---

### Post by tjones00 on 2011-01-31
You are not using a probemask in the /etc/asound.conf file are you? If  so remove it and check for eld again. The eld_valid check should be done  before the application of any probemask so you can determine which  probemask to use. I've seen results like yours when using the probemasks found on the xbmc wiki. I've also seen results like yours when using an improperly patched alsa 1.0.23 when the hdmi sense was faulty.

eld stands for EDID Like Data. It is used by snd-hda-intel (the alsa module responsible for nvidia hdmi audio) to determine the audio capabilities of the display/etc connected via hdmi.

The EDID is gathered upon probe of the device by the nvidia driver and contains the video/audio capabilities of the display. I'm not sure but I think this information is partially shared with snd-hda-intel. So if the nvidia driver can't gather a proper EDID I wouldn't expect snd-hda-intel to have a valid eld.

The grep query of eld_valid is to determine that snd-hda-intel has recognized there is an hdmi connection and has all the necessary audio information. Since this step does not work for you I'd suspect it's an EDID issue. (assuming that alsa 1.0.23 should be fine in 10.10)

If you want to go about troubleshooting the apparent eld issue I'd do this.

1) Start with generating a brand new xorg.conf (not merged)
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
sudo nvidia-xconfig
```2) reboot then grep for eld again. If there still isn't anything check the xorg.0.log again. If you are using a **32b system** you can install read-edid from the repository and use it to grab an edid.bin from the display. You can then use that edid.bin with the CustomEDID option in your xorg.conf 

```
sudo apt-get install read-edid
```test the edid:

```
sudo get-edid | parse-edid
```this will display resolutions if they look fine then:
```

sudo get-edid > edid.bin
```Use that file with the CustomEDID option in your xorg.conf see the following links.

[http://www.nvnews.net/vbulletin/showthread.php?t=126648](http://www.nvnews.net/vbulletin/showthread.php?t=126648)
[https://wiki.archlinux.org/index.php/NVIDIA](https://wiki.archlinux.org/index.php/NVIDIA)

Most people use it in the Device section there is an example with the arch linux link at "X with a TV" ignore the DFP part since you're using hdmi. Check your Xorg.0.log to determine what the actual connection is for your display.

If you are using a 64b system I don't know of any trick you can use to get a proper edid.bin in linux. There might be something out there though. If you have another O/S installed you could try using that to get an edid.bin.

Edit:
Also check this thread for nvidia chipsets to force the alsa sink, from your aplay -l it appears you're using a chipset and not a discrete graphics card. Perhaps the chipset doesn't require eld, it's worth a shot.
[http://ubuntuforums.org/showthread.php?t=1678549](http://ubuntuforums.org/showthread.php?t=1678549)

---

### Post by BicyclerBoy on 2011-02-15
Additional info source.

[ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)

---

### Post by bedege on 2011-02-15
> **BicyclerBoy said:**
> Additional info source.

[ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)
The ftp link is apparently broken (at least now :cry:)
I was able to fetch this (excellent) document at
[http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html]("http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html")

Need to give it a try now!

---

### Post by tjones00 on 2011-02-16
Nice find! The probemask breakdown is really nice info.

This seems interesting to those who can't find any eld data.

> 13.5. Verify Your ELD Is Valid
To validate that the ALSA driver is aware of your monitor, check the eld files. Recall that older chipsets (ION and earlier) don’t support ELD reporting, and hence the ELD files will not exist. In this case, ALSA always assumes that all audio features are available.

So for an older card/chipset if you don't have any eld data and multiple devices listed you'll have to test each device with aplay to determine which device is responsible for audio.

eg. aplay -D plughhw:1,8 /path/to/wav.file

---

### Post by bedege on 2011-02-16
Hi there
Well, I followed this HOWTO and did not get any sound from [FONT="Courier New"]aplay[/FONT]...

My system is a Jetway Ion Top (JBC231C98, based on Jetway's NC98 mini-ITX motherboard, with an Atom D525 and a Ion2 GPU).
I have Xubuntu 10.04 on it, with a 2.6.36 kernel (trying to have my IR remote working too...) and have removed pulseaudio (was giving me trouble with Skype on other machines, so decided to get rid of it).

I've followed the Howto and found an active eld (whatever I understand of it ;)) when my HDTV is hooked up onto my system. Also added the [FONT="Courier New"]probe_mask[/FONT] info in [FONT="Courier New"]/etc/modprobe.d/sound.conf[/FONT]. But when I try to play a wav file, I get

[FONT="Courier New"]aplay: set_params:996: Channels count non available[/FONT]

Any idea on what I should look at next? In particular, I'm a little confused by the linux-backports-modules-alsa package that is often mentionned in many threads. I did not install it, since I was not able to find any such package matching my 2.6.36 kernel.
Thks ):P

---

### Post by tjones00 on 2011-02-16
You shouldn't need to update alsa with a 2.6.36 kernel the updates are generally required for kernels lower than 2.6.35.

So you added the proper probemask. Which device is it? 

I think yours should be device 7. From my understanding of the jetway setups typically the nvidia card should be card 0.

After adding the probemask and updating the initramfs have you done the following?

1) Test the probemask:

```
aplay -D hdmi:NVidia /path/to/wav.file
```

2) Also to test the device (this will work with or without the probemask):

```
aplay -D plughw:card#,device# /path/to/wav.file
```

Replacing card# and device# with the calls for your hardware. You can use NVidia instead of card#. So for you NVidia,7 should work if it is device 7.

If plughw works but hdmi:NVidia doesn't that means the probemask doesn't work for your hardware setup I'd refer to the link BicylerBoy posted and go over the probemask definitions. Perhaps for your system the probemask needs to be different.

If hdmi:NVidia works just set it as default in asound.conf. See post [http://ubuntuforums.org/showpost.php?p=10381472&postcount=11](http://ubuntuforums.org/showpost.php?p=10381472&postcount=11)

---

### Post by bedege on 2011-02-16
Thanks for your comments.
For the moment, I've only tested [FONT="Courier New"]aplay [/FONT]with [FONT="Courier New"]hdmi:NVidia[/FONT], not [FONT="Courier New"]plughw[/FONT]. You're perfectly right, my device is 7.

I'm at work, but I should be able to test it tonight and keep you posted :)

---

### Post by tjones00 on 2011-02-16
Well this is interesting.

From the new resource.

> 13.9.2. probe_mask

The probe_mask ALSA HD-audio module parameter may be used to tell the ALSA kernel driver to ignore some of the codecs in a GPU. This is useful in the following situations:

This method affects ALSA as well PulseAudio.

You use two HDMI ports, use PulseAudio, want to use the PulseAudio configuration options mentioned in the previous section, and neither of the two HDMI ports has logical ID 0.

You prefer to completely disable hardware you will never use, perhaps so it&#8217;s more obvious what you should be using.

You prefer kernel command-line options over PulseAudio configuration for whatever reason.

When using probe_mask, the logical ID of all codecs will remain unchanged, even those not in use. However, physical IDs are assigned dynamically, in a contiguous fashion. Hence, the mapping of logical to physical IDs will change. Refer to /proc/asound/cardx/codec#y to find the physical ID assigned to each codec.

The probe_mask is a bit-mask of the codecs you wish the kernel to expose. Each codec is assigned a mask based on its logical ID:

Logical Codec ID / Bitmask
0         /        1
1         /        2
2         /        4
3         /        8

For each codec you want to remain enabled, add the bitmask column together, e.g. to support codecs with logical IDs 1 and 3, 2 + 8 == 10 (or in hex, 0x2 + 0x8 = 0xa).

Other online sources, and earlier revisions of this document, indicated that 256 (0x100) should be added to this number. This isn&#8217;t a good practice, since adding 256 may force the kernel to probe hardware that isn&#8217;t actually present, whereas not adding 256 tells the kernel to restrict its probing to the subset of hardware that you specify; a safer option.

The format of the module parameter is probe_mask=value (e.g. probe_mask=0xa). When multiple sound cards are present in the system, a mask may be specified per card, in the format probe_mask=value_card1,value_card2. A value of -1 may be used to request default handling. So, to set the probe_mask for a discrete NVIDIA GPU and leave a motherboard analog audio controller unaffected, use probe_mask=-1,0xa.

Note: Some sources recommend values such with format 0xfffa, 0xfffffffa, or 0xffffff0a. Thes are all equivalent to 0x10a; bits above bit 8 are ignored, and specifying them only serves to make things more complex than they need be. Specifying bit 8 itself is also no longer recommended as previously described.

For the same reason, you should use a mask of -1 for any cards for which you want default handling, rather than 0xffff, since the latter is again forcing the kernel to probe hardware that may not be present.

To test probe_mask, you can manually remove and reload the appropriate kernel model, for example:

# Custom value
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=-1,0xa
# Default
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=-1,-1
To make the value permanent, create a modprobe configuration file, for example:

$ cat /etc/modprobe.d/snd-hda-intel.conf
options snd-hda-intel probe_mask=-1,0xa
On older distributions, you may need to place this line in /etc/modprobe.conf instead.

On some distributions, you may need to rebuild your initrd (initial ramdisk) after making such a change; consult with your distribution vendor or help forums for details.

For Ubuntu, run:

sudo update-initramfs -k all -u

This means the nvidia suggested probemasks in the first post of this thread are bad practice because they use the +256 (0x100 method and we should be using these instead.

eld#0.0=device 3 probe_mask=0x1
eld#1.0=device 7 probe_mask=0x2
eld#2.0=device 8 probe_mask=0x4
eld#3.0=device 9 probe_mask=0x8

Try 
```
probe_mask=0x2
``` 
for device 7 and see what happens.


Two cards on the system:

I think nvidia is usually card 0 with jetway ion2 setups aplay -l will tell you which it is.


Nvidia hdmi on card 1:
Try 
```
probe_mask=-1,0x2

``` 
and
```
probe_mask=-1,0x102
```

Nvidia hdmi on card 0 in a two card system:
Try
```
probe_mask=0x2,-1
```
and 
```
probe_mask=0x102,-1
```

To test any of these probe masks use aplay hdmi:NVidia.

If you are unsure where I got any of these values just read the section of the link that I have quoted in this post.

---

### Post by bedege on 2011-02-17
> **bedege said:**
> Thanks for your comments.
For the moment, I've only tested [FONT="Courier New"]aplay [/FONT]with [FONT="Courier New"]hdmi:NVidia[/FONT], not [FONT="Courier New"]plughw[/FONT]. You're perfectly right, my device is 7.

I'm at work, but I should be able to test it tonight and keep you posted :)

OK, some feedback of my tests last night.
First, I NOW HAVE SOME SOUND! For the first time I was able to get output on my HDTV from my Ion2 system! I'm so thrilled! :popcorn:

First, you were right, on my Jetway NC98 system, NVidia HDMI device is on Card#1,Device#7. Please note that to make it work, I first had to remove the probe_mask by deleting [FONT="Courier New"]/etc/modprobe.d/sound.conf[/FONT] and running [FONT="Courier New"]sudo update-initramfs -u[/FONT]. Don't know whether it was 100% necessary, but that's what I did.
Then, some commands on my (French) system:
> bedege@HTubuntu:/usr/share/sounds/alsa$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC662 rev1 Digital [ALC662 rev1 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  1: NVidia [HDA NVidia], périphérique 3 : NVIDIA HDMI [NVIDIA HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  1: NVidia [HDA NVidia], périphérique 7 : NVIDIA HDMI [NVIDIA HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  1: NVidia [HDA NVidia], périphérique 8 : NVIDIA HDMI [NVIDIA HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  1: NVidia [HDA NVidia], périphérique 9 : NVIDIA HDMI [NVIDIA HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

bedege@HTubuntu:/usr/share/sounds/alsa$ grep eld_valid /proc/asound/NVidia/eld#*
/proc/asound/NVidia/eld#0.0:eld_valid		0
/proc/asound/NVidia/eld#1.0:eld_valid		1
/proc/asound/NVidia/eld#2.0:eld_valid		0
/proc/asound/NVidia/eld#3.0:eld_valid		0


After confirmation of the device#, I was able to hear some sounds by typing the following.
> bedege@HTubuntu:/usr/share/sounds/alsa$ aplay -D plughw:1,7 *.wav
Lecture en cours WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Taux 48000 Hz, Mono


bedege@HTubuntu:/usr/share/sounds/alsa$ aplay -D plughw:NVidia,7 *.wav
Lecture en cours WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Taux 48000 Hz, Mono
which confirms that the right output is device#7. Howesome! :p

Later, I tried to pick the right [FONT="Courier New"]mod_probe[/FONT] to have the system directly pick the "right" sound card (that's what mod_probe are for, right?).

Instead of editing the [FONT="Courier New"]/etc/modprobe.d/sound.conf[/FONT] file, I tried to use [FONT="Courier New"]sudo modprobe snd-hda-intel probe_mask=-1,0x2[/FONT], as explained in the NVidia document that is linked in posts #15, #16 and #21 of this thread, in order to load the module dynamically.

Well... No luck! Nothing worked, even if I changed the [FONT="Courier New"]probe_mask[/FONT] value and tested [FONT="Courier New"]aplay [/FONT]width [FONT="Courier New"][FONT="Courier New"]-D hdmi:NVidia[/FONT][/FONT]. I've tried several combinations, as per the previous post, but none worked. AFAIR, all gave the same type of output as before, like:
> aplay: set_params:996: Channels count non available

Also, since I have removed pulseaudio on my system, I'm curious on how to set up the different multimedia applications (vlc, exaile, listen, etc) to instruct them to use my hdmi card. Any idea? Maybe I need to fix the mod_probe issue first?

In any case, I'm really pleased that I have some sound working. I guess there's still a little work to do to set up the right mod_probe, but I might end up watching a good movie on my system this week end! :)

---

### Post by tjones00 on 2011-02-17
Well thats odd, post the output from:

cat /proc/asound/NVidia/codec#1

Ideally you want to use the probemask with hdmi:NVidia.

If you can't get the probemask working then you have to resort to making an asound.conf file at /etc/asound.conf.

Some people have been using the following asound.conf but it has issues with multichannel audio also this setup is strictly for a stereo system.

[https://bbs.archlinux.org/viewtopic.php?pid=789152](https://bbs.archlinux.org/viewtopic.php?pid=789152)

```
pcm.dmixer {
  type dmix
  ipc_key 2048
  slave {
    pcm "hw:1,7" # Always use pure hw. dmix will reformat/resample audio.
    period_size 512 # If you get stuttering/or non-working audio, fiddle around with these
    buffer_size 4096
    rate 48000 # HDMI, I'll assume 48kHz
    format S16_LE # Should be default for pretty much any soundcard.
  }
  bindings {
    0 0
    1 1
  }
}

pcm.!default {
  type plug
  slave.pcm dmixer
}
```

The second entry on that thread seems more ideal to me since it has less definitions. I'd use that one first.

```
pcm.!default {
  type plug
  slave.pcm "dmix:1,7"
}
```

^^use this one.

I have never used a custom asound.conf myself so that's all the direction I can give you.

---

### Post by bedege on 2011-02-18
Little progress here: I've been able to launch vlc and hear sound output, by specifying in vlc's options that I *want* it to use Alsa output 1,7. And it works, I can now watch DVDs from vlc and listen to the soundtrack on my HDTV thru HDMI. Good! :KS

Still have some questions, though. The ultimate goal would be for any audio application to be able to send its output to my TV, without having to fiddle in their individual options or preferences. Also recognize that I have removed pulseaudio just because in the past, it has created issues with skype (which I haven't tried on this new HTPC btw) and I've read in some other treads that pulseaudio can also create some issues with hdmi...

Having said that, what would be the next logical step to have a system globally hooked up to alsa 1,7 sound card with hdmi?
- I understand that finding the right mod_probe might be one solution. Is this a true statement?
- There is the solution of adding the pcm.dmixer configuration from the thread above
- Finally, I've also read another proposal in [ossnotebook]("http://ossnotebook.blogspot.com/2010/07/ubuntu-1001-maverick-on-lenovo-q150.html").
> In case you want to make a permanent change for the hdmi sound as the deafult card you can update /usr/share/alsa/alsa.conf and change these lines:

defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0

to this:

defaults.ctl.card NVidia
defaults.pcm.card Nvidia
defaults.pcm.device 9

I must admit I'm a little lost into which option should be the best. Any advice/feedback?

Thanks

---

### Post by tjones00 on 2011-02-19
Ideally you want it setup as it was meant to be setup eg. probe_mask with hdmi:NVidia.



Second best option is a plughw type of filter/mixer to ensure audio compatibility with your receiving hardware. eg. dmix asound.conf, or a static alsa sink to plughw via pulseaudio. You could even try type plug with a straight hw call in asound.conf.



Third best option is a basic hw output eg. hw definition in asound.conf You could even look at your eld data and determine what specific variables need to be set for your receiving hardware.

Some people have used the full dmixer example left in my earlier post and have had issues with multichannel audio. It really isn't one size fits all.

This link will give you all the information you need to setup a custom asound.conf.
[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

 

As to oss blogspot I tried his method on an identical system lenovo q150 and it didn't work for me. I got the weird audio (improper rate) but it never corrected itself automagically. So I think the correction he describes is dependent on the receiving hardware.

The alsa.conf change is the same as making an asound.conf and setting hw:1,7 as default. 

eg.

```
pcm.!default {
  type hw
  card NVidia
  device 7
} 
```

asound.conf and .asoundrc are methods of modifying the alsa base settings without having to sift through and edit the full alsa.conf file.

---

### Post by tjones00 on 2011-02-20
@bedege

Your last post got me interested as to where alsa gets it's definition for hdmi:NVidia from.

I started snooping around the conf files and found these to be of interest.

/usr/share/alsa/alsa.conf
/usr/share/alsa/cards/HDA-Intel.conf
/usr/share/alsa/pcm/hdmi.conf

Unfortunately, I will not have access to my own nvidia hdmi machine for another 2-3 weeks so I can't do any experimenting myself. 

It seems to me by modifying or coping the format or some of the sections of HDA-Intel.conf and hdmi.conf to an asound.conf(or editing the files directly but this will be overwritten with alsa upgrades/reinstalls) you may be able to properly tell snd-hda-intel what device to use for the default hdmi pcm in a case such as yours where the probe_mask does not work.

It may be as simple as hdmi:NVidia,7 but as I said I can't test anything myself.

I have no clue if you'll return to this thread so instead of posting walls of conf files and trying to link everything together I'll just leave it at that for now.

---

### Post by bedege on 2011-02-21
@tjones00

Thanks for all your support!
Well, I first tried what looked like the easiest solution, ie ossnotebook's solution and modified /usr/share/alsa/alsa.conf to make NVidia and 7 my default options. And it worked! Thus I'm now able to hear on my TV sounds of other audio application like exaile, listen and vlc, w/o the need to modify their individual settings.

Note however that I cannot play sound from several softs at the same time. It looks like once an application has grabbed the audio output, it doesn't want to share it with others... No a big issue, since my HTPC is mainly for watching movies, thus only one at a time. Still, another fix would be more elegant. Thus, I might give a try to the other solutions you offer, later.

---

### Post by bedege on 2011-02-22
Since it seams like the modprobe solution should be prefered, I'm gonna try to make it work...

First, I'm stumbling on a small issue. Rather than modifying the /etc/modprobe.d/sound.conf file each, and have to reboot my system, I'd rather use the modprobe command. However, once the system is started, I'm unable to unload the sound module. sudo modprobe -r snd-hda-intel gives an error message, something like "FATAL: Module snd_hda_intel is in use". Is there a way to force the unload, or is rebooting the system each time the only way forward?

Having said that, I followed your instruction and added:
> options snd-hda-intel mod_probe=-1,0x2since my working hdmi card is 1,7. Makes sense?

After running update-initramfs and rebooting, I see that the only sound card with NVidia is Card#1, and device 3 (I have another Intel sound card that shows up, under Card#0, though). So, I now have:
> 
aplay -D plughw:1,3 foo.wav    <== works

aplay -D plughw:NVidia,3 foo.wav   <== works

aplay -D hdmi:NVidia foo.wav    <== does not work
aplay: set_params:996: Channels count non available


Of course the audio applications do not work. Thus several questions come to mind:
- shouldn't I try to get rid of the card#0, so that alsa only offers *ONE* possible output for sound? If yes, what would be the syntax to "get rid of" card #0, in the "mod_probe=???,0x2" line? I saw some options like "index=-2", but that's greek to me...
- one some other [Ion/hdmi threads]("http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240"), I see that they also use "enable_msi=0". What's the use of that option? Might it be useful here?

All advice/comments welcome! Thks

---

### Post by tjones00 on 2011-02-22
Edit: As to your earlier post about only one app being able to output sound at a time I assume this is why pulseaudio was implemented ontop of alsa it allows multiple apps to access an alsa output at the same time.

As to modprobe odd that -r doesn't work did you try --remove?

Don't worry about the other card for now. 


That's interesting the mod_probe=-1,0x2 reducing the device count to just 1 (device 3) on the nvidia card.

Another interesting point is that plughw:1,3 or NVidia,3 works but hdmi:NVidia still doesn't work. hdmi:NVidia should be defaulting to device 3 on the nvidia card as described in HDA-Intel.conf.

contents of /usr/share/alsa/cards/HDA-Intel.conf

```
#
# Configuration for the Intel HD audio (ICH6/ICH7)
#

<confdir:pcm/front.conf>

HDA-Intel.pcm.front.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type softvol
	slave.pcm {
		type hw
		card $CARD
	}
	control {
		name "PCM Playback Volume"
		card $CARD
	}
}	

# default with dmix+softvol & dsnoop
HDA-Intel.pcm.default {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type asym
	playback.pcm {
		type plug
		slave.pcm {
			type softvol
			slave.pcm {
				@func concat
				strings [ "dmix:" $CARD ]
			}
			control {
				name "PCM Playback Volume"
				card $CARD
			}
		}
	}
	capture.pcm {
		type plug
		slave.pcm {
			type softvol
			slave.pcm {
				@func concat
				strings [ "dsnoop:" $CARD ]
			}
			control {
				name "Digital Capture Volume"
				card $CARD
			}
			min_dB -30.0
			max_dB 30.0
			resolution 121
		}
		# to avoid possible phase inversions with digital mics
		route_policy copy
	}
	hint.device 0
}

<confdir:pcm/surround40.conf>
<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>
<confdir:pcm/surround71.conf>

HDA-Intel.pcm.surround40.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround51.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround71.0 cards.HDA-Intel.pcm.front.0

<confdir:pcm/iec958.conf>

HDA-Intel.pcm.iec958.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type asym
	playback.pcm {
		type hooks
		slave.pcm {
			type hw
			card $CARD
			device 1
		}
		hooks.0 {
			type ctl_elems
			hook_args [
			{
				name "IEC958 Playback Default"
				lock true
				preserve true
				value [ $AES0 $AES1 $AES2 $AES3 ]
			}
			{
				name "IEC958 Playback Switch"
				lock true
				preserve true
				value true
			}
			]
		}
	}
	capture.pcm {
		type hooks
		slave.pcm {
			type hw
			card $CARD
			device 1
		}
		hooks.0 {
			type ctl_elems
			hook_args [
			{
				name "IEC958 Capture Switch"
				lock true
				preserve true
				value true
			}
			]
		}
	}
	hint.device 1
}

<confdir:pcm/hdmi.conf>

HDA-Intel.pcm.hdmi.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type hooks
	slave.pcm {
		type hw
		card $CARD
		device 3
	}
	hooks.0 {
		type ctl_elems
		hook_args [
		{
			name "IEC958 Playback Default"
			lock true
			preserve true
			value [ $AES0 $AES1 $AES2 $AES3 ]
		}
		{
			name "IEC958 Playback Switch"
			lock true
			preserve true
			value true
		}
		]
	}
	hint.device 3
}

<confdir:pcm/modem.conf>

HDA-Intel.pcm.modem.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type hw
	card $CARD
	device 6
	hint.show off
}
```

Notice the hdmi section <confdir:pcm/hdmi.conf> where is explicitly states device 3 and hints device 3. If you reset the system without the mod_probe you may be able to simply change this to device 7 to get hdmi:NVidia working.


Can you post /usr/share/alsa/pcm/hdmi:NVidia.conf if it exists on your system? I want to look at this file if it exists.

We might be able to fix hdmi:NVidia with a simple edit to this file as well.

---

### Post by bedege on 2011-02-23
Here are a couple of files to answer your questions.

1st, you were requesting the content of /proc/asound/NVidia/codec#1
```
Codec: Nvidia GPU 0b HDMI/DP
Address: 1
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000b
Subsystem Id: 0x10de0101
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04

```

Then, the output of aplay -l, once the mod_probe is in place 
```
bedege@HTubuntu:~/Bureau$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC662 rev1 Digital [ALC662 rev1 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  1: NVidia [HDA NVidia], périphérique 3 : NVIDIA HDMI [NVIDIA HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

```
which shows that only one device (#3) is listed under NVidia

The content of HDA-Intel.conf
```
#
# Configuration for the Intel HD audio (ICH6/ICH7)
#

<confdir:pcm/front.conf>

HDA-Intel.pcm.front.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type softvol
	slave.pcm {
		type hw
		card $CARD
	}
	control {
		name "PCM Playback Volume"
		card $CARD
	}
}	

# default with dmix+softvol & dsnoop
HDA-Intel.pcm.default {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type asym
	playback.pcm {
		type plug
		slave.pcm {
			type softvol
			slave.pcm {
				@func concat
				strings [ "dmix:" $CARD ]
			}
			control {
				name "PCM Playback Volume"
				card $CARD
			}
		}
	}
	capture.pcm {
		type plug
		slave.pcm {
			type softvol
			slave.pcm {
				@func concat
				strings [ "dsnoop:" $CARD ]
			}
			control {
				name "Digital Capture Volume"
				card $CARD
			}
			min_dB -30.0
			max_dB 30.0
			resolution 121
		}
		# to avoid possible phase inversions with digital mics
		route_policy copy
	}
	hint.device 0
}

<confdir:pcm/surround40.conf>
<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>
<confdir:pcm/surround71.conf>

HDA-Intel.pcm.surround40.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround51.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround71.0 cards.HDA-Intel.pcm.front.0

<confdir:pcm/iec958.conf>

HDA-Intel.pcm.iec958.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type asym
	playback.pcm {
		type hooks
		slave.pcm {
			type hw
			card $CARD
			device 1
		}
		hooks.0 {
			type ctl_elems
			hook_args [
			{
				name "IEC958 Playback Default"
				lock true
				preserve true
				value [ $AES0 $AES1 $AES2 $AES3 ]
			}
			{
				name "IEC958 Playback Switch"
				lock true
				preserve true
				value true
			}
			]
		}
	}
	capture.pcm {
		type hooks
		slave.pcm {
			type hw
			card $CARD
			device 1
		}
		hooks.0 {
			type ctl_elems
			hook_args [
			{
				name "IEC958 Capture Switch"
				lock true
				preserve true
				value true
			}
			]
		}
	}
	hint.device 1
}

<confdir:pcm/hdmi.conf>

HDA-Intel.pcm.hdmi.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type hooks
	slave.pcm {
		type hw
		card $CARD
		device 3
	}
	hooks.0 {
		type ctl_elems
		hook_args [
		{
			name "IEC958 Playback Default"
			lock true
			preserve true
			value [ $AES0 $AES1 $AES2 $AES3 ]
		}
		{
			name "IEC958 Playback Switch"
			lock true
			preserve true
			value true
		}
		]
	}
	hint.device 3
}

<confdir:pcm/modem.conf>

HDA-Intel.pcm.modem.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type hw
	card $CARD
	device 6
	hint.show off
}

```

and /usr/share/alsa/pcm/hdmi.conf
```
#
#  Hardware output from HDMI
#

pcm.!hdmi {
	@args [ CARD DEV AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_IEC958_CARD
				ALSA_PCM_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.pcm.iec958.card
			}
		}
	}
	@args.DEV {
		type integer
		default {
			@func igetenv
			vars [
				ALSA_IEC958_DEVICE
			]
			default {
				@func refer
				name defaults.pcm.iec958.device
			}
		}
	}
	@args.AES0 {
		type integer
		# consumer, not-copyright, emphasis-none, mode=0
		default 0x04
	}
	@args.AES1 {
		type integer
		# original, PCM coder
		default 0x82
	}
	@args.AES2 {
		type integer
		# source and channel
		default 0x00
	}
	@args.AES3 {
		type integer
		# fs=48000Hz, clock accuracy=1000ppm
		default 0x02
	}
	type empty
	slave.pcm {
		@func refer
		name {
			@func concat
			strings [
				"cards."
				{
					@func card_driver
					card $CARD
				}
				".pcm.hdmi." $DEV ":"
				"CARD=" $CARD ","
				"AES0=" $AES0 ","
				"AES1=" $AES1 ","
				"AES2=" $AES2 ","
				"AES3=" $AES3
			]
		}
	}
	hint {
		show {
			@func refer
			name defaults.namehint.basic
		}
		description "HDMI Audio Output"
		device $DEV
	}
}

```

Note that I have no /usr/share/alsa/pcm/hdmi:NVidia.conf. The content of this directory is 
```
bedege@HTubuntu:~/Bureau$ ls /usr/share/alsa/pcm/
center_lfe.conf
dsnoop.conf
modem.conf
surround41.conf
default.conf
front.conf
rear.conf
surround50.conf
dmix.conf
hdmi.conf
side.conf
surround51.conf
dpl.conf
iec958.conf
surround40.conf
surround71.conf

```

Hope this helps making my Ion2 rock :guitar:

---

### Post by tjones00 on 2011-02-23
I'm still mystified as to why your hdmi:NVidia doesn't work when you used the modprobe to reduce it to a working device 3 config. Maybe it has something to do with the french system. But that would be pretty far fetched since all config files should still be in english or whatever tech english is used.

The reasons for why those files are of interest.

/proc/asound/NVidia/codec#1

This is the file that the probe_mask method (without the mod probe) tries to get snd-hda-intel to use the codec#1. It looks fine to me but I can't compare it to the other codec files in that folder. So I forget which value actually changes with device.


/usr/share/alsa/cards/HDA-Intel.conf

This is the configuration file for HDA-Intel aka snd-hda-intel the module used for nvidia hdmi audio. As I stated in my last post you can see how it defaults to device 3.


/usr/share/alsa/pcm/hdmi:NVidia.conf that doesn't exist
/usr/share/alsa/pcm/hdmi.conf

From exploring these we now know hdmi:NVidia isn't a discrete pcm otherwise it would have a config file.

hdmi.conf tells us that typing hdmi as a device defaults to defaults.pcm.iec958.card as defined in HDA-Intel.conf and alsa.conf.

Now we need to test hdmi to confirm it is a pcm type therefore without a probe_mask or mod_probe aka nvidia hdmi over 1,7 the following should be true.

aplay -D hdmi:NVidia,7 
aplay -D hdmi:1,7

Both of these should work if you take a closer look at hdmi.conf and HDA-Intel.conf.

Since hdmi:NVidia is ideally the format we want to use since it should be a standard the real fix would be to remove all non working probe_masks/modprobe etc and to change the default suggestions for hdmi.

hdmi.conf does not suggest any devices just a card call that appears to be replaced once hdmi:NVidia is used. HDA-Intel.conf appears to be the file that contains the device suggestion.

Backup your HDA-Intel.conf and replace it with this.

```
 
#
# Configuration for the Intel HD audio (ICH6/ICH7)
#

<confdir:pcm/front.conf>

HDA-Intel.pcm.front.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type softvol
	slave.pcm {
		type hw
		card $CARD
	}
	control {
		name "PCM Playback Volume"
		card $CARD
	}
}	

# default with dmix+softvol & dsnoop
HDA-Intel.pcm.default {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type asym
	playback.pcm {
		type plug
		slave.pcm {
			type softvol
			slave.pcm {
				@func concat
				strings [ "dmix:" $CARD ]
			}
			control {
				name "PCM Playback Volume"
				card $CARD
			}
		}
	}
	capture.pcm {
		type plug
		slave.pcm {
			type softvol
			slave.pcm {
				@func concat
				strings [ "dsnoop:" $CARD ]
			}
			control {
				name "Digital Capture Volume"
				card $CARD
			}
			min_dB -30.0
			max_dB 30.0
			resolution 121
		}
		# to avoid possible phase inversions with digital mics
		route_policy copy
	}
	hint.device 0
}

<confdir:pcm/surround40.conf>
<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>
<confdir:pcm/surround71.conf>

HDA-Intel.pcm.surround40.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround51.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround71.0 cards.HDA-Intel.pcm.front.0

<confdir:pcm/iec958.conf>

HDA-Intel.pcm.iec958.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type asym
	playback.pcm {
		type hooks
		slave.pcm {
			type hw
			card $CARD
			device 1
		}
		hooks.0 {
			type ctl_elems
			hook_args [
			{
				name "IEC958 Playback Default"
				lock true
				preserve true
				value [ $AES0 $AES1 $AES2 $AES3 ]
			}
			{
				name "IEC958 Playback Switch"
				lock true
				preserve true
				value true
			}
			]
		}
	}
	capture.pcm {
		type hooks
		slave.pcm {
			type hw
			card $CARD
			device 1
		}
		hooks.0 {
			type ctl_elems
			hook_args [
			{
				name "IEC958 Capture Switch"
				lock true
				preserve true
				value true
			}
			]
		}
	}
	hint.device 1
}

<confdir:pcm/hdmi.conf>

HDA-Intel.pcm.hdmi.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type hooks
	slave.pcm {
		type hw
		card $CARD
		device 7
	}
	hooks.0 {
		type ctl_elems
		hook_args [
		{
			name "IEC958 Playback Default"
			lock true
			preserve true
			value [ $AES0 $AES1 $AES2 $AES3 ]
		}
		{
			name "IEC958 Playback Switch"
			lock true
			preserve true
			value true
		}
		]
	}
	hint.device 7
}

<confdir:pcm/modem.conf>

HDA-Intel.pcm.modem.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type hw
	card $CARD
	device 6
	hint.show off
}

```

Remove any asound.conf or .asoundrc you might possibly have and reboot.

Then test hdmi:NVidia

If that doesn't work there are a couple more things we can try.

---

### Post by bedege on 2011-02-25
Hi there
Just tried the solution you proposed:
- removed modprobe and reran update-initramfs
- edited HDA-Intel.conf and changed device 3 to 7, per your file (see post #31)
- rebooted computer
- checked with aplay: NVidia again shows 4 devices (3, 7, 8 and 9)
- tested the following:```

aplay -D plughw:1,7 foo.wav        <== works
aplay -D plughw:NVidia,7 foo.wav   <== works
aplay -D hdmi:NVidia foo.wav       <== doesn't work
aplay: set_params:996: Channels count non available

```
So, we're back to square one, in term of making alsa work with modprobe.

I'm still unsure why this solution should be prefered to modifying /usr/share/alsa/alsa.conf per ossnotebook blog. This later solution worked for me. I guess I don't know enough about alsa configuration to truly grip the subttle differences between all those configurations...

---

### Post by tjones00 on 2011-02-26
...I just got that "I've been chasing my tail feeling"

Well I was about to post how to edit the defaults for iec958.card and device (digital audio) when I came across this in alsa.conf. 

```
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
```

These defaults are called upon in hdmi.conf.

```
pcm.!hdmi {
	@args [ CARD DEV AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
		default {
			@func getenv
			vars [
				ALSA_IEC958_CARD
				ALSA_PCM_CARD
				ALSA_CARD
			]
			default {
				@func refer
				name defaults.pcm.iec958.card
			}
		}
	}
	@args.DEV {
		type integer
		default {
			@func igetenv
			vars [
				ALSA_IEC958_DEVICE
			]
			default {
				@func refer
				name defaults.pcm.iec958.device
			}
		}
	}
```

As you know the the fix that worked for you redefined these earlier in the file.

```
defaults.pcm.card NVidia
defaults.pcm.device 7
```

My assertion that it was equivalent to hw:1,7 is incorrect because this also redefines the defaults for iec958/hdmi. This fix should actually properly correct the hdmi:NVidia or strictly hdmi output as well.

eg. 
aplay -D hdmi:NVidia should work
aplay -D hdmi should work

So if that works for you then it is your definitive fix after all.

My apologies for not spotting this relationship earlier on.

This may also work.

/usr/share/alsa/alsa.conf

```
defaults.pcm.iec958.card NVidia
defaults.pcm.iec958.device 7
```

Instead of redefining your entire system to use nvidia,7 as defaults.

If anybody trying this method has issues just make a similar HDA-Intel.conf edit to ensure the proper device is used since HDA-Intel.conf does try to explicitly redefine the device as 3.

---

### Post by bedege on 2011-02-26
Well, I reverted to the configuration I had in post #27, ie
- I returned HDA-Intel.conf to its pristine state (device is back to its default value of 3)
- I edited  /usr/share/alsa/alsa.conf to change
```
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0

```
to
```
defaults.ctl.card NVidia
defaults.pcm.card NVidia
defaults.pcm.device 7

```
and again all my applications (exaile, listen, totem and vlc) are able to play audio thru my TV in hdmi.

More interesting
```

aplay -D plughw:1,7 foo.wav        <== works
aplay -D plughw:NVidia,7 foo.wav   <== works
aplay foo.wav                      <== works
aplay -D hdmi:NVidia foo.wav       <== doesn't work
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.HDA-Intel.pcm.hdmi.7:CARD=NVidia,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: Aucun fichier ou dossier de ce type
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: Aucun fichier ou dossier de ce type
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hdmi:NVidia
aplay: main:608: Erreur d'ouverture audio: Aucun fichier ou dossier de ce type
aplay -D hdmi foo.wav              <== doesn't work
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.HDA-Intel.pcm.hdmi.7:CARD=NVidia,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: Aucun fichier ou dossier de ce type
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: Aucun fichier ou dossier de ce type
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hdmi
aplay: main:608: Erreur d'ouverture audio: Aucun fichier ou dossier de ce type

```
For the later two commands, aplay complains about my alsa config; but I do not understand much of it...

---

### Post by ScottSatkin on 2011-02-27
I am having the same issue with an Nvidia 8400GS.  However, I cannot get alsa to even list the nvidia card as an audio output option:

```
sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/scott not ours.
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have tried installing the latest alsa and nvidia drivers which has not helped.  Any advice would be greatly appreciated!

---

### Post by bedege on 2011-02-27
> **ScottSatkin said:**
> I am having the same issue with an Nvidia 8400GS.  However, I cannot get alsa to even list the nvidia card as an audio output option:

```
sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/scott not ours.
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have tried installing the latest alsa and nvidia drivers which has not helped.  Any advice would be greatly appreciated!

Hi, what Ubuntu release and kernel version do you use? I'm using 10.04 (Lucid Lynx) with kernel upgraded to 2.6.36.

---

### Post by ScottSatkin on 2011-02-27
> **bedege said:**
> Hi, what Ubuntu release and kernel version do you use? I'm using 10.04 (Lucid Lynx) with kernel upgraded to 2.6.36.

I was using 10.10 with kernel: 2.6.35-25-generic, I just upgraded to 2.6.35-27-generic which did not help.

---

### Post by bedege on 2011-03-04
Can you see your card when running 'lshw'?

---

### Post by ScottSatkin on 2011-03-04
Thanks for following up Bedege!

> **bedege said:**
> Can you see your card when running 'lshw'?

The Nvidia card shows up when running lshw under the PCI section:
```

*-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:8000(size=4096) memory:f8700000-fe7fffff ioport:bfe00000(size=536870912)
           *-display
                description: VGA compatible controller
                product: G98 [GeForce 8400 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:fa000000-fbffffff ioport:8c00(size=128) memory:fe7e0000-fe7fffff

```

However, it does not appear as an audio device, the only audio device I have is the Intel onboard audio controller:

```

*-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:febf8000-febfbfff

```

Any advice would be greatly appreciated!

---

### Post by bedege on 2011-03-04
I wish I could *really* help, but when other gurus like tjones00 are away, I admit I'm more or less speechless...

Couple of commands listed on some "my hdmi doesn't work" page. It might help pinpoint what's wrong with ubuntu on your system.

```

cat /proc/asound/cards
lspci | grep -i audio
lsmod | grep snd
asoundconf-gtk

```

Also, does your system's sound thru hdmi work with other OS like XP, Vista or Seven?

---

### Post by ScottSatkin on 2011-03-04
> **bedege said:**
> I wish I could *really* help, but when other gurus like tjones00 are away, I admit I'm more or less speechless...

Couple of commands listed on some "my hdmi doesn't work" page. It might help pinpoint what's wrong with ubuntu on your system.

```

cat /proc/asound/cards
lspci | grep -i audio
lsmod | grep snd
asoundconf-gtk

```



```

$ sudo cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 45

$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

$ lsmod | grep snd
snd_hda_codec_analog    59649  1 
snd_hda_intel          22235  0 
snd_hda_codec          87552  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  9 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm

```

And... I get an error running asoundconf-gtk:

```

$ sudo asoundconf-gtk
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

```

I have no ~/.asoundrc file, perhaps this is part of the issue?

> Also, does your system's sound thru hdmi work with other OS like XP, Vista or Seven?

Another OS...  I wouldn't dare install Windows!  :)

Thanks for the continued help, any further advice is greatly appreciated!

---

### Post by bedege on 2011-03-04
> **ScottSatkin said:**
> 
Another OS...  I wouldn't dare install Windows!  :)


I understand, I'm on the same boat here!

Still, are you sure your NVidia card is supposed to be a sound card, and not only a GPU?

---

### Post by BicyclerBoy on 2011-03-04
@Scott

The G98 8400GS does not have any HDMI audio codecs..This card uses a S/PDIF header cable from mobo soundcard to the video card..
The audio setup is completely separate from the video card.

It is rumoured that a GT218 GPU exists as a 8400GS , that would support HDMI audio.

---

### Post by ScottSatkin on 2011-03-05
> **BicyclerBoy said:**
> @Scott

The G98 8400GS does not have any HDMI audio codecs..This card uses a S/PDIF header cable from mobo soundcard to the video card..
The audio setup is completely separate from the video card.

It is rumoured that a GT218 GPU exists as a 8400GS , that would support HDMI audio.

Thank you BicyclerBoy!

I do have the S/PDIF header cable installed.  You say the "audio setup is completely separate from the video card."  Could you please provide me a bit more information on the audio setup process for this card?  I would have expected there to be an output option relating to the graphics card or S/PDIF.

Thanks!
-Scott

---

### Post by uschxc on 2011-03-05
hey everyone,

i've been working at this for a couple days now, this is what i have.

i have an asus at5iont with HDMI running through the receiver, and i can happily say i'm watching, and hearing, Boiler Room right now, but ubuntu isn't playing its sounds.  on to the config...

it seems that all ion2's are card 3, or device 1,7.  so aplay -D plughw:1,7 and aplay -D plughw:NVidia,7 work for me.

so my steps were,
1. install nVidia's closed drivers from the ubuntu repository.
2. install  the backported linux-alsa=driver-module-$(uname -r)
3. edited /etc/pulse/default.pa to include the line load-module module-alsa-source device=plughw1,7 (note the absence of a colon).  
4. edited /usr/share/alsa/alsa.conf, changing
defaults.ctl.card 0 to defaults.ctl.card NVidia
defaults.pcm.card 0 to defaults.pcm.card NVidia
defaults.pcm.device (err i forget) to defaults.pcm.device NVidia

restarted, and ubuntu came up without sound as usual.  however, vlc mplayer and totem played mp3s and video with audio.  XBMC would play music by setting "Audio Output Device" to default, and I got it to play audio with video files by setting "passthrough output device" to custom, using "plughw:1,7" as the custom device.  My receiver says DTS 5.1, so it seems like its sending the proper signal.

so at this point, i have all the audio i want except for ubuntu.  i can live with this but would rather it be working properly

now, to the colon i mentioned, its a typo and should be there.  without it, ubuntu doesn't understand and doesn't play its sounds through pulse.  the applications though seem to just reading the alsa.conf file and playing through NVidia without worrying about pulse.  XBMC is another animal though...

so with the correction (adding the colon) in /etc/pulse/default.pa, ubuntu comes up just fine with sounds and everything.  vlc mplayer and totem still work fine, music and video alike.  XBMC is still playing music fine, however audio now isn't working with video.  I tried changing the "passthrough output device" to all of the options including the custom "plughw:1,7" and "plughw:NVidia" and none of them work.  I hear the menu sounds in XBMC, so it seems to be using only alsa i guess for those sounds.  

so does anyone have an idea whats going on or what to try?

---

### Post by bedege on 2011-03-05
> **uschxc said:**
> 
4. edited /usr/share/alsa/alsa.conf, changing
defaults.ctl.card 0 to defaults.ctl.card NVidia
defaults.pcm.card 0 to defaults.pcm.card NVidia
defaults.pcm.device (err i forget) to defaults.pcm.device NVidia

restarted, and ubuntu came up without sound as usual.  however, vlc mplayer and totem played mp3s and video with audio.

Have similar kind of ion2 hardware (mine is a Jetway, not Asus).
Couple of questions:
- did you try fiddling with the mod_probe thing? It did not work for me at all, so I was curious if that applied to all ion2 cards.
- as for editing the alsa.conf file, shouldn't defaults.pcm.device be set to '7' and not 'NVidia'?

Besides that, I cannot really help re. systems sounds. I'm running Xubuntu, which doesn't play much of such sounds at all. Besides that, sound works in vlc, exaile and listen for me, like for you. Haven't tried xbmc yet.

---

### Post by Ted_C on 2011-03-07
> so with the correction (adding the colon) in /etc/pulse/default.pa,  ubuntu comes up just fine with sounds and everything.  vlc mplayer and  totem still work fine, music and video alike.  XBMC is still playing  music fine, however audio now isn't working with video.  I tried  changing the "passthrough output device" to all of the options including  the custom "plughw:1,7" and "plughw:NVidia" and none of them work.  I  hear the menu sounds in XBMC, so it seems to be using only alsa i guess  for those sounds.  

If you take a look at the XBMC log - whenever you choose hw:1,7 or plughw:1,7  - you'll notice an error about how the device is busy. 

It seems once the device has been defined in Pulseaudio - pulseaudio hogs the resource and wont let it go.

I have not found a solution for this in XBMC - as it doesn't give you the same options as VLC or Mplayer may give in choosing a specific layer to send the sound through (its either going to have to be Alsa or Pulse - it cant be both) - for passthrough at least

---

### Post by BicyclerBoy on 2011-03-07
@Scott
It is still HDMI audio but only a S/PDIF subset: AC3 DTS or 2 ch PCM <=96KHz.

The HDMI audio S/PDIF link cable is a direct link from the on-board mobo sound card to the HDMI connector. All the audio config is done in the normal non-HDMI way..
The video driver does nothing..

HDMI audio can be S/PDIF or multi-channel LPCM & HD versions of DTS & AC3.
You can only use 2ch PCM & AC3/DTS multi-channel with 8400GS.

Just select your default audio device as IEC958 output & it should just work..
I believe your onboard S/PDIF connector is live by default..

---

### Post by tjones00 on 2011-03-09
@bedege

> **bedege said:**
> Well, I reverted to the configuration I had in post #27, ie
- I returned HDA-Intel.conf to its pristine state (device is back to its default value of 3)
- I edited  /usr/share/alsa/alsa.conf to change
```
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0

```to
```
defaults.ctl.card NVidia
defaults.pcm.card NVidia
defaults.pcm.device 7

```and again all my applications (exaile, listen, totem and vlc) are able to play audio thru my TV in hdmi.

More interesting
```

aplay -D plughw:1,7 foo.wav        <== works
aplay -D plughw:NVidia,7 foo.wav   <== works
aplay foo.wav                      <== works
aplay -D hdmi:NVidia foo.wav       <== doesn't work
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition  'cards.HDA-Intel.pcm.hdmi.7:CARD=NVidia,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: Aucun fichier ou dossier de ce type
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: Aucun fichier ou dossier de ce type
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hdmi:NVidia
aplay: main:608: Erreur d'ouverture audio: Aucun fichier ou dossier de ce type
aplay -D hdmi foo.wav              <== doesn't work
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition  'cards.HDA-Intel.pcm.hdmi.7:CARD=NVidia,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: Aucun fichier ou dossier de ce type
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: Aucun fichier ou dossier de ce type
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hdmi
aplay: main:608: Erreur d'ouverture audio: Aucun fichier ou dossier de ce type

```For the later two commands, aplay complains about my alsa config; but I do not understand much of it...


Sorry I was in the process of traveling from Florida back to California and taking care of some local business.

This is suggesting it's not happy with hdmi.conf or HDA-Intel.conf which  you stated you've reverted back to their native configurations. It's  saying hdmi as a pcm type isn't working.

So lets take a look at the files again.

HDA-Intel.conf

```
#
# Configuration for the Intel HD audio (ICH6/ICH7)
#

<confdir:pcm/front.conf>

HDA-Intel.pcm.front.0 {
    @args [ CARD ]
    @args.CARD {
        type string
    }
    type softvol
    slave.pcm {
        type hw
        card $CARD
    }
    control {
        name "PCM Playback Volume"
        card $CARD
    }
}    

# default with dmix+softvol & dsnoop
HDA-Intel.pcm.default {
    @args [ CARD ]
    @args.CARD {
        type string
    }
    type asym
    playback.pcm {
        type plug
        slave.pcm {
            type softvol
            slave.pcm {
                @func concat
                strings [ "dmix:" $CARD ]
            }
            control {
                name "PCM Playback Volume"
                card $CARD
            }
        }
    }
    capture.pcm {
        type plug
        slave.pcm {
            type softvol
            slave.pcm {
                @func concat
                strings [ "dsnoop:" $CARD ]
            }
            control {
                name "Digital Capture Volume"
                card $CARD
            }
            min_dB -30.0
            max_dB 30.0
            resolution 121
        }
        # to avoid possible phase inversions with digital mics
        route_policy copy
    }
    hint.device 0
}

<confdir:pcm/surround40.conf>
<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>
<confdir:pcm/surround71.conf>

HDA-Intel.pcm.surround40.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround51.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround71.0 cards.HDA-Intel.pcm.front.0

<confdir:pcm/iec958.conf>

HDA-Intel.pcm.iec958.0 {
    @args [ CARD AES0 AES1 AES2 AES3 ]
    @args.CARD {
        type string
    }
    @args.AES0 {
        type integer
    }
    @args.AES1 {
        type integer
    }
    @args.AES2 {
        type integer
    }
    @args.AES3 {
        type integer
    }
    type asym
    playback.pcm {
        type hooks
        slave.pcm {
            type hw
            card $CARD
            device 1
        }
        hooks.0 {
            type ctl_elems
            hook_args [
            {
                name "IEC958 Playback Default"
                lock true
                preserve true
                value [ $AES0 $AES1 $AES2 $AES3 ]
            }
            {
                name "IEC958 Playback Switch"
                lock true
                preserve true
                value true
            }
            ]
        }
    }
    capture.pcm {
        type hooks
        slave.pcm {
            type hw
            card $CARD
            device 1
        }
        hooks.0 {
            type ctl_elems
            hook_args [
            {
                name "IEC958 Capture Switch"
                lock true
                preserve true
                value true
            }
            ]
        }
    }
    hint.device 1
}

<confdir:pcm/hdmi.conf>

HDA-Intel.pcm.hdmi.0 {
    @args [ CARD AES0 AES1 AES2 AES3 ]
    @args.CARD {
        type string
    }
    @args.AES0 {
        type integer
    }
    @args.AES1 {
        type integer
    }
    @args.AES2 {
        type integer
    }
    @args.AES3 {
        type integer
    }
    type hooks
    slave.pcm {
        type hw
        card $CARD
        device 3
    }
    hooks.0 {
        type ctl_elems
        hook_args [
        {
            name "IEC958 Playback Default"
            lock true
            preserve true
            value [ $AES0 $AES1 $AES2 $AES3 ]
        }
        {
            name "IEC958 Playback Switch"
            lock true
            preserve true
            value true
        }
        ]
    }
    hint.device 3
}

<confdir:pcm/modem.conf>

HDA-Intel.pcm.modem.0 {
    @args [ CARD ]
    @args.CARD {
        type string
    }
    type hw
    card $CARD
    device 6
    hint.show off
}
```

Ok a quick scan of that and you see this a couple times.

@args [ CARD AES0 AES1 AES2 AES3 ] these appear to be variables in the  config which are defined by various functions. eg card# channel count  rate etc all the stuff you be able to define with a pcm in asound.conf.

The following pcm configs are listed in the file.

HDA-Intel.pcm.front.0
HDA-Intel.pcm.default
HDA-Intel.pcm.surround40.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround51.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround71.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.iec958.0
HDA-Intel.pcm.hdmi.0
HDA-Intel.pcm.modem.0

The ones of interest are *.default and *.hdmi.0 and maybe *.iec958.0.

Now compare hdmi.0 and .default remember you've set nvidia,7 as default.


HDA-Intel.pcm.default
```
# default with dmix+softvol & dsnoop
HDA-Intel.pcm.default {
    @args [ CARD ]
    @args.CARD {
        type string
    }
    type asym
    playback.pcm {
        type plug
        slave.pcm {
            type softvol
            slave.pcm {
                @func concat
                strings [ "dmix:" $CARD ]
            }
            control {
                name "PCM Playback Volume"
                card $CARD
            }
        }
    }
    capture.pcm {
        type plug
        slave.pcm {
            type softvol
            slave.pcm {
                @func concat
                strings [ "dsnoop:" $CARD ]
            }
            control {
                name "Digital Capture Volume"
                card $CARD
            }
            min_dB -30.0
            max_dB 30.0
            resolution 121
        }
        # to avoid possible phase inversions with digital mics
        route_policy copy
    }
    hint.device 0
}
```

HDA-Intel.pcm.hdmi.0
```
HDA-Intel.pcm.hdmi.0 {
    @args [ CARD AES0 AES1 AES2 AES3 ]
    @args.CARD {
        type string
    }
    @args.AES0 {
        type integer
    }
    @args.AES1 {
        type integer
    }
    @args.AES2 {
        type integer
    }
    @args.AES3 {
        type integer
    }
    type hooks
    slave.pcm {
        type hw
        card $CARD
        device 3
    }
    hooks.0 {
        type ctl_elems
        hook_args [
        {
            name "IEC958 Playback Default"
            lock true
            preserve true
            value [ $AES0 $AES1 $AES2 $AES3 ]
        }
        {
            name "IEC958 Playback Switch"
            lock true
            preserve true
            value true
        }
        ]
    }
    hint.device 3
}
```

Notice with *.default the only arg is CARD but with hdmi there is also the AES definitions.

 @args [ CARD AES0 AES1 AES2 AES3 ] is also present in hdmi.conf itself  they actually seem to get their definitions from hdmi.conf.

hdmi.conf

```
#
#  Hardware output from HDMI
#

pcm.!hdmi {
    @args [ CARD DEV AES0 AES1 AES2 AES3 ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_IEC958_CARD
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.pcm.iec958.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_IEC958_DEVICE
            ]
            default {
                @func refer
                name defaults.pcm.iec958.device
            }
        }
    }
    @args.AES0 {
        type integer
        # consumer, not-copyright, emphasis-none, mode=0
        default 0x04
    }
    @args.AES1 {
        type integer
        # original, PCM coder
        default 0x82
    }
    @args.AES2 {
        type integer
        # source and channel
        default 0x00
    }
    @args.AES3 {
        type integer
        # fs=48000Hz, clock accuracy=1000ppm
        default 0x02
    }
    type empty
    slave.pcm {
        @func refer
        name {
            @func concat
            strings [
                "cards."
                {
                    @func card_driver
                    card $CARD
                }
                ".pcm.hdmi." $DEV ":"
                "CARD=" $CARD ","
                "AES0=" $AES0 ","
                "AES1=" $AES1 ","
                "AES2=" $AES2 ","
                "AES3=" $AES3
            ]
        }
    }
    hint {
        show {
            @func refer
            name defaults.namehint.basic
        }
        description "HDMI Audio Output"
        device $DEV
    }
}
```


This should result in the following defaults for @args [ CARD DEV AES0 AES1 AES2 AES3 ] 


CARD = defaults.pcm.ice958.card from alsa.conf
DEV = defaults.pcm.iec958.device from alsa.conf
hex values for aes
AES0 = 0x04 
AES1 = 0x82
AES2 = 0x00 (channel number)
AES3 = 0x02 (rate)

As to AES0 and AES1 these are the hints we have as to what they actually define.

    @args.AES0 {
        type integer
        # consumer, not-copyright, emphasis-none, mode=0
        default 0x04
    }
    @args.AES1 {
        type integer
        # original, PCM coder
        default 0x82


Perhaps AES1 is codec#. We need to figure out what these define google and alsa wiki have produced nothing for me so far.


Back to your output as quoted at the top of this post shows the following.

CARD = NVidia
DEV = 7
AES0 = 4 = 0x04
AES1 = 130 = 0x82
AES2 = 0 = 0x00
AES3 = 2 = 0x02

So it appears that for you hdmi:NVidia or hdmi is grabbing these hex defaults (aplay is just used a decimal output).

All of these AES variables should be gathered from the codec and eld  file and since we could never get the probemask working for you this  could be the root of your hdmi pcm doesn't work problem. You've stated  in this thread that you have found eld_valid 1 on your system so no eld  shouldn't be the issue.

The good news is we should be able to redefine all of these arg defaults within the hdmi.conf file eliminating any guesswork.

But hey whats could be easier than using plughw which we know works fine for your system.

HA how about this!

Set

defaults.ctl.card NVidia
 defaults.pcm.card NVidia
 defaults.pcm.device 7

back to 0,0,0 in alsa.conf

Backup/copy your hdmi.conf

Create a new /usr/share/alsa/pcm/hdmi.conf using the plughw format.


new /usr/share/alsa/pcm/hdmi.conf using plughw:NVidia:7
```
#
#  Bastardized plughw:NVidia,7 as hdmi
#  Original hdmi.conf can be found at <insert location>
#

pcm.!hdmi {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                NVidia
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_PCM_DEVICE
            ]
            default {
                7
            }
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.pcm.subdevice
        }
    }        
    type plug
    slave.pcm {
        type hw
        card $CARD
        device $DEV
        subdevice $SUBDEV
    }
    hint {
        show {
            @func refer
            name defaults.namehint.extended
        }
        description "Hardware device with all software conversions"
    }
}
```

Reboot and try aplay -D hdmi and hdmi:NVidia.

This will be funny if it works.  It should handle all necessary conversions and fix your hdmi definitions.

If this doesn't work for you then we need to play around with hdmi.conf and the AES variables a bit more.

---

### Post by driedsponge on 2011-03-12
I have pretty much the exact same issue as bedege.  So far I've modified the alsa.conf file and it works, so thanks for that.

I am currently fighting to get an HD-PVR working correctly, but once I do that, I can try and come back here and help out in any way possible.  Fixed is good, but correct is better.

I did try your last note, tjones00 and it didn't change anything, at least on mine.

---

### Post by tjones00 on 2011-03-12
Still no luck in finding actual definitions for the AES variables.

Anyway I did figure this out. the hdmi.conf is pretty much identical to iec958.conf and they use the same args. The args/variables themselves are called "iec958 pcm parameters".

For now revert everything back to normal.

We can try the xbmc reference. 

[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

> 
If you still have no sound, you can try editing/creating /etc/asound.conf: 
 pcm.!default hdmi:NVidia
pcm:iec958 hdmi:NVidia

Where they redefine the iec958 pcm output as hdmi:NVidia.

You could also try this calling upon iec958 directly.

[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

```
aplay -D iec958:CARD=NVidia,DEV=7 /path/to/wav.file
```

We can also mess around with iecset a tool written by the author of hda-intel if aplay iec958 doesn't want to work.

[http://www.spinics.net/linux/fedora/alsa-user/msg09440.html](http://www.spinics.net/linux/fedora/alsa-user/msg09440.html)


man iecset

```


iecset(1)                                                            iecset(1)



NAME
       iecset - Set or dump IEC958 status bits


SYNOPSIS
       iecset [options] [cmd arg...]


DESCRIPTION
       iecset  is  a  small  utility  to  set or dump the IEC958 (or so-called
       "S/PDIF") status bits of the specified sound card via ALSA control API.

       When iecset is started without arguments except for  options,  it  will
       show the current IEC958 status in a human-readable form.  When the com&#8208;
       mands are given in the arguments, they are parsed and the IEC958 status
       bits are updated.  The resultant status is shown as well.

       The commands consist of the command directive and the argument.  As the
       boolean argument, yes, no, true, false, or a digit number is allowed.


EXAMPLES
       iecset -Dhw:1
              Displays the current IEC958 status  bits  on  the  second  card.
              This is equivalent with -c 1.

       iecset -x
              Displays  the current IEC958 status bits in a style of the argu&#8208;
              ments for the PCM stream.  The output string can  be  passed  to
              the iec958 (or spdif) PCM type as the optional argument.

       iecset pro off audio off
              Sets  the  current  status to the consumer-mode and turns on the
              non-audio bit.  The modified status will be shown, too.


OPTIONS
       -D device
              Specifies the device name of the control to open

       -c card
              Specifies the card index to open.  Equivalent with -Dhw:x.

       -n index
              Specifies the IEC958 control element index,  in  case  you  have
              multiple IEC958 devices and need to choose one of them.

       -x     Dumps the status in the form of AESx bytes.

       -i     Reads  the  command  sequences from stdin.  Each line has single
              command.


COMMANDS
       professional <bool>
              The professional mode (true) or consumer mode (false).


       audio <bool>
              The audio mode (true) or non-audio mode (false).


       rate <int>
              The sample rate in Hz.


       emphasis <int>
              The emphasis: 0 = none, 1 = 50/15us, 2 = CCITT.


       lock <bool>
              Rate lock: locked (true), unlocked (false).  This command is for
              the professional mode only.


       sbits <int>
              Sample bits:  2 = 20bit, 4 = 24bit, 6 = undefined.  This command
              is for the professional mode only.


       wordlength <int>
              Wordlength: 0 = No, 2 = 22-18 bit, 4 = 23-19 bit, 5 = 24-20 bit,
              6 = 20-16 bit.  This command is for the professional mode only.


       category <int>
              Category:  the value is from 0 to 0x7f.  This command is for the
              consumer mode only.


       copyright <bool>
              Copyright: copyrighted (true),  non-copyrighted  (false).   This
              command is for the consumer mode only.


       original <boo>
              Original  flag:  original  (true), 1st generation (false).  This
              command is for the consumer mode only.


AUTHOR
       Takashi Iwai <tiwai@suse.de>



                                  23 Oct 2003                        iecset(1)
```


iecset --help

```
iecset: invalid option -- '-'
Usage: iecset [options] [cmd arg...]
Options:
    -D device   specifies the control device to use
    -c card     specifies the card number to use (equiv. with -Dhw:#)
    -n number   specifies the control index number (default = 0)
    -x          dump the dump the AESx hex code for IEC958 PCM parameters
    -i          read commands from stdin
Commands:
    professional (common)
    off = consumer mode, on = professional mode
    audio (common)
    on = audio mode, off = non-audio mode
    rate (common)
    sample rate in Hz (0 = not indicated)
    emphasis (common)
    0 = none, 1 = 50/15us, 2 = CCITT
    lock (prof.)
    off = rate unlocked, on = rate locked
    sbits (prof.)
    sample bits 2 = 20bit, 4 = 24bit, 6 = undef
    wordlength (prof.)
    0=no, 2=22-18bit, 4=23-19bit, 5=24-20bit, 6=20-16bit
    category (consumer)
    0-0x7f
    copyright (consumer)
    off = non-copyright, on = copyright
    original (consumer)
    off = 1st-gen, on = original

```


As for now instead of posting walls of config files that don't work perhaps we should meet up on irc or pm if you want to figure this out then we can come back to this thread with the solution.

---

### Post by d00derino on 2011-03-21
Word of advice, in alsamixer you need to enable the last item. It won't be on the screen, you need to press the right key to get to it. 

I didn't need to do any of this, just enable that last item and change the settings in System > Sound (HDMI output will suddenly appear!). If XBMC wasn't installing right now I'd tell you what it is, but I can't right now!

---

### Post by bedege on 2011-03-24
> **tjones00 said:**
> 
HA how about this!

Set

defaults.ctl.card NVidia
 defaults.pcm.card NVidia
 defaults.pcm.device 7

back to 0,0,0 in alsa.conf

Backup/copy your hdmi.conf

Create a new /usr/share/alsa/pcm/hdmi.conf using the plughw format.


new /usr/share/alsa/pcm/hdmi.conf using plughw:NVidia:7
```
#
#  Bastardized plughw:NVidia,7 as hdmi
#  Original hdmi.conf can be found at <insert location>
#

pcm.!hdmi {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                NVidia
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_PCM_DEVICE
            ]
            default {
                7
            }
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.pcm.subdevice
        }
    }        
    type plug
    slave.pcm {
        type hw
        card $CARD
        device $DEV
        subdevice $SUBDEV
    }
    hint {
        show {
            @func refer
            name defaults.namehint.extended
        }
        description "Hardware device with all software conversions"
    }
}
```

Reboot and try aplay -D hdmi and hdmi:NVidia.

This will be funny if it works.  It should handle all necessary conversions and fix your hdmi definitions.

If this doesn't work for you then we need to play around with hdmi.conf and the AES variables a bit more.

@tjones00

I gave your proposal a try last night.
1. Reverted back alsa.conf to its original state (no reference to NVidia nor 7)
2. Replaced hdmi.conf with your proposed file
3. Rebooted

Here is the output of several aplay commands
```
$ aplay -D plughw:1,7 Front_Center.wav 		<= works
Lecture en cours WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Taux 48000 Hz, Mono
$ aplay -D plughw:NVidia,7 Front_Center.wav 		<= works
Lecture en cours WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Taux 48000 Hz, Mono
$ aplay Front_Center.wav 			<= doesn't work
ALSA lib conf.c:1645:(snd_config_load1) /usr/share/alsa/pcm/hdmi.conf:21:6:Unexpected char
ALSA lib conf.c:3425:(snd_config_hook_load) /usr/share/alsa/cards/HDA-Intel.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286:(snd_config_hooks_call) function snd_config_hook_load_for_all_cards returned error: Argument invalide
Lecture en cours WAVE 'Front_Center.wav' : Signed 16 bit Little Endian, Taux 48000 Hz, Mono
$ aplay -D hdmi:NVidia Front_Center.wav     <= doesn't work
ALSA lib conf.c:1645:(snd_config_load1) /usr/share/alsa/pcm/hdmi.conf:21:6:Unexpected char
ALSA lib conf.c:3425:(snd_config_hook_load) /usr/share/alsa/cards/HDA-Intel.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286:(snd_config_hooks_call) function snd_config_hook_load_for_all_cards returned error: Argument invalide
ALSA lib conf.c:4600:(snd_config_expand) Unknown parameters NVidia
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hdmi:NVidia
aplay: main:608: Erreur d'ouverture audio: Argument invalide
$ aplay -D hdmi Front_Center.wav 		<= doesn't work
ALSA lib conf.c:1645:(snd_config_load1) /usr/share/alsa/pcm/hdmi.conf:21:6:Unexpected char
ALSA lib conf.c:3425:(snd_config_hook_load) /usr/share/alsa/cards/HDA-Intel.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286:(snd_config_hooks_call) function snd_config_hook_load_for_all_cards returned error: Argument invalide
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
aplay: main:608: Erreur d'ouverture audio: Aucun fichier ou dossier de ce type

```

Doesn't know exactly what other testing you'd like to do. In any case, I agree we should pm rather that fill up some more walls of config files with no clear end!

Thanks!

bedege

---

### Post by uniden9 on 2011-03-27
Thanks for the info, I have been trying to get sound through my hdmi cable for sometime.  I got the NVidia:hdmi working for my MSI Nvidia GTX 560 ti with this thread. Its hard to find information specifically on the Nvidia 500 series video cards, and hdmi sound, so I thought I post this. 

I just added the following to /etc/modprobe/sound.conf
options snd-hda-intel probe_mask=-1,0x2

The settings come from page 3 of this thread. I did validate that /proc/asound/NVidia/eld#1.0 was the sound card, device 7.  I did not have to change alsa configuration files(hdmi.conf or alsa.conf) or create asound.conf.  I'm running Alsa 1.0.24 on Ubuntu 10.10 x64, with no pulse audio installed. Nvidia video card is sound card 1, as 0 is the on board intel. I am using a few extra repositories for the newer alsa, ffmpeg, nvidia binary driver. I don't believe this is absolutely necessary, its just that I have been trying to get this to work for sometime, and I was running out of ideas. With a quick reboot and setting XBMC to use NVidia:hdmi for audio, and I have working sound. 

uname -a
Linux mediapc 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dpkg --list |grep alsa
ii  alsa-base                                      1.0.24+dfsg-0ubuntu1~10.10~ricotz1
ii  alsa-firmware                                  1.0.20-0medibuntu4.2
ii  alsa-firmware-loaders                          1.0.24.1-0ubuntu1~10.10~ricotz1
ii  alsa-oss                                       1.0.17-4
ii  alsa-source                                    1.0.24+dfsg-0ubuntu1~10.10~ricotz1
ii  alsa-tools                                     1.0.24.1-0ubuntu1~10.10~ricotz1
ii  alsa-tools-gui                                 1.0.24.1-0ubuntu1~10.10~ricotz1
ii  alsa-utils                                     1.0.24.2-0ubuntu3~10.10~ricotz1
ii  alsamixergui                                   0.9.0rc2-1-9
ii  bluez-alsa                                     4.69-0ubuntu2
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2
ii  gstreamer0.10-alsa                             0.10.30-2
ii  linux-alsa-driver-modules-2.6.35-28-generic    2.6.35-28.201103261604
dpkg --list |grep nvidia-current
ii  nvidia-current                                 270.29-0ubuntu1~maverick~xup2
ii  nvidia-current-modaliases                      270.29-0ubuntu1~maverick~xup2

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Mar 26 2011 for kernel 2.6.35-28-generic (SMP).

cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  270.29  Wed Feb 23 16:18:35 PST 2011
GCC version:  gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5)

Thanks again.

---

### Post by cartman85 on 2011-04-01
Have been trying to make this work for a while now... 
Version is good
```
xbmc@Buntu:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
GCC version:  gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 
xbmc@Buntu:~$ 
```


It lists all my devices nicely:

```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

xbmc@Buntu:~$ grep eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid           0
/proc/asound/NVidia/eld#1.0:eld_valid           0
/proc/asound/NVidia/eld#2.0:eld_valid           0
/proc/asound/NVidia/eld#3.0:eld_valid           1
xbmc@Buntu:~$ 

```

Trying to play audio through the device seems to "work" as well, but absolutely no sounds is being passed!

```

xbmc@Buntu:~$ aplay -D plughw:NVidia,3 /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
xbmc@Buntu:~$ 

```

What can be wrong? I have tried playing sound through the others as well, and all the devices are unmuted in alsamixer, but I still get nothing? :confused:

EDIT: Sound plays nice through the regular speakers on my pc, but although it looks to be playing through the hdmi via aplay, there comes no sound at all :\ Really don't understand this... Appreciate all help
ASUS GT430 (LP) Card...

---

### Post by cartman85 on 2011-04-02
HAH, big protip guys... Wiggle your HDMI connectors if this problem happens to anyone else.. Sound works now the "hard way".

But in xbmc I only get the "ticking" in the menus, but no sound on music playback..?

---

### Post by bedege on 2011-04-02
> **cartman85 said:**
> 
```

xbmc@Buntu:~$ grep eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid           0
/proc/asound/NVidia/eld#1.0:eld_valid           0
/proc/asound/NVidia/eld#2.0:eld_valid           0
/proc/asound/NVidia/eld#3.0:eld_valid           1
xbmc@Buntu:~$ 

```

Trying to play audio through the device seems to "work" as well, but absolutely no sounds is being passed!

```

xbmc@Buntu:~$ aplay -D plughw:NVidia,3 /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
xbmc@Buntu:~$ 

```

What can be wrong? I have tried playing sound through the others as well, and all the devices are unmuted in alsamixer, but I still get nothing? :confused:

EDIT: Sound plays nice through the regular speakers on my pc, but although it looks to be playing through the hdmi via aplay, there comes no sound at all :\ Really don't understand this... Appreciate all help
ASUS GT430 (LP) Card...
Hi
From the list of eld you give, sounds like you should use device#9 (see #1 post of this thread for explanation).
Could you check that the following works?
```
aplay -D plughw:NVidia,9 /usr/share/sounds/alsa/Front_Center.wav

```

---

### Post by mwl128340 on 2011-04-03
> **efflandt said:**
> After using 2 different nvidia cards GT 220 and GT 430 I settled on a somewhat different method than suggested here, which has worked for others including GTX cards.

After tjones00 Step 1 to verify if HDA NVidia devices show up in **aplay -l**,  run **alsamixer**, use F6 to pick HDA Nvidia, then unmute all the S/PDIF devices (press **m** for any that are MM so they become 00).

Then find out which one works for following, also trying 1,7 1,8 or 1,9 in place of 1,3 (use your nvidia card number in place of the 1):

```
aplay -D plughw:1,3 /usr/share/sounds/Front_Center.wav
```Then using **gksu gedit** (or **sudo nano** ) edit **/etc/pulse/default.pa** and add a line after the commented out line for alsa-sink for the card and device that worked for that aplay sound.  In my case it was 1,9, so I added the bolded line below:

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```Then reboot, play music in Rythmbox or other audio player, and see if one of the devices in the **Output** tab of **Sound Preferences** works for HDMI sound.  In my case I ended up with an extra device and the one that worked for HDMI was an HDA NVidia device that did not say HDMI.
Well, after months of configuring everything to get the hdmi audio to work with no luck, i wanted to send mad props out to efflandt and tjones00 for finally directing me in the right direction. i have a galaxy geforce gt220 card and all i needed to do all along was add the bolded line that efflandt pointed out. i am somewhat new to ubuntu, but the support from everyone in the community is nothing short of kick a$$. thank you all.

---

### Post by oooh on 2011-04-04
Too bad, stuck in step 1

```
Aplay -l 
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

Though I have my 1.0.23 alsa, and my 2.6.35-28generic

```
aplay --version
aplay: version 1.0.23 by Jaroslav Kysela <perex@perex.cz>
uname -r
2.6.35-28-generic

```

---

### Post by beermotor on 2011-04-12
> **oooh said:**
> Too bad, stuck in step 1

```
Aplay -l 
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

Though I have my 1.0.23 alsa, and my 2.6.35-28generic

```
aplay --version
aplay: version 1.0.23 by Jaroslav Kysela <perex@perex.cz>
uname -r
2.6.35-28-generic

```


this is exactly my problem, too ( although mine is ALC662 ). I suspect that it's my cheapo 42" Sharp TV ( purchase via a Dell deal for $700 back in mid-2008 ). It was a total ***** to get hdmi video working, had to do a bunch of EDID hacking of Xorg.conf and I'm thinking that probably is screwing with the audio.

I know the hardware works cause booting to XP works just fine, sound comes through w/out issues. :P Damn thee, legacyOS!

Anybody got some ideas on how to fix this? Xorg.conf scares me.

---

### Post by BicyclerBoy on 2011-04-13
@ last 2 posters..
The video driver is most important as it is providing the audio device for HDMI.

What's in the /var/log/Xorg.0.log file ?

Configuring the xorg.conf is not that bad if you have a good idea what the display accepts.
Find this from windoze or spec sheet.
Don't assume the VGA & HDMI/DVI capabilities are the same.

---

### Post by Sctmon on 2011-05-15
I followed the guide in the first post and now have my audio working over HDMI but the problem is that it is now the only output device listed and my on board audio has gone. The computer is now attached via HDMI to the TV in another room (previously VGA & audio) and also connected to a couple of monitors and local speakers (form analogue audio out) next to the computer.

My device list was as follows:
scott@MythtvFrontend:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 7: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 8: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 9: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0

(Card 1, device 8 was the one that worked for me)

but is now :
scott@MythtvFrontend:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

How can I have my on board analogue audio back and still keep the audio over HDMI which I will be using for mythTV?

---

### Post by declanmullen on 2011-05-21
Followed thread's modprobe.d and asound instructions but got same problem as bedege (post [#28]("http://ubuntuforums.org/showpost.php?p=10484555&postcount=28")). Ie "aplay -D plughw:NVidia,..." works but "aplay -D hdmi:NVidia ..." doesn't (complains about "Channels count non available"). 

Below are the details of what i've done, can anyone please tell me what i've done wrong and what I should have done. Many thanks.

The hardware consists of a Gigabyte MA78LMT-S2 motherboard (chipsets AMD 760G & SB710 which includes ATI 3000 video which I've disabled via the BIOS) with an Athlon II 420e. I've added a Gigabyte GV-N430OC-1GI Nvidia GT 430 card. I'm using the GT 430's HDMI interface to connect to the TV rather than using the motherboard's HDMI interface. Expecting HDMI sound from GT 430 to be heard from TV's speakers.

My OS distribution is the x86 32bit Mythbuntu edition of Ubuntu 10.10 with its proprietary nVidia drivers and the latest distribution updates. Pulse audio server not installed, only client present.

Software versions:
```

# uname -a
Linux pvr 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 i686 GNU/Linux

# cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
GCC version:  gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5)

# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

# dpkg --list |grep alsa
ii  alsa-base            1.0.23+dfsg-1ubuntu4 ALSA driver configuration files
ii  alsa-utils           1.0.23-2ubuntu3.4    Utilities for configuring and using ALSA
ii  gstreamer0.10-alsa   0.10.30-2            GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa 1.2.14-6ubuntu3      Simple DirectMedia Layer (with X11 and ALSA options)
ii  libsox-fmt-alsa      14.3.1-1build1       SoX alsa format I/O library

# dpkg --list | grep pulse
ii  libpulse-mainloop-glib0 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1  PulseAudio client libraries (glib support)
ii  libpulse0               1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1  PulseAudio client libraries
ii  vlc-plugin-pulse        1.1.4-1ubuntu1.5                                   PulseAudio plugin for VLC


```
Prior to setting probe mask:
```

# cat /etc/asound.conf
cat: /etc/asound.conf: No such file or directory

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# grep eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid           0
/proc/asound/NVidia/eld#1.0:eld_valid           0
/proc/asound/NVidia/eld#2.0:eld_valid           0
/proc/asound/NVidia/eld#3.0:eld_valid           1

```
Prior to the probe mask being applied the following commands failed to produce sound via the HDMI. I was expecting the last one (ie for "-D plughw:NVidia,9") to produce sound but it didn't :confused:
```

# aplay -D plughw:NVidia,3 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
# aplay -D plughw:NVidia,7 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
# aplay -D plughw:NVidia,8 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
# aplay -D plughw:NVidia,9 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```

Created /etc/asound.conf and populated with:
```

pcm.!default hdmi:NVidia

```

Created /etc/modprobe.d/sound.conf and populated with:
```

options snd-hda-intel probe_mask=0x108

```

Ran "update-initramfs -u"

Rebooted

After reboot:

```

# grep -H eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#3.0:eld_valid           1

# cat /proc/asound/NVidia/codec#3
Codec: Nvidia GPU 14 HDMI/DP
Address: 3
Function Id: 0x1
Vendor Id: 0x10de0014
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=3
  Converter: stream=6, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Ran "alsamixer" to un-mute all devices (ie the default device and the HDA NVidia device).

Following produce errors and NO sound:
```

# aplay -D hdmi:NVidia /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:1059: Channels count non available

# aplay -D hdmi:NVidia,0 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:1059: Channels count non available

# aplay -D hdmi /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:1059: Channels count non available

# aplay  /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:1059: Channels count non available

```

Following DOES produce sound via HDMI:
```
# aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```

The loaded modules:
```

# lsmod
Module                  Size  Used by
snd_hda_codec_nvhdmi    13615  1
tda18271               52053  1
af9013                 19970  2
nvidia               9331115  28
snd_hda_intel          22299  0
snd_hda_codec          87552  2 snd_hda_codec_nvhdmi,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
dvb_usb_af9015         24754  2
dvb_usb                14597  1 dvb_usb_af9015
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
dvb_core               88505  1 dvb_usb
agpgart                32075  1 nvidia
snd                    49038  8 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                 2607  0
i2c_piix4               8795  0
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
lp                      7342  0
parport                31492  1 lp
usbhid                 36978  0
hid                    67742  1 usbhid
ahci                   19198  2
r8169                  36777  0
libahci                21792  1 ahci
mii                     4425  1 r8169
pata_atiixp             3288  0

```

---

### Post by declanmullen on 2011-05-21
I left the probe mask in place, and based upon the below suggestion by tjones00, I changed my /etc/asound.conf to:
```

pcm.!default {
  type plug
  slave.pcm "dmix:0,3"
}

```
And now the following produces sound through the HDMI cable to the TV:
```

aplay /usr/share/sounds/alsa/Front_Center.wav

```
So I'm now happy. :)

> **tjones00 said:**
> 
[https://bbs.archlinux.org/viewtopic.php?pid=789152](https://bbs.archlinux.org/viewtopic.php?pid=789152)
[...]
The second entry on that thread seems more ideal to me since it has less definitions. I'd use that one first.

```
pcm.!default {
  type plug
  slave.pcm "dmix:1,7"
}
```


---

### Post by declanmullen on 2011-05-21
If the asound.conf of "pcm.!default hdmi:NVidia" had worked for me, does it have any advantages over the asound.conf I'm now using:
```

pcm.!default {
  type plug
  slave.pcm "dmix:0,3"
}

```
Ie are there any reasons why I should try to get "pcm.!default hdmi:NVidia" to work ?

---

### Post by dwiamo on 2011-06-02
hi, having the same issue as bedege

any more progress after your last updates?

Thanks

Dwiamo

---

### Post by bedege on 2011-06-02
Hi
Haven't really made any progress on my side. I've been able to find a workaround (see post #27 of this thread) that enables sound through HDMI.
I'm planning to upgrade to 11.04 sometimes, and see if that makes any difference.

What distro/hardware are you using?

---

### Post by e64462 on 2011-06-11
I'm on Ubuntu 10.10, stuck on trying to patch the kernel and alsa. I've never patched anything before, I was hoping someone could explain how to take the link provided in the first post: 

[http://git.kernel.org/?p=linux/kernel/git/tiwai/sound-2.6.git;a=commitdiff;h=38faddb1afdd37218c196ac3db1cb5fbe7fc9c75](http://git.kernel.org/?p=linux/kernel/git/tiwai/sound-2.6.git;a=commitdiff;h=38faddb1afdd37218c196ac3db1cb5fbe7fc9c75)

and apply it to my kernel. I've installed git-core, and already grabbed the kernel, but I don't know what to do with the link above. Do I copy and paste the contents to a file, or is there some saveas option I'm missing? I'm also wondering how updates will work after I apply the patch, will these steps need to be repeated after each update?

Thanks for the help!

---

### Post by BicyclerBoy on 2011-06-11
Kind warning..
If you don't know how to apply a patch file then don't be upset if it all goes pear shaped..

I would suggest a safer way to get the latest kernel/audio is from the an updated kernel ppa
[http://www.ubuntuupdates.org/ppa/kernel-ppa?dist=lucid](http://www.ubuntuupdates.org/ppa/kernel-ppa?dist=lucid)
**or**
add these to synaptic
[http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu)  maverick main
[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) maverick main

Change the maverick part to suit your release..
No guarantees this is a fix & 
**DO NOT** try adding both ppa & reloading/updating at the same time... 
Do the kernel ppa first & see if it fixes your problem.

---

### Post by e64462 on 2011-06-11
Okay well, the audio-dev ppa was already activated on my end, so I added the kernel ppa and did a 'sudo apt-get update && sudo apt-get upgrade'. It didn't update the kernel at all, but strangely it updated some pulseaudio and other sound-related programs. 

aplay -l still fails to detect my gtx 280 after a restart though; it only shows the hda intel devices on my system. 

So this brings me back to my original question, how do I follow this guide and patch the kernel? I'm not afraid of fubar'ing the thing, it takes ~20 minutes to format and retheme it, I just want to know how to get this done.

Also, thanks for the reply!

Best

---

### Post by BicyclerBoy on 2011-06-12
From memory..
The kernel ppa will not automatically replace anything because your current kernel package is a meta-package that points to a std latest version.

You need to use synaptic & look at all the packages from that source & pick a kernel image version (& headers etc).

---

### Post by e64462 on 2011-06-12
OK, well... I did as you suggested, and searched synaptic for "linux-image". It seems that I have the most recent kernel available even with the kernel ppa. The latest version I could find in Synaptic was 2.6.35-28-generic, which also happens to be the output of uname -r. 

Is this the latest version I should be seeing in Synaptic (with the ppa), and if so, do I have any other options? 

I mean, in the first post, it was indicated that a patched configuration was unnecessary, but aplay -l does not give the desired output. So I'm just trying to do my best to fill in the gaps here, if there's a better way I'm open to it.

Thanks Again

---

### Post by BicyclerBoy on 2011-06-13
Well when enable the kernel ppa I get..
 
linux-headers-2.6.38-8

as the latest kernel image & that is for lucid 10.04..

So something's wrong..

---

### Post by TenPlus1 on 2011-06-13
Have you tried installing 'pavucontrol' from synaptic package manager and selecting your HDMI sound output from the Configuration tab...

---

### Post by e64462 on 2011-06-13
Which kernel ppa are you referring to? Because the first one you linked me to was only available for 10.04 and 11.04. I'm attempting to use the launchpad.net/kernel-ppa you sent me.

Just so we can be sure I'm not delusional, here's some output

```
nick@desktop:~$ uname -r
2.6.35-28-generic
```


```
nick@desktop:~$ sudo apt-get update | grep kernel
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ maverick/main Translation-en_US
```

So the ppa is there. Next I started up Synaptic, and as you can see from the screenshot, there is no such package. So... where did I go wrong? Does the second ppa maybe not work for 10.10 either?

---

### Post by e64462 on 2011-06-13
@ TenPlus1

pavucontrol doesn't show an hdmi option, from what I can gather from the notes made in the first post, these patches are going to allow programs like pavucontrol to see the hdmi output device.

```
nick@desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

As you can see though, my system doesn't even believe it's there.

---

### Post by e64462 on 2011-06-13
Well, my guess appears to have been correct. For whatever reason, the maverick ppa doesn't contain what I need. I changed everything to lucid, and things went more swimmingly, for a minute. When I booted in to the new kernel, not only did aplay -l still not give the desired output, but several of my configurations were gone. I rebooted 3 times to make sure it wasn't just a glitch, same thing each time, no output from aplay, and fubar'ed configurations.

---

### Post by BicyclerBoy on 2011-06-13
Sorry. I'm running 10.04 & 11.04 boxes..
Did not check/realise that that ppa did not have maverick release kernel images..must be LTS only..

I don't see the harm in adding the natty kernel package from the kernel ppa only.

But don't go running apt-get dist-upgrades etc etc..
Use synaptic or synaptic-manager & browse & select specific packages only.

If you add/enable kernel ppa (natty) & carefully pick on (1) kernel image package (+headers) & then only install that package.
Then disable the ppa (untick in synaptic-manager).

That might work ?..

---

### Post by e64462 on 2011-06-13
Well, strangely, the natty ppa didn't work any better than the maverick ppa did. I tried that before trying the lucid ppa, which as I mentioned, didn't produce the desired output of aplay -l, either. I think this puts us back to trying to patch the kernel. Unless you have any other ideas?

---

### Post by BicyclerBoy on 2011-06-13
Well you only need to patch replace the alsa-driver module

The kernel ppa was an attempt to get everything in one hit.
The audio-dev ppa was an attempt to replace the alsa driver module (in kernel).

Maybe you will have to build alsa from latest source..
You'll need the linux-headers package that matches your kernel.

The instructions are in the sticky topic/thread first post..

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by e64462 on 2011-06-13
Wait, sorry I'm confused now tjones mentioned that we should be aware of this post before starting:

> [http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)

One segment of that post is:

> a) For all GPUs, and the MCP89 chipset: You need a fix for the PresenceDetect issue:

[http://git.kernel.org/?p=linux/kerne...1cb5fbe7fc9c75](http://git.kernel.org/?p=linux/kerne...1cb5fbe7fc9c75)

Status:
* In linux-next git
* In linux 2.6.36-rc1
* In linux 2.6.35
* In linux 2.6.34.2

Since that says "For all GPUs" doesn't that mean me, or am I misreading that post?

---

### Post by e64462 on 2011-06-14
Well, I've discerned a few more things after some digging. The link that I referenced in my previous post seems to be obsolete, correct me if I'm wrong. According to:

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=history;f=sound/pci/hda/patch_hdmi.c;h=bd0ae697f9c4118ae5947e1f6015d41cff3638ea;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=history;f=sound/pci/hda/patch_hdmi.c;h=bd0ae697f9c4118ae5947e1f6015d41cff3638ea;hb=HEAD)

the patches which tjones was referencing have been in mainline since July 2010, before the August release date of 10.10 Maverick. So, whatever is wrong here, it doesn't appear to be a patching issue.

I've also realized that my system doesn't even believe that my gtx280 has audio capabilities. here is some output:


```
nick@desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0000000 irq 49
 1 [Q9000          ]: USB-Audio - QuickCam Pro 9000
                      Logitech, Inc. QuickCam Pro 9000 at usb-0000:00:1d.7-5, high speed
```

```
nick@desktop:~$ lspci | grep idia
02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 280] (rev a1)
```

```
nick@desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Each of the above commands should have at least mentioned an nvidia audio controller, but that's clearly not the case. So, what would cause my system to completely ignore the patches?

---

### Post by mechanizedmedic on 2011-06-14
great thread with lots of great info! i'd like to add that folks should try the easy, but often overlooked, fixes before messing with modprobe. i only needed to do these simple things to get my card working.

[LIST=1]make sure your user is included in the "audio" group or any others you may need access to.```
$ groups
```
[*]ensure that your card is not muted in [alsamixer]("http://linux.dsplabs.com.au/alsamixer-and-alsactl-store-adjust-and-save-alsa-mixer-settings-p29/")
[*](kubuntu) make sure your HDMI output is given preference in your multimedia settings.
[/LIST]

these things worked for me until i would reboot. then pulseaudio would default back to the analog output. i found the fix for that issue [in THIS tutorial.]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240#If_that_doesn.27t_work...")

EDIT: xbmc also has [THIS]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller") excellent tutorial

---

### Post by BicyclerBoy on 2011-06-14
We should have checked if the driver is loaded..
That might explain the audio device absence.

lsmod | grep hdmi
look for something like..
snd_hda_codec_nvhdmi

Be aware that the name of this module changed at some point..

If it is not loaded try
modprobe snd_hda_codec_nvhdmi
then try
aplay -l
or look in
dmesg.

Did you see this package in the kernel ppa..
linux-image-generic-lts-backport-natty   (2.6.38.10)

---

### Post by e64462 on 2011-06-15
Interesting. The output should speak for itself, and since nothing I googled returned anything useful, I'm going to hope that you have an idea.

```
nick@desktop:~$ lsmod | grep hdmi
nick@desktop:~$
```

```
nick@desktop:~$ sudo modprobe snd-hda-codec-nvhdmi
FATAL: Error inserting snd_hda_codec_nvhdmi (/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-nvhdmi.ko): Invalid argument
```

```
nick@desktop:~$ sudo updatedb && sudo locate hdmi | grep $(uname -r)
/lib/modules/2.6.35-28-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.35-28-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.35-28-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-hdmi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-nvhdmi.ko
/usr/src/linux-headers-2.6.35-28-generic/include/config/snd/hda/codec/atihdmi.h
/usr/src/linux-headers-2.6.35-28-generic/include/config/snd/hda/codec/intelhdmi.h
/usr/src/linux-headers-2.6.35-28-generic/include/config/snd/hda/codec/nvhdmi.h
```

So the driver is clearly there, it just won't load. Have any idea how we get it to do so?

I also installed linux-image-generic-lts-backport-natty, and rebooted. The module is still not loaded, and does not load with modprobe either. I'm so confused -_-'

---

### Post by e64462 on 2011-06-16
First, a question. Do you think it matters that the hdmi audio functionality is supplied to the gtx280 by a cable which connects the s/pdif headers on my motherboard to the gpu, and not some sort of onboard audio controller on the gpu itself?

I decided to see if the module ever loaded, and so I booted into 10.10 with a live disk. The module did load without error, but I wasn't able to test anything further since I could not activate the proprietary nVidia driver. If I want to simulate those conditions with the gtx280 driver, I would need to format. This isn't the ideal solution for me just yet, so if you have some idea how to proceed, then I'm open to it.

Thanks again for the help

Best

---

### Post by BicyclerBoy on 2011-06-16
Yes it probably matters a whole lot..
The GTX280 is meant to have HDMI audio codecs/devices..(wrong!)

But if you have S/PDIF header (old style HDMI non HD audio) then this may mean that your GPU PCB version has the real HDMI audio disabled.

What nvidia driver release are you running 270 ?

The GTX260 (GT200) running 10.04 nvidia 260 shows no hdmi audio device.
Quote from wikipedia
> All GT21x GPUs also contain an audio processor inside and support 8 channel LPCM output through HDMI.
Quote from GTX280 datasheet (nvidia)
> Incorporates HDMI technology for combine video + audio output

I think the answer is that the GT200 GPU **does not** have real HDMI audio.
They are also not so good as video decode HTPC graphics cards (purevideo3) , very power hungry & noisy.

---

### Post by e64462 on 2011-06-16
```
nick@desktop:~$ cat /proc/driver/nvidia/version 
NVRM version: NVIDIA UNIX x86_64 Kernel Module  **270.41.06**  Mon Apr 18 14:53:56 PDT 2011
GCC version:  gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 
```

Does all of this mean that I'm out of luck, or is there still a way to trick ubuntu in to using the TV speakers?

---

### Post by BicyclerBoy on 2011-06-17
If the nvidia marketing dept was not so hell bent on obfuscating model specifications we would all understand capabilities of each model variant.

This means you can do non-HD audio over HDMI using an external soundcard (external to the videocard).
The videocard will combine the S/PDIF data stream with the video..

You link the mobo S/PDIF header to the video card S/PDIF header.

S/PDIF supports stereo PCM & multi-channel 5.1 AC3/DTS as digital pass thru'.
I think all are possible relayed over HDMI using the S/PDIF.

You add the cable & then configure mobo soundcard as IEC958 output..

---

### Post by e64462 on 2011-06-17
I had some notion of all of that already, what I can't seem to find is anyone who's successfully made that happen in Ubuntu. IDK if I've mentioned it in this topic (I've been trying to get support for this problem for years), but the cable is already connected and has been tested in Windows, where I can hear audio through the tv speakers. Now I just need to get it done in Ubuntu. I've never successfully found a guide or accurate description of the process which accomplishes this though. Do you have an idea or resource which might help, because Ubuntu support for this is lacking.

Thanks again for the help

Best

---

### Post by BicyclerBoy on 2011-06-17
The name for your HDMI audio is pre-Azalia..

What do you get with
speaker-test -D iec958 -c2

speaker test can only do LPCM, this means 2 ch stereo for S/PDIF.

Maybe you need to force the rate to 48KHz (as was posted earlier ?)
speaker-test -D iec958 -c2 -r 48000

---

### Post by e64462 on 2011-06-17
Hey BicyclerBoy, 

I had no success with either. Not that it seems to be much help, but the exact output is:

```
nick@desktop:~$ speaker-test -D iec958 -c2 -r 48000

speaker-test 1.0.23

Playback device is iec958
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
```

I had to adjust the rate in Windows to get it to work, I don't recall what the rates were exactly, but the range was limited. When using speaker-test, should I have made any alterations in Preferences->Sound, or anything similar?

---

### Post by BicyclerBoy on 2011-06-17
You have fitted the cable from mobo S/PDIF header to video card ? You must have because it works in windows...

Then the rate could be the problem.
Your TV or your soundcard may have limited capability.
Try the 2 ch stereo PCM CD rate..

speaker-test -D iec958 -c2 -r 44100

no settings in prefererence->sounds  need to be changed.

If this works then you will not be able to use AC3 with your TV over HDMI

---

### Post by e64462 on 2011-06-17
I sure have.. and the fitting has been tested in Windows.

---

### Post by e64462 on 2011-06-17
Still not a peep or a crack from these things. Just to get all of the 'duh' things out of the way... 

The channels: 'S/PDIF' and 'S/PDIF Default PCM' are unmuted in alsamixer

```
nick@desktop:~$ groups
nick adm dialout cdrom [COLOR="Red"]audio[/COLOR] plugdev lpadmin admin sambashare
```

And the volume on my hdtv is set to blaring.

From the command you suggested in the edit,

```
nick@desktop:~$ speaker-test -D iec958 -c2 -r 44100

speaker-test 1.0.24.2

Playback device is iec958
Stream parameters are 44100Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 44100Hz (requested 44100Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 169.998487
 0 - Front Left
 1 - Front Right
Time per period = 170.030198
```

Again, not much useful output here. Just seems to repeat this with no audio.

---

### Post by BicyclerBoy on 2011-06-17
Try some other weird rate  22050..
Try windows & spdifer & find the rates that work.

Maybe ubuntu & S/PDIF HDMI has never worked.
Maybe the latest nvidia driver has broken pre-azalia audio.
 

Give up & get a GT430/GT240/GT220 card..& give the GTX card to a gaming box.
Use the S/PDIF mobo bracket jack & connect direct to TV (if possible) ?

Buy a HT amp AVR & enjoy audio the way no TV can ever deliver..

---

### Post by e64462 on 2011-06-18
Hey, I double checked in Windows, looks like we've already tested two of the rates this setup 'supports': 44.1 KHz and 48.0 KHz, the only other rate which produces sound under Windows is 96.0 KHz. 

Unfortunately none of the other solutions are viable though, I'm just a starving college student with no money for extra hardware. 

I do appreciate the help, it's stumped me for a few years too, was just hoping there was more insight to be had out there. Like you said, maybe ubuntu just doesn't support this feature.

---

### Post by e64462 on 2011-06-18
This is a somewhat coincidental find, but audio through the TV speakers does work, just not the way I want it to. I plugged my mic in to the front jack of my computer, and my voice came through the TV speakers when I unmuted the appropriate channels in gnome-alsamixer! Do we have any ideas what might cause that, or a way to redirect the stream?

---

### Post by BicyclerBoy on 2011-06-18
Unmuted which channels ??
Not just the mic input ?

Un-mute everything with alsamixergui & pavucontrol & try speaker-test again.
Maybe speaker-test is still muted by other settings..

---

### Post by e64462 on 2011-06-18
Yeah, by "appropriate channels" I meant that I selected "Input Source" (the second one, see screenshot), and checked "Rec" under the second "Capture" channel. Then when I began speaking through my mic, it came through the TV speakers.

More exciting developments. For no apparent reason, I've literally done nothing differently than I've been doing for the last 2 years, the audio is transmitting through the tv speakers. Not in any pleasant way though. The behavior is completely erratic. For example, when I open pavucontrol, this obnoxious 'ringing buzz' starts blaring through the speakers. It stops as soon as I run 'speaker-test -D iec958 -c2 -r 48000' But if I run speaker-test again, I get nothing. Then if I open an mp3, the song plays, but with the same horrible 'ringing buzz' blaring simultaneously. After stopping the song, the 'ringing buzz' continues until I again run speaker-test. Keep in mind that speaker-test doesn't generate any of the 'pink noise' that it's supposed to. What's also weird, is that even though the mp3 is playing through my tv speakers, in Preferences->Sound, the "output device" is still set to my normal non-tv speakers. Also, when I run "speaker-test -D default" (which should test the normal speakers), I instead get audio output through the TV speakers. Not good output though, again that obnoxious ringing buzz.

---

### Post by BicyclerBoy on 2011-06-18
Can you stop the buzzing/ringing/harmonic clipping sound by muting all the inputs ?

Maybe your mobo audio setup needs a special modprobe mask/options.
What exactly is the mobo ?

Remember speaker-test does not share IEC958 & it does not always stop/close/exit cleanly...close the terminal & re-open.

What does
speaker-test -D default -c2 -r 48000
do ?

---

### Post by e64462 on 2011-06-18
The motherboard is an intel DX58SO here's a link.

```

http://www.newegg.com/Product/Product.aspx?Item=N82E16813121361
```

No special options were needed in Windows, but it might've been doing it automagically. Closing / re-opening terminal doesn't seem to help much. 

So... things seem to shuffle around a lot, as I play with various settings in gnome-alsamixer. I'm also currently trying to get a voice chat program working. When I was testing audio by playing an mp3, the sound came through my buddy's speakers. So somehow 'primary' audio is now being sent through the mic. I haven't figured out which combination of switches cause the outputs to shuffle though. I'll report back if I figure out anything else.

---

### Post by BicyclerBoy on 2011-06-19
Intel mobos:
That's an expense mobo & CPU..must be others using it..
Had to do a bios update on an Intel DP55WG after the network stopped with 10.04 kernel 2.6.32-33..
14 Bios updates in 2 years ..

Found this:

[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-April/015901.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-April/015901.html)
ALC889 has two SPDIF outputs: 0x06, 0x10. Board vendors can use either or both.
DX58SO uses 0x10, but the driver assumes 0x06. The safe solution is to add
0x10 as slave output to the existing 0x06.

[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-January/013831.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-January/013831.html)

The Intel DX58SO board works fine with model ALC883_3ST_6ch_INTEL

maybe you need the module modprobe options 

options snd-hda-intel model=3stack-6ch-intel
to your /etc/modprobe.d/alsa-base.conf file, 

sudo update-initramfs
to make it stick in the boot image.

where MODEL_NAME might be one of these:

[ALC883_3ST_2ch_DIG]    = "3stack-dig",
        [ALC883_3ST_6ch_DIG]    = "3stack-6ch-dig",
        [ALC883_3ST_6ch]        = "3stack-6ch",
        [ALC883_6ST_DIG]        = "6stack-dig",
        [ALC883_TARGA_DIG]      = "targa-dig",
        [ALC883_TARGA_2ch_DIG]  = "targa-2ch-dig",
        [ALC883_ACER]           = "acer",
        [ALC883_ACER_ASPIRE]    = "acer-aspire",
        [ALC888_ACER_ASPIRE_4930G]      = "acer-aspire-4930g",
        [ALC883_MEDION]         = "medion",
        [ALC883_MEDION_MD2]     = "medion-md2",
        [ALC883_LAPTOP_EAPD]    = "laptop-eapd",
        [ALC883_LENOVO_101E_2ch] = "lenovo-101e",
        [ALC883_LENOVO_NB0763]  = "lenovo-nb0763",
        [ALC888_LENOVO_MS7195_DIG] = "lenovo-ms7195-dig",
        [ALC888_LENOVO_SKY] = "lenovo-sky",
        [ALC883_HAIER_W66]      = "haier-w66",
        [ALC888_3ST_HP]         = "3stack-hp",
        [ALC888_6ST_DELL]       = "6stack-dell",
        [ALC883_MITAC]          = "mitac",
        [ALC883_CLEVO_M720]     = "clevo-m720",
        [ALC883_FUJITSU_PI2515] = "fujitsu-pi2515",
        [ALC888_FUJITSU_XA3530] = "fujitsu-xa3530",
        [ALC883_3ST_6ch_INTEL]  = "3stack-6ch-intel",
        [ALC1200_ASUS_P5Q]      = "asus-p5q",
        [ALC883_AUTO]           = "auto",

Try it from terminal first
sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel model=3stack-6ch-intel

---

### Post by e64462 on 2011-06-19
I'll try to apply this patch tonight, I'm currently in Windows investigating something. But that patch was released in 2009, are we sure it hasn't been introduced in to mainline, like the other patches in tjones' initial post?

---

### Post by BicyclerBoy on 2011-06-19
Even with the patch you still have to use the right module options.

I believe a lot of (if not most) laptop users need to use snd-hda-intel module options.
The actual h/w connection of the audio devices is not at all consistent because the audio mux/ADC/DACs are designed to be flexible/configurable.

If you search this forum you will find audio/sound problems relating to incorrect model detection..check all the posts by lidex..

---

### Post by e64462 on 2011-06-19
I see, sorry, misinterpreted your post. I'm now on unfamiliar ground again. 

I get the following output when I try to apply the options manually:

```
nick@desktop:~$ sudo rmmod snd-hda-intel
ERROR: Module snd_hda_intel is in use
```

And then when I try to do it at boot time (after adding the lines to /etc/modprobe.d/alsa-base.conf), I get:

```
nick@desktop:~$ sudo update-initramfs
You must specify at least one of -c, -u, or -d.

Usage: /usr/sbin/update-initramfs [OPTION]...
```

I'm guessing there is no way to circumvent the 'module in use' error, but what would be the proper options for update-initramfs, so that the options are loaded after a reboot?

---

### Post by BicyclerBoy on 2011-06-19
My mistake

sudo update-initramfs -u

This the correct format..
options snd-hda-intel model=3stack-6ch-intel

With ubuntu the module options in the .conf file will not do anything until you run update-initramfs or it is triggered by some other event like kernel update.

To be able to stop the snd-hda-intel module you have to stop all audio & maybe kill some other processes...

---

### Post by e64462 on 2011-06-19
Wow, really great progress. It's a little buggy, but absolutely usable. For whatever reason, speaker-test returns no output through the TV speakers (using the 'speaker-test -D iec958' options). However when I use Preferences->Sound to select the different output devices, I'm able to alternate between the various speaker sets without that obnoxious ringing. My normal speakers have completely quit functioning, as of this most recent restart, but I believe that has something to do with all the switches I was playing with in gnome-alsamixer. I'm going to restart and try again, but for the time being it seems that the model we chose has solved most, if not all, of my problems.

---

### Post by BicyclerBoy on 2011-06-19
That's a relief here as well..

It is possible that one of the other models is a better match..or that my posted model list is really out-of-date..


patch_realtek.c is the source code that seems to enumerates the current model options

---

### Post by e64462 on 2011-06-19
Yeah, there seems to be a completely manageable bug in either gnome-alsamixer / pavucontrol / alsa / pulseaudio, where when I switch on/off certain channels in gnome-alsamixer (specifically: Headphone, Front, Surround, Center, LFE) my main speakers are shut off, but unmuting the switch doesn't return audio. To return the audio I have to enter 'pavucontrol->Output Devices' and unmute the audio device from there. In other words, for whatever reason gnome-alsamixer will disable my main speakers, but not re-enable them. This is just a note for any other poor and unfortunate DX58SO users who find their way here, and manage to sift through my onslaught of retarded questions.

Thank you so much though BicyclerBoy, you're literally my hero. I would probably have your babies, if given the chance. I've been looking for support on this issue for years, and it finally seems (so easily, in retrospect) resolved. So really, thank you.

Since I've made so many apparently unnecessary changes in pursuit of this problem, I'll probably format tomorrow. I'll report back here if anything unexpected happens, but I suspect that simply setting the model parameter will quickly resolve any issues.

As one more note: speaker-test is still completely silent, even now when audio clearly transmits via S/PDIF. For example:

> nick@desktop:~$ aplay -L
...
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889 Digital
    IEC958 (S/PDIF) Digital Audio Output
...

And yet I don't hear a peep when I use the following command:

> nick@desktop:~$ speaker-test -D iec958 -c 2 -r 48000

Once again, thank you BicyclerBoy! I'm truly grateful!

Best Regards
Nick

---

### Post by BicyclerBoy on 2011-06-19
You are welcome..glad to have been able to help.
I'm sure we took the long way round...

Maybe the syntax was not right..maybe speaker-test has some problem with this sound device because of some driver problem.

speaker-test -Dplug:spdif -c2 -r 48000

If you setup your ubuntu install with the /home folder mounted in a separate partition you can minimise the damage/loss of re-installs/distro-upgrades.

I doubt you have done the install any harm..
You could just un-install the natty kernel then remove the kernel ppa.
You could need to re-run
sudo update-initramfs -u
although the kernel scripts should do this.

(or to update all kernel images in GRUB
sudo update-initramfs -d all -u  )

---

### Post by MrCorleone87 on 2011-06-20
Hey man, I have this problem with HDMI audio and I tried to follow your guide but I'm stuck at step 2. Basically I did update ALSA here [https://wiki.ubuntu.com/Audio/Instal...aDriverModules](https://wiki.ubuntu.com/Audio/Instal...aDriverModules) as you advised but then after typing grep eld_valid /proc/asound/NVidia/eld* in terminal all of my eld_valid are still 0. So I went to [http://http.download.nvidia.com/XFre...dmi-audio.html](http://http.download.nvidia.com/XFre...dmi-audio.html) and I've read the whole thing but I don't really get most of it as I'am pretty new to the Linux Community. So what could I do now? Is there a chance for a newbie like me to get this thing working? I'd be really really happy if this could be fixed because except for the sound problem I totally love Ubuntu.By the way I run the OS on Toshiba Satellite A660 Laptop Thanks in advance for any help!

---

### Post by BicyclerBoy on 2011-06-20
Points to note:
The HDMI audio ELD entries are generated from handshake/bi-directional comms between the video driver & the HDMI receiver (TV/monitor/AVR/HT-amp).
This may or may not be PlugNPlay (real time updated).

This means:
- receiver must be turned on
- receiver must be connected by HDMI
- nvidia X server must be running with active X screen
- alsa driver compatible with video driver

So you should make sure the X server starts/loads after the HDMI is powered up.

---

### Post by Tinnum on 2011-06-21
Could I have a bit of guidance please? - I am a raw nubie and have been struggling to get HDMI audio through an Asus ION5T motherboard. I can follow (just) this guidance until Step 3. My question is "Why use the probe mask for "0x108"? Is it because it is the fourth 'eld' result and it was the fourth device listed which was responsible for HDMI audio?. I had the "1" alongside the second line down when I confirmed which device was responsible for HDMI audio.
 
(Incidentally, when I load *alsamixer* I can see the HDMI card but cannot alter the configuartion other than to change the spdif from mute to unmute.)  Please help - in desperation........

---

### Post by BicyclerBoy on 2011-06-21
That bit mask is wrong..you should read further...
The mask should be <= 0x0F  (15 decimal)

A value of 0x08 (0%1000) would hide all but the 4th device.
I don't think the mask is really needed, it just hides the unusable devices.

Have you tried using speaker-test ?
You should read the nVidia hdmi audio document ?

---

### Post by Tinnum on 2011-06-21
Thanks so much for the quick response!! A voice in the darkness...
I have tried the speaker test without any success.
 
Also thanks for the advice about the Nvidea audio document....Is it on the Nvidea site or somewhere on this forum please (or are those the criteria for a search)/??

---

### Post by BicyclerBoy on 2011-06-21
What speaker-test cmd opts did you try ?

speaker-test -c 2 -r 48000 -D hw:1,9

Post #16 has the http URL to the nVidia HDMI doc.

The snd-hda-intel probemask has to allow for any mobo soundcard...
So if your nvidia hdmi audio is the 2nd soundcard then the probemask should look like
options snd-hda-intel probe_mask=-1,0x8 
if you what to hide hdmi logical codec IDs 0, 1 & 2.

Try
aplay -D hw:1,9 /usr/share/sounds/Front_Center.wav
(assuming hdmi is 2nd soundcard in aplay -l)

---

### Post by Tinnum on 2011-06-21
Many thanks for your effort . Will try and report back.
(used your recommended speaker test and although it seems to be generating a sound signal,no HDMI sound. I have analogue sound through my front ear phones)

---

### Post by BicyclerBoy on 2011-06-21
You had better post your 
aplay -l

maybe your hdmi devices appear as the 1st card.
change the 1 --> 0

---

### Post by Tinnum on 2011-06-21
Many thanks. I am afraid the Nvidea link was a bit beyond my comprehension!

This is what I got from sudo aplay -Lpulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC887 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output


Does that tell you anything...my brain is fried....
MANY THANKS IN ANTICIPATION

---

### Post by Tinnum on 2011-06-21
...And here is aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by BicyclerBoy on 2011-06-21
So your HDMI is the 2nd soundcard (Card 1)
The mobo ALC887 is card 0.

To clarify...
speaker-test -c 2 -r 48000 -D hw:1,9

this produces no sound from anywhere ?

You are running the nVidia driver (X server) & the gnome desktop is active on a monitor.

---

### Post by Tinnum on 2011-06-21
Not a peep.....
I am running x server  and gnome is active on desktop.

---

### Post by BicyclerBoy on 2011-06-21
alsamixer -c [I]1

[/I]check unmuted..
Probably need to go back to the step by step process of checks..
Have you checked the ELD /proc/asound/cardx/...
cat /proc/asound/card1/codec#3

It is possible your audio output could be on codec#0, 1, 2 (logical codec#)

---

### Post by Tinnum on 2011-06-21
Yep - unmuted on all 4 s/pdif channels.
Incidently I did not use the mask-probe as you thought it was probably unnecessary.
This is the last stage I got to:
$ grep eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid        0
/proc/asound/NVidia/eld#1.0:eld_valid        1
/proc/asound/NVidia/eld#2.0:eld_valid        0
/proc/asound/NVidia/eld#3.0:eld_valid        0
anthony@AntsLinux:~$

---

### Post by BicyclerBoy on 2011-06-21
cat /proc/asound/card1/codec#1


The probe mask just gets in the way by hiding the devices before you are sure which one to use..

speaker-test -c 2 -r 48000 -D hw:1,7

if the above works then your probe_mask = -1,0x2

Getting the right probe_mask will allow pulseaudio to work with HDMI device.
This is just a work-around...one day it may not be necessary.
If you don't use pulse then it does not matter as much.
As alsa will only allow (2) audio output streams per GPU, using different HDMI socket (if you have them) tricky; the probe_mask can expose only the (2) you might want to/can use...

---

### Post by Tinnum on 2011-06-21
Well an am bursting with joy!!! I am getting "white noise"  out to the speakers!!! Is that what I should have got?? Believe me after all this time even  white noise is music!!
Is there anything else I have to do now to get proper audio please?

---

### Post by BicyclerBoy on 2011-06-21
It's Pink 1/f noise .

If you want to use pulse-audio (a good idea)

The nvidia HDMI doc..
13.9.1. Adding Extra Outputs To PulseAudio
/etc/pulse/default.pa
Only add one..& you need this one.
load-module module-alsa-sink device=hw:1,7


If you have more than 1 HDMI output sockets AND you use a different output then you will then need to determine the exact codec#n that works &  edit the above pulse audio file.
Just use the same socket connector...

---

### Post by Tinnum on 2011-06-21
I only have one HDMI output  - 
If I am understadnign you correctly I need to enter "load-module module-alsa-sink device=hw:1,7" into a terminal??
I did and got "command not found" - or am I being too simplistic??  Sorry this learning curve is almost vertical....

---

### Post by BicyclerBoy on 2011-06-21
You should take the time & read the section of the nvidia doc..13.9.1

gksudo gedit /etc/pulse/default.pa

& add this in that file (at the end)...
```

load-module module-alsa-sink device=hw:1,7

```

logout/login..
Gnome sound preferences should then show (2) HDMI devices..select the second device as default output...
The app
pavucontrol
is much nicer than gnome sound prefs..

---

### Post by Tinnum on 2011-06-21
I cannot thank you enough for your patience! I am going to take a break now but will let you know the outcome and recommend you for a sainthood.......many thks

---

### Post by Tinnum on 2011-06-22
Hi Again.
I have followed your instructions (i believe) to the letter but still get no sound. The Gnome speaker icon is now showing "---".
This is now my aplay -l.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




Any clues as to what I have done wrong please??

---

### Post by BicyclerBoy on 2011-06-22
Did you use an modprobe option probe_mask ?
You do not need to & it could be better not to use one..

I understand the probe_mask could be used to allow pulse audio to work without requiring the editing of pulse config files..

But you have edited the pulse file default.pa & added "load-module module-alsa-sink device=hw:1,7" ???

Note that with Ubuntu you need to run this after any changes to modprobe.d/*.conf options.

[sudo] update-initramfs -u


But before you do anything.......
try the

---

### Post by Tinnum on 2011-06-22
[SIZE=2]Synopsis of what I did[/SIZE]
 

 [SIZE=2]**Steps 1 & 2** were almost exactly like your example[/SIZE]
 

 [SIZE=2]**Step 3**[/SIZE]
 [SIZE=2]I typed into a terminal:[/SIZE]
 
[SIZE=2]gksudo gedit /etc/modprobe.d/sound.conf[/SIZE] 

 [SIZE=2]an empty box opened up and I typed  in[/SIZE]
 [SIZE=2]options snd-hda-intel probe_mask=-1,0x2[/SIZE]  [SIZE=2]
and saved.[/SIZE] [SIZE=2]
Then ran 
[/SIZE]      [SIZE=2]sudo update-ininramfs -u[/SIZE]  [SIZE=2][B]

Step 4
[/B][/SIZE] [SIZE=2]I typed in terminal[/SIZE]      [SIZE=2]gksudo gedit /etc/pulse/default.pa[/SIZE]  [SIZE=2]added   [/SIZE]     [SIZE=2]load-module module-alsa-sink device=hdmi:NVidia[/SIZE]  [SIZE=2]in position  advised.[/SIZE]  [SIZE=2]Saved and closed[/SIZE]  [SIZE=2][B]
Next Step[/B][/SIZE]
 [SIZE=2]I then ran [/SIZE]     [SIZE=2]gksudo gedit /etc/pulse/default.pa[/SIZE]  [SIZE=2]and at the end typed in[/SIZE]     [SIZE=2]load-module module-alsa-sink device=hw:1,7[/SIZE]  [SIZE=2]then re-booted.................[/SIZE]

---

### Post by BicyclerBoy on 2011-06-22
When did I ever say to add
[SIZE=2]load-module module-alsa-sink device=hdmi:NVidia[/SIZE]


We want pulse audio working..

The confusion stems from this..
The physical codec ids are not fixed. They are allocated as exposed.
If the probe mask is used it changes the codec physical id needed in the default.pa file
Alsa only sees the codecs exposed by probe_mask.

For example (I believe):
logical[0,1,2,3] ==physical*[3,7,8,9]==mask value[1,2,4,8] but only if mask =0xf.
(the meaning of logical & physical is completely wrong/swapped)
1.
probe_mask value -1, 0x2
expose card1 pin codec #7 only to alsa.
one codec logical 1 == physical #3  device=hw1:3
alsa reports hw:1,3 but it connects to real logical 1 output.
2.
probe_mask value -1, -1
alsa will report first 2 codecs of each card.
card1 codec logical 0 == physical #3 device=hw1:3
card1 codec logical 1 == physical #7 device=hw1:7

3. complex ex
probe_mask -1,0x6
alsa will report logical 1 & 2
card1 codec logical 1 & 2 ==physical #3 & #7 device=hw1:3 & hw1:7

Therefore change your probe_mask to -1,-1

Speaking as a electronics h/w engineer The confusion is not helped by the complete stupid mixing up the meaning of logical & physical ids.

---

### Post by Tinnum on 2011-06-22
Sorry, I was confusing your advise by the guide put out by TJONES00.

Will try again  - really appreciate your help!!

---

### Post by Tinnum on 2011-06-22
.Thank you  thank you - sound nearly took my head off......I have sooo much to learn. You have been brilliant. Not quite sure what the problem was but will endeavor to find out. Thanks again!

---

### Post by BicyclerBoy on 2011-06-22
Glad it is working.

In the pulse default.pa file:
You can not have (2) "load module-alsa-sink" lines in the file because pulse always loads hw1:3 & alsa only allows max number =2.
So (2) entries == 3 alsa devices (bad) & pulse will fail.
The mask value 0x2 would have forced you to use a different hw1:3.

This thread has evolved as more h/w & info has become available.
There have also been alsa updates..
There are multiple solutions possible (linux in general) but incompatible.

All this means there is a moving target & you have to read the whole thread in context.
But I'm not sure the context can be understood unless you were following from the start.

Reading thru' the whole thread again has given me a headache..

---

### Post by TxRx on 2011-07-08
This is THE guide that resolves it every time for me. If I've tinkered about with other guides it screws up. If I flatten my install of 10.10 and go through this lot, it's perfect. 

Many thanks!!!

:KS:KS:KS:KS

---

### Post by soft_kitten on 2011-07-08
Thank you so much for your guide! Your instructions were both easy to follow and seemed to have accomplished the task. I did the steps except for "Remove any local pulseaudio/alsa settings" and "test the probemask after the reboot do the following" and after a reboot I got glorious sound from my monitor's speakers.

But it did remove my motherboard-supplied sound from the sound options. Oh well, good enough anyways.

---

### Post by sir4taye on 2011-07-21
It worked for me on my new Natty Narwhal 11.04 x64 install with onboard nvidia turned off in bios, but a geforce 210 512 installed. 

Natty Narwhal NVidia Geforce 11.04 hdmi Audio sound Working now!!!!

---

### Post by windscryer on 2011-08-30
Running 11.04 with a GT240. Followed this thread through from beginning, never found success, and managed to completely jack up my settings to the point where typing in 

```
grep eld_valid /proc/asound/NVidia/eld*
```gave me only one entry and it had a 0 for the end value.

Went back and UNdid everything I'd done and am now back to square one.

I currently can get sound when I do

```
aplay -D plughw:NVidia,9 /usr/share/sounds/alsa/Front_Center.wav
```(I tried it because that is the device listed by 

```
grep eld_valid /proc/asound/NVidia/eld* 
```.)

but testing my speakers in the sound preferences GUI gets me nothing, nor does running any sound-producing program.

So now that I'm once again effectively at step 3 of the OP's tutorial, does anyone have any suggestions for possible fixes?

Don't know if it's needed, but just in case my aplay -l is:

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Thanks in advance for anyone who can help me untangle this issue!

---

### Post by BicyclerBoy on 2011-08-31
gksudo gedit /etc/pulse/default.pa

& add this in that file (at the end)...
Make sure there is only one line with module-alsa-sink.
```

     load-module module-alsa-sink device=hw:1,9 

```
logout/login..
Gnome sound preferences should then show (2) HDMI devices..select the second device as default output...
This is because pulse-audio enumerates the first alsa device exposed (hw1,3).
This behaviour can be changed by using the probe mask value.

---

### Post by windscryer on 2011-09-01
> **BicyclerBoy said:**
> gksudo gedit /etc/pulse/default.pa

& add this in that file (at the end)...
Make sure there is only one line with module-alsa-sink.
```

     load-module module-alsa-sink device=hw:1,9 

```logout/login..
Gnome sound preferences should then show (2) HDMI devices..select the second device as default output...
This is because pulse-audio enumerates the first alsa device exposed (hw1,3).
This behaviour can be changed by using the probe mask value.

Thanks for the reply! Sorry it took me a day to get back here.

Okay, I have the two devices showing in my preferences, but picking the second (under the Output tab, the Hardware tab still only lists one device) still doesn't give me sound except through specific commands in terminal. I also double-checked and everything is unmuted in alsamixer. Is there anything else I can tweak?

Actually...

When you say there should only be one line with module-alsa-sink, are you including

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-udev-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
```that fourth line there? It was in the file to begin with.

---

### Post by BicyclerBoy on 2011-09-02
The lines starting with "#" are commented out.

That entry in pulse/default.pa can get you running with system wide audio over HDMI.

With HDMI turned on & plugged in & X server running. ( **no** AVR HT amp)

cat /proc/asound/card1/codec#3
(this is hw:1,9 codec)

cat /proc/asound/card1/eld#3.0
(ELD EDID data from display or receiver)

dmesg | grep HDMI
(hot plug detection events etc)

It is possible that hw:1,9 is not the correct output..

---

### Post by windscryer on 2011-09-02
It was my understanding that adding that line to the pulse/default.pa would help (from the original tutorial) and yet it doesn't seem to be enough. (Unless I messed something else up along the way in my efforts to do/undo things. *sigh*)

```
 cat /proc/asound/card1/codec#3
Codec: Nvidia GPU 0d HDMI/DP
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000d
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Device: name="HDMI 0", type="HDMI", device=9
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04

``````
 cat /proc/asound/card1/eld#3.0
monitor_present        1
eld_valid        1
monitor_name        LD-3255VX   
connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0x855c
product_id        0x17f2
port_id            0x40000
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x1] FL/FR
sad_count        1
sad0_coding_type    [0x1] LPCM
sad0_channels        2
sad0_rates        [0xe0] 44100 48000 88200
sad0_bits        [0xe0000] 16 20 24

``````
 dmesg | grep HDMI
[   16.074786] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   16.094525] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   16.892019] HDMI: detected monitor LD-3255VX    at connection type HDMI
[   16.892043] HDMI: available speakers: FL/FR
[   16.892050] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24
[   17.668117] HDMI: detected monitor LD-3255VX    at connection type HDMI
[   17.668121] HDMI: available speakers: FL/FR
[   17.668125] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24

```hw:1,9 is the only one I can get sound from in any way shape or form, even if it's only through a specific terminal command. Unless there's some way for me to override that?

---

### Post by BicyclerBoy on 2011-09-02
The load-module module-alsa-sink device=hw:1,9 entry  should force pulse-audio to enumerate the default hw:1,3 & the extra hw1,9.
Then you should be able to pick the 2nd HDMI device in pavucontrol.
This should then be the default output system wide.

If this refuses to work then maybe we have to use the probe_mask to only expose the logical codec #3 currently reported by alsa as hw:1,9 device.
probe_mask=-1,0x8
You would then delete the load module module-alsa-sink device entry. Then only one HDMI device listed by pulseaudio would be logical pin codec#3 & this will now be reported by alsa as hw:1,3.

Many programs let you output direct ..VLC, mplayer, Clementine etc.. 

Your HDMI receiver (display or TV) supports 2 ch PCM at 44K1, 48K & 88K2Hz.
speaker-test -c 2 -r 48000 -D hw:1,9

---

### Post by windscryer on 2011-09-02
> **BicyclerBoy said:**
> The load-module module-alsa-sink device=hw:1,9 entry  should force pulse-audio to enumerate the default hw:1,3 & the extra hw1,9.
Then you should be able to pick the 2nd HDMI device in pavucontrol.
This should then be the default output system wide.

I had to download pavucontrol, but my sound now works (YAY! \o/). However, I have to open pavucontrol and select the HDMI output for each program individually, so I'm thinking I still didn't set it to system default somehow. Is there a button or option somewhere in pavucontrol that lets me pick one as the permanent default?

---

### Post by BicyclerBoy on 2011-09-02
pavucontrol tab configuration profiles should do this...

Make the "other" audio devices OFF and set the working HDMI device to digital stereo.

pavucontrol should do much the same things as gnome sound preferences tool but with more options.

---

### Post by windscryer on 2011-09-02
> **BicyclerBoy said:**
> pavucontrol tab configuration profiles should do this...

Make the "other" audio devices OFF and set the working HDMI device to digital stereo.

pavucontrol should do much the same things as gnome sound preferences tool but with more options.

Ah! I found it and it does indeed work now exactly as it should. (And, yes, I do feel more than a little dumb for not seeing that the first time. :oops:)

Thank you so much for all your help and your patience with me!

---

### Post by BicyclerBoy on 2011-09-02
You're welcome..We only filled one page of posts, when it gets to 10 pages there's trouble.

---

### Post by windscryer on 2011-09-02
LOL At that point, I'd probably just give up on sound on this compy and watch my movies on my lappy. Good thing it didn't come to that! :)

---

### Post by mitanc on 2011-09-09
Dear all you experts,

I just got myself a Lenovo Q150 as a HTPC. Sound works just fine under gnome and in XBMC, but for the life of me I cannot get AC3 pass thru to work in XBMC. 

I hear menu clicks and non AC3 video is fine. 

I am running 11.04 with Nvidia proprietary driver installed from additionL drivers tab in ubuntu. 

I have tried setting the custom setting to plughw:1,9 but that gives me an audio cannot be initialized in XBMC. 

I have tried NVidia,9 and hw:1,9 but none of these work as well. 

Any tips on how to proceed? Like I said works fine for everything else, just can't get AC3 pass thru.

---

### Post by James- on 2011-09-20
I wanted to thank you! I'm currently running arch linux, but boils down to the same thing: alsa & pulse
When I tried the probe_mask and rebooted, my NVIDIA were not listed(running two dual core GPU (x295 and x590)) so I reverted and only modified:

/etc/pulse/default.pa

to include:
> load-module module-alsa-sink device=hw3,9

removed the local configs:
> rm -r ~/.pulse ~/.asound* ~/.pulse-cookie

and remade the ram disk file:
> sudo mkinitpcio -p linux

and works flawlessly :D
I did have to change the selected device in pavucontrol and unmute the SPDIF channels on the alsamixer

---

### Post by mbaxter89 on 2011-09-24
I ran steps 1-4 and it dint work and made my hard ware dis aper. so i started working backwords undoing every thing one step at a time. when I got to step 3  and rebooted with option snd-hda-intel probe_mask=0x102 and it worked great.

Ubuntu 11.04 NVidia GTS 450


sudo bash
cd /etc/modprobe.d/
gedit sound.conf
options snd-hda-intel probe_mask=0x10[COLOR=Red](*) (*=step 2)
[/COLOR]update-initramfs -u
[COLOR=Red][SIZE=3](Restart)[/SIZE][/COLOR]

---

### Post by BicyclerBoy on 2011-09-24
Note: that probe_mask is effectively 0x02.

You are not to use numbers > 0x0f

The probe_mask of 0x02 exposes 2nd HDMI codec maybe hw:0,7.
You must not have onboard/chipset audio.

---

### Post by noe005 on 2011-10-06
> **mbaxter89 said:**
> I ran steps 1-4 and it dint work and made my hard ware dis aper. so i started working backwords undoing every thing one step at a time. when I got to step 3  and rebooted with option snd-hda-intel probe_mask=0x102 and it worked great.

Ubuntu 11.04 NVidia GTS 450


sudo bash
cd /etc/modprobe.d/
gedit sound.conf
options snd-hda-intel probe_mask=0x10[COLOR=Red](*) (*=step 2)
[/COLOR]update-initramfs -u
[COLOR=Red][SIZE=3](Restart)[/SIZE][/COLOR]
Great Help that worked for with a GTX 550ti. Thanks again.

---

### Post by Balyrion on 2011-12-09
I have gone through the thread and I have a problem I have not seen listed. Ultimately the problem is that with my current configuration, running Mythbuntu 11.10, I only get audio from HD videos inside MythTV, anything that was not 720p or better provides no audio output. I can get sound using speaker-test and aplay from the command line. Also of interest is addressing the hardware via hdmi:NVidia does not work from the command line I have to use either hw:0,3 or plughw:NVidia,3, etc. I have applied what I believe to be the proper probe_mask and that made no difference. Also of interest is if I add the device to an asound.conf file everything breaks, aplay throws errors, no sound, etc. Here is the current configuration:
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

``````

ls -l /proc/asound/card0/
total 0
-r--r--r-- 1 root root 0 2011-12-09 06:43 codec#0
-rw-r--r-- 1 root root 0 2011-12-09 06:43 eld#0.0
-rw-r--r-- 1 root root 0 2011-12-09 06:43 eld#0.1

``````

cat /proc/asound/card0/eld#0.1 
monitor_present         1
eld_valid               1
monitor_name            SAMSUNG
     
connection_type         HDMI
eld_version             [0x2] CEA-861D or below
edid_version            [0x3] CEA-861-B, C or D
manufacture_id          0x2d4c
product_id              0x3ea
port_id                 0x20000
support_hdcp            0
support_ai              0
audio_sync_delay        0
speakers                [0x4f] FL/FR LFE FC RL/RR RLC/RRC
sad_count               4
sad0_coding_type        [0x1] LPCM
sad0_channels           2
sad0_rates              [0x6e0] 44100 48000 88200 176400 192000
sad0_bits               [0xe0000] 16 20 24
sad1_coding_type        [0x1] LPCM
sad1_channels           8
sad1_rates              [0x6e0] 44100 48000 88200 176400 192000
sad1_bits               [0xe0000] 16 20 24
sad2_coding_type        [0x2] AC-3
sad2_channels           6
sad2_rates              [0xe0] 44100 48000 88200
sad2_max_bitrate        640000
sad3_coding_type        [0x7] DTS
sad3_channels           6
sad3_rates              [0xe0] 44100 48000 88200
sad3_max_bitrate        1536000

``````

cat /etc/modprobe.d/sound.conf 
options snd-hda-intel probe_mask=-1,0x1

```At this point I am stumped as to why it only works for HD streams. If anyone has any ideas I would love to hear it.

---

### Post by BicyclerBoy on 2011-12-09
Your probe_mask is doing nothing because it is configured for 2 soundcards where HDMI is card1 (2nd soundcard).
You are masking 'on' the first codec of card1 & all codecs on card0.

The alsa/pulse in 11.10 has made the use of probe_mask redundant..
Pulse audio now enumerates all hdmi sub-devices not just the first with max=2.

I would have thought that GT220 would have sub-devices 3,7,8,9..

Your ELD file for hw:0,3 should be:
eld#0.0

The eld#0.1 could be a secondary ELD for another device on same HDMI cable ?

Can you try:
speaker-test -c 2 -r 48000 -D hw:0,3
speaker-test -c 6 -r 48000 -D hw:0,3
dmesg | grep HDMI

What do you mean by HD videos/recordings ?
DTS-MA or Dolby-TrueHD
or just AC3/DTS ??
The only HD audio formats in the ELD are multi-channel (>2) LPCM 192KHz.

Do you not get any audio from stereo AAC/mpeg2/mp3 ?

---

### Post by Balyrion on 2011-12-10
Well probe masking is pointless anyway since there is only one codec. This is a GT520 BTW. I pasted in eld#0.1 because eld#0.0 is essentially empty:
```

cat /proc/asound/card0/eld#0.0 
monitor_present         0
eld_valid               0

```
I did figure out what was wrong which was the upgrade stripped out the restricted extras repo and that broke my ability to play avi files but HD mkv files were unaffected for whatever reason. Also pulseaudio was seemingly only partially installed (the server itself appeared to be missing although there were components and references to it in the filesystem). I think last night I had just been working on it for too long and was too tired, thanks for the help. One thing of interest, today I tried installing the dev hda-intel-dkms deb package to see if the daily build of alsa would help any of the problems. It actually introduces a new one for me which is I have 2 SPDIF outputs in alsamixer and sound breaks again. At this point I am happy everything works and do not want to even start playing with it, but I imagine at some point in the future this will crop up again.

> **BicyclerBoy said:**
> Your probe_mask is doing nothing because it is configured for 2 soundcards where HDMI is card1 (2nd soundcard).
You are masking 'on' the first codec of card1 & all codecs on card0.

The alsa/pulse in 11.10 has made the use of probe_mask redundant..
Pulse audio now enumerates all hdmi sub-devices not just the first with max=2.

I would have thought that GT220 would have sub-devices 3,7,8,9..

Your ELD file for hw:0,3 should be:
eld#0.0

The eld#0.1 could be a secondary ELD for another device on same HDMI cable ?

Can you try:
speaker-test -c 2 -r 48000 -D hw:0,3
speaker-test -c 6 -r 48000 -D hw:0,3
dmesg | grep HDMI

What do you mean by HD videos/recordings ?
DTS-MA or Dolby-TrueHD
or just AC3/DTS ??
The only HD audio formats in the ELD are multi-channel (>2) LPCM 192KHz.

Do you not get any audio from stereo AAC/mpeg2/mp3 ?

---

### Post by BicyclerBoy on 2011-12-10
The GT520 does have one codec but 2 converters that feed as many HDMI outputs as wired via pin widget muxes..

Therefore:
eld#0.0 --> physical stream 3 (same 1 codec)
eld#0.1 --> physical stream 7 (same 1 codec)

Not sure how probe_mask value will effect single-codec/multi-stream h/w but this is another good reason **not** to use probe_mask when debugging.

Your eld file suggests that you should have alsa physical stream ID hw:0,7 & that is your correct connection..

The nVidia HDMI audio readme (updated Sept 2011) states that for GT520:
linux kernel 3.1-rc1 and later. 

Also need nVidia proprietary video driver 275 &/or later.

---

### Post by opg on 2012-04-07
None of this worked for me in XBMCbuntu (XBMC Live based on Lubuntu). For my solution see: [http://forum.xbmc.org/showthread.php?tid=76544&pid=1069025#pid1069025](http://forum.xbmc.org/showthread.php?tid=76544&pid=1069025#pid1069025)

---

### Post by Tikhon03 on 2012-04-26
When 11.10 was released I lost audio.  I found a temporary solution that worked for a while, but after an update the audio was killed again.   I waited for a while, hoping it would be fixed in a future update.  I tried a couple more suggested fixes, and still nothing.  So now I have tried your HowTo. Here is what I am getting so far:

```

NVRM version: NVIDIA UNIX x86 Kernel Module  295.40  Thu Apr  5 21:28:09 PDT 2012
GCC version:  gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 

``````

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

/proc/asound/NVidia/eld#0.0:eld_valid           0
/proc/asound/NVidia/eld#1.0:eld_valid           0
/proc/asound/NVidia/eld#2.0:eld_valid           0
/proc/asound/NVidia/eld#3.0:eld_valid           0

```OK, so then I tried upgrading the alsa driver modules, and it wouldn't do it because I have a pae kernel.  So what would you suggest?

---

### Post by zhanglini on 2012-08-11
> ```
aplay -D plughw:1,7 /usr/share/sounds/Front_Center.wav
```Then using ```
gksu gedit /etc/pulse/default.pa
``` and add a line after the commented out line for alsa-sink for the card and device that worked for that aplay sound.  
```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,7**
```Then reboot
Thank you!  this worked for me!

---

### Post by tonezone on 2013-07-14
I know this thread has long grown cold, but a similar issue with 13.04 brought me here, and the solutions in this thread did not resolve the issue. I found the solution in another thread. The 3.8 kernel has some sort of problem with the audio and the solution is to use the script in this github repository to use the latest version of the mainline kernel:
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

---

### Post by lisati on 2013-07-14
> **tonezone said:**
> I know this thread has long grown cold, but a similar issue with 13.04 brought me here, and the solutions in this thread did not resolve the issue. I found the solution in another thread. The 3.8 kernel has some sort of problem with the audio and the solution is to use the script in this github repository to use the latest version of the mainline kernel:
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

Things change between releases. It might be best to start a new thread.

---

