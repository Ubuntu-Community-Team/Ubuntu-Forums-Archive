---
title: "Make line-in and microphone play on speakers"
date: 2009-12-23
forum: Multimedia Software
---

### Post by SoftwareExplorer on 2009-12-23
I used to have my sound in jaunty set up so I could hear my microphone on the speakers, as well as line in. Now that I'm using Karmic, I can't seem to figure out how to send the line-in and microphone signals to the speakers.

---

### Post by RedSingularity on 2009-12-24
Are you using pulseaudio?  Look at the pulseaudio device chooser.

---

### Post by SoftwareExplorer on 2009-12-24
Yes, I'm using pulseaudio, and I have PulseAudio device chooser. Could you give me instructions on what to change in it?

---

### Post by RedSingularity on 2009-12-24
U want the sound coming out of both the speakers and headset correct?

---

### Post by SoftwareExplorer on 2009-12-24
I have a standalone microphone that plugs in to a pink port in the back of the computer. I would like to have it play on the speakers, or the headphones that I Sometimes plug in. (They're a set of usb-connected headphones that has a microphone, but I don't use the microphone on the headset because it doesn't work (not even with windows, it's broken). Anyway, when I plugin the headphones I like to switch all sound output to the headphones, which I currently do manually through the standard volume control. So I would like to be able to treat the microphone sound like any of the sound producing programs are treated: to be able to switch between the output going to the speakers or the headphones.

---

### Post by RedSingularity on 2009-12-24
In the device chooser select a "Default Source".

Select the one for you soundcard and not the one for your USB headset.

---

### Post by SoftwareExplorer on 2009-12-24
Ok, I open the device chooser program and the icon appears in the tray. If I left click the icon I get a menu 
Default server
Default Sink
Default Source
--------------
Manager
Volume Control
Volume Meter (Recording)
Volume Meter (Playback)
Configure local sound server
----------------------------
Preferences
---------------------------
Quit

What one should I choose?

---

### Post by RedSingularity on 2009-12-24
Default source is the one for the microphone.

---

### Post by SoftwareExplorer on 2009-12-25
I went to the default source, which opens a sub menu. It has default and other, each with a radio button. When I Do default, I still can't hear the microphone on the speakers. I then tried other and it wanted me to enter a name into the text box. I tried entering the name I get when I go to the icon, then Manager, then the devices tab, and then under sources 'alsa_input.pci-0000_00_1b.0.analog-stereo'. I still couldn't hear the microphone. I'm wondering if by source they mean a source for programs to record from, not a source of sound that will be played on the speakers.

---

### Post by RedSingularity on 2009-12-25
Go to System>Pulseaudio Preferences.  

In the first tab check on the first 3 boxes.

Second tab Check none of them

Third tab check on the one option there.

Then go to default source again and see if you can select it properly.

---

### Post by SoftwareExplorer on 2009-12-26
Well, it works, but the audio on the speakers clicks on and off once or twice a second, and is high when it is working, getting higher and higher over time. Even when you are not talking at all you can hear a continuous tapping in the background. Thanks for the help though.

---

### Post by bobbysmith007 on 2010-09-15
An alternative way to enable playing the microphone/line-in through the speakers:
   * go the terminal
   * Type "alsamixer" and hit enter
   * go right a bunch till you find the input you are looking for ( you may have to go past the end of the screen)
   * make sure you turn the volume up and press m to unmute (if necessary)
   * you should hear your guitar / tv / game console etc (with no lag)

---

### Post by SoftwareExplorer on 2010-09-16
> **bobbysmith007 said:**
> An alternative way to enable playing the microphone/line-in through the speakers:
   * go the terminal
   * Type "alsamixer" and hit enter
   * go right a bunch till you find the input you are looking for ( you may have to go past the end of the screen)
   * make sure you turn the volume up and press m to unmute (if necessary)
   * you should hear your guitar / tv / game console etc (with no lag)

Thanks bobbysmith007!
It works great now. If I get some free time I think I'll file a bug about how this is harder to find than it should be.

---

