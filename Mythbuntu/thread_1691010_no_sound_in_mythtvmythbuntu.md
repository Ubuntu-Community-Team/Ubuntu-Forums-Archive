---
title: "no sound in mythtv/mythbuntu"
date: 2011-02-19
forum: Mythbuntu
---

### Post by adub on 2011-02-19
I have yet to get sound working wiht anything.  The goal is to get HDMI sound.  I have HDMI sound working on everything else i was trying this on 0.23+fixes then updated to 0.24 as there is the scan for audio devices in this version


below is my .asoundrc

pcm.!default hdmi:NVidia
pcm:iec958 hdmi:NVidia


this is in my /etc/modprobe.d/alsa-base.conf

#i added these settings after install
options snd-hda-intel enable_msi=0 probe_mask=0xfff2


I basically did the above to get sound working via hdmi through everything else

lspci gives
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

any other info to troubleshout this just ask i have tried just about every combination i can think of but probably the correct one on audio system setup in the mythfrontend

thanks to all who reply

---

### Post by MythMuk on 2011-02-19
Make sure all the audio channels on your HDMI card are un-muted.
In a terminal session, enter the alsamixer command. This will bring up a gui right in the terminal window. Press F6 to choose your audio card - it will be the one with HDMI in the name. Then use right/left arrow keys to navigate the channels and if any say MM, then press the M key to mute or un-mute. Then press esc to exit.

---

### Post by adub on 2011-02-19
yes this is one of the first things i checked showing 00 so it is enabled and the volume on the mixer is 100%

---

### Post by PaulReaver on 2011-02-19
If you've got sound working on everything else your soundcard is working.

you need to set the audio output device in MythTV Frontend General Settings....

the ALSA:hdmi option won't work....

I had to set my geforce 210 sound output manually as
ALSA:plughw:1,3

and after I disabled my onboard sound it changed to 'ALSA:plughw:0,3'

yours might be different 
use
$ aplay -l

to tell you what card and device number your nvidia hdmi sound output is.

hope it helps.

---

### Post by BicyclerBoy on 2011-02-20
Your probe_mask is wrong..the mask should be < 0x1FF & not recommended to set bit8 either..

 [FONT=Verdana]If you have an onboard audio device that uses the same driver use
probe_mask=-1,0x2

That exposes only logical codec ID 2 or 2nd audio device.

It may be better to just apply the default probe mask while debugging..
[/FONT][FONT=Verdana]probe_mask=-1,-1
[/FONT](this is for 2 audio devices)

quote from the defining doc
[http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)
```

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


```

---

