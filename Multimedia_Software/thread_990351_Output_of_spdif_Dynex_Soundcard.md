---
title: "Output of spdif Dynex Soundcard"
date: 2008-11-22
forum: Multimedia Software
---

### Post by ericwait on 2008-11-22
I just purchased a Dynex DX-SC51 sound card with the intentions to use the optical spdif out for mythbuntu.

So far I am able to get analogue sound from the card but have not been successful in getting anything from the spdif.

dmesg gives me:

```

ICE1724 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
ice1724: No matching model found for ID 0xc3140517
ice1724: Invalid EEPROM version 1

```

Also, when I:
```
aplay -L
```

I do not see a spdif.

```

default:CARD=ICE1724
    ICEnsemble ICE1724, ICE1724
    Default Audio Device
front:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    Front speakers
rear:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724
    Rear speakers
center_lfe:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724
    Center and Subwoofer speakers
side:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724
    Side speakers
surround40:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    4.0 Surround output to Front and Rear speakers
surround41:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=ICE1724,DEV=0
    ICEnsemble ICE1724, ICE1724
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

I am able to use the optical out with XP just fine and when I go into alsamixer and unmuted the iec958, I get a pcm icon on my receiver.

So to me it seems as though the card is functioning properly, there must be some settings that I am missing.

Let me know if you have any suggestions on how to trouble shoot this problem.

Also, this card shows up in XP as a envy24 Family Audio Controller.  I have seen many other people say that the envy24 chip is heavily supported in Linux.

Lastly, this is all being done on a new clean install of mythbuntu 8.10.

Thanks in advance.

---

### Post by paul.sijpkes on 2008-11-24
Have you had any luck getting the SPDIF to work? I am using the same card, but on Puppy 4.0 linux.  The SPDIF is definitely working, I can see the red light coming out of the other end of the cable...

---

### Post by ericwait on 2008-11-24
Nothing new on this yet.

I am living with just stereo sound at least through Thanksgiving.

Hopefully I will get this fixed before the super bowl!

---

### Post by markbuntu on 2008-11-24
This is a little excerpt from my guide.

Digital Output
Digital output has two different formats. S/PDIF and IEC958. The easiest way to get your digital output working is to just turn it on in your mixer by checking the box labeled S/PDIF or IEC958. You may have number of these boxes so you need to play around with them to find the ones that work for you. If you have a IEC958 or S/PDIF Capture box and you check that, it may direct your microphone to the digital output which will make it unavailable for recording so be careful with that.

These boxes may not appear in the Volume Control and so may need to be accessed directly in the mixer. I highly recommend the gnome-alsamixer for this (see below). If checking any of these boxes causes your sound to disappear, uncheck them. You also may need to reboot before these changes take place as some hardware configuration files are only read at startup.

Mplayer, has an option for AC3 passthrough. VLC has an option to use S/PDIF when available. These options will redirect the audio stream from these players directly to the digital output. Players without these options will use the digital outputs through the ALSA sound server and driver. More in depth information about getting digital output working is available here:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

Digital Output and Pulse Audio
If you are using Pulse Audio, you may have noticed that your digital outputs are unavailable to Pulse Audio. You can still control them in your alsa mixer and their use should not effect your use of Pulse Audio. If you would like to make them available in Pulse Audio, you can look here for a possible solution:

devguy came up with this for controlling digital streams with PulseAudio:

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

The original ticket at pa:

[http://www.pulseaudio.org/ticket/139](http://www.pulseaudio.org/ticket/139)

HDMI
If you are trying to get your HDMI working with your ati card, you need the 8.9 driver, if you have an nvidia card, you need the update 177.78. These have been reported to work by some desktop users and some laptop users, but not all so if it still does not work for you, you may have to wait for a later update. Check that the HDMI or SPDIF/IEC958 output is switched on in the ALSA mixer. HDMI may be in a separate section in alsa mixer or gnome-alsamixer if you have a pci card. Also, because these devices are not generally device 0 on the video card, they may have to be added manually to be used with PulseAudio. See the section immediately above for all that and more general digital output help.

The rest of the guide is here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by ericwait on 2008-11-24
Thanks, I will have to try a couple of things and follow some of you links.  Unfortunately it will not be until after Thanksgiving.

One thing I don't recall is if I had restarted the computer after I unmuted the ice958.

My main goal is to get sound from mythtv into my reciver using the optical plug, but the other app info is a nice fyi.

But shouldn't the system sounds come through the spdif port if it is set up properly?  Say a warning popup or maybe utube video?

I will post my progress as soon as possible.

Thanks again.

---

### Post by ericwait on 2009-01-06
Here is where I stand.
I decided to do a clean install of Ubuntu 8.10.  Now I am able to get sound to go through the optical port for everything but Mythtv.

What I did to get sound was quite simple really:
Go to System->Preferences->Sound
Change all of the drop down menus in the Devices tab to "ICEnsemble ICE1724 IEC1724 IEC958 (ALSA)"
The Default Mixer Tracks is: "ICEnsemble ICE1724 (Alsa mixer)"
Now either through a command prompt #alsamixer or double click the speaker and make sure that the IEC958 Output is switched on (not muted).

That allowed me to use rhythmbox, mplayer, and the like.

However, I am still struggling to get sound to come out of mythtv.  I have tried some but not all of the suggestions on myth's site.  I will continue to weed through them.

In the meantime, if anyone has some suggestions, I would appreciate it.

Thanks. :)

---

