---
title: "Bad sound? Try this..."
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by psyke83 on 2007-06-16
Hi,

I have a Dell Inspiron 510m laptop with an Intel 82801DB-ICH4 (STAC9750/51 / AC'97) sound chipset. Under Windows, sound reproduction is pretty good considering that it's coming from a pair of laptop speakers - clear with good bass. Under linux (Ubuntu, Fedora and others), however, something is wrong...

When the volume is beyond around 50%, the sound seems distorted, particularly with bass sounds; it seems as though the speakers are damaged/loose, with a rattling sound at the higher frequencies, and overall sound seems "muffled". Upon experimenting with VLC's equalizers, I managed to tweak sound until it sounded almost perfect, just like XP's sound reproduction. Unfortunately, this only solved audio playback in VLC, so after some research and experimentation, I found out how to equalize sounds system-wide, using ALSA with a LADSPA (audio processing) plugin.

If anybody is suffering a similar issue, here's the solution:

1. Install the "C* Audio Plugin Suite" (caps), which contains the required ladspa plugin (requires the universe repository):
```
$ sudo apt-get install caps
```2. Create a new .asoundrc file:```
gedit ~/.asoundrc
```
Insert the following text into the new file:```
   pcm.!default {
       type plug
       slave.pcm "equalized";
   }

   pcm.equalized {
       type ladspa
       slave.pcm "[COLOR="Red"]plug:dmix[/COLOR]";
       path "/usr/lib/ladspa";
       plugins [
           {
               id 1773
               input {
                   controls [ 8 5 3 -5 -6 -10 -6 -5 8 8 ]
               }
           }
       ]
   }
```NOTE: Regarding the part highlighted red. There's a bug in ALSA causing crackles if the sound volume on any mixer is above 75%, causing disturbing pops. To work around this problem you can either keep the volume mixers below 75% or disable mixing which eliminates the popping, but allows only one application to play sound at a time. To disable mixing, change the part in red to: ```
plughw:0,0
```

Save the file, and try playing an audio or movie file with a high volume (but make sure that you restart any apps that may be using the sound card).

Can I ask that anybody who notices a difference (positive, negative or indifferent) report back? This fixes audio for me under Feisty, but may work for earlier releases.

---

### Post by nSTER on 2007-06-16
This is great, I think it is working but for some reason in VLC while the audio is playing it would randomly start crackling, everything would stop playing in terms of the actual audio and will start to crackle for about 10 seconds then resumes again with the audio. This does not happen in any other media player. And this also only happens with my laptop speakers not my usb headsets. ATI IXP is my laptop audio driver. Great tip though thanks!

---

### Post by psyke83 on 2007-06-16
nSTER,

That's a different issue (that I experienced in the past as well) :). VLC's ALSA output plugin is buggy, try changing it to OSS in the preferences (you may need to enable advanced options to find it). That eliminated the crackling sound on my systems with VLC (which isn't the same as the the issue I posted in this thread initially).

---

### Post by Morbett on 2007-06-23
Wow, the sound on my Dell Inspiron 1300 laptop sounds much better now.

---

### Post by Wiseman1024 on 2007-06-23
I admire the work, though this is just running circles around the issue which must be in something gone horribly wrong in the sound drivers. You're basically getting bad quality sound, and fixing it artificially, introducing even more noise and distortion, even if it gives the impression of higher quality. The sound you're getting is not so close to how it should sound as it seems, I'm afraid.

---

### Post by psyke83 on 2007-06-23
> **Wiseman1024 said:**
> I admire the work, though this is just running circles around the issue which must be in something gone horribly wrong in the sound drivers. You're basically getting bad quality sound, and fixing it artificially, introducing even more noise and distortion, even if it gives the impression of higher quality. The sound you're getting is not so close to how it should sound as it seems, I'm afraid.

I understand what you mean. I've reported the issue to the ALSA bug tracker with no response as of yet, and I discussed it with some ALSA developers on IRC regarding this issue several times.

Under XP, I've made a discovery of sorts: Windows XP's generic "Intel AC'97 Audio" driver has the same bad quality as ALSA, whilst the "Sigmatel C-Major Audio" drivers (from Dell's site) has excellent quality.The impression I have been given by the ALSA developers is that the Sigmatel drivers equalize the audio, perhaps because the laptop's speakers can't exploit the full frequency range of the audio chipset.

Either way, this is the only way to somewhat fix the poor audio quality on my laptop at the moment.

---

### Post by Morbett on 2007-06-24
Hmm, yeah, I sort of discovered that's an artificial fix today.  In Exaile I put on an album that is very recent (great production and high levels) and the louder parts of songs were distorting.  

So now I reverted back to the way my speakers were before I followed these instructions.  Unfortunate the drivers/ALSA don't work properly!

---

### Post by psyke83 on 2007-06-24
Morbett,

You need to keep the PCM volume below 74% to avoid distortions. That's a bug with ALSA's ladspa plugin system. Using the same caps ladspa filter in Audacious with it's ladspa plugin system, there's no distortion at higher volumes. However, keeping the PCM/Master below 74 almost always avoids distortion.

This isn't a perfect fix by any means, but the ALSA developers aren't responding to my bug report...

---

### Post by Morbett on 2007-06-24
Ah, ok, thank you for the tip!  I had it above 74%.

---

### Post by CompactDestruction on 2007-06-24
I have a laptop too and also think this issue is simply from being able to turn up the volume much higher than in Windows, thereby causing distortion to occur on those tinny laptop speakers.

I notice on your equalizer controls that your settings are to reduce the volume of mid-frequencies, which would help by lowering the volume and allowing less audible portions of audio to come through better.

---

### Post by psyke83 on 2007-06-25
CompactDestruction,

Good theory, but not quite correct re: volume. On Windows, the Sigmatel drivers produce louder audio than ALSA without distortion - turning everything up in ALSA doesn't come close, and yet on Windows there's still no distortion at the loudest volume level.

When the volume is limited to below 70%, audio still suffers, e.g. ppracer sounds identical when the audio is set to 22050Hz as to when it's 44100hz, yet in XP (using the Windows port), the difference is clearly distinguishable.

Try playing the GTA IV trailer on Windows - there's excellent bass and the car's engines are clearly heard, but in Ubuntu the bass is muffled and the car engines almost inaudible. Something's wrong with the ALSA drivers, but equalizing certain frequency bands counteracts the effect somewhat.

---

### Post by fragility14 on 2007-07-07
I'm having horrible sound problems with the same card, it sounds really poor  at higher levels, but it also starts messing up really badly if other system resources are being used, even if not that many...

---

### Post by zelsuk on 2007-07-19
this works..

i'm using hp pavilion laptop and i have better sound quality.. (feisty)

thank you

---

### Post by psyke83 on 2007-07-23
> **Wiseman1024 said:**
> I admire the work, though this is just running circles around the issue which must be in something gone horribly wrong in the sound drivers. You're basically getting bad quality sound, and fixing it artificially, introducing even more noise and distortion, even if it gives the impression of higher quality. The sound you're getting is not so close to how it should sound as it seems, I'm afraid.

I can now say definitively that you're incorrect. In a nutshell:

1. Windows XP's built-in "Intel AC97 Audio" driver sounds identical to ALSA (bad);
2. Sigmatel's Windows XP drivers sound good, and;
3. Sigmatel's Windows XP drivers use a 10 band software equalizer.

With regard to point three; after hacking with the Sigmatel drivers in the Windows registry I discovered calibration data for a 10-band equalizer, and even found a hidden option to enable the equalizer settings in the Sigmatel Control Panel applet. However, the calibration data is reset after each system restart, possibly because the settings are read from the laptop's BIOS (an ALSA developer helped discover that).

The only problem with the .asoundrc file posted is that it doesn't match the "official" calibration data. I am dissatisfied with the available LADSPA EQ plugins, but VLC has an excellent built-in equalizer that can give excellent quality audio on my laptop.

---

### Post by windrider001 on 2007-07-25
I have an Intel 865 motherboard and AC97 audio and it does sound bad in Feisty Fawn. So is there a solution to this?

---

### Post by psyke83 on 2007-08-07
> **windrider001 said:**
> I have an Intel 865 motherboard and AC97 audio and it does sound bad in Feisty Fawn. So is there a solution to this?

It depends; what I found out for my particular laptop is that XP's driver perform software equalization, and the settings seem to be embedded in the BIOS. You can try the solution in this thread for a start, and experiment with the settings to see if it helps.

---

### Post by theyain on 2007-08-07
I was having a little pit of a problem with my sound, but there is nothing wrong with it now!  Wow, thank you so much for posting this!

---

### Post by jusmurph on 2007-08-12
Is that piece meant to append on the end of ~/.asoundrc or replace it?

Because i appended and it did nothing for me.

---

### Post by psyke83 on 2007-08-13
> **jusmurph said:**
> Is that piece meant to append on the end of ~/.asoundrc or replace it?

Because i appended and it did nothing for me.

No, it needs to be replaced. My suggestion is:

1. Backup your current .asoundrc file
2a. Delete your .asoundrc file and play some media with VLC. Activate the audio equalizer and experiment with the bands, and see if it fixes your sound distortion/crackling.
2b. Use the .asoundrc file provided in this thread if step 2a worked for you.

Look at this part:
```
 controls [ 8 5 3 -5 -6 -10 -6 -5 8 8 ]
```

You have ten possible values, each one equalizing a particular band's gain - if you experiment with these numbers it can make a difference. I updated the values in the original post, so you may want to edit it again, but let me emphasize: these values work for **my laptop's speakers** - it may sound worse for you.

---

### Post by PARO on 2007-08-15
I messed around with the equalizer in vlc and the distortion and cracking stopped, but it completely changed the sound too, and I was about to give up and I set it back to the defaults and just lowered the preamp to under 6 (default is 12) and it fixed it.  I've played quite a few normally crackly songs this way now and all is good. My computer speakers are the best speakers I have, so it's nice to finally have them sounding properly.

I tried your CAPS fix for global sound, and that didn't work for me though, still plenty of cracks.  Anyway I can configure one of those plugins to limit db gain only, like in vlc? I went to their site and couldn't find anything on configuring anything really, and tried a little googling and even things like caps --help, man CAPS, and a few other guesses, but nothing. It's great to finally have good sound in vlc, but it would be nice to get other programs sounding like that now too.

---

### Post by AlanD on 2007-08-16
Using the .asoundrc file made every drum beat a deafening crackle, but installing caps without that made my sound a lot better. Using Feisty on an Asus A8V deluxe mobo. Thanks!

---

### Post by MillDaKill on 2007-08-21
Thanks, this really helped.  Still getting some little cracks and pops but the bass is way better.

---

### Post by psyke83 on 2007-08-21
> **AlanD said:**
> Using the .asoundrc file made every drum beat a deafening crackle, but installing caps without that made my sound a lot better. Using Feisty on an Asus A8V deluxe mobo. Thanks!

I'm glad your sound is better now, but let me make something clear:

Installing the caps package without using an .asoundrc file will make absolutely no difference to your sound quality. Either you're experiencing a placebo effect or perhaps you do have the .asoundrc file present in your home directory.

The equalization settings have been tweaked by myself for my laptop's speakers, and those speakers alone - it certainly could make things worse for others. It's simply a matter of try-and-see for yourself ;).

---

### Post by psyke83 on 2007-08-21
> **MillDaKill said:**
> Thanks, this really helped.  Still getting some little cracks and pops but the bass is way better.

I updated the original post, take a look again. Specifically, check your mixer settings and see if any mixer is above 75%, as it can cause cracks/pops (it's a bug in ALSA) - or else your speakers need different equalization settings, perhaps.

---

### Post by psyke83 on 2007-08-21
> **PARO said:**
> I messed around with the equalizer in vlc and the distortion and cracking stopped, but it completely changed the sound too, and I was about to give up and I set it back to the defaults and just lowered the preamp to under 6 (default is 12) and it fixed it.  I've played quite a few normally crackly songs this way now and all is good. My computer speakers are the best speakers I have, so it's nice to finally have them sounding properly.

I tried your CAPS fix for global sound, and that didn't work for me though, still plenty of cracks.  Anyway I can configure one of those plugins to limit db gain only, like in vlc? I went to their site and couldn't find anything on configuring anything really, and tried a little googling and even things like caps --help, man CAPS, and a few other guesses, but nothing. It's great to finally have good sound in vlc, but it would be nice to get other programs sounding like that now too.

There are a lot of LADSPA plugins around, one of which may be able to reduce the gain. To find them, try "apt-cache search ladspa", install any relevant packages and then install a ladspa-aware program, e.g. audacious and audacious-plugins-*, then you can directly manipulate and experiment with all the ladspa plugins in realtime.

HOWEVER, I have to warn you that there's a crackling audio bug in VLC's ALSA driver, and it sounds like this is the problem in your case. Try this: open VLC, go to Settings, Preferences, Audio, Output modules, check "Advanced options" and change the "Audio output module" to OSS, then save. See if there's any popping after that.

---

### Post by PARO on 2007-08-24
> HOWEVER, I have to warn you that there's a crackling audio bug in VLC's ALSA driver, and it sounds like this is the problem in your case. Try this: open VLC, go to Settings, Preferences, Audio, Output modules, check "Advanced options" and change the "Audio output module" to OSS, then save. See if there's any popping after that.

Ah! Thanks! It probably was just the ALSA issue then, changing it to OSS made VLC sound much better (almost as good as changing the gain... but maybe that's just my imagination becasue they sounded a lot alike), but more importantly that fixed my problem with my other audio programs! Changing each program's settings to use OSS made a world of difference. I had no idea they were using ALSA, maybe something I installed changed my default setting to ALSA or something? One was set to "Use Gconf settings" it said, so maybe that's where the culprit lays. Anyway, Thanks!

---

### Post by GrouchoMarx on 2007-08-27
psyke83:

Do you have any idea why equalizing the signal results in better sound quality? Are you simply preventing clipping / distortion? Or is there something more complex going on. Because even if you eliminate clipping using LADSPA, that still doesn't seem to account for the fact that the overall sound is much louder in windows with sigmatel's software equalization, does it?

---

### Post by psyke83 on 2007-08-27
GrouchoMarx,

Well, I can only speak about my laptop (Dell Inspiron 510m), other systems may be different.

In XP, Windows has built-in "Intel AC'97 Audio" drivers - they sound precisely the same as ALSA/OSS's output in linux. On Dell's site you can download Sigmatel drivers, which sound very good. Only after poking around in the registry did I find the 10-band equalizer as part of the drivers (otherwise there's no indication in the control panel or elsewhere). Modifying those registry entries and rebooting never took effect; they always regenerated - leading to my suspicion that the BIOS stores equalizer settings, or else it's hardcoded into the Sigmatel drivers.

As to your question about the loudness of the volume, it's feasible that the drivers also increase the master gain via software, which my "solution" doesn't do, hence the lower volume.

---

