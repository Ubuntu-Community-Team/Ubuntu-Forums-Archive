---
title: "Simultaneous Analog and SPDIF"
date: 2009-01-28
forum: Mythbuntu
---

### Post by uncle hammy on 2009-01-28
I installed a Turtle Beach Riviera in my main front end and disabled the onboard sound.  I then installed gnome-alsamixer and checked "IEC958 Out", which enabled the SPDIF output on the sound card.

In Myth, I had no sound at all, so I went to the General Settings and left everything as ALSA:default and checked off both DTS and AC3 passthrough, and low and behold, I have full digital sound coming through my receiver.  

However, I am trying to get the analog signal to go through the TV as well, so I don't HAVE to use the receiver (it's a waf thing).  So, I closed down myth, started a song playing in VLC and started going through the settings in gnome-alsamixer.  Once I checked "IEC958 Monitor", I had digital audio out of the receiver and analog sound coming through the tv!  However, when I went into myth and started a recording, the digital sound is good but the analog coming through the TV is the worst jackhammer static you've ever heard.  If I go back to the general settings and uncheck the passthrough options, the tv sound is fine AND there is a signal being sent to the receiver, however it is only 2 channel stereo PCM.

In going though the wiki about digital sound here [http://www.mythtv.org/wiki/Configuring_Digital_Sound](http://www.mythtv.org/wiki/Configuring_Digital_Sound) there is mention to adding something to the end of alsa configuration files...

"If you would like simultaneous digital and analog output, add the following at the end of the above /etc/asound.conf or .asoundrc file: "

However, my system doesn't seem to have either of those files.  So right now, I have to leave the passthroughs unchecked for most viewing.  Then if I really want the 5.1 digital sound, I have to go to settings, check them, then be sure to mute my TV, lest I freak my entire household out of their skins with the jackhammer.

I know I am right on the door step, but can anyone help me get full digital audio going out to my receiver, while still having the analog 2 channel going out to my tv?

Thanks,
Scott

---

### Post by Dewey_Oxberger on 2009-01-29
Generally you only need the asound.conf (or .asoundrc) if you want to change the default behavior of the the alsa stuff.  Typical installations don't have those files.

this might help you:

[http://alsa.opensrc.org/index.php/Asoundrc](http://alsa.opensrc.org/index.php/Asoundrc)

---

### Post by uncle hammy on 2009-01-29
Thanks, that's very helpful.  Will play around with it tonight.

---

### Post by uncle hammy on 2009-01-29
No luck, I went through that created a config file, added the section to have simultaneous analog /spdif and same results.  Using Gnome-AlsaMixer, with "IEC958 Output" checked, I MUST have "IEC958 In Monitor" checked to get anything at all through the analog output (which I think is simply re-feeding the spdif back through, for recording purposes).  When AC3 / DTS passthrough is checked in MythTV, if the audio signal is more than 2 track stereo (i.e. Listen to music works fine, Watch HDTV not so much), the sound that comes out of the analog output is a horrific jackhammer like static, which I think may have something to do with my hunch that "IEC Monitor In" is simply feeding the spdif signal back through the analog for recording purposes.

There must be a way to set this up, or am I expecting too much?

---

### Post by fatmonk on 2009-01-30
I'm with you on this one Uncle Hammy (in fact I posted the question a few weeks ago and got no replies AFAIR).

What I noticed was with my standard ALSA install and ALSA:SPDIF selected in the general setup screens, I get digital including ac3 passed through, but no analogue at all EXCEPT in streaming content.

If I go into MythStream I get BOTH digital audio out AND analogue audio out.

These are just Stereo streams, so it is exactly what I want within MythTV live TV, TV recordings and MythVideo.

So it must be possible within the realms of ALSA and even in a standard ALSA setup, my guess is its something internal within MythTV itseld that the MythStream developers managed to get right.

-FM

---

### Post by uncle hammy on 2009-01-31
Yours is easy, I think.  If I uncheck both "passthrough" options in the general settings, then I get sound out of both my tv and stereo.  It's only 2 channel coming out of the stereo though.

I am looking to get the full Dolby digital 5.1 out of the stereo, and 2 channel analog out of my tv.

---

### Post by fatmonk on 2009-02-04
I'm actually looking for exactly the same thing as you, Uncle Hammy.

As I say, everything works in MythStream (digital stereo to my AV Amp, and analogue stereo to the TV).

Playing DVDs gets me 5.1 to my AV amp, but nothing to my TV.

Watching TV or recordings getsme digital stereo to my AV amp, but nothing to my TV.

-FM

---

