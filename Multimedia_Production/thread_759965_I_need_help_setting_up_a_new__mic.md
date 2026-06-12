---
title: "I need help setting up a new  mic"
date: 2008-04-19
forum: Multimedia Production
---

### Post by zami on 2008-04-19
I just got a Logitech USB desktop mic, but I'm not sure how to set it up and test it.  

Right now I'm just trying to test it, and I'm using gnome-sound-recorder (Sound Capture in the menu).

In Sound Preferneces there are a couple different settings for "sound capture" and using TEST on all of them results in this error
```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

```  
(except for "test sound" which of course just results in hearing the horrible test sound.)

And then in gnome-sound-recorder (aka Sound Capture in the menu) there are a couple of different options for "input" and so far none of them capture anything, but that may be because I don't have the correct "sound capture" option in Sound Preferences.  I just don't know.

Lastly, in the Volume Control (alsa) I've un-muted the mic.  And also followed the instructions for 'Audio Capture" as per documentation here
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

So!  Any hints on what to do?  

-zami

---

### Post by zami on 2008-04-19
I feel I should clarify something. I didn't list sound card, laptop model, etc here, because I don't think I'm having a problem (yet), I just am not sure what I need to "turn on".  And I'd like to knock the easy stuff out of the way before diving into wrestling with my sound card.

I would hate to fight with my sound card and gimp my computer for three days just to stumble upon some silly fix like "go here and click 'enable mic'" , ya know?

But! There might be known conflicts with my particular setup that I would never find on my own, so here goes - 

Dell Inspiron 9300 laptop
Logitech USB desktop microphone
Sound Card?  phttt, no clue.  Device manager tells me
Intel, 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller , PCI

-zami

EDIT:
Another detail - when I'm looking at Sound Preferences, if I select USB Audio under Sound Capture the mic works when I run the test, but I still  get the error I listed above.  So I know the mic itself works, I know at some level the machine can hear it, I just don't know how to make use of it.

-zami

---

### Post by zami on 2008-04-19
Well, hours later I'm right where I was hours ago, except for incredibly frustrated.  There are just too many variables.  I just don't know what to "turn on" to get Skype and my USB mic working.

In 
System > Preferences > Sound
I've left everything at ALSA, because that's what works - 
but what should I put for Auto Confercing Capture?  Other posts say ALSA, but USB Input is the only one that performs for testing.  (though even it gives the previously stated error)

Do I disable or enable "Enable software sound mixing" ?  I've left it enabled because I like my system sounds, but I've also tried it disabled  because of other posts suggesting such for mic problems.  No change, so I just turned it back on.

Then in the Volume Control... uhg, this is where it gets hairy.

Device - Intel ALSA
Master, Master Mono, Headphone, 3d Control Center, 3D Control Depth, PCM, Line-in, CD, Microphone, Video, Phone, IEC958 Playback AC97-SPSA, PC Speaker, AUX 
so confusing because my mic is not on "mic", it's a usb mic.  And "master" does not control my volume, PCM does.
Also in ALSA?  The Recording tab - I cranked this up.
The Switches tab.  This one boggles me.  It's got 
3D Control switch, line-in capture, microphone capture, mic boost, video capture, phone capture, iec958, Aux Capture, Mix, Mix Mono, External Amplifier
I'll I've found is I have to keep External Amplifier checked or I have no sound at all.
Last in ALSA is Options.
PCM Out Path & Mute : pre3D or post3D ?  
Mic Selet : Mic1 or Mic2?
Mono Output Select: Mix or Mic?

And then? There are MORE devices with MORE options!

AK5370 - Microphone with mute and volume controls

SigmaTel STAC9750,51 OSS 
Playback tab has Speaker, PCM-2, In-gain, Digital-1
Recording tab has Volume, Line-in, Microphone, CD, Line-1, Phone-in, Phone-out, Video

AAAAGH! TOO MANY variables!  Even rulling out the obviously unneeded, like "phone out" in OSS because I'm not dealing with a phone or using OSS, this is just too many option combinations.

Can anyone give me some pointers on what should be "turned on" to get my USB Mic + Skype going on my Dell laptop?

-zami

---

