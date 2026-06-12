---
title: "NEED better audio quality"
date: 2008-04-25
forum: Multimedia Software
---

### Post by ztheory on 2008-04-25
Hi all,

I've been using Ubuntu and Linux for a while, but have never been able to make a %100 dedicated switch (not counting games)... simply because I'm an audiophile, and the sound in linux is... poor compared to a windows.

I need to figure out a way to get a superior sound quality out of ubuntu. There just has to be something I'm missing. Audiophiles can't have been left out for this long. 

What do I need to do?

External Sound card? Which one? External sound blaster live?

Optical to external amp?

Some multimedia player that has DSP? Or you can override the kHz settings?

I even went as far as to try to dedicated a PCI sound blaster to play through a Windows XP VM through virtual box... but quickly found out that's most likely a dead end.

Please... calling all audiophiles... WHAT DO YOU DO!?

---

### Post by warbread on 2008-04-25
I couldn't get the optical out on my nForce2 to work, but I know some other people could.  I'm in a slightly different boat since I do music recording, so I don't go for any more than 2 channels.  I used an M-Audio audiophile 24/96, and I get clear, quality recordings.  

Your needs are going to depend on what you have.  What is it that you used in Windows that doesn't work right in Linux?

---

### Post by studo77 on 2008-04-25
M-audio. I will be checking into that. My system is getting upgrades the next months. (M-audio is only for recording/creating sound [http://www.m-audio.com/index.php?do=products.family](http://www.m-audio.com/index.php?do=products.family))

For now i am on Audigy 2 SE and Logitech 5500s. I have a Denon cd player (dcd-f102) connected to them and if i play the same file on Ubuntu or the Denon, then Denon wins all the time. And as i will be upgrading, and eventually get a _very_ silent pc for multimedia, good audio quality is needed.

So i take a guess on the thread owners question. It is best audio quality output for Ubuntu. Stereo or Surround, that is what you tell us? 

Hoping for other audiophiles to share their experience! :-P

Forgot: What about Audiotrak cards? They get great reviews, but how do they work in Linux/Ubuntu?

---

### Post by eye208 on 2008-04-25
> **ztheory said:**
> simply because I'm an audiophile, and the sound in linux is... poor compared to a windows.
If you prefer bass/treble boost, dynamics compression (aka. loudness) and spatial effects over bit-accurate reproduction, then you are not an audiophile.

---

### Post by studo77 on 2008-04-25
No need to define audiophiles here.

Just a way to get better audio quality output of the Ubuntu pc is needed. We are more dependent on the drivers being incoorperated good in the kernel/alsa/outputsystem so the question is not on what an audiphile is, but how to get the best audio out.

From the pc and out, the best solution will be amplifier and real speakers. Although these could do it for you, but then you limit yourself in connection possibilities:
[http://audioengineusa.com/index.htm](http://audioengineusa.com/index.htm)

After a fast look around with google i have my eyes set on Audiotrak Prodigy HD2 when we get the 2.6.25 kernel:
[http://news.softpedia.com/news/Linux-kernel-2-6-25-Released-83599.shtml](http://news.softpedia.com/news/Linux-kernel-2-6-25-Released-83599.shtml)
[http://www.audiotrak.net/](http://www.audiotrak.net/)
Testing sound is hard. You cannot just switch one audio to the next to hear the difference. It is a install/setup-reboot-listen-cycle.


On the optical/analog choise. It depends on the soundcard. It differs a lot on what the different outputs sound like. It is not a given that the optical is best. Digital in sound is not possible all the way. You do not end up with an 01100010011001010110010101110000 in the speakers.

and do not turn up the sound card on more than 70-80% the rest should be done externally. If i crank up my Audigy (alsamixer) to 100% the sound gets real bad.

---

### Post by studo77 on 2008-04-25
In a newsgroup this was linked the other day:
[http://mp3ornot.com/](http://mp3ornot.com/)

If you are the least audiophile you will finde the differences when playing these. And please, change settings on sound card and speakers. Let them work at mediocre levels. aka pretty high, but not maxed.

If you hear no difference then your system or ears does not pick up the difference. If you hear the difference, burn a cd with an uncompressed song, and burnt versions of different compressions. Then go to your audioshop and play the cd. If you can hear no difference from your home system, then you are all fine. If the sound is better at the shop, invest. If you hear difference on the compressed/uncompressed, try different setups, and decide what compression, if any, you want on your music collection.

---

### Post by ztheory on 2008-04-25
Hi everyone,

Thanks for some responses. Although I have to say... I didn't realize I would be put on trial for a simple statement.

> **eye208 said:**
> If you prefer bass/treble boost, dynamics compression (aka. loudness) and spatial effects over bit-accurate reproduction, then you are not an audiophile.

I fail to see where I mentioned to ran into WMP and toyed with the shitty equalizer like a 13 year old with an IPOD...

Through Foobar I was able to maximize the sampling rate, bypass the systems drivers, and many other things. I can tell you flat out that foobar with the secret rabbit plugin, even without any internal or external equalizer completely tears up linux sound.

Speaking with a friend last night I was actually able to increase the sound quality quite a bit by switching to Audacious. I switched from ALSA to OSS and i could instantly tell it was better. While this was a big step up... I'm still looking for anything I can for the best solution.

I rip all my (200+) albums in level-8 FLAC with EAC, so I can definitely hear the difference, even when only taking about a minuscule difference such as V2 to V0. 

Also, I stumbled across "Ubuntu Studio"... if anyone uses that, or ubuntu in general for recording... how's it compare to Acid or Pro tools? I must say I'm skeptical.

---

### Post by ztheory on 2008-04-25
Hi everyone,

Just thought I'd update this thread. I downloaded the audacious-plugins through synaptic package manager, and switch the output plugin to ESD output plugin. Wow! What a difference! This enhanced my sound quality 10 fold. I am at work right now using a Dell Optiplex 745 with onboard sound and it sound amazing. Can't wait to go home and configure this with my onboard HD card.

---

### Post by eye208 on 2008-04-25
> **ztheory said:**
> I can tell you flat out that foobar with the secret rabbit plugin, even without any internal or external equalizer completely tears up linux sound.
No, it doesn't.

In Linux you can easily choose Secret Rabbit in SRC_SINC_BEST_QUALITY mode as your system-wide sample rate converter by adding a single line to either /etc/asound.conf or ~/.asoundrc (requires libasound2-plugins and libsamplerate0 to be installed):
```
defaults.pcm.rate_converter "samplerate_best"
```
Now show me how to do that in Windows.

---

### Post by _K3nt_ on 2008-04-26
> **ztheory said:**
> Hi everyone,

Just thought I'd update this thread. I downloaded the audacious-plugins through synaptic package manager, and switch the output plugin to ESD output plugin. Wow! What a difference! This enhanced my sound quality 10 fold. I am at work right now using a Dell Optiplex 745 with onboard sound and it sound amazing. Can't wait to go home and configure this with my onboard HD card.

Well,i think so with you.Audio quality in Ubuntu is too bad (window comparison),i'll try to do as your idea.Hope it better !

---

### Post by nirudha on 2008-04-26
> **ztheory said:**
> I rip all my (200+) albums in level-8 FLAC with EAC, so I can definitely hear the difference, even when only taking about a minuscule difference such as V2 to V0. 


What is V2 and V0? Isn't V the option to run a parallel encode to verify any bugs in encoding?

---

### Post by eye208 on 2008-04-26
> **_K3nt_ said:**
> Well,i think so with you.Audio quality in Ubuntu is too bad (window comparison),i'll try to do as your idea.Hope it better !
The problem with his idea is that ESD is going away soon, and most applications are not using it anyway.

Just in case you missed it, I described [here](http://ubuntuforums.org/showpost.php?p=4793993&postcount=9) how to replace ALSA's default sample rate converter with libsamplerate, also known as Secret Rabbit Code. Since ALSA is the core of the Linux sound system, this will give you *perfect* sound quality with all applications.

Frankly, calling Windows' sound system superior is the most ridiculous claim I've heard in a long time. You guys really have no clue. I'd suggest you look up some articles about ASIO and find out why it had to be invented in the first place and why even Vista's new WaveRT is no match. In Linux there is no need for ASIO because ALSA is like a system-wide version of ASIO on steroids. In terms of quality it may well be the best sound system ever implemented in a desktop operating system. Its flexibility may be too much of a challenge for simple-minded individuals, but hey, there's nothing you can't learn. :roll:

---

### Post by warbread on 2008-04-26
> **eye208 said:**
>  Its flexibility may be too much of a challenge for simple-minded individuals, but hey, there's nothing you can't learn. :roll:

Truly, we all stand in the shadow of greatness.

---

### Post by _K3nt_ on 2008-04-26
> **eye208 said:**
> The problem with his idea is that ESD is going away soon, and most applications are not using it anyway.

Just in case you missed it, I described [here](http://ubuntuforums.org/showpost.php?p=4793993&postcount=9) how to replace ALSA's default sample rate converter with libsamplerate, also known as Secret Rabbit Code. Since ALSA is the core of the Linux sound system, this will give you *perfect* sound quality with all applications.

Frankly, calling Windows' sound system superior is the most ridiculous claim I've heard in a long time. You guys really have no clue. I'd suggest you look up some articles about ASIO and find out why it had to be invented in the first place and why even Vista's new WaveRT is no match. In Linux there is no need for ASIO because ALSA is like a system-wide version of ASIO on steroids. In terms of quality it may well be the best sound system ever implemented in a desktop operating system. Its flexibility may be too much of a challenge for simple-minded individuals, but hey, there's nothing you can't learn. :roll:
Allright,but can you tell me how to config Ubuntu's audio louder ? It's lower than window.

---

### Post by eye208 on 2008-04-26
> **_K3nt_ said:**
> Allright,but can you tell me how to config Ubuntu's audio louder ? It's lower than window.
The ALSA mixer adapts itself to the audio interface, i.e. it may look slightly different depending on which sound card you are using. In most cases the overall volume is defined by several sliders at once. For example, if your Front slider is at 50% and your PCM slider is at 50%, the overall volume will be 25% of the maximum possible, which is, of course, pretty quiet. If you use Gnome's default volume applet, make sure all the sliders are visible. You can unhide them in Edit-->Preferences. In the playback tab, pull all the sliders up to maximum gain. Then mute everything you don't need. For example, an unconnected analog line-in or mic socket may introduce noise, so you'll want to mute them when they're not being used. This will reduce the noise floor of your sound card and improve the SNR of its output.

Applications may have their own soft volume sliders which are independent of ALSA. For example Totem, Ubuntu's default media player, has such a slider. Make sure it's at maximum gain as well. The same thing applies to VLC and probably others. However be careful not to introduce digital distortion (aka. "clipping").

The only way to make things even more louder is by using compressor plugins which reduce the dynamic range of the audio stream and bring its average amplitude closer to 0 dBFS. You can configure ALSA to insert LADSPA plugins into the audio chain as described [here](http://alsa.opensrc.org/index.php/Ladspa_%28plugin%29), however this is not recommended if accurate reproduction is your goal. Dynamic compressors _always_ introduce various degrees of distortion. If your laptop or monitor speakers are too weak, consider using an external amplifier to raise the volume.

Note that all the info given here applies to ALSA, not Pulse Audio, ESD or OSS. Pulse Audio in Ubuntu 8.04 has several bugs. I recommend not to use it. Plain ALSA or Jack is your best option.

---

### Post by _K3nt_ on 2008-04-26
> **eye208 said:**
> The ALSA mixer adapts itself to the audio interface, i.e. it may look slightly different depending on which sound card you are using. In most cases the overall volume is defined by several sliders at once. For example, if your Front slider is at 50% and your PCM slider is at 50%, the overall volume will be 25% of the maximum possible, which is, of course, pretty quiet. If you use Gnome's default volume applet, make sure all the sliders are visible. You can unhide them in Edit-->Preferences. In the playback tab, pull all the sliders up to maximum gain. Then mute everything you don't need. For example, an unconnected analog line-in or mic socket may introduce noise, so you'll want to mute them when they're not being used. This will reduce the noise floor of your sound card and improve the SNR of its output.

Applications may have their own soft volume sliders which are independent of ALSA. For example Totem, Ubuntu's default media player, has such a slider. Make sure it's at maximum gain as well. The same thing applies to VLC and probably others. However be careful not to introduce digital distortion (aka. "clipping").

The only way to make things even more louder is by using compressor plugins which reduce the dynamic range of the audio stream and bring its average amplitude closer to 0 dBFS. You can configure ALSA to insert LADSPA plugins into the audio chain as described [here](http://alsa.opensrc.org/index.php/Ladspa_%28plugin%29), however this is not recommended if accurate reproduction is your goal. Dynamic compressors _always_ introduce various degrees of distortion. If your laptop or monitor speakers are too weak, consider using an external amplifier to raise the volume.

Note that all the info given here applies to ALSA, not Pulse Audio, ESD or OSS. Pulse Audio in Ubuntu 8.04 has several bugs. I recommend not to use it. Plain ALSA or Jack is your best option.

I've tried,nothing changed.I thing it's unable to make a difference thing.

---

### Post by eye208 on 2008-04-26
> **_K3nt_ said:**
> I've tried,nothing changed.I thing it's unable to make a difference thing.
OK, now it's your turn to provide some info:

Which soundcard? (lspci | grep -i audio)
PCI or USB?
Which version of Ubuntu?
Which audio application?
Is it configured to use ALSA?
Have you checked out the "switches" and "options" tabs of the Gnome mixer? There may be some settings to control pre-amps etc.

---

### Post by _K3nt_ on 2008-04-26
> **eye208 said:**
> OK, now it's your turn to provide some info:

Which soundcard? (lspci | grep -i audio)
PCI or USB?
Which version of Ubuntu?
Which audio application?
Is it configured to use ALSA?
Have you checked out the "switches" and "options" tabs of the Gnome mixer? There may be some settings to control pre-amps etc.

- Onboard soundcard(5.1):
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
-Ubuntu 8.04
-I try with Amarok,VLC,MPlayer...(try to turn up the equalizer)
-Have configured to use ALSA (In output device ...)
-Have checked the mixer...
Give me some idea!Thank u very much.

---

### Post by eye208 on 2008-04-26
> **_K3nt_ said:**
> -Ubuntu 8.04
I'm not yet using Ubuntu 8.04 but I read that Gnome's volume control is now managing Pulse Audio levels by default. You can probably change this by opening the volume control, then going to File-->Change Device and selecting the ALSA device from the list.

For example, in my volume control (Ubuntu 7.10) there are the following device options:

0: HDA Intel (Alsa mixer)
1: Realtek ALC885 (OSS mixer)

In your case there is most likely one ALSA mixer entry and another for Pulse Audio, the latter being selected by default. Try selecting the ALSA entry and then setting all the sliders to maximum as described earlier.

Pulse Audio is currently causing lots of problems in Ubuntu 8.04. It's one of the reasons why I have not yet upgraded from Ubuntu 7.10. I'll keep an eye on the bug reports in Launchpad and maybe upgrade in a few weeks when fixes are available.

---

### Post by vanadium on 2008-04-27
For your information: Gnome volume control is using Alsa mixer by default. Indeed, might be because there are too much issues remaining with Pulse Audio.

---

### Post by ThinkDave on 2008-04-27
I have a
02:05.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
And to me it does seem that OSS has better sound reproduction im not claiming i know anything technical about it but when i change to the OSS device the highs and lows separate and the sound becomes clearer as opposed to a slight muddiness with alsa. 
Any ideas eye208?

---

### Post by ThinkDave on 2008-04-29
Just installed Hardy and my god the improvements were staggering guess I just needed a newer version of alsa.

---

### Post by JPorter on 2008-06-30
Most of the audio quality complaints I've seen under Linux could be traced directly to improper settings in the ALSA mixer.

Check your levels by running [FONT="Courier New"]alsamixer[/FONT] in a console.

Make absolutely sure that the master and the PCM gains are all set to 0.00 db.  This is not all the way up, it is some value in the upper half of the scale.  You should only pay attention to the actual gain value, not the position on the slider.

To make the settings persist over a reboot, exit (press Q) and run [FONT="Courier New"]sudo alsactl store 0[/FONT] to save the settings.

---

### Post by markbuntu on 2008-06-30
The best thing you can do for high quality sound is get a good set of speakers. Crappy speakers need all sorts of tweaking. Good ones need no eq unless you are playing them at high volume and need to adjust them for the room dynamics. It does not matter how much money you spent on your speakers, if you need to eq them at low volumes they are crap.

The key to quality sound with a pc is to set the sample rate to what your sound card can handle and what your sound is sampled at, usually 44,1khz or 48khz ( 96khz and above is completely unecessary unless you are a recording engineer doing actual live recording), set the volumes to below max, leave the eq alone and run the sound through your stereo.

When you try to play a standard audio cd (which has a sample rate of 44.1khz) at a higher rate, a (faulty) conversion takes place. This does not result in better sound since the conversion necessarily introduces errors.

Some of the best quality sound available today is streamed live concerts at high sample rates. These come right off the soundboard at 96khz or 192khz.

---

