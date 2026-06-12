---
title: "Can only play one sound at a time"
date: 2011-10-05
forum: Multimedia Software
---

### Post by GraemeUK on 2011-10-05
Hi Guys,

I have tried to search for anyone having the same problem, but could not find it anywhere.

I have a problem with my Mythbuntu 10.10 system, the problem is that I can only seem to play one sound at a time.  Not a major problem you may think, using this box as a TV recorder you would be right, but I also play games and listen to music on it.

To be honest the real problem I am having is that I have started playing Minecraft and while this is running I cannot watch any youtube tutorials as only one application can have sound at a time.

For example if I was to open an mp3 in VLC this would play but then I open a movie in mplayer and no sound in mplayer but the VLC sound still works.  Is this normal and just something I need to get used to with Linux or is there a solution to this.

I have previously struggled to get any sound out of this system as it runs over HDMI.  Here are the entire contents of my asound.conf:

pcm.!default {
    type plug
    slave.pcm {
            type hw
            card 0
            device 3
    }
}


My understand of this is it points to the HDMI as the default sound output, could this be causing my problem?

Thanks in advance for your help

---

### Post by BicyclerBoy on 2011-10-05
The current behaviour is because you are using alsa devices directly & your config does not allow shared access.

Two solns: 
- setup alsa for sharing (to hard & confusing)
- setup pulse audio to use the alsa hw:0,3

Note: if using hdmi for digital pass thru (AC3/DTS/DTS-MA etc) then there can not be sharing. i.e. cannot dmix AC3/DTS etc.

If you add one line to /etc/pulse/default.pa you can share the hdmi output (PCM):
load-module module-alsa-sink device=hw:0,3

Please check there is only one module-alsa-sink entry in the file..

Set the gnome sound preferences or pavucontrol to make this hdmi output the system wide default.
Now point your audio apps at pulse..

I would leave MythTV/Mythbuntu pointing directly at alsa device to allow digital pass-thru'.
MythTV releases the audio device when not playing, so no problem...

Your existing alsa asound.conf is just redefining default alias..it has no effect on pulse audio.

---

### Post by GraemeUK on 2011-10-07
Thank you for your help, I have tried what you suggested.  Now Pulse audio works with VLC, but I have no sound in my Firefox or in Minecraft.

Here is what I have done:

I reinstalled pulse audio and added the line "load-module module-alsa-sink device=hw:0,3" then I checked for other instances of this (there were none)

I then opened pavucontrol, and checked the settings opened VLC set to Pulse audio and started a track, but no sound.  On the Configuration Tab in pavucontrol I selected Digital Stereo (HDMI Output) and I began to hear my music :)

Now I think I just need to get the system to use this setting as default, as Firefox and other applications have no sound.  Have I missed something?

Thank you again for your help

---

### Post by GraemeUK on 2011-10-07
Sorry Guys,

Strangest thing just happened, the sound has started working in firefox and minecraft (I swear I haven't changed anything or restarted)

Unfortunately it still won't play at the same time.

---

### Post by BicyclerBoy on 2011-10-07
With pavucontrol
did you select the configuration tab & select the HDMI output as default ?
Are there (2) of them ?

I'm thinking that you should not have needed the /etc/pulse/default.pa alsa-sink hw:0,3 entry..Pulse audio should have already found this device & created a pulse device.

post your aplay -l

Have not used minecraft..
Minecraft can be run in JRE outside of firefox or in the browser.

I guess there must be some audio config for JRE or browser java plugin.
Would have thought these programs would have pointed at the pulse default audio device.
Not sure firefox has any audio config because the plugins make the audio output.

mplayer needs cmdline options to use pulse device & then it will not be able to output AC3/DTS/DTS-MA etc using pulse. (unless pulse has fixed pass-thru'). Depending on your audio receiver you can use multi-channel LPCM over HDMI.

---

### Post by GraemeUK on 2011-10-07
Here is my aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I run Minecraft outside of the browser in the java application, but cannot find any sound preferences.

I can see 2 options for HDMI in pavucontrol one of them is HDMI + Analogue Stereo., but I don't see a "set as default" option on this tab.  That would be too easy!

Again thank you for your help.

---

### Post by BicyclerBoy on 2011-10-07
On 3rd thoughts & seeing the aplay -l you do need the /etc/pulse/defaults.pa alsa-sink entry.

Alsa & pulse only enumerate the first (2) devices of each card. So without the default.pa entry, pulse will not see the HDMI codec.

The configuration tab of pavucontrol sets the pulse default system wide.
You might have to set the port on outputs tab.

[https://wiki.archlinux.org/index.php/Java#Java_sound_with_Pulseaudio](https://wiki.archlinux.org/index.php/Java#Java_sound_with_Pulseaudio)

or maybe try this package:
alsa-plugins-pulseaudio

---

### Post by GraemeUK on 2011-10-08
I fixed it!

Actually I cheated, I noticed that the previous sound over HDMI problem I had was fixed for Mythbuntu 11.04, so I did a fresh load of 11.04 and installed Pulse Audio and setup as BicyclerBoy advised.

Now everything runs through Pulse Audio and now I can play music and games at the same time.  

Ubuntu works!!!!

Thank you for your help, I wouldn't have been able to setup Pulse Audio without your help BicyclerBoy!

Just got to get used to the 11.04 quirks now (like neither xfce4-popup-menu or xfce4-popup-applicationsmenu working correctly)

Thank you again

---

