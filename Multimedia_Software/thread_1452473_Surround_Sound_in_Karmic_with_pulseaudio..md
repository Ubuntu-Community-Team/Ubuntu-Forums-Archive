---
title: "Surround Sound in Karmic with pulseaudio."
date: 2010-04-12
forum: Multimedia Software
---

### Post by quequotion on 2010-04-12
Perhaps I am beating a dead horse, but I'm trying to get 5.1 Analog Surround out of a SoundBlaster Audigy Live! Value 5.1 using pulseaudio in Karmic.

My cabling and speakers are good. Everything has been independently tested. However, only the physical front-left, front-right, and center speakers actually produce sound from the PC. Most likely it is a problem of configuration.

I've tried the obvious way, by selecting "Analog 5.1 Surround" from the list of profiles. That gave me a list of all the correct channels in pavucontrol for the device, but makes no difference in pulseaudio's output.

Pulseaudio has a list of channels specified for its "combined" module that does not make much sense... (front-left,front-left-of-center,front-center,front-right-of-center,front-right,rear-center) It seems only these channels are actually available, even if I do not use the "combined" module.

I also modified /etc/pulse/daemon.conf to have 6 channels. (below that option was a place to specify speaker mapping, but my choices were ignored)

I also added a ~/asoundrc with a ttable configuration to distribute 2-channel stereo across 5.1 channel surround... (is this just theoretical?)

I've checked all the controls in alsamixer and made sure all relevant controls are set appropriately, but I noticed that there are no controls for front-left/right or rear-left/right, only center, lfe, and surround.

I've run "speaker-test -c 6" and to test each sound channel, but some really odd stuff is happening. I've attached the following screenshots from pavumeter (sorry for my poor gimp skills):

When speaker-test tests "center" it comes out of pulseaudio as "front-center and rear-center" and plays throught the front-center speaker.

When speaker-test tests "front-left" it comes out as of pulseaudio as "mostly front-left and a little front-left-of-center" and plays through the front-left speaker.

When speaker-test tests "front-right" it comes ouf of pulseaudio as "mostly front-right and a little front-right-of-center" and plays throught the front-right speaker.

When speaker-test tests "lfe" it comes out of pulseaudio as "a little on all channels" *and does not come out of the actual subwoofer*, but plays faintly through the front-left, front-center, and front-right speakers.

when speaker-test tests "rear-left" it comes out of pulseaudio as "a little front-left-of-center" *and does not output from the rear-left speaker*, but faintly outputs from the front-left speaker.

when speaker-test tests "rear-right" it comes out of pulseaudio as "a little front-right-of-center" *and does not output from the rear-right speaker*, but faintly outputs from the front-right speaker.

Before anyone suggests it: No I will not purge pulseaudio from my system. I *like* pulseaudio.

---

### Post by quequotion on 2010-04-12
::UPDATE::

If I disable the creation of simultaneous output ("combined"), pavumeter will show the correct audio channels and displays the audio being sent to the correct channels. I can hear very faint audio coming from the rear left and right speakers, but still nothing at all from the subwoofer.

I'd rather not give up "combined" (I use it to play audio from the internal soundcard and a usb-audio stereo simultaneously).

---

### Post by quequotion on 2010-04-12
::UPDATE::

I've checked them over and over, but I can't make up my mind about two of the controls in alsamixer, "Sigmatel Output Bias" and "Sigmatel Surround [gain]".

Neither control seems to affect the surround sound in any useful way. Whether "Sigmatel Output Bias" is on or off, I still get audio from front-left, font-center, and front-right and just the slightest noise from rear-left and rear-right with no sound at all from the sub-woofer.

If I enable "Sigmatel Surround [gain]" and turn it up a bit, the channels start to blend (front-left, front-center, and front-right gradually blend together and lfe immediately comes out of all channels).

For now I'm leavign "Sigmatel Output Bias" on, as I have the impression this enables/disables surround sound mode and muting "Sigmatel Surround [gain]"

---

### Post by quequotion on 2010-04-12
::update::

After a reboot, with Simultaneous Output disabled in pulseaudio; Sigmatel Output Bias and Sigmatel Surrond [gain] muted in alsamixer, I now have all speakers producing sound independently.

Unfortunately the rear-left, rear-right, and subwoofer are so quiet as to I need to put my ear against the speaker to notice that sound is in fact coming out. while doing speaker test, pavumeter shows a more or less equal level of sound going to each channel, but the sound is definitely output much louder on the front-left, front-right, and front-center channels.

I've tried inverting all the connections to make sure they work (front to rear/sub to center and vice versa) and all it seems somewhere between pulseaudio and the actual sound card the volume of the rear channels and the lfe are being cut very low.

Also, there is a bug in the way Pulseaudio handles alsa device volume control. Pulseaudio is capable of forcing a card to exceed 100% output, and whenever I adjust a setting (any setting) using pulseaudio, it does so automatically. This causes a sharp metallic ring across all channels (due to the low quality of my sound card I think) which can be stopped by turning the volume down a notch with alsamixer. I tried to correct this with pulseaudio-equalizer, but it only makes things worse.

I'm all out of ideas.

Help!

---

### Post by quequotion on 2010-04-12
::update::

"speaker-test -c 6" Doesn't test a real set of 5.1 channels. I've seen some guides that say to add "-D plug:surround51" and "-t wav" to test properly, but just those options will result in a failed test. There's some .asoundrc hacking needed to make those options do something other than break speaker-test.... and now I can't find the site where I saw it before...

I took a look through my video collection and found that Ghost In the Shell - Stand Alone Complex is encoded with MPEG4 AAC 5.1 Surround.  It looks to be working well for the moment, but I still have some issues....

1. The SDL problems Karmic shipped with are now back in full force and pretty much all games are unplayable again due to offensive noise.

2. After going through a few threads on this forum about the LFE, I am not entirely confident that this will continue to work.

3. I've found that any volume or balance adjustment made by pulseaudio, up or down; left or right; front or rear, to any channel, results in high-pitched metallic ring across all channels until the volume is adjusted again by alsamixer (even a very minor adjustment usually solves the problem). This ring is also audible at login. I still don't want to lose pulseaudio, but this is annoying.

---

### Post by quequotion on 2010-04-13
Ever since disabling "combined" and setting up surround SDL applications, like zsnes, are worse than ever before. Some have quit producing sound altogether and don't show up in pavucontol at all. It's possible they are attempting to use the ALSA driver directly and failing, but I don't know how or, especially, why.

I'm still working on my ~/.asoundrc, but I can't seem to get any kind of functional stereo-to-surround upmix and besides I hate alsa. Is there a pulseaudio means of doing this?

Only surround sound encoded audio makes use of the subwoofer and even then I don't much like the balance. There are some .asoundrc hacks to make a lowpass filter, but I am loosing faith in such fairytales and once again, *I'd much rather be doing this with pulseaudio*.

Would anyone like to join my little party here? Or should I continue talking to my self and poking around in the dark until I blow something up or get put into the looney bin? (Love it as I do, Ubuntu is slowly driving me mad...)

---

### Post by lidex on 2010-04-13
> Would anyone like to join my little party here? Or should I continue talking to my self and poking around in the dark until I blow something up or get put into the looney bin? (Love it as I do, Ubuntu is slowly driving me mad...)
Why? You seem to be doing so well - off playing all alone... :wink:
Have you tried installing
```
libsdl1.2debian-pulseaudio
```
for the game issues?

For surround, maybe you saw this:
[http://ubuntuforums.org/showthread.php?t=795525]("http://ubuntuforums.org/showthread.php?t=795525")

---

### Post by quequotion on 2010-04-16
> **lidex said:**
> Why? You seem to be doing so well - off playing all alone... :wink:

LOL it's my childhood all over again

> Have you tried installing
```
libsdl1.2debian-pulseaudio
```
for the game issues?

yes, and combined that with always having pavucontrol open when using SDL apps, which seemed to fix the problem more or less, but now my audio set up is quite different and it seems some apps just gave up...

> For surround, maybe you saw this:
[http://ubuntuforums.org/showthread.php?t=795525]("http://ubuntuforums.org/showthread.php?t=795525")

Indeed I have. Tried most of it. I've also been through the official wikis for alsa, pulseaudio, and ubuntu regarding surround sound in addition to a dozen or so threads scattered around the Internet. The ALSA wiki has the most concrete information, including guides to make a lowpass filter and upmix, but I'm not sure it works with pulseaudio and I'd rather be doing that through pulseaudio itself.

---

### Post by quequotion on 2010-05-12
::Final Update::

I apologize for reviving an old thread, but this needs to be said.

I am preparing to upgrade to Lucid in hopes that it will solve my problems. (I really don't think so as my packages are already at or above the Lucid versions since I've pumped karmic so full of PPA's it's growing hair on it's back and experiencing erectile dysfunction)

The final results in Karmic were this:

1. The recommendations I found in the offcia wikis for ALSA and PulseAudio for making/modifying ~/.asoundrc broke sound support for all SDL programs and in no case resulted in "surround" audio. I deleted ~/.asoundrc and audio functions "normally" once again.

2. The best I can get with Karmic is 5.? surround. Note that "?". The center, front left and front right channels are marvelous. The rear left and right make some audible noises on occasion. The subwoofer (LFE) however, makes only the most inaudible clicks now and then. On occasion, by switching pulseaudio to Stereo output and then back to Surround 5.1 output, I am able to get LFE support at a reasonable volume but it goes away after a while...

3. Pulseaudio, and hence media keys, will cause a metallic ringing when used to set the volume, but there is a fix/workaround. Make sure that your volume control is adjusting PCM and not Main (device) volume. I can't seem to find the forum post that was in.. which is very unfortunate because it was not a straightforward thing to do and required editing a text file somewhere... wish I could remember where...

Onward! to Lucid!

---

### Post by diegorodriguezv on 2010-06-11
Hi.

I've also tried to have 5.1 sound in my vostro 1400 to no avail. I tried in Hardy, Jaunty, Karmic and Lucid but haven't got lucky yet, although Lucid got 4.0 out of the box.


quequotion:
How was your experience with lucid?

---

### Post by lidex on 2010-06-12
#3
[http://www.uluga.ubuntuforums.org/showpost.php?p=9438177&postcount=8]("http://www.uluga.ubuntuforums.org/showpost.php?p=9438177&postcount=8")

---

### Post by JD82 on 2010-11-10
> **quequotion said:**
> ::update::
3. **I've found that any volume or balance adjustment made by pulseaudio**, up or down; left or right; front or rear, to any channel, **results in high-pitched metallic ring across all channels until the volume is adjusted again by alsamixer** (even a very minor adjustment usually solves the problem). This ring is also audible at login. I still don't want to lose pulseaudio, but this is annoying.

> **quequotion said:**
> ::Final Update::

3. **Pulseaudio, and hence media keys, will cause a metallic ringing when used to set the volume**, but there is a fix/workaround. Make sure that your volume control is adjusting PCM and not Main (device) volume. I can't seem to find the forum post that was in.. which is very unfortunate because it was not a straightforward thing to do and required editing a text file somewhere... wish I could remember where...
Onward! to Lucid!

I have the very same problem in Ubuntu 10.10 on my Gigabyte X58A-UD7 (Realtek ALC889) :(

I tried with _[this]("http://ubuntuforums.org/showpost.php?p=8243843&postcount=2")_ but the result is that no sound card is recognized by Pulseaudio.

My [_alsa-info_]("http://www.alsa-project.org/db/?f=613d56a1dc14dafa952d2f7b4c099945f97ad27e").

Any suggestions?

---

