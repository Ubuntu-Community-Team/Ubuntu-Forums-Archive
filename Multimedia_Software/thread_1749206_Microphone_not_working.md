---
title: "Microphone not working"
date: 2011-05-04
forum: Multimedia Software
---

### Post by Dry Lips on 2011-05-04
I've got an Asus motherboard with an integrated Nvida sound card 
(nVidia Corporation MCP61). I've also got a headset with a microphone
that I intend to use for Skype (it has two normal mini-jack connectors). 
Unfortunately, although the sound work as it is supposed to do, I don't 
manage to record any sound from the mic using “Sound Recorder”. 
The headset works just fine (tried it with another computer), but no sound
 when I try to use it on my own. (Only static noise.) I've got it to record with 
Xubuntu (although with bad sound quality), but not in Ubuntu nor Kubuntu.

    Under sound Preferences>Input>Connector there are only two options: 
Analogue Microphone and Analogue Line-in. None of them work.

---

### Post by lidex on 2011-05-04
So what profile do you have selected on the hardware tab?

---

### Post by Dry Lips on 2011-05-05
Thanks for replying lidex!

Internal audio/Analogue Stereo Duplex

---

### Post by lidex on 2011-05-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Dry Lips on 2011-05-06
I had to run this command twice in order to get a link. There was no link the first time... Anyway, here goes:
[http://www.alsa-project.org/db/?f=93ea901b5fa7179c2d036aaf049701fb3a096f45](http://www.alsa-project.org/db/?f=93ea901b5fa7179c2d036aaf049701fb3a096f45)

---

### Post by lidex on 2011-05-06
So you're using a headset mic plugged into the front mic input, correct?

---

### Post by Dry Lips on 2011-05-07
> **lidex said:**
> So you're using a headset mic plugged into the front mic input, correct?

Aye, but I've tried using the output at the back of the computer as well...

---

### Post by lidex on 2011-05-08
B4 we get too technical you should try mucking about with these settings in your mixer of choice:
```
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: [COLOR="Red"]Playback 0 [0%][/COLOR] [-34.50dB] [on]
  Front Right: [COLOR="Red"]Playback 0 [0%][/COLOR] [-34.50dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: [COLOR="Red"]Capture 0 [0%] [0.00dB][/COLOR]
  Front Right: [COLOR="Red"]Capture 0 [0%] [0.00dB][/COLOR]
```

**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by Dry Lips on 2011-05-08
I'm afraid the settings in alsamixer don't exactly match the output you provided:

---

### Post by Dry Lips on 2011-05-08
It's alive! ...sort of.  In alsamixer I first set “front” to zero. 
(As you can see from the screenshot above.)
But "front" needed to be switched on in order to get any sound. 
At "capture" I set one of the channels to 50%, the input source to
“front mic”, and then I got sound when I recorded. The only thing
that bugs me now, is that there is a horrible humming sound that 
accompanies the recording.

Any ideas on how to get rid of this?

Another thing I found out was that the Byobu Terminal doesn't handle 
alsamixer very well, I had to use the normal terminal to be able to switch
between playback and capture.

Thank you so much for your help so far! :)

---

### Post by lidex on 2011-05-08
Since you have gnome-alsamixer, use the 'Edit -> Soundcard Properties' to make sure required elements are enabled. When in alsamixer, hit <F4> to show capture elements. This may help further:
From ubuntu wiki:
> Changing default subdevice configuration

Some sound devices have multiple capture subdevices (eg. hda-intel), 
but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. 
ALSA may not be configured to use your preferred device as subdevice #0 by default.

Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), 
so we are watching for movements that correspond to our voice. 

Use alsamixer -c n (where n is your sound card number, probably 0)
Press F4 to get to the capture console
Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), 
and the volume turned up.
Check the first input source is switched to your chosen plug (Mic, in my case) 
At this point, you should see the record meter bouncing in response to your voice.
I found that I had to repeat this procedure each time I wanted to use the Mic, 
even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized 
until it was repeated. This also works if you use the "Options" tab in the standard mixer app to do the same thing.

---

### Post by Dry Lips on 2011-05-09
I've found these settings to work nicely:

My settings in **alsamixer**:
*Playback *
Master F: 8%
PCM: 99%
Front: 100%
Front Mic: 0%
Line: 0%
(there are other settings too, but these are the important ones.) 

*Recording*
Front mic boost: 100%
Mic boost: 0% 
Capture: 18%
Capture1: 0%
Input Source : Front Mic

However, once you start Skype, Skype changes the mixer settings automatically 
(for the worse). The sound is adjusted so that a humming background noise is noticeable. To change this (in Skype) go to options (click the blue button at the bottom left) click at &#8220;sound devices&#8221;, untick the box that says: "Allow Skype to automatically adjust my mixer levels".

So to sum this up for people who might encounter the same problem:
**1**. Make sure the microphone is connected, and not muted.
**2**. Type ```
alsamixer
``` in the terminal (install it if you haven't got it) 
**3**. Adjust the settings for the playback to match those above (YMMV)
**4**. Press F4 and adjust the settings for the mic to match those above (YMMV)
**5**. Prevent Skype from messing with your settings, as described above.


Thank you so much for helping me out **lidex**! :D

---

### Post by lidex on 2011-05-10
Nicely done and thanks for posting your fix for others to see.

---

### Post by secretaznman3 on 2011-05-10
lidex,

Ive searched through more forums than i have wanted to (with your advice showing up on a majority of them btw) and i still cannot fix my microphone. I get no sound when using sound recorder or any audio captured through skype.

I uploaded my alsa settings: [http://www.alsa-project.org/db/?f=123458e32d7416fb587eba7e99c901ae0dbf6c08](http://www.alsa-project.org/db/?f=123458e32d7416fb587eba7e99c901ae0dbf6c08)

If you could help i would be eternally grateful haha thanks

Also, as I am a noob in a sense, could you make it rather detailed on how to fix it? lol thanks again.

---

### Post by lidex on 2011-05-11
> **secretaznman3 said:**
> lidex,

Ive searched through more forums than i have wanted to (with your advice showing up on a majority of them btw) and i still cannot fix my microphone. I get no sound when using sound recorder or any audio captured through skype.

I uploaded my alsa settings: [http://www.alsa-project.org/db/?f=123458e32d7416fb587eba7e99c901ae0dbf6c08](http://www.alsa-project.org/db/?f=123458e32d7416fb587eba7e99c901ae0dbf6c08)

If you could help i would be eternally grateful haha thanks

Also, as I am a noob in a sense, could you make it rather detailed on how to fix it? lol thanks again.

Why don't you try adjusting these levels in alsamixer:
```
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 1 [1%] [-73.00dB] [on]
  Front Right: Capture 1 [1%] [-73.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '40dB'

```

Turn your capture level up. The range is 0 - 80 and currently set at 1.

This may help as well. From ubuntu wiki:
> Changing default subdevice configuration

Some sound devices have multiple capture subdevices (eg. hda-intel), 
but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. 
ALSA may not be configured to use your preferred device as subdevice #0 by default.

Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), 
so we are watching for movements that correspond to our voice. 

Use alsamixer -c n (where n is your sound card number, probably 0)
Press F4 to get to the capture console
Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), 
and the volume turned up.
Check the first input source is switched to your chosen plug (Mic, in my case) 
At this point, you should see the record meter bouncing in response to your voice.
I found that I had to repeat this procedure each time I wanted to use the Mic, 
even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized 
until it was repeated. This also works if you use the "Options" tab in the standard mixer app to do the same thing.

---

### Post by secretaznman3 on 2011-05-11
> **lidex said:**
> Why don't you try adjusting these levels in alsamixer:
```
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 1 [1%] [-73.00dB] [on]
  Front Right: Capture 1 [1%] [-73.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '40dB'

```

Turn your capture level up. The range is 0 - 80 and currently set at 1.

This may help as well. From ubuntu wiki:


I changed my capture settings now to 80 shown here in my new alsa script log thing: [http://www.alsa-project.org/db/?f=29dd9eec9c823138ccb25cdfe8d83a3ed20759ad](http://www.alsa-project.org/db/?f=29dd9eec9c823138ccb25cdfe8d83a3ed20759ad)

I then went into my sound preferences and didn't see anything in the input tab. Then i opened PulseAudio Volume Control and in the recording tab it said that the GNOME Volume Control Dialog was recording but the green level beneath that was extremely small (maybe 1% of the full bar) and when i yelled it fluttered a tiny bit. 
So in the GNOME Volume Control I set the input volume in the input tab to full, past the unamplified 100% mark, and saw that the green bar in PulseAudio grow to maybe 5% full, but fluttering.

My recorded voice in 'Sound Record' is audible but only when my ear is right against my speakers when the output volume is set to full.

I tried to write everything I did so if it's unclear im sorry. Thanks!

---

### Post by lidex on 2011-05-11
On closer inspection, namely your dmesg output, it looks like that hp-laptop model is incorrect. Edit it to look like this:
```
options snd-hda-intel model=thinkpad
```

Open for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```

---

### Post by secretaznman3 on 2011-05-11
> **lidex said:**
> On closer inspection, namely your dmesg output, it looks like that hp-laptop model is incorrect. Edit it to look like this:
```
options snd-hda-intel model=thinkpad
```

Open for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```

Ok i just did that. Do i need to update anything afterwards? ALso, I don't have a thinkpad..does that matter?

---

### Post by lidex on 2011-05-11
> **secretaznman3 said:**
> Ok i just did that. Do i need to update anything afterwards? ALso, I don't have a thinkpad..does that matter?

You'll need to reconfigure your settings - check the previous posts.

---

### Post by secretaznman3 on 2011-05-11
> **lidex said:**
> You'll need to reconfigure your settings - check the previous posts.

When i change "hp-laptop" to "thinkpad" and then i reset my computer and go back to PulseAudio there is no longer any green bar indicating recording in the record tab.

---

### Post by lidex on 2011-05-11
What profile and soundcard are chosen in 'Sound Preferences'?

---

### Post by Veetmo on 2011-05-12
Hello lidex!

I have a different kind of problem, but it is related I believe.

I am using a mac mini with Phillips SPC 900 NC camera.
I am also trying to use headphones with mic, but the mic does not seem to work.

The Phillips SPC 900 NC has a built in mic. Lately after upgrading to natty either the mic or the camera work, but not both. I was hoping that using headphones with mic will help. It does not. 

Let me know if you can help.

Thank you in advance!

[http://www.alsa-project.org/db/?f=df454f0109510d78ec7dc3d03da803ca9fbf2c13](http://www.alsa-project.org/db/?f=df454f0109510d78ec7dc3d03da803ca9fbf2c13)

---

### Post by secretaznman3 on 2011-05-12
> **lidex said:**
> What profile and soundcard are chosen in 'Sound Preferences'?

The profile selected is Analog Stereo Duplex. The soundcard is HDA Intel.

---

### Post by lidex on 2011-05-12
> **Veetmo said:**
> Hello lidex!

I have a different kind of problem, but it is related I believe.

I am using a mac mini with Phillips SPC 900 NC camera.
I am also trying to use headphones with mic, but the mic does not seem to work.

The Phillips SPC 900 NC has a built in mic. Lately after upgrading to natty either the mic or the camera work, but not both. I was hoping that using headphones with mic will help. It does not. 

Let me know if you can help.

Thank you in advance!

[http://www.alsa-project.org/db/?f=df454f0109510d78ec7dc3d03da803ca9fbf2c13](http://www.alsa-project.org/db/?f=df454f0109510d78ec7dc3d03da803ca9fbf2c13)
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=macmini3" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Use alsamixer to increase mic 0 capture level in USB mixer

---

### Post by Veetmo on 2011-05-13
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=macmini3" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Use alsamixer to increase mic 0 capture level in USB mixer

Thank you for your reply!

I am now using a camera that does not have mic included. Therefore the USB device mic does not exist anymore as I am trying to use the mic from the mac mini mic line-in, that does not seem to work at the moment.

Therefore the new settings are:
[http://www.alsa-project.org/db/?f=637e453c0ff40a34c0eb5c2e31bd164e2fed3cd1](http://www.alsa-project.org/db/?f=637e453c0ff40a34c0eb5c2e31bd164e2fed3cd1)

---

### Post by lidex on 2011-05-13
You're using capture 0 and you also have 1 and 2. Try using those.

---

