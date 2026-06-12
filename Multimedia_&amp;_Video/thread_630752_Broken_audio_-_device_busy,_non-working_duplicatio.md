---
title: "Broken audio - device busy, non-working duplication"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by OliW on 2007-12-03
I moved house a couple of days ago. That seems to be the beginning of my issues, though I know it must be unrelated. I have a Realtek ac97 7.1 chipset with 5.1 speakers plugged in. I had it set up to clone the front speakers. All worked fine.

As of a couple of days ago (and kicking several multimedia applications around before noticing an issue), the cloning stopped working. I've been through the cli alsamixer and the gui mixer and both seem to be setup correctly. What's more is I cannot run more than one ALSA-utilising application at the same time (eg: Firefox (setup to use aoss), Amarok, Kaffeine, Rhythmbox, et al). I always get a dsp/device busy message until I quit the hogger and try again.

So I'm fairly sure I've completely borked something as this used to work fine. Ideally I would love to shake my PC until all the bad config just fell out the CD tray but I know (from experience) this doesn't tend to work. Can anybody advise me a way to nuke the current sound setup and restore a stock-installation's config?

... Even if that means temporarily killing amarok, xine and all my codecs. I just want this working.

Edit: Skype dies too when trying to make any noise (or enter config):

```
oli@bert:~$ skype
ALSA lib conf.c:1588:(snd_config_load1) _toplevel_:21:10:Unexpected char
ALSA lib conf.c:2849:(snd_config_hook_load) /home/oli/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3076:(snd_config_update_r) hooks failed, removing configuration
Aborted (core dumped)
```Just magical, eh?

Edit2: Well after some more random package-kicking, config deleting and a restart amarok, kaffeine, firefox/flash and even skype are all happy to use the dsp at the same time. I'm either an idiot or something is really messed up. It's probably the first.

However, I still can't get sound out of my read speakers. Here's the speaker-test output (I've marked what worked and what didn't):```
oli@bert:~$ speaker-test -Dplug:surround51 -c6

speaker-test 1.0.14

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 3 to 5461
Period size range from 3 to 5461
Using max buffer size 5460
Periods = 4
was set period_size = 1365
was set buffer_size = 5460
 0 - Front Left
 4 - Centre  -- Broken
 1 - Front Right
 3 - Rear Right  -- Broken
 2 - Rear Left  -- Broken
 5 - LFE -- NA
```

In the Alsa mixer I've got duplicate-front on. Where can I go from here?

---

### Post by kyphi on 2007-12-03
To remove ALSA you need to do this:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```Then you need to reinstall all the removed packages.

---

### Post by OliW on 2007-12-04
When I do that it says:

```
The following packages will be REMOVED
  alsa-base* alsa-utils* fast-user-switch-applet* gdm* linux-sound-base*
  ubuntu-minimal*
```

Aren't ubuntu-minimal and gdm pretty essential?

---

### Post by macabro22 on 2007-12-04
I have the same problem and I pushed that line. Don't do it. It fixes nothing.

Here's an example of what is happening in spite pulseaudio being uninstaled.

> 
 alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused


---

### Post by OliW on 2007-12-04
I've not (to my knowledge) played with any pulseaudio stuff to try and remedy this. I feared I would just screw things up even more. I played around a bit more, reinstalled a few packages and restarted and the sound concurrency issue seems to have vanished as mysteriously as it appeared.

I'm now just stuck with stereo output from my front two satellites. I've edited my original post to show this.

---

