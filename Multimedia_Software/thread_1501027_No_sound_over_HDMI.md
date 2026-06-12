---
title: "No sound over HDMI"
date: 2010-06-03
forum: Multimedia Software
---

### Post by frigginacky on 2010-06-03
I rebooted my HTPC today, and all of a sudden, I have no sound! I didn't change any of my settings (at least not intentionally). I double-checked alsamixer, and nothing is muted. If I open the sound preferences dialog and look at the applications tab, I can see the programs that are trying to play audio.  There's just no actual sound.

Here's the .asoundrc I used to get HDMI audio working in the first place.  It's worked flawlessly since 9.04 (I'm now on Lucid):

```
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
  card 0     #  <-----  Put your card number here
  device 1  #  <-----  Put your device number here
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
```   

My aplay -l (the device I want to use is bolded):

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
[B]card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Anybody have any ideas/suggestions?  :confused:  I'm at a loss here.

EDIT: After removing & reinstalling pulseaudio & upgrading alsa to the latest version, I actually took a look inside the computer.  Broken wire on my spdif cable. D'oh!

---

### Post by puntua on 2010-06-03
i will try your code
im with a gt240 with no sound.
thx for posting it

---

### Post by frigginacky on 2010-06-03
Now this is strange.  After discovering the broken wire, I pulled out the 9800GT (card I was trying to get working) and went back to my mobo's onboard HDMI (last item in my aplay -l)...and it doesn't work either!  So my problem remains unsolved. :(

> **puntua said:**
> i will try your code
im with a gt240 with no sound.
thx for posting it

Good luck!  It always worked for me...before today that is.

EDIT: And right after I post it starts working spontaneously.  I think it's possessed, and I'm not gonna touch it anymore now that it's working.

---

### Post by puntua on 2010-06-04
jeje i think im cursed lol
glad it worked for you.
actually your code put me in the right direction, and finally i get it working after 2 LONG weeks, i wont touch anything either, jeje, also wont update anything lol
maybe, if you had automatic updates, yesterday ubuntu pushed a new kernel, maybe this had something to do with your on and off problem, or your code should change if you add or remove sound devices, sometimes new kernels drop some drivers backported, like alsa that you upgraded.
also since 10.04 settings, especially with drivers seems to work sometimes after the second or third restart, dont know why, but thats was my case several times with nvidia drivers, maybe that push for faster boot ups its not good with changing hardware and drivers.
anyway, thx for posting your code, it really help me a lot to find out a solution with my problem

---

