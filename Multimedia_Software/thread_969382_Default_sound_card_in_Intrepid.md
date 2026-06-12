---
title: "Default sound card in Intrepid"
date: 2008-11-03
forum: Multimedia Software
---

### Post by billstei on 2008-11-03
I am running Intrepid and I have two sound cards (and a third in the form of a tv tuner) and when I do cat /proc/asound/modules I get this:

 0 snd_hda_intel
 1 snd_emu10k1
 2 em28xx_alsa

The device snd_had_intel is the card I want to be the default sound card that Gnome uses, and with index 0 it looks correct, yet Gnome is using the second card snd_emu10k1 with index 1.  I have also tried using the asoundconf-gtk program to set the default sound card to snd_had_intel, but there is no change.  What is the problem?

Bill

---

### Post by lakerssuperman on 2008-11-04
I too have this problem.  I wanted my Soundblaster Live 5.1 to be the default, which it is not currently.  I tried "sudo asoundconf list" to list my sound cards.  I then tried "sudo asoundconf set-default-card Live" with no luck.  Even after rebooting it isnt the default card.

---

### Post by rlhawk on 2008-11-04
Same, or at least similar, problem here.  Only for me cat /proc/asound/modules only has one card: 0 snd_emu10k1

But when I type amixer or alsamixer, it only has a master volume.  To get my desired behavior, I have to use `amixer -c 0` or `alsamixer -c 0` and then everything works the way I want it to.  Any ideas how to make this the default?  Really messes things up because one of the programs I use uses amixer for adjusting the volume and I can't make that program add the -c 0 or anything...

---

### Post by billstei on 2008-11-15
Another problem that I have (had) is that running certain audio applications under Wine produces audio playback stuttering and sample rate problems, which is largely due to incompatibilities with PulseAudio.  To solve this I removed the pulseaudio package, which unfortunately required the removal of the ubuntu-desktop package.  This resulted in yet another issue, which is that Gnome aborts session startup (use Gnome failsafe session if you get caught by this) because /usr/bin/pulse-session no longer exists, while /etc/X11/Xsession.d/70pulseaudio does exist and tries to run /usr/bin/pulse-session.  The solution was to do apt-get purge on pulseaudio, which would not run/purge until I installed pulseaudio (!). ](*,)

So, what does this have to do with "Default sound card in Intrepid" ?  After pulseaudio was throughly purged (meaning that /etc/X11/Xsession.d/70pulseaudio was removed) Gnome had one of those suggestion/information icons appear and said it might be a good idea to run asoundconf set-default-soundcard, which was the right idea but failed to mention that you need to say *which* soundcard, like this:

asoundconf set-default-soundcard NVidia

where the name of your sound card (aka mine is NVidia) can be determined like this:

asoundconf list

It would seem that I now have the correct default sound card, and my Wine audio application(s) works too, all while not interfering with Jack which is set to use the non-default sound card.  =D>

Bill

---

