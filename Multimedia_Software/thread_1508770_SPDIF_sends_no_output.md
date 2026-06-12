---
title: "S/PDIF sends no output"
date: 2010-06-13
forum: Multimedia Software
---

### Post by seppl82 on 2010-06-13
Dear all,

i've installed Mythbuntu 10.4. On my Asrock 890GM Pro 3 Mainboard.
Chipset Northbridge=AMD890GX
Chipset Southbridge=AMD850


In Mythbuntu two Sound Cards are shown.



```
frsc@frsc-media:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

frsc@frsc-media:~$ lspci | grep Audio
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
05:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
```

In the Alsa Mixer i've checked the option "IEC958" for the ATI HDMI device, but i did not get an output running Mythtv on the optical out.
I've also tried mplayer and VLC but no luck.

Any ideas what else i should try?

---

### Post by OdinOrion on 2010-06-13
I've got the same problem with the same AMD chip set but different audio device.  In my case, I am trying to get ALC892 to work.  Analog works, but no IEC958.

Here is my thread, unfortunately I haven't received much help.  I may be having different issues due as my audio chip set is different, but there is always a chance the root cuase is the same.

[http://ubuntuforums.org/showthread.php?t=1493093](http://ubuntuforums.org/showthread.php?t=1493093)

BTW, the audio works perfectly under Windows XP.

---

### Post by lidex on 2010-06-13
> **seppl82 said:**
> Dear all,

i've installed Mythbuntu 10.4. On my Asrock 890GM Pro 3 Mainboard.
Chipset Northbridge=AMD890GX
Chipset Southbridge=AMD850


In Mythbuntu two Sound Cards are shown.



```
frsc@frsc-media:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

frsc@frsc-media:~$ lspci | grep Audio
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
05:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
```

In the Alsa Mixer i've checked the option "IEC958" for the ATI HDMI device, but i did not get an output running Mythtv on the optical out.
I've also tried mplayer and VLC but no luck.

Any ideas what else i should try?
Have you tried gnome-alsamixer? Sometimes you need to enable and unmute spdif.
**Gnome-alsamixer**
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
I don't have it installed right now, but I believe VLC has an option in advanced properties to select the digital out that may need to be set. Also go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by seppl82 on 2010-06-14
Hi,

i've installed gnome-alsamixer but there is only the check to enable IEC958 but no slider or mute or unmute button.

---

### Post by seppl82 on 2010-06-17
Okay this solved the issue...

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
Now it shows as fist device a VIA VT2020 with an IEC958 option


And select Settings / General Settings / goto Auto Settings

Select Audio Ouput device ALSA:spdif
And your Speakerconfiguration

---

