---
title: "No audio on HDMI, Help!"
date: 2013-05-13
forum: Mythbuntu
---

### Post by gga96 on 2013-05-13
I have lost audio on my AsRock ion 3D HDMI connector to the TV. Video is fine.

Many googles refer to fixes but I have not been able to fix the problem.

Some terminal results may help:
> 
glen@frontend-1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC892 Digital [ALC892 Digital]
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

I have tried the following with values card 1 and values 3, 7, 8, 9 but no sound.
> glen@frontend-1:~$ aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono


I hope I have not missed the obvious.
I dont know what to do next.

Any help will be appreciated.
Glen

---

### Post by SJR Dorset on 2013-05-13
After upgrading to 13.10 I too lost the audio from my HDMI connection. After exploring the forum and other sites on the web I fixed my problem by upgrading the Kernel to a newer version.

---

### Post by Rotak on 2013-05-13
Did you try to configure the frontend to use these ports? I didn't get it to work using aplay in the commandline, but it worked when setting the correct output device in the frontend.

---

### Post by deri on 2013-05-13
I have the exact problem. I don't know what happened...after reboot I will try 3.10

---

### Post by gga96 on 2013-05-14
Thanks Guys,

I have SOLVED my problem, sound was muted, I found out that "m" in terminal app alsamixer would toggle the selected value on/off. 

I think a resent software change may have reset some ALSA values.  Also I had to set Frontend>Utilities/Setup>Setup>Audio: to the correct ALSA value. The choice of which card:device to use was not clear and was desided by trial and error. I could not get aplay to make a sound.

deri: Try terminal app alsamixer before going to 3.1 it may fix your problem too.

Thanks to all it was a great help.
Glen

EDIT 2: It is NOT solved I have just found that I have lost frontend internal volume control, the slider echos the volume change but the tv  sound does not change. The same applies to Mute, echos on screen but sound continues.

---

### Post by Rotak on 2013-05-16
Your 2nd problem (MythTV slider doesn't control volume) is not an issue. HDMI is transports a digital signal with no volume control. You need to control volume on your TV or DTS receiver.

---

### Post by BicyclerBoy on 2013-05-17
You can utilize mythtv volume control with HDMI by:
- sw decode to PCM
- enable mythtv volume control
- use multi-channel PCM over HDMI

If (and a big if) the s/w decode is working then this is as lossless as pass-thru'.

Another alternative (without any loss or downside) is CEC volume control of TV/HT-amp from mythtv.

---

### Post by gga96 on 2013-05-18
Thanks BicyclerBoy,

Pursuing your suggestions I found [http://ubuntuforums.org/archive/index.php/t-1501027.html](http://ubuntuforums.org/archive/index.php/t-1501027.html) and it refers to a asound.comf authored by Dewey Oxberger in 2009.

I believe my card:device is 1:7 (see first post), /etc/asound.conf follows:
> 
# Dewey Oxberger (aka Jon B)
# ASound.Conf file for HDMI Audio on MythTV
# HDMI configuration with volume control for MythTV
# Works in Ubuntu 9.04  5/9/2009
# Instructions for use
# 1) Find your hmdi hardware Card Number and Device Number.  Open a terminal and do:  
#    aplay -L
#    That will list all of the hardware audio devices.  Look for the one labeled HDMI.
#    Note what Card Number and Device Number it lists (they seem to be card 0,
#    device 3 but your system may be different).
# 2) Edit the pcm.hdmi_hw device defined here to set your Card Number and Device Number.
# 3) Put this file in either /etc/asound.conf or in your home directory as .asoundrc.
#    sudo cp deweys_asound.conf /etc/asound.conf
#      or 
#    sudo cp deweys_asound.conf $HOME/.asound.conf
# 4) Exit mythfrontend.  Then restart the sound system:
#    sudo /etc/init.d/alsa-utils restart
# 5) Start mythfrontend and go to the audio setup screen
#    "Utilities / Setup"  then "Setup" then "General" then "Next" until you
#    get to the Audio tab.
# 6) Fill in the info - it's case sensitive:
#    Audio output device: ALSA:hdmi_complete     <--- note you have to type in this field
#    Passthrough output devide: Default
#     ... Stereo... ... Passive...
#    Mixer Device: ALSA:default
#    Mixer controls: hdmi_volume                 <--- type in this field
# 7) Work your way back to Watch TV and give it a try.
pcm.hdmi_hw {
  type hw
  card 1     #  <-----  Put your card number here
  device 7  #  <-----  Put your device number here
}
pcm.hdmi_formatted {
  type plug
  slave {
    pcm hdmi_hw
    rate 48000
    channels 2
  }
}
pcm.hdmi_complete {
  type softvol
  slave.pcm hdmi_formatted
  control.name hdmi_volume
  control.card 0
}
#pcm.hdmi_complete {
#  type copy
#  slave.pcm hdmi_volume
#  slave {
#    pcm front
#  }
#}
pcm.!default hdmi_complete


I could not find his myth reference to "Passthrough output devide: Default" and values for Digital Audio Capabilities "Dolby Digital" and "DTS " I have left un-checked.  The Advanced Audio Settings only has "HBR Passthrough support" checked. 
Do you think these setting are correct?

Have your suggestions been covered by this conf?
> 
- sw decode to PCM
- use multi-channel PCM over HDMI


At the moment I am now getting HDMI Audio, Video and myth volume/mute control working! Thank you.

Is there more tweaks I should try?

Thanks again for your help.
Glen

---

### Post by BicyclerBoy on 2013-05-20
I think you have created a alsa soft-mix volume control & have forced the output to be stereo 48K.
I don't believe you need to use that asound.conf..

There are 4 ways (I can think of) to get volume control in PC (in mythtv)
- use alsa soft mix
- use pulse audio
- mythtv audio volume control
- CEC direct amp/TV volume control.

The 3rd option is best if:
- don't have or want pulse8 CEC adapter
- mythtv only audio solution with very good flexibility

To achieve that you set in mythtv FE audio config:
- pick the correct hdmi output device
- untick all digital audio capabilities
- set speaker-config to 2 or 5.1
- enable mythtv internal volume control (on the next screen)

If this connection only goes to a TV then 2 ch stereo is fine & any form of pass-thru' is probably pointless.

Your TV should accept AC3 2 ch & 5.1 but to get volume control you must (allow myth to) decode to PCM, apply volume control, re-encode to AC3. MythTV, VLC & XBMC have AC3 encoder support to allow this feature etc..(tick the advanced audio option stereo PCM only).

---

### Post by gga96 on 2013-05-22
Hi BicyclerBoy thanks for helping,

I implemented Oxberger and then "mythtv audio volume control" method from the previous post and with both methods I had volume and mute control from FE. But some recordings would get the staggers. The good playbacks I think were DH recordings. I thought I must have screwed up so I re-installed the FE but still the same staggers. I think there must be a conversion process for the SD video to HDMI. 

My FE hardware is an AsRock 3D ion2  152D running 32 bit mythbuntu FE and connecting to a Panasonic 47" via HDMI.  I hope this is not a lemon. It is better than the original ion recommended for FE hardware.

I am lost, have you any ideas what caused the staggers?
Glen

---

### Post by BicyclerBoy on 2013-05-22
The ION2 should be okay..
But are the problem recordings/files decoded in this h/w ?

Not enough RAM allocated to GPU
scaling SD to HD &/or other feature set C/D options
wrong video modes (causes bad jitter with 0.25 to master)
Old playback profiles (some filters/keywords have been removed like vdpaubuffers)
bad playback profiles

Some users here had to create a new FE hostname to get clean playback profiles (upgrade path no new installs)

Should analyse (contrast/compare) the good & bad recordings with mediainfo.

Start FE from terminal:
mythfrontend -v playback
& try play bad file..
Have a look at the OSD playback/playback data..

---

### Post by gga96 on 2013-05-22
Thanks,
I will work through your list which may take some time. Will report later.
Glad to hear ion2 should be ok.
Glen

---

### Post by gga96 on 2013-05-25
[COLOR=#000000][FONT=Arial][FONT=Verdana][COLOR=#222222]Hi had some progress,

> 
[FONT=Tahoma][COLOR=#000000]Not enough RAM allocated to GPU.
[/COLOR][/FONT][FONT=Tahoma][COLOR=#000000]
Google found [http://www.mythtv.org/wiki/VDPAU#Enabling_VDPAU_in_MythFrontend](http://www.mythtv.org/wiki/VDPAU#Enabling_VDPAU_in_MythFrontend) and that lead to looking at the FE Playback Profiles (3/8): "Current Video Playback Profile".  I cycled through values Slim, Normal and “VDPAU: High Quality” saving and testing at each value. The staggers disappeared for each setting. I do not know why this fixed the problem and I guess I never will find out.
[/COLOR][/FONT][/COLOR][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][FONT=Tahoma]I thought the following may be related and reflect a DB hiccup.
> 
Some users here had to create a mew FE hostname...

[/FONT][FONT=Tahoma]
I looked at updating the GPU driver from 304.88 to 319.23 but Nvidia [http://www.nvidia.com/object/linux-display-ia32-319.23-driver.html](http://www.nvidia.com/object/linux-display-ia32-319.23-driver.html) said:
> 
[FONT=tahoma][SIZE=2][COLOR=#000000]Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this 
rather than NVIDIA's official package.[/COLOR][/SIZE]
[/FONT]

[/FONT][FONT=Tahoma]Do you think I should stay with the older river?[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][FONT=Tahoma]
Glen[/FONT][/FONT][/COLOR]

---

### Post by BicyclerBoy on 2013-05-27
The VDPAU memory requirement has always been 512MB (GPU RAM).
I still think this is a requirement.

Some ION systems need 2 sticks of RAM for required mem bandwidth..
You need to use the BIOS setup to allocate >=512MB to GPU..

Don't try update your nVidia driver from the nVidia website unless you are expert.
The only benefit of later driver is the return of a GUI tool for overscan/underscan & support for GTX780 or sim..
Zero benefit for ION except overscan/underscan adjustment & that is only a last resort should the TV be rubbish..

---

### Post by gga96 on 2013-05-28
Hi BicyclerBoy,

The HDMI av is now stable and has worked well over the last couple of days. If problems come up in the future I will pursue the RAM suggestion.

I have only been using Linux for a few months so I am far from expert and will not update the Nvidia driver unless forced to do so.  I do have a messy myth due to overscan but have tried  FE Theme/Screen Settings to adjust myth GUI but could not fix the GUI without side affects with TV. I will have to live with the overscan.

Thanks for your help.
Glen

---

### Post by BicyclerBoy on 2013-05-28
Think I was wrong about the RAM on gen 2 ION2 chipset..
These gen 2 ION2 have dedicated 512MB GPU RAM..so more like discrete graphics but fitted to the mobo.

You can get the later nVidia driver from various package managed *buntu ppa..
x-swat team ppa
xorg-edgers ppa (this one will undate kernel + many other things.)

It could already be available in mainstream distro thru' jockey (additional proprietary drivers) labelled as "experimental".

---

### Post by gga96 on 2013-05-29
I spent several hours browsing the 3 ppa mentioned but only jockey had a reference to the latest nvidia driver 319.23 version and many posts seemed to indicate that jockey was unstable. I don't understand why driver updates in ubuntu should be so hairy. So I am going to stay with the current 304.88 version and perhaps look at an upgrade when I am more experienced with linux.
Glen

---

### Post by nickrout on 2013-05-31
If you want to control your passthrough audio from mythtv (which is not recommended because you interfere with the acrefully studio crafted digital stream) then simply set your mixer device to software. This is a mythtv frontend setting.

---

