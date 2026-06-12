---
title: "Hair tear: SPDIF distorts but analog does not"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by Lotharsson on 2007-04-29
Hi all,

I hope someone has some insight here - this problem has me tearing my hair out - or it would if my head were not shaved already!  Any help you can give would be appreciated.

I've got an Ubuntu Feisty/MythTV box set up on an Asus P5B Deluxe motherboard.  It's using the on-board Intel HDA audio device which uses an Analog Devices 1988B codec.  I've connected both analog and SPDIF outputs to my AV receiver and some hi-fi speakers.  I have FLAC rips of all my CDs on the hard drive.

I want to be able to play (ideally bit-perfect) stereo music over SPDIF using my receiver and speakers.  I also want to be able to play MythTV recordings over the same digital output to the receiver/speakers.

**The good news **:) 
I have SPDIF output going through my amplifier and it's producing sound (e.g. via Amarok using Xine as the engine to ALSA device spdif).  Even better - the output automatically switches rates between 44.1kHz and 48kHz depending on the sources.  I also have sound going over the analog output device into the amplifier if I configure that option.

**The bad news** :( 
is that analog output seems to be clean (and sounds pretty good with a decent amp and speakers) - but SPDIF output of the same source has a bit of distortion, most noticable in female vocals and the mid-upper registers of the piano or in violins (especially if you put your ear a little closer to the tweeter and focus on it).  You might not hear it at first, but once you do it's hard to ignore in the future.  It's definitely there and sticks out as something ugly.  I'm mystified why it only occurs with SPDIF (which should in theory be cleaner than analog output.  It could be a problem with the amplifier, although that would be a little unusual.  I don't have an easy way to test that hypothesis yet.)

I had the same distortion problem on Edgy before I upgraded going, although back then I think I had sound output to the default device which produced both analog and SPDIF output at the same time, at the sampling rate of the data source.  I suspect the codec was sampling the analog output in order to create the SPDIF output data stream.  (And before I tweaked things it was resampling to a different rate which was also distorting quite noticably, but even after I fixed that this type of distortion remains.)  Feisty doesn't seem to do combined digital/analog output by default.

I'm using module snd-hda-intel.  I don't have an asound.conf or a .asoundrc.  I get the distortion on SPDIF if I talk directly to ALSA:hw0,1 (my digital device) and pretty good analog sound if I talk directly to ALSA:hw0,0 (my analog device).

**Other bad news**
There are also odd issues with TV playback over SPDIF - the amp appears to re-detect Dolby Digital every couple of seconds and never gets around to outputting the audio stream.  I can play an AC3 stream from a DVD via MythTV with no problems though.

**Questions**
[LIST=1]
[*]Has anyone seen these issues before?  Any idea what would cause this?
[*]Are there any ideas for troubleshooting this?
[*]Failing that, would it be quicker to just go out and buy a reasonably priced card that does reliable SPDIF output at different sampling rates?  If so, what cards are recommended?[/LIST]

Thanks,
   Lotharsson

---

