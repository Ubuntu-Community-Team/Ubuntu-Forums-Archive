---
title: "foobar2000 and Wine issue - tracing sample rate of sound card output under Hardy?"
date: 2008-08-12
forum: Multimedia Software
---

### Post by lossfound on 2008-08-12
Hi all - I am a Linux newb and have a problem that I've been searching for, but cannot find discussed elsewhere. I am trying to run the well-known Windows media playback program foobar2000 0.9.5.4 under Wine 1.0 with a 3-week-old fresh install of Hardy (Ubuntu Studio 8.04.1). 

I know that Wine's issues with PulseAudio are well documented, but it *does* seem to work, *mostly*, on my setup-- I have other audio apps running under Wine with no issue from the start. 

The only problem I have with Wine and Pulse right now is that winecfg makes all kinds of horrid noises when I switch to the Audio tab and that the "Test Sound" button doesn't work. If I killall pulseaudio, these problems in winecfg are resolved. But my troublesome issue with fb2k persists even if I killall pulseaudio at the terminal.

Basically, foobar2000 under Wine is playing back files at what is audibly the wrong sample rate if not the wrong sample and bitrate combination. It sounds particularly horrid with quiet material. 

I should note that I also have the Win32 recording software REAPER set up under Wine and it sounds just fine playing back the same MP3s through the default Wine audio setup. Unfortunately, REAPER is a great recording package but a pretty lousy excuse for an MP3 player.

I can find no evidence that fb2k is aware of downsampling its output and I think this is happening somewhere between either fb2k and Wine, or between Wine and the sound hardware.

What should I look at on the Wine and Linux end? Is there any way to look at or verify the sample rate and bitrate of the audio stream that Hardy is attempting to produce? 

Thank you!

---

### Post by NESFreak on 2008-08-31
[http://www.hydrogenaudio.org/forums/index.php?showtopic=54933](http://www.hydrogenaudio.org/forums/index.php?showtopic=54933)
> The beta version of foobar2000 uses Directsound by default, which can cause some problems when playing music. In order to get the program to play music properly, you must set the Hardware Acceleration to emulate Directsound. Go to a terimal and type in "winecfg". A window will open with options for you to modify. Click on the Audio tab, and then look for "Hardware Acceleration". It is currently on "Full". Click on it, and you will have a list of options. Click on "Emulation", and then click on "Apply". foobar2000 should now be able to play music. Note that this will make foobar2000 version 0.8.3 give out an error when you try to play an audio file. Just change it back to "Full" in winecfg when you're done using foobar2000 version 0.9 beta.

search the thread for some more tips/tricks

---

### Post by lossfound on 2008-08-31
Thanks for the reply - I have encountered that particular (older) thread several times in trying to solve the problem. 

fb2k does in fact work with Wine out of box now-- or at least, I should say it sets up and plays with no *functional* issues, just the sound quality concern-- and I had no problems with skipping, which are the two issues mostly cited in that thread. 

I cannot find any seeming mention of aliased or aggressively downsampled audio that applies to my system configuration or hardware.

I strongly suspect this is a PulseAudio-related problem that I was simply not smart enough to solve in several attempts. Ultimately this was perhaps the single major reason why I had to ditch Ubuntu and go back to XP for now-- I need foobar2000, as none of the presently available playback software for Linux is up to par.

---

