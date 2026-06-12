---
title: "audio hum in right channel"
date: 2014-09-30
forum: Multimedia Software
---

### Post by edison23 on 2014-09-30
I have fairly clean installation (just few apps added, no messing with drivers and stuff) of Ubuntu 14.04 64bit version and I am experiencing fairly audible (and thus annoying) sort of static/hum in headphones (can't hear it from in-built speakers). When I mute audio, it dissapeares, doesn't change with volume level and doesn't change when connected to/disconnected from power suply. I've never encountered it on Windows installations on this laptop nor on Mint install I've had here before. What should I try to get rid of this hum?
My laptop is Asus N56V.
Output from aplay -l:
```

root@edison23-N56VM:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Thank you very much for your help.

---

### Post by tgalati4 on 2014-09-30
Have you tried different headphones?  If you only get it with one pair of headphones, then you can reasonably sure that you have a bad headphone cord.  If it happens with multiple headphones, then you might have a bad audio channel--perhaps a solder connection problem with the headphone jack in the laptop.

Open a terminal and run *alsamixer*.  See if you have an "auto-mute-mode" and try turning it off.  Also see if you have any other channels that correspond to the noise by muting and unmuting each channel separately.

---

### Post by edison23 on 2014-09-30
Thank you for your advices.
> **tgalati4 said:**
> Have you tried different headphones? 
Yes, I have tried it with two, both manifest same hum. Moreover, the hum would be OS independent, wouldn't it?

> **tgalati4 said:**
> If it happens with multiple headphones, then you might have a bad audio channel--perhaps a solder connection problem with the headphone jack in the laptop.
Again, this would be OS independent, wouldn't it?

> **tgalati4 said:**
> Open a terminal and run *alsamixer*.  See if you have an "auto-mute-mode" and try turning it off.  Also see if you have any other channels that correspond to the noise by muting and unmuting each channel separately.
In the screenshot appended you can see what I see in alsamixer, if there's anything wrong, I don't see it. I have tried turning off the auto-mute-mode, to no avail. I've also turning volume down in every single output (as in Master, Headphones, Bass, ...), which didn't mute the hum. When I tried muting the channels (as in Headphones and/or Speaker, which usually mutes also Master, btw), it muted the hum (and, of course, every other sound as it probably turns off the sound card completely, if I understand it correctly).

What else should I try? Thank you very much, I'd really like to solve this.

---

### Post by tgalati4 on 2014-09-30
So, muting the input channels does not affect the hum, but muting the output channel turns the hum off.  It sounds like the amplifier chip has an issue.  Try shutting down, pull the battery (and AC cord) and let the computer sit for an hour.  It's possible there is a stray noise connection inside your sound chip.  Windows handles the chip differently so it will behave differently.

Have you played this computer at loud volumes for long periods of time?

---

### Post by edison23 on 2014-09-30
> Try shutting down, pull the battery (and AC cord) and let the computer sit for an hour.
Ok, I will try that later in the night and let you know about the result.

> Have you played this computer at loud volumes for long periods of time?
No, not really, but I do recall that my AC adapter for USB HDD dock was probably letting 230 V (with very small current) through to the USB cable connecting to the computer - I have metal chasis so I found out as I felt the slight tingling from the high voltage (I'm sorry, I'm not really sure about the English terminology here). So that might be the cause... I hope it's not permanent. I wonder, though - in what way does Windows handle the chip differently, if it's explainable in reasonably easy way?

Anyway, thanks again, I'll post later about the results.

---

### Post by tgalati4 on 2014-09-30
Many sound chips have field-programmable gate arrays that allow swapping of the inputs and outputs and complex routing of audio signals.  If one of those arrays gets burned, then you will get leakage of noise into the output channel.  You can work around it if your audio driver allows patching then you can isolate where the noise is coming from.

A more common issue is the sound chip burning out--the operational amplifier (opamp) gets hot and simply burns out--affecting one or both channels.  It's possible for an opamp to fail with just noise, but then you normally can't mute it.

The [ALC663]("http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=37&Level=5&Conn=4&ProdID=165") is a complex chip with a lot of stuff in it.  Read the datasheet.  It's only 82 pages.  

One interesting fact:

> Headphone amplifier on port-I (HP-OUT) is designed to drive output without external DC blocking capacitors 

That's good, it will give you better audio quality, but the downside is it makes the output circuitry more susceptable to electrostatic shock.  The chip is rated to 3500Volts electrostatic charge, but I'm not sure how it is measured.  Most audio circuits can't take more than 30 Volts before breakdown.  So if you really did zap your computer with 230VAC, it's possible that the audio amplifier took a hit.

Perhaps your module has switches that you can play with:

> tgalati4@Mint14-Extensa ~ $ lsmod | grep real
snd_hda_codec_realtek    78193  1 
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
snd                    78921  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tgalati4@Mint14-Extensa ~ $ modinfo snd_hda_codec_realtek
filename:       /lib/modules/3.5.0-51-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
description:    Realtek HD-audio codec
license:        GPL
alias:          snd-hda-codec-id:10ec*
srcversion:     954D86FFF6A0D8739F68AA8
depends:        snd-hda-codec,snd
intree:         Y
vermagic:       3.5.0-51-generic SMP mod_unload modversions 


There are no switches for the ALC268 on my laptop.

---

### Post by edison23 on 2014-10-01
So, I have tried leaving the laptop be without battery and AC power for the night, and it didn't help. 
As for 230 V, I'm not really sure where it went and where it didn't, so there's no way to say for sure.

As for the switches - I don't really know what it means, but this is what lsmod gives me for "real":
```

root@edison23-N56VM:~# lsmod | grep real
snd_hda_codec_realtek    65580  1 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd                    69322  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi

```

Any ideas what could be done more? I can't believe it doesn't have a solution (I'm may be naive, I know).
And once more, thanks for the effort, really appreciated.

---

### Post by tgalati4 on 2014-10-01
You are using a standard, realtek audio module.  So you may not have access to the complex routing available in the Windows driver.  Boot into Windows and open the Realtek audio control panel and write down the settings available.  See if you can move the audio patches around.  Try 5.1 or 6.1 audio and see if you get hum on any of the channels.  Leave the system at stereo when you shut down, then boot into linux and test again.

Install *audacity* and try recording the noise.  If it is an input channel creating the noise, then it should show up during a recording session.  Capture a few seconds of noise, highlight it and then perform a frequency analysis.  See what the dominant frequencies are.  Is it only a 60Hz hum or is it hum with white noise as well?

---

### Post by edison23 on 2014-10-01
Wow, thanks. Ok, I will do that, but again - I can't perform it right now, so I'll write back later - evening (DST CET)/tommorow/Friday

---

### Post by edison23 on 2014-10-02
So, as for the meddling with audio driver in Windows - I haven't found any settings allowing me to use 5.1 or 6.1 audio in Realtek nor the default Windows audio driver (and I don't have any way to try out S/PDIF connector, which is supposedly combined with the normal jack (according to the label on laptop). The only settings are effects and enhancements as in Bass and Room compensation and such (totalling four, none of them seemed relevant). I did, however, noticed the same hum in the same channel in Windows too, although on such low level I've never noticed it before. Dunno if important. Also, the hum on that low level is in the left channel too in Linux... in Windows it's inaudible I guess.

And as for Audacity - I've never worked with it, but I guess I found out some basics about recording, however I'm not sure if I recorded the sound right. I tried it by connecting the output audio jack with the input for microphone by cable (fairly decent one, btw). It's with default settings for input and output device and I tried mute-unmute audio somewhere in the middle, there's audible change there I think.
However, sadly I don't have idea how to actually analyze it so I'm appending it - you sound like a very knowledgeble person, so I'm hoping you might know what to do with it.

Thank you very much for your time.

Btw, I'm starting to think about buying a cheap external sound card... I don't like the idea though.

---

### Post by tgalati4 on 2014-10-03
To get the multichannel output, you need a fiber optic cable (called a TOSLink) plugged into the audio jack and then into a home stereo receiver that has an optical (SPDIF) input.

If you get noise in your stereo system with the digital connection, then you know the noise is upstream in the sound chip.  If the noise is absent, then you are getting noise in the analog output amplifiers.  

The fact that you are getting noise in both Ubuntu and Windows means that you have either a hardware fault, or just crappy audio section.  It could be dust and dirt inside the computer causing some pickup in the sound chip.  Try cleaning it with compressed air.  Blow some air right into the audio jack.

The noise is interesting.  It is linear from 6 Hz to 100 Hz, no 60 Hz peak.

To view the graph, open the track in Audacity, Control-A to select all, Analyze, Plot Spectrum, select 8192 points, and Axis Log Frequency, Replot.  You should see a purple hill that starts at -48 dB at 6 Hz and goes down to -90 dB at 141 Hz, a nice linear slope.  60 Hz noise would show up as a nice, clean spike at 60 Hz--that is not your problem.  So it appears that you are getting low frequency noise from someplace.  Normally, output capacitors on cheaper sound chips would filter that out, but a balanced transister output stage (known as push-pull) without those output capacitors allows the low frequency signals through.  This is good for audio fidelity and is only detected with decent headphones that can produce such low frequencies.  Most earbuds can't so the noise is not noticeable.

By any chance do you have "bass enhancement" turned on?  It could be a simple switch that is turned on by default and you need to find a way to turn it off.  It really looks like someone cranked up the bass--which also amplifies noise in low frequencies.  You don't notice it when you are playing loud music.  It can be annoying when listening to classical music.

The difference in volume levels between Linux and Windows is simply a matter of gain and how the sound chips are set in each driver.

Once you have gone down this rabbit hole, there is no going back.  Laptops are not considered high fidelity, and although realtek chips are good, how they sound depends on quality construction and adequate shielding.  You want a purpose-designed sound section for decent audio:  [http://www.element14.com/community/community/raspberry-pi/raspberry-pi-accessories/wolfson_pi](http://www.element14.com/community/community/raspberry-pi/raspberry-pi-accessories/wolfson_pi)

RaspberryPi's are neat little Linux computers for $40, but they have horrible sound.  So some smart folks designed a decent sound card for it.

Once you start down the path of looking for better audio, there is no going back.

---

### Post by edison23 on 2014-10-05
Crap... I always forget that eventually the thread gets paginated...and then I miss the new replies. Aaanyway...

Thank you for analysis. I will try to clean it, although I'm not sure how accessible the sound card and stuff around are (blowing air into jack didn't help). I'll also look into the bass enhancement (there was such setting in Windows driver, but didn't change anything iirc, not sure, where to look for it in Linux, gotta research on that). As for the S/PDIF, I don't own TOSLink or reciever, so I'll have to wait till I get to my parents' who have it... I'll report back in few weeks/months.

And as I'm looking at it, I'll really have to buy an external sounds card. Oh well.

Anyway, I'm very grateful that you've spent your time helping me, tgalati4.

(Note for mods: I don't consider this thread solved nor would I like it closed since I plan to do further research in this matter... it's just not gonna be now... thanks)

---

