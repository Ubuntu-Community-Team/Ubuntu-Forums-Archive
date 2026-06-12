---
title: "Sound stops working after suspend"
date: 2011-08-06
forum: Multimedia Software
---

### Post by Dalekk on 2011-08-06
My problem is this: when I suspend, sound disappears, and I have to reboot to get it back, which is, needless to say, rather annoying. I'm using Ubuntu 11.04, with a low-latency kernel.

I have three sound cards:
1) Delta 1010LT, which uses snd_ice1712
2) Sound Blaster Audigy 2, which uses snd_emu10k1
3) Some on-board Realtek thingy, which I guess uses snd_hda_codec_realtek

I use jack on the Delta1010LT, and I run pulseaudio through jack.

When, after a suspend, I try to restart jack via qjackct, it gives up and prompt the following:

```

Acquire audio card Audio1
creating alsa driver ... hw:M1010LT|hw:M1010LT|128|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver ICE1712 running on card 1 - M Audio Delta 1010LT at 0xec00, irq 16
configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
port created: Midi-Through:midi/playback_1
port created: Midi-Through:midi/capture_1
port created: M-Audio-Delta-1010LT:midi/playback_1
port created: M-Audio-Delta-1010LT:midi/capture_1
port created: SB-Audigy-2-Platinum--SB0240P-:midi/playback_1
port created: SB-Audigy-2-Platinum--SB0240P-:midi/capture_1
port created: SB-Audigy-2-Platinum--SB0240P-:midi/playback_33
14:02:12.636 ALSA connection graph change.
port created: SB-Audigy-2-Platinum--SB0240P-:midi/capture_33
port created: Emu10k1-WaveTable:midi/capture_1
port created: Emu10k1-WaveTable:midi/capture_2
port created: Emu10k1-WaveTable:midi/capture_3
port created: Emu10k1-WaveTable:midi/capture_4
14:02:21.618 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
ALSA: poll time out, polled for 4353072 usecs
JackAudioDriver::ProcessAsync: read error, stopping...
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
Cannot open qjackctl client

```

Now, I did try to look through the error messages above, but I couldn't figure out what the problem is. On a side note, I wonder if anybody could tell me why jack also creates sockets for my Sound Blaster? 

Anyway, I tried to unload the snd_ice1712 and snd_emu10k1, but I get the following: 

```
ERROR: Module snd_ice1712 is in use
ERROR: Module snd_emu10k1 is in use
```

Doing this:
```
sudo fuser -k /dev/snd/*
```
before trying to unload the modules didn't work either.

So that's it, I'm pretty stuck. Any help would be very welcome. Thank you!

---

### Post by Dalekk on 2011-08-08
Er, bump...

---

### Post by Quadari on 2011-09-11
Bumping this thread because I just ran into the very same problem.

I just did a new install of 11.04 on a Toshiba Satellite P105 laptop.  The sound works just fine until I suspend. After waking from suspend there's no sound whatsoever.

In the help site this is addressed:
[https://help.ubuntu.com/community/SoundTroubleshooting#Getting_ALSA_to_work_after_suspend_.2BAC8_hibernate](https://help.ubuntu.com/community/SoundTroubleshooting#Getting_ALSA_to_work_after_suspend_.2BAC8_hibernate)

However, I tried the script suggested there to no avail.  Anyone have any other thoughts?  Happy to post whatever debugging output you need.

The audio on this beast is (output from lshw):
```


        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:d0340000-d0343fff

```

Thanks!

---

### Post by Quadari on 2011-09-12
Also, I should mention that I tried setting 
```

force_unload_modules_before_suspend="all"

```
in /etc/default/alsa

as per the discussion here:
[http://ubuntuforums.org/showthread.php?t=1348916&highlight=suspend&page=3](http://ubuntuforums.org/showthread.php?t=1348916&highlight=suspend&page=3)

That didn't fix it.

---

### Post by tigerstripedcat on 2011-09-26
I have the same problem, and it sure is annoying.  Does anyone even know of a workaround so I don't have to restart each time?

---

### Post by tigerstripedcat on 2011-09-26
we should all probably subscribe to this bug:

[https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/586209](https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/586209)

I think it's the same thing.  If we make some noise over there maybe people will start to notice.

---

### Post by lidex on 2011-09-27
> **tigerstripedcat said:**
> I have the same problem, and it sure is annoying.  Does anyone even know of a workaround so I don't have to restart each time?

Does reloading alsa work:
```
sudo alsa force-reload
```

---

### Post by ter31 on 2012-05-17
I had the same problem and I think the culprit is the /usr/bin/qjackctl script. It runs pasuspender (which disables pulseaudio for the duration qjackctl runs), which is not needed, since jack2 can negotiate hardware sharing with pulseaudio via dbus. If one modifies the qjackctl script to run qjackctl.real directly, suspend-resume works correctly. Maybe someone could mention this at launchpad and fill another bug report in the upstream bug tracker ([http://sourceforge.net/tracker/?group_id=86211&atid=578826)?](http://sourceforge.net/tracker/?group_id=86211&atid=578826)?)

---

### Post by vladaionescu on 2013-02-02
Hey guys,

I figured it out. What you need to do is

$ jack_control stop

and then start jack again (in whichever way you were starting it). Due to jack being confused, the command will hang for a while (10-30 secs), but eventually jack does stop.

I've described a slightly nicer (and automatic) way to fix this in a blog post here:

[http://www.vladalexandruionescu.com/2013/01/using-your-guitar-or-other-instrument.html](http://www.vladalexandruionescu.com/2013/01/using-your-guitar-or-other-instrument.html)

(in particular the subheading "Some more hackery (fixing suspend)"). Though that's pretty specific to my setup.

But the idea is to have a script /etc/pm/sleep.d/00_restart-jack which stops Jack just before suspending (using 'jack_control stop') and then starts it again (I do it via qjackctl) just after resuming. Because I stop it *before* suspending, it doesn't hang for a long time and it goes pretty smoothly. :guitar:

HTH

---

