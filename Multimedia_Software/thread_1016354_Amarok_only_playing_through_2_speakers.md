---
title: "Amarok only playing through 2 speakers"
date: 2008-12-19
forum: Multimedia Software
---

### Post by ajm8127 on 2008-12-19
Hi,

I just did a fresh install of 8.10 today, and I installed Amarok, which I used in 7.04

The first time I tried to play an mp3, it asked me to install some libraries. I wasn't surprised, as I know ubuntu does not come with mp3 support.  I installed what it asked me to install. So I played a 311 song, and it was only playing through my front speakers. I checked my mixer setting, and the PCM Front, PCM Surrond, PCM Center, and PCM LFE we all high enough. so I tried Rhythmbox. I asked me to install addition libraies. Then I dawned on me, the libraries Amarok installed, weren't the right ones. Rhythmbox works fine, through all speakers.

I check into the amarok setting and found a "speaker arrangement" drop down. I'm pretty sure this is what I changed before in 7.04 to make it work, but now, no matter what Output Plugin is selected, I cannot change the arrangement because there are no options in the dropdown. I have also uninstalled amarok and reinstalled, to no avail. This is really frustrating because I like amarok so much. So basically what I want to know, is how do I get Amarok to play through all of my speakers without reinstalling my operating system?

---

### Post by ajm8127 on 2008-12-20
I finally got it working after much install/uninstall frustration and a little fowl language. I used the OSS output plugin because it just wouldn't work with ALSA. Whatever, Stranglehold comes out of all five speakers now.:guitar:

---

### Post by ajm8127 on 2008-12-21
Alright,

So the problem is more widespread than Amarok. Like I said, Rhythmbox worked fine out of the box, and I got Amarok to output 5.1 by using OSS as an output pluging, but in Firefox, flash only works from two speakers also. So it seems to me more like an ALSA configuration problem but like I said Rhythmbox is fine. Can anyone shed some light on this. It's a Sound Blaster Audigy and I am running 8.10. If I do the tone test in the System->Preferences->Sound dialog, it comes from all five speakers using the Multichannel Playback (ALSA) option for all settings.

---

