---
title: "Jaunty = pulseaudio = no AC3 DTS passthrough from spdif"
date: 2009-05-07
forum: Multimedia Software
---

### Post by Peevy on 2009-05-07
Does anyone else think that Canonical were a bit too hasty in relying so heavily on pulseaudio for audio integration? I mean how many of us use Ubuntu as our main OS on our HTPC & Media centre PC's? And now those of us who have our HTPC's hooked up to a Digital amp decoder through spdif can no longer get AC3 or DTS passthrough. ( of which Im sure there are many):frown:

Come on Ubuntu get this sorted.

If anyone has an easy enough workaround for this please let us know. I say easy because Im tired of trying out all the other unsuccessful tips I've come across. Killing pulseaudio doesn't seem to cut it anymore, at least not in Jaunty.

So if anyone can help or just wanna voice there opinion on this please do.

---

### Post by JohnAStebbins on 2009-05-24
I also found this to be *exceedingly* annoying. The default settings for pulseaudio now makes it a hassle to bypass it when you need ac3 passthru.  The audio device is "busy".  Since the main purpose of my Ubuntu box is media playback through xbmc, I just completely disabled pulse.
```

sudo update-rc.d -f pulseaudio remove
sudo update-rc.d pulseaudio stop 2 3 4 5 .
sudo mv /etc/X11/Xsession.d/70pulseaudio ~/
asoundconf unset-pulseaudio
asoundconf set-default-card Intel

```

Note the '.' at the end of update-rc.d stop above.  Its important.
Replace "Intel" with the name of your audio card.  You can find it with
'aplay -l'. You will see something like "card 0: Intel ..."

Then in "System->Preferences->Audio" choose alsa for everything.
Reboot and hopefully your audio behaves better.

---

### Post by meermanr on 2009-07-04
While less than ideal, I managed to get AC3 / DTS to pass through pulseaudio, output on SPDIF and decoded by my amp by:

[LIST]
[*]Putting pulseaudio's volume controls all on MAX
[*]Change pulseaudio's default sampling rate to 48kHz
[*]Telling my media player (XBMC) to use the "default" audio output when doing passthough (NOT "iec958" or "spdif"!)
[/LIST]

Because the volume is on 100%, the sound data is unchanged by pulseaudio and just "passes through" (so long as no other apps are producing sound, in which case the data gets garbled and my external decoder spits out static until the interfering app shuts-up).

AC3 (Dolby Digital) is signed 16-bit little-endian 2-channel 48kHz PCM data (as far as we want pulseaudio and ALSA to be concerned), but the default pulseaudio sample-rate is 44.1kHz, so when an application attempts to connect to pulseaudio for passthrough pulse rejects the connection *because of the sample-rate*.

You can change pulseaudio's default sample rate by creating ~/.pulse/daemon.conf like so:
```
default-sample-rate = 48000
```

You have to restart pulseaudio for this to take affect (restarting the PC will work as well). I happen to have the pulseaudio-utils package installed which provides the `pacmd` command, and I used it to verify my sample-rates before and after:

```

# Before reboot
$ pacmd list-sinks | grep sample
	sample spec: s16le 2ch 44100Hz
	sample spec: s16le 2ch 44100Hz

# After reboot
$ pacmd list-sinks | grep sample
	sample spec: s16le 2ch 48000Hz
	sample spec: s16le 2ch 48000Hz

```

I've read that changing the default sample rate may cause audible crackling and pops when playing sound at the non-default rate, but I've not noticed any after making this change.

---

### Post by fidoboy on 2009-09-15
Hello, i've installed pulseaudio into XBMC Live, but i'm unable to get i working, i get no sound at all in XBMC. how do you edited the .asoundrc file? what changes do i need to make in XBMC setup?

thanks in advance,

---

