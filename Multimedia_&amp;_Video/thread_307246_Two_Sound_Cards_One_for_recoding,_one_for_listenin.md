---
title: "Two Sound Cards: One for recoding, one for listening"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by Kalinda on 2006-11-26
Having been unable to get my microphone to work via the line in on my SBLive 24-bit card, I've come up with another idea.

I have an onboard sound card.. and it works very well with my mic.. but playing back audio with it sounds like crap, which I assume is because the Linux drivers for my VIA chipset aren't very good; the sound card gave me the same trouble in Suse, too. So I put the SBLive in.

Now, I re-enabled my VIA card in the BIOS, so the system made it the default. I've already changed it so my Creative card is the default (using ALSA), which was easy. How to do it is written in the Sound Problems Solutions sticky. The problem is that I can't use the other one now, just as before I couldn't use the Creative when VIA was default. 

Does anyone know if there is a way to make it so I can use the VIA for recording sound only.. and nothing else? If not, I could set it up so I'm using both cards at the same time and just turn down the VIA one.. but I might need some direction there, too...

This might seem more complicated then it needs to be.. but I want to be able to use Skype and the voice clips in aMSN's SVN, so I figured this might work.

Anyone got any ideas?

Thanks!

---

### Post by xgorgx on 2006-11-30
Hi!

They mentioned here about this solution and sadly also about a bug...
[http://www.ubuntuforums.org/archive/index.php/t-188148.html](http://www.ubuntuforums.org/archive/index.php/t-188148.html)
Lucky me, I don't have to reboot often ;)

First of all: cat /proc/asound/modules
mine is:
0 snd_via82xx
1 snd_emu10k1

In /etc/modprobe.d/alsa-base replace (don't forget to make a backup first!):

install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1

with:

install sound-slot-0 modprobe snd_emu10k1
install sound-slot-1 modprobe snd_via82xx

or the other one depending on which card you want as the default (sound-slot-0, hw:0,0)

and

options snd_emu10k1 index=0
options snd_via82xx index=1

at the end of file

I also uncomment the rest of options for safety

sudo-update modules and restart the system.
Voila!

Just for check
cat /proc/asound/modules
0 snd_emu10k1
1 snd_via82xx

The rest is alsamixer and/or Gnome-Mixer thing:

My configuration for using emu10k1 (Sound Blaster Live! 5.1) as default card (hw:0,0) in Gnome-Mixer for using 5.1 set is:

Marked Tone switch
Bass, Treble
Wave Center
Wave LFE
Wave Surround
EMU10k1 PCM
EMU10k1 PCM Send

For skype and other OSS applications:
Install aoss (If you still have problems with sound, install skype_dsp_hijacker)

In Gnome-Mixer switch view to second card mixer
File/change device: (mine is: 1:VIA82C686A/B rev50 (Alsa Mixer)
Active channels:
Master
PCM
Microphone (In Recording Tab)

In Skype:
Tools/Options/Sound Devices:
Audio system to use: ALSA - 2 devices found

Audio in: VIA82C686A/B rev50
Audio out: VIA82C686A/B rev50
Ringing: SBLive 5.1 - thanks to this i don't have to wear headphones all the time to hear ringing :D

If it won't help maybe try also

[http://alsa.opensrc.org/index.php?page=FAQ026](http://alsa.opensrc.org/index.php?page=FAQ026)

and:

[http://alsa.opensrc.org/index.php?page=MultipleCards](http://alsa.opensrc.org/index.php?page=MultipleCards)
[http://alsa.opensrc.org/MultipleCards](http://alsa.opensrc.org/MultipleCards)

But I still can't get what are they writing about :), thats why I moved from Debian to Ubuntu. 
It just works :D

Cheers!

---

### Post by Kalinda on 2006-11-30
Thanks for posting a solution!

I already got my microphone working on my Creative sound card; I am now using the same one as you are, the 5.1. However, your solution will probably work for other people. So I want to make a how-to about fixing microphone problems, I will include your how-to in it along with one that I'm going to write to get the microphone working on the Creative 5.1; it's actually rather simple to get it to work.

However, I don't have time to do it right now because I'm rather busy with school. I will see are doing it up this weekend.

Thanks again!

---

