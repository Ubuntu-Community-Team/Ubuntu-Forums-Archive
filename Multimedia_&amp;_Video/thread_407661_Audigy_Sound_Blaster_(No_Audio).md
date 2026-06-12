---
title: "Audigy Sound Blaster (No Audio)"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by aqualad on 2007-04-12
I have an Audigy Sound Blaster ZS sound card which is recognized in Device Manager, but I can't get any sound through my speakers.

I'm fairly unsure at what to do with audio problems, seeing as how everything has always been automatically detected before now, but here's a command I found that might help in troubleshooting:
```
aqualad@desky:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I think the problem might be the integrated Intel sound card, but I don't know if there's any way to blacklist it or anything.

I went back to windows to check and make sure the speakers are all connected properly and working.  Also, I tried turning up the volume on all of the various settings of my sound card just to be sure (and yes, in alsa mixer I did set the device to Audigy Sound Blaster and not the integrated)

I'm on Feisty 7.04

Any help is always appreciated :]

Edit: I'm using the version of Alsa that came with Feisty, so I believe it's the most up to date 1.0.13

---

### Post by RJARRRPCGP on 2007-04-14
```
 device 0: emu10k1 
```

I dunno, because at least to Linux, it has the same APU as my SoundBlaster Live CT4670, the Emu 10K1.  

My SoundBlaster Live is automatically detected and is usable.

---

### Post by studbucket on 2007-04-14
I have almost the exact same problem.  It started happening after yesterday's updates (I got a dsdt.aml error, and flashed the BIOS, after some time, Ubuntu worked great, but no sound).

Here's my 'aplay' output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 [SB0240]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 2 [SB0240]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 [SB0240]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 [SB0240]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by OldGaf on 2007-04-14
Check this out:

[http://ubuntuforums.org/showthread.php?t=408742]("http://ubuntuforums.org/showthread.php?t=408742")


"Originally Posted by Timbuck.3 View Post 
Kubuntu Feisty: Kernel 2.6.20-15-generic
Same sound card, same Problem........
 
 But now it works

Go in KMix ( or the same program on Gnome )
Uncheck Audigy Analog/Digital Output Jack"

---

### Post by studbucket on 2007-04-14
> **OldGaf said:**
> Check this out:

[http://ubuntuforums.org/showthread.php?t=408742]("http://ubuntuforums.org/showthread.php?t=408742")


"Originally Posted by Timbuck.3 View Post 
Kubuntu Feisty: Kernel 2.6.20-15-generic
Same sound card, same Problem........
 
 But now it works

Go in KMix ( or the same program on Gnome )
Uncheck Audigy Analog/Digital Output Jack"

Hi, I saw the other thread, unfortunately I can't find the Audigy Analog or Digital Output Jack options anywhere in my sound control panels (Gnome).

---

### Post by OldGaf on 2007-04-14
Mine is KDE, but in KMix it was under the "switches" tab, not the "input" or the "output". Maybe Gnome has something similar?

---

### Post by studbucket on 2007-04-14
Well, I just rebooted and my sound works now.  Thanks for the help though :)

---

### Post by OldGaf on 2007-04-14
Glad to hear it....... got to have sound woot?

---

### Post by Subw00fer on 2007-04-14
I'm having the exact same problem but a reboot didn't fix my error.  I looked thru that thread and I didn't see anything that would fix this for me.  Any suggestions?

Also I'm using Edgy and I don't have KMix

---

### Post by Subw00fer on 2007-04-14
alright I fixed it.....stupid.....the PCM was turned all the way down.

---

### Post by OldGaf on 2007-04-14
lol...... welcome to the stupid club!

Just remember..... I was here first!

---

### Post by aqualad on 2007-04-18
My problem isn't solved by changing the "Audigy Analog/Digital Output Jack" option, though it does make my speakers make a funny crackle noise for a sec.

I'm pretty sure I've played with all the settings and gotten no response other than that one option, which all it does it make a click noise through the speakers.  I've got the volume up on every setting and the speakers physically turned up, yet still nothing.

I think my problem might be that by default it's trying to use the Intel integrated card on my motherboard.  Is there any way for me to black list that and get it to only use my Audigy card?  Maybe it's got some kind of intel drivers instead of Audigy.

I really need sound, it's driving me crazy!

Thanks

---

### Post by deadgobby on 2007-04-18
Here is what you need to do. Go into your BIOS and disable the on board sound card. It is very easy to do and once you disable the on board sound card. All sound should default to the SB. To control volume and such you'll need ALSA installed. 
If you run Gnome you can install Gnome ALSA mixer through Synaptic. Or you can install the simple form of ALSA mixer through the Terminal. The command to install through the Terminal would be

sudo aptitude install alsamixer

Once install type in the terminal

alsamixer

Gnome mixer after it is install can be found in
Apps> Sound> Gnome Mixer
 
[http://ubuntuforums.org/showthread.php?t=405615](http://ubuntuforums.org/showthread.php?t=405615)

Gobby

---

### Post by superm1 on 2007-04-18
Really, I'm wondering if something in recent Feisty updates did break Audigy for some people.  I just upgraded to Feisty and had sound functioning fine the first few boots.  I rebooted for a new kernel and a few other things, and lone behold no sound.  Didn't change any settings, didn't touch any cables.  I started fumbling with the mixers, testing speakers, replacing cables, and in the end I conclude something went wrong during these updates.

---

### Post by aqualad on 2007-04-18
Wow, so I completely forgot about the BIOS setting.  I remember I had this problem a while ago back when I was using Hoary I think, it happens when I dual boot with windows, because every time it goes into windows for some reason it resets the setting in BIOS.

The good news is that it works now, and that's all that matters.  Thanks all :]

Oh, also, I think I actually had to enable the "Audigy Analog/Digital Output Jack" before it worked.

Thanks again :]

---

### Post by polomint on 2007-04-19
@OldGaf  

I've been having this stupid problem for a few days now following an upgrade to feisty beta, and thanks to your post, it's working again!!  You are a genius...

it's strange that the "audigy digital output is enabled" after install. 

still i have another problem tho: everytime I reboot there is chance that the default sound card changes. I can tell because the when the login screen appear the drum sound sometimes comes from my speaker (Audigy), and sometimes through my headphones (Built-in soundcard)... but hey, at least I got sound!!

---

### Post by plb on 2007-04-19
Found Solution: open alsamixer goto "Audigy Analog/Digital Output Jack" and turn it off = hit "M"

---

### Post by The Keeper on 2007-04-20
I too have problems with my Audugy 2 ZS. I had these same problems in Edgy as well, reported the problem to launchpad but apparently nothing was done about it. The funny thing is that sound worked fine in Feisty Ubuntu liveCD, but after installation it didn't.

Gnome mixer detects both onboard audio and Audigy. Disabling "Audigy Analog/Digital Output Jack" in gnome mixer does nothing, neither does "External Amplifier". After reboot all audio settings are mysteriously back to their default values, including  "Audigy Analog/Digital Output Jack" and PCM volume is all the way down to mute. Raising PCM volume and disabling  "Audigy Analog/Digital Output Jack" won't bring audio live though.

Alsamixer is no good because it displays the disabled on-board audio settings instead of Audigy and I couldn't figure out how to switch to Audigy in alsamixer, if it even supports multiple audio devices.

In short, none of the tricks in this thread helps. In Edgy I got Audigy working after blacklisting about all on-board audio modules, I have yet to try this in Feisty. Seriously though, this should work out of the box already! The last time audio worked properly without dirty tricks was in Dapper. I wonder if I would have better luck with Kubuntu.

Edit: Well now sound won\t work even on livecd.

---

### Post by Madmoose on 2007-04-20
Ever since I updated I just noticed that my "alsamixer" is pointing to my system boarded sound card, and not my Audigy sound card

Edgy did this, so I went into sound. Then switched it to the right card, but here on Feisty it's already on that card. Yet, alsomixer is pointing to my other unused card. 

How do I fix this?

Thanks

---

### Post by snotface on 2007-04-21
Hi guys, first post here so hope this helps.  I was having the same problem with my Audigy 2 ZS with Feisty / Gnome.  I found that if you right click on your volume control and go to 'Open Volume Control' then 'Edit -> Preferences' you can add options to the control panel.  My Audigy Analog/Digital Output Jack was disabled and my PC Speakers were muted.  Also, under 'File -> Change Device' it was set to the wrong sound card.  Once I corrected these settings, my sound has worked ever since.

Hope this helps.  Good luck!

---

### Post by The Keeper on 2007-04-21
Done all that yesterday, didn't help.

Edit: Nevermind this. Sound doesn't work, flash 9 plugin freezes firefox and gnome all the time and fonts still look like crap. I wonder what else I would've found after more than 3 hours. Maybe ubuntu should've switched to 12 month development cycles after Dapper, 6 months obviously isn't enough to release a solid distro. I'll go back to WinXP and wait for Gutsy. After edgy and feisty disappointments I don't hold much faith in gutsy though.

---

### Post by fafek2 on 2007-04-21
I think there are problems becuase configuration files are corrupted. 

When i try to launch GNOME's Alsamixer, I receive following error message:
```

"Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Bass": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Bass": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Treble": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Treble": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-3D_Control_Sigmatel_-_Depth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PCM_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PCM_Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Front": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Surround": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Center": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-LFE": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Synth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Synth": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Line": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Line": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Line2": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Line2": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Mic": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Mic": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Phone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Phone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-IEC958_Optical": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-IEC958_Optical": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-PC_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-PC_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Aux": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Aux": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Aux2": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Aux2": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Analog_Mix": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Analog_Mix": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Audigy_CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9721,23-Audigy_CD": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Tone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Tone": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-3D_Control_-_Switch": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-3D_Control_-_Switch": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Mic_Boost___20dB_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Mic_Boost___20dB_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-IEC958_Optical_Raw": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-IEC958_Optical_Raw": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Audigy_Analog_Digital_Output_Jack": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Audigy_Analog_Digital_Output_Jack": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-External_Amplifier": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Sigmatel_4-Speaker_Stereo": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Sigmatel_4-Speaker_Stereo": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/SigmaTel_STAC9721,23-Sigmatel_Surround_Phase_Inversion_Playback_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/SigmaTel_STAC9721,23-Sigmatel_Surround_Phase_Inversion_Playback_": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/SigmaTel_STAC9721,23": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_names/SigmaTel_STAC9721,23": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash (/)
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash (/)

```

By the way, I don't want disable on-board music card as I'm using it to listen music using my headphones.

Changing default card using GNOME's applet doesn't work. When I choose "Audigy" it changes after reboot to "Brooktree" which is midi device I suppose. Nonetheless, audio is played by on-board music card - Intel ICH5.

---

### Post by zerosystem on 2007-04-22
Heh, I had the same problem as the people in this thread:

[http://ubuntuforums.org/showthread.php?t=415894](http://ubuntuforums.org/showthread.php?t=415894)

And I was about to reboot and go into the BIOS (I still intend to), but you saved me a couple of minutes. I had the same 'FATAL: Module snd_ not found.' error as the people in the thread,  but all I had to do is *disable* digital output.

---

### Post by elsaturnino on 2007-04-22
> **studbucket said:**
> Hi, I saw the other thread, unfortunately I can't find the Audigy Analog or Digital Output Jack options anywhere in my sound control panels (Gnome).

I had this exact problem. First I used did "sudo asoundconf list" to list my soundcards then "sudo asoundconf set-default-card Audigy" to set the default soundcard to audigy. This didn't do the trick so I right clicked on the volume control icon in the gnome system tray thingy (ya, whatever that is called up in the upper right corner), then "open volume control" and under the "Switches" tab there is the option for "Audigy Digital/Analog Output jack" which I turned off and my sound suddenly started working.

Bad, bad ubuntu for making this such a pain!

---

### Post by stewilliamson on 2007-04-25
Many thanks to all, I now have sound - w00t! 

T'was the "Digital Audio jack" setting for me - why on earth is it enabled by default? Daft.....:guitar:

---

### Post by Pop_A_Squat on 2007-04-25
I got mine working by Going into my Bios and Disabling My on board, then going into sound options and Turning the Digital Audio Jack on. 

I have a Audigy 4 so if people with a A4 are having problems try this.

---

### Post by tadtoll on 2007-04-27
I have an Audigy LS card. I fixed the problem (no sound after dist upgrade to Feisty) in Gnome by opening  the volume control, going to Edit>Preferences, and turing on all the ticks to make everything visible, which exposed a tab called "Switches". I then turned the tick for IEC958 off and got my sound back instantly. 

Hope that helps somebody out there.

---

### Post by phansiizwe on 2007-04-27
> **stewilliamson said:**
> Many thanks to all, I now have sound - w00t! 

T'was the "Digital Audio jack" setting for me - why on earth is it enabled by default? Daft.....:guitar:

This seems to be a rather complicated problem, see: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/94189](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/94189)

---

### Post by icantdothatdave on 2007-04-28
My problem seems to be a little more complicated. I also don't have audio, but when I play a movie with Xine, I do get audio. I have digital output turned on (I'm using coax on my speakers), but my sound only works when I'm using the dolby digital in a movie. My sound used to work with these settings. Xine is set to use passthrough so that might explain why it's working, but why doesn't the rest of my sound work anymore? :confused:

---

### Post by djsamsel on 2007-05-04
> **tadtoll said:**
> I have an Audigy LS card. I fixed the problem (no sound after dist upgrade to Feisty) in Gnome by opening  the volume control, going to Edit>Preferences, and turing on all the ticks to make everything visible, which exposed a tab called "Switches". I then turned the tick for IEC958 off and got my sound back instantly. 

Hope that helps somebody out there.

THANKS!!!! I've been working on this for a week. Reading all over the place, this finally got my sound back!!!

---

### Post by sam_i on 2007-05-05
disabling the digital output jack was the answer for me. Cheers guys!

---

### Post by andreigbs on 2007-05-05
Here's a pickle: how do you change the sound config file when my sound card shows up as ATI Tech. SB450 but names the chip SiSXXXx which is my phone modem!!!  The only options i get for sound control are Caller ID and Off-hook.  Somehow it mixed two different and totally separate devices and no wonder the sound card doesn't work.  It's likely the phone modem doesn't work either but I've got wireless LAN so who cares.  How do i fix it?  What do you need me to post so you can see my config?  Thanks i advance.

---

### Post by svenmeier on 2007-10-26
Just for the record:

I searched half a day for the reason why my Soundblaster Live refused to produce any sound at all (after working fine with Kubuntu 7.10 for almost a week).

The cause for this problem was a zero (0) 'Wave' setting in AlsaMixer. Note that the corresponding slider in KMix is located on the *Input*-Tab :confused:.

I don't know, when I accidentially changed that value, but it surely didn't help that:

~$ alsactl restore 0

.. resets this value to zero :(.

I hope this information helps someone.

---

### Post by kleph on 2007-10-27
I had exactly the same problem with my SB Live card - Gutsy saw my card (from aplay -l), but no sound would play. It seems that Gutsy defaulted to the on-board card (an intel-something-or-other)

*** HOW I FIXED THE PROBLEM ***
1) Go to Console
2) Type 'asoundconf list'
    You should see something along the lines of:
    
    > kleph@firefly:~$ asoundconf list
    Names of available sound cards:
    I82801DBICH4
    Live

3) Next, type 'asoundconf set-default-card Live'

This, I assume, tells Gutsy that the SB Live is the default card to be used. My sound worked without a problem, except for a bit of distortion. To fix this I played quite an intense MP3, opened 'alsamixer' and played around till it sounded right.

*NOTE* When using alsamixer, be aware that certain settings can cause some very serious feedback - watch your ears.

Also, if you hear a persistent hissing through the speakers, but still *sort of* hear sounds, the problem might be that you have Digital Out enabled. You can fix this by double-clicking on the sound icon in Gnome > 'Switches' Tab > uncheck the 'SB Live Digital Analog/Digital Output Jack' option.

---

