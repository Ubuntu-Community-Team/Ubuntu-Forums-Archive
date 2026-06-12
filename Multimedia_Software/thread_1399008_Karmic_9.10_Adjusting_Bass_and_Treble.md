---
title: "Karmic 9.10: Adjusting Bass and Treble"
date: 2010-02-05
forum: Multimedia Software
---

### Post by Jivinathejamboree on 2010-02-05
Hi All,

Its become desperate. I didn't realise when I installed ubuntu that it requred knowing about 'terminals' and 'computer speak'. this is not my thing. I just want a graphical interface that works.

Please, can someone give the most simple answer to how to adjust bass and treble levels? PulseAudio doesn't have a mixer, Alsa doesn't have a mixer in the terminal GUI... And please don't redirect me to any other links, nothing else that anyone else has written has made any sense, or they seemed to be based on assumptions - 'well, this should work if this and that...'  Please write a response only if you've managed to simply adjust your bass and treble in Karmic Koala. Can it be so hard? Ubuntu, this is a very, very basic feature. It needs to work if people are going to take this platform seriously...

---

### Post by ajgreeny on 2010-02-05
I have no idea what you have already looked at or tried, but I think you are going to be unlucky if you want to do this without any terminal use at all.  I would say, however, do not be afraid of the terminal, it is really not a scary as you seem to think, and in this case you only need to use it to set up the PPA repository in your apt sources.list.

Have a long look at this thread from psyke83 [http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838) which goes into detail about what is needed.   It does require one terminal entry, which you can copy and paste, but basically it is as simple as this:-

**Installation:**
Since v2.6, the pulseaudio-equalizer package is available from [my PPA]("https://launchpad.net/%7Epsyke83/+archive/ppa"), which you can access like so:
     Code:
     $ sudo software-properties-gtk --enable-ppa=psyke83/ppa; sudo apt-get update; sudo apt-get install pulseaudio-equalizer 
**Source code:**
The source is [available]("https://code.launchpad.net/%7Epsyke83/+junk/pulseaudio-equalizer") on Launchpad.

**Usage:**
Open the PulseAudio Equalizer (Applications -> Sound & Video). The interface should be fairly self-explanatory:

[LIST]
[*]**15 frequency bands** you can adjust to your liking;
[*]**Preamp** will boost your equalized volume (as a multiplier value from 1x to 4x);
[*]**Presets** are included (based on VLC's built-in equalizer), or you can choose to save own favourite configuration as a new preset;
[*]**EQ Enabled** will enable the equalizer in the current session (which applies to all running applications);
[*]**Keep Settings** will configure your PulseAudio configuration to remain permanently equalized (and therefore, you won't need to run the PulseAudio Equalizer interface each time you login);
[*]**Advanced** menu options so that you can reset all settings (useful for troubleshooting) or delete user presets;
[*]**Apply Settings** will apply all changes.
[/LIST]
Don't thank me for this, I am just the messenger, thank psyke83, and if you like it perhaps it's worth a private message to him to say so.

---

### Post by warfacegod on 2010-02-05
Many media players have built in EQ's already. I use Amarok 1.4 and it's EQ does just fine for my needs. Perhaps you should look around in the media player you are using.

---

### Post by VertexPusher on 2010-02-05
> **Jivinathejamboree said:**
> Can it be so hard? Ubuntu, this is a very, very basic feature. It needs to work if people are going to take this platform seriously...
Ballshot. I am sitting at a Windows XP machine right now, and its sound card mixer has no bass and treble controls. Because equalizers are hardware features, and most sound cards, especially onboard ones, don't have it.

By providing a software equalizer as a workaround, Ubuntu is already ahead of the most successful desktop operating system of all times. If that's not good enough for you, feel free to format your drive.

---

### Post by ajgreeny on 2010-02-05
Whilst I mostly agree with you VertexPusher, did you have to put it so bluntly?

Yes it is something of a workaround to get a system wide software equaliser, but it is something I have seen requested many times in the past.  I have searched myself before without success, though this time it was dead easy to find that thread.

It does seem, however, that the OP is sacred stiff of using the terminal, and even though it is not often needed nowadays, I was trying to comfort him a little, and get him to realise that "terminal" is no longer a swear word, but it is a powerful and occasionally useful tool in our armoury that he would need to get the gui application he wants.

---

### Post by VertexPusher on 2010-02-08
> **ajgreeny said:**
> Whilst I mostly agree with you VertexPusher, did you have to put it so bluntly?

Yes it is something of a workaround to get a system wide software equaliser, but it is something I have seen requested many times in the past.
It's a feature that doesn't make sense, and it is mostly requested by people without a clue. For more than half a century, the holy grail of sound reproduction has been a playback system with a linear frequency response, i.e. sound comes out exactly as it went in. The digital domain has this feature. It does not need system-wide equalizers because its sound reproduction is transparent by default.

If your amplifier or your speaker system introduces distortion, fix the problem where it happens. You can't turn a 3cm diameter laptop speaker into a full-range driver using an equalizer in the digital domain. The result of trying to do so will make your ears bleed and eventually kill the onboard amplifier or the speaker because of digital clipping. If you don't know what digital clipping means, look it up.

---

