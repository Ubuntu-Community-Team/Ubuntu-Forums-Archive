---
title: "Audio issue with mythbuntu 10.10 and mythtv .24"
date: 2010-11-15
forum: Mythbuntu
---

### Post by thatguruguy on 2010-11-15
Simply put, I am unable to get any audio when trying to watch live TV or trying to record anything. I have pulseaudio installed. I use a Hauppauge 950Q usb tv stick, which worked under 10.04 and mythtv .23.1.

Here are some of the strange things about this:

[LIST]
[*]I can hear music fine when using MythMusic, which uses the default audio setup for the frontend, which implies that the audio setup is OK.
[*]I can hear audio (although slightly out of synch) when I use tvtime, which lets me know that it's possible to capture sound from the tuner.
[*]If I open the pulseaudio volume control, it shows that sound is coming out of the tuner.
[/LIST]
The only options listed for audio in the backend for my tuner are "Null" and "ALSA:default". I'm using ALSA:default.

Any suggestions?

---

### Post by uncle hammy on 2010-11-15
Have you done a scan for audio hardware on the audio settings screen?  When you load that screen with 0.24, no options will show until you do the scan.

With mine, which uses SPDIF out, I had to set it to the default sound card (which now showed up as the actual card, ALSA:default was no longer an option), then enable "Advanced Audio Configuration" and enable "Separate Digital Output Device" and then select the IEC598 device.

That gave me full surround for TV and ungrabled stereo for music.

---

### Post by thatguruguy on 2010-11-15
> **uncle hammy said:**
> Have you done a scan for audio hardware on the audio settings screen?  When you load that screen with 0.24, no options will show until you do the scan.

With mine, which uses SPDIF out, I had to set it to the default sound card (which now showed up as the actual card, ALSA:default was no longer an option), then enable "Advanced Audio Configuration" and enable "Separate Digital Output Device" and then select the IEC598 device.

That gave me full surround for TV and ungrabled stereo for music.

I did, indeed, run the scan for audio hardware.  As stated previously, sound works for MythMusic.  It also works when watching videos (but not recordings from Myth) using the internal player, which implies that the sound is set up correctly on the frontend.  The implication is that sound is not working on the backend.

---

### Post by nickrout on 2010-11-16
> **thatguruguy said:**
> I did, indeed, run the scan for audio hardware.  As stated previously, sound works for MythMusic.  It also works when watching videos (but not recordings from Myth) using the internal player, which implies that the sound is set up correctly on the frontend.  The implication is that sound is not working on the backend.

what is your source? I see that card does:

          o NTSC Analog Cable, Over the Air TV
          o ATSC Digital Over the Air HDTV
          o Clear QAM Digital Cable TV

> The only options listed for audio in the backend for my tuner are "Null" and "ALSA:default". I'm using ALSA:default.

I think you are confused. There is no backend sound setting.

---

### Post by thatguruguy on 2010-11-16
> **nickrout said:**
> what is your source? I see that card does:

          o NTSC Analog Cable, Over the Air TV
          o ATSC Digital Over the Air HDTV
          o Clear QAM Digital Cable TV

Right now, I'm just trying to get the regular over the air analog cable working.  The card type listing is Analog V4L capture card (which is what worked on this same box using mythbuntu 10.04 and mythtv .23.1).

> **nickrout said:**
> I think you are confused. There is no backend sound setting.

I expressed myself poorly.  I was referring to the "Audio device" listing for the card.  It's set to "ALSA:default".  When I was using mythbuntu 10.04, it was set to /dev/dsp1, which worked fine.  Unfortunately, that's no longer an option, since OSS was removed from the kernel included with mythbuntu 10.10.

---

### Post by nickrout on 2010-11-16
> **thatguruguy said:**
> Right now, I'm just trying to get the regular over the air analog cable working.  The card type listing is Analog V4L capture card (which is what worked on this same box using mythbuntu 10.04 and mythtv .23.1).



I expressed myself poorly.  I was referring to the "Audio device" listing for the card.  It's set to "ALSA:default".  When I was using mythbuntu 10.04, it was set to /dev/dsp1, which worked fine.  Unfortunately, that's no longer an option, since OSS was removed from the kernel included with mythbuntu 10.10.

Do the recordings actually have audio in them? Test with another player.

What happens with recordings made before the upgrade?

What does the frontend log say?

---

### Post by thatguruguy on 2010-11-16
> **nickrout said:**
> Do the recordings actually have audio in them? Test with another player.

What happens with recordings made before the upgrade?

What does the frontend log say?

The recordings do not appear to have any audio in them. I don't have any recordings from before the upgrade, although movies (.mp4 and .avi) play just fine on mythtv's internal player.

---

### Post by nickrout on 2010-11-16
OK. Perhaps the best way to determine whether there really is some sort of audio track is to run mediainfo on a recordings file. 

```
sudo add-apt-repository ppa:shiki/mediainfo 
sudo aptitude update
sudo aptitude install mediainfo
mediainfo /some/recordings/file.mpg
```

it is a long long time since I set up an analogue device, are there audio options in the backend setup?

As you aren't getting a lot of joy (as opposed to diagnosis) here, i wonder if you might want to post to the mailing list?

EDIT; going in circles a bit now, looking at backend setup, there IS an audio device setting for analogue tuners, my error above!

What is your audio output? do you need to force the sampling rate per the backend setting to get a rate playable by your soundcard?

---

### Post by thatguruguy on 2010-11-17
OK, it's fixed.  This is what I did, based upon the instruction from Pulseaudio's wiki (you can read it [here]("http://www.pulseaudio.org/wiki/PerfectSetup")).  This may be helpful to anyone else with a Hauppauge 950Q.

First, you need to create or edit /etc/asound.conf as follows:
```
sudo mousepad /etc/asound.conf
```In that file, you need to add the following:
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
    hint.description "Default Audio Device"
}
ctl.!default {
    type pulse
}

```Reboot, and now requests sent to ALSA:default will be routed through pulseaudio, which is what you want.

Then, set up the V4L (analog) part of the capture card so that the "Audio device" points to ALSA:default, and you should be good to go.

FWIW, I also updated my kernel in accordance with reply 17 of [this thread]("http://ubuntuforums.org/showthread.php?t=1593695").

Also, creating an ".asoundrc" in your home directory rather than /etc/asound.conf DOES NOT WORK, since it's a different user (mythtv) running mythbackend.

---

### Post by thatguruguy on 2010-11-17
As an aside, when I used the /dev/dsp1 as the audio device for the capture card in the backend setup, there was always a noticeable "crackle" in the sound.  Despite the fact that there was a lot of headache involved in setting this up under 10.10 and mythtv .24, that crackle is now gone. Sounds works MUCH better now under pulseaudio than it did when I was using OSS.

---

### Post by nickrout on 2010-11-18
> **thatguruguy said:**
> As an aside, when I used the /dev/dsp1 as the audio device for the capture card in the backend setup, there was always a noticeable "crackle" in the sound.  Despite the fact that there was a lot of headache involved in setting this up under 10.10 and mythtv .24, that crackle is now gone. Sounds works MUCH better now under pulseaudio than it did when I was using OSS.

pulse has been regarded as a bit evil in mythland, but I am referring to output rather than input.

And all bets are off given the huge audio rework in 0.24.

However I do know that as output pulse will cause digital tracks to be decoded and recoded, which is a Bad Thing(TM).

However whether any of that applies to input, I do not know.

---

### Post by Kanji_Man on 2011-01-28
Try entering *ALSA:plughw:1,0* where you used to put */dev/dsp1*.  I found the setting all the way at the bottom of [this page]("http://www.mythtv.org/wiki/PCI_TV_audio") and it worked wonders for me.

---

