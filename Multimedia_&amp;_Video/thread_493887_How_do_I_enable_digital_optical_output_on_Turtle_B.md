---
title: "How do I enable digital optical output on Turtle Beach Riviera 5.1"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by kidcharles on 2007-07-06
I think I found the answer to this problem a few days ago, but after literally hours of fruitless searching I can't for the life of me find it again.

I'm trying to enable my digital optical output from my Turtle Beach Riviera 5.1 sound card for both 2-channel and Dolby Digital 5.1 on my stereo amplifier. I know that the card will not output both the analog stereo and the digital output simultaneously, but I don't know how to switch to the digital output.

When I run alsamixer it appears and I can adjust the settings for the card "C-Media PCI CMI8738-MC6" which is the correct card, but I don't see any options for the digital output.

Does anyone know how to do this? Thanks.

---

### Post by kidcharles on 2007-07-06
Here's an update on my progress:

I was able to get PCM audio from the optical output by simply unmuting the "IEC958 Output" channel using alsamixer. (This is done by using the arrow key to select the channel and pressing 'm' to unmute.) I also set all items under System -> Preferences -> Sound -> Devices to "ALSA - Advanced Linux Sound Architecture", but setting them all to "C-Media PCI IEC958" also works.

I am now trying to get 5.1 passthrough for decoding by my external amplifier. I mostly need this to happen in xine. I uncommented the "audio.output.speaker_arrangement:" line in ~/.xine/config and replaced "Stereo 2.0" with "Pass Through". This caused an error in xine whenever Dolby Digital audio is attempted to be played:

"The audio device is unavailable. Please verify if another program already use it."

Any thoughts on a fix to this problem? Thanks.

---

### Post by Tech^CF on 2007-07-09
**Thanks a lot!** This helped me get optical out on my HDA X-Mystique which is based on the same chip. I notice the alsa mixer won't adjust volume, but that is a minor annoyance as I always do it on the stereo

---

### Post by kidcharles on 2007-07-14
Bumpity bump bump.

It's astonishing how difficult it is to simply pass a digital stream through an output. What could be simpler?

---

### Post by ArcticChicken on 2007-07-15
[quote=kidcharles]It's astonishing how difficult it is to simply pass a digital stream through an output.[/quote]

I wound up here trying to figure out how to get my Auzentech HDA Xplosion audio card to send Dolby Digital or DTS to my receiver.  At first I couldn't get any output over the optical SPDIF connection at all, which was really, really annoying.  In my case it turns out I had to have the "IEC958 Loop" setting set to OFF and the "IEC958 Output" setting set to ON.  The other Advanced / IEC958 settings might make some type of quality difference, but for just getting some darn sound to come out they don't at all in my case.

So now, kidcharles, I think I've found  myself in the same situation as you.  I've got my digital optical connection up, but my receiver only sees PCM data arriving.

Looking through the manual for my Xplosion card, it seems like the card is expecting to assume total control of the audio data.  It expects to be doing the digital information decoding, so that it can control exactly gets sent to which speaker.

Doing a little more research, at the[ Auzentech website's FAQ](http://www.auzentech.com/site/support/FAQ.php) I came across this entry:

> Q :  Are Auzentech Soundcards compatible with Linux?
A : Auzentech soundcards have limited compatibility with Linux. C-Media, our chipset manufacturer, has released the Linux driver for 8738, 8768, and 8770 chipsets. However, the driver does not support Dolby Digital Live and DTS Interactive. According to C-Media, Dolby and DTS do not intend to open their source for Linux OS.

So that's where I'm at (basically a dead end, I guess).

Do I take it from what you've written here that you're trying to get around a similar sound card limitation by sending the raw, unprocessed-by-the-soundcard audio data straight out the optical connection, leaving it up to the amplifier/receiver to figure out what the heck to do with it?  Did I get that right?  If so, now you've got my interest so I have to ask:  is that really possible?  Will the hardware at either end really be able to make that happen?

And yes, I am an audio newb.  :-)

---

### Post by ArcticChicken on 2007-07-15
Wow.  Kidcharles, I owe you a donut. :-)

If you hadn't posted here looking for help, I might have just given up and assumed that 2-channel PCM stereo was the best I'd be able to do.

In Xine (with the "Configuration experience level" set to "Master of the known universe"), in the Setup, under the Audio tab, I changed the "Speaker arrangement" from the default "Stereo 2.0" to "Pass Through".

One setting.  That was all I had to do.  I can now play content in either Dolby Digital or DTS!

I'll add that Xine shows a number of other, complicated settings under the Audio tab that appear to have defaulted to good choices.  Maybe it's one of those that's the missing key for your needs?

In lieu of a donut, I'll offer the list of the settings under my Audio tab:

notify changes to the hardware mixer [checked]
audio driver to use ["auto"]
use A/52 dynamic range compression [UNchecked]
downmix audio to 2 channel surround stereo [UNchecked]
A/52 volume [dead center]
device used for mono output ["default"]
device used for stereo output ["default"]
alsa mixer device ["PCM"]
sound card can do mmap [UNchecked]
device used for 5.1-channel output ["iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2"]
device used for 4-channel output ["plug:surround40:0"]
device used for 5.1-channel output ["plug:surround51:0"]
speaker arrangment ["Pass Through"]
offset for digital passthrough ["0"]
play audio even on slow/fast speeds [UNchecked]
method to sync audio and video ["metronom feedback"]
always resample to this rate (0 to disable) ["0"]
enable resampling ["auto"]
startup audio volume [dead center]
restore volume level at startup [UNchecked]

My values are in the square brackets.  Anything in quotes just means the text between them is actually typed in in the field.  Leave the quotes out if you use the values.

I hope something there helps you out.  Let me know if you think there's something else I might be able to look at that could help.

---

### Post by kidcharles on 2007-07-15
> **ArcticChicken said:**
> Do I take it from what you've written here that you're trying to get around a similar sound card limitation by sending the raw, unprocessed-by-the-soundcard audio data straight out the optical connection, leaving it up to the amplifier/receiver to figure out what the heck to do with it?  Did I get that right?  If so, now you've got my interest so I have to ask:  is that really possible?  Will the hardware at either end really be able to make that happen?

That quote about "Dolby Digital Live and DTS Interactive" refers to real-time encoding of multi-channel (well, more than 2 anyway) digital streams for things like video games. This is different from simply passing an already-encoded audio stream from a DVD or HDTV recording. This chipset can definitely handle this, as you have discovered, you lucky duck (or should I say chicken?).

> **ArcticChicken said:**
> 
In Xine (with the "Configuration experience level" set to "Master of the known universe"), in the Setup, under the Audio tab, I changed the "Speaker arrangement" from the default "Stereo 2.0" to "Pass Through".


I've actually already tried this simple step and it didn't work for me. I'm going to try to set all my Xine audio settings the same as you have and see if that does the trick. I'll report back.

---

### Post by kidcharles on 2007-07-15
I'm still getting that same error about the audio device being unavailable (see above post). I have a feeling it might be an issue with the fact that the card itself has 3 devices on it, check out this 'aplay -l' output. Notice the IEC958 output is device 2:

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I shall bark up this tree for awhile...

Update:  I set the "device used for 5.1 channel output" to "iec958:AES0=0x2" which I am certain is the correct device but I still get the error. I even turned off my Mythtv Frontend to make sure it wasn't using the device but no luck.

---

### Post by ArcticChicken on 2007-07-16
Hmm.  Well, keeping in mind I'm working with an Auzentec card, I figured it'd at least be interesting to try that 'aplay' command to see what differences, if any, turned up.  I'd never even seen 'aplay' referenced anywhere before, but sure enough it's available on my system (which is running Debian by the way, but don't tell anyone  ;-)  ):

```

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC8 [C-Media PCI CMI8738-MC8], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by ArcticChicken on 2007-07-16
Well this is clearly all over my head, but a quick search on a simple string of "iec958:AES0" shows that my passthrough device setting isn't all that unique.  There are also a lot of occurrences of "iec958:AES0=0x2,AES1=0x82,AES2=0x0,AES3=0x2" (i.e. AES0=0x2 instead of my AES0=0x6).  Same as your guess, only longer.  Trying the longer string might be worthwhile?

---

### Post by kidcharles on 2007-07-16
No luck. I tried the long string and "iec958:AESX=0x2" with X = 0,1,2,3 but no luck with any of those either.

---

### Post by kidcharles on 2007-08-05
Success! I sort of gave up for a couple of weeks then within 15 minutes of trying to get it working again I did it. The key for me was to add the following lines to my ~/.asoundrc file:

```

defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device

```

I thought to do this because when I tried the following action:

$ mplayer -ac hwac3 video.mpg

An error popped up saying:

alsa-lib: confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.iec958.device'

Adding these two lines did the trick.

I can now get 5.1 audio out of both mplayer and xine.

---

### Post by hondoslack on 2007-08-08
Hi KC, I'm thinking of returning my current ENVY24 based card (AC3 passthrough doesn't work) and ordering the TB Riviera. Could you post your entire asoundrc file for posterity? Thx :guitar:

---

### Post by hondoslack on 2007-08-09
never mind, I went and bought one last night, installed feisty fresh, and voila, hwac3 comes out the optical output just fine :-). No file tweaking whatsoever. Unlike that POS AV-710. I tried getting just the analog to work on my main box (feisty as well), no go. Its all I could to not chuck the thing out the window. I'm sending it back for a refund...

Anyone trolling the forums, do NOT buy Chainlink AV-710. Its a piece of crap. After several hours wasted, trying to get it working, I found a bug posted for it on launchpad. The bug clearly states that ENVY24 based cards DON'T WORK. Spend the extra five bucks and get the Riviera instead.

---

### Post by kidcharles on 2007-08-12
Good to hear you didn't have much trouble with the Riviera hondoslack. I'll post my asoundrc files anyway:

.asoundrc:
```

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/mark/.asoundrc.asoundconf>
pcm.!default { type hw card 0 }
ctl.!default { type hw card 0 }
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device

```

.asoundrc.asoundconf:
```

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card CMI8738MC6
defaults.ctl.card CMI8738MC6
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix_max_periods 0
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0

```

---

### Post by prashanth1204 on 2008-06-30
I spent quite some time trying to enable the Optical output myself. Then I came across your post. My PC has Hardy (8.04) 64 bit with ALC888 and this tip worked for me. Thanks!

---

### Post by luke16 on 2008-07-05
> **prashanth1204 said:**
> I spent quite some time trying to enable the Optical output myself. Then I came across your post. My PC has Hardy (8.04) 64 bit with ALC888 and this tip worked for me. Thanks!

Are you using pulse audio? Did you just get optical working in stereo, or did you manage to get surround working as well?

---

