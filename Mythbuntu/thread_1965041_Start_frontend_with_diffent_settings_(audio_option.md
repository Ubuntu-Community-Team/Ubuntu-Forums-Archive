---
title: "Start frontend with diffent settings (audio options)"
date: 2012-04-25
forum: Mythbuntu
---

### Post by iitywygms on 2012-04-25
Hi all.
Running mythbunt .24 with the latest fixes.
video is gt430 
audio spdif is on the motherboard.

I have asked on the mailing list and other places if it is possible to have digital audio piped to both hdmi and spdif.  It is not currently possible without giving up passthrough.
So.
I would like to be able to start the frontend with different audio settings.
One would be set up to use spdif for sound. (to my stereo)

The other would send the audio straight to my tv via hdmi.

I am thinking I could use a script or something, but have no idea how to do that, or if it is even possible.

Any ideas?
Thanks.

---

### Post by iitywygms on 2012-04-29
No way??

---

### Post by nickrout on 2012-04-29
> **iitywygms said:**
> No way??

The best way would be to have a script that runs a mysql query to change the audio ouput device, then launch mythfrontend. eg

```
#!/bin/sh
mysql -h machinewherebackendislocated -u mythtv -p password mythconverg -e "UPDATE settings SET data='ALSA:HDMI' WHERE hostname=Nameofmythmachine AND value=AudioOutputDevice"
mythfrontend &
exit 0

```

then another that sets it to the device for spdif, then starts mythfrontend.

Start via whichever script you want for your particular session.

---

### Post by jyavenard on 2012-04-30
> **nickrout said:**
> The best way would be to have a script that runs a mysql query to change the audio ouput device, then launch mythfrontend. eg

```
#!/bin/sh
mysql -h machinewherebackendislocated -u mythtv -p password mythconverg -e "UPDATE settings SET data='ALSA:HDMI' WHERE hostname=Nameofmythmachine AND value=AudioOutputDevice"
mythfrontend &
exit 0

```


What a complicated and convoluted way. It's certainly not required to do any mysql stuff.

Go into mythfrontend and select the hdmi audio card, configure it with all the options you need: AC3, DTS, E-AC3, TruHD, upmix etc...

so start mythfrontend with the default options, give you hdmi.

For stereo playback, start mythfrontend with:
mythfrontend -O AudioOutputDevice=ALSA:default -O MaxChannels=2 -O AC3PassThru=0 -O DTSPassThru=0

That's assuming the device you want to use otherwise is ALSA:default

note that if you select a device like PulseAudio: , ALSA:pulse, or any alsa device that would otherwise be detected as analog (so all digital features are greyed out when selected), then you can simply start mythfrontend with:
mythfrontend -O AudioOutputDevice=ALSA:pulse -O MaxChannels=2

no need to override the digital settings.

---

### Post by nickrout on 2012-04-30
> **jyavenard said:**
> What a complicated and convoluted way. It's certainly not required to do any mysql stuff.

Go into mythfrontend and select the hdmi audio card, configure it with all the options you need: AC3, DTS, E-AC3, TruHD, upmix etc...

so start mythfrontend with the default options, give you hdmi.

For stereo playback, start mythfrontend with:
mythfrontend -O AudioOutputDevice=ALSA:default -O MaxChannels=2 -O AC3PassThru=0 -O DTSPassThru=0

That's assuming the device you want to use otherwise is ALSA:default

note that if you select a device like PulseAudio: , ALSA:pulse, or any alsa device that would otherwise be detected as analog (so all digital features are greyed out when selected), then you can simply start mythfrontend with:
mythfrontend -O AudioOutputDevice=ALSA:pulse -O MaxChannels=2

no need to override the digital settings.

Excellent I didn't know you could do all that from the command line -O stuff.

---

### Post by iitywygms on 2012-05-02
> **jyavenard said:**
> What a complicated and convoluted way. It's certainly not required to do any mysql stuff.

Go into mythfrontend and select the hdmi audio card, configure it with all the options you need: AC3, DTS, E-AC3, TruHD, upmix etc...

so start mythfrontend with the default options, give you hdmi.

For stereo playback, start mythfrontend with:
mythfrontend -O AudioOutputDevice=ALSA:default -O MaxChannels=2 -O AC3PassThru=0 -O DTSPassThru=0

That's assuming the device you want to use otherwise is ALSA:default

note that if you select a device like PulseAudio: , ALSA:pulse, or any alsa device that would otherwise be detected as analog (so all digital features are greyed out when selected), then you can simply start mythfrontend with:
mythfrontend -O AudioOutputDevice=ALSA:pulse -O MaxChannels=2

no need to override the digital settings.


This is fantastic news.  I will give this a try when I can.  
Thank you for the help.

---

### Post by anonymousdog on 2012-05-03
Totally different suggestion: is there digital passthrough on your TV?  If so, you can use HDMI from MythTV frontend to TV which pipes output to A/V system over SPDIF.  This works well for me on one of our frontends.

---

### Post by nickrout on 2012-05-03
> **anonymousdog said:**
> Totally different suggestion: is there digital passthrough on your TV?  If so, you can use HDMI from MythTV frontend to TV which pipes output to A/V system over SPDIF.  This works well for me on one of our frontends.

very dependent on how your TV implements this and what exactly it passes through.

---

### Post by anonymousdog on 2012-05-03
> **nickrout said:**
> very dependent on how your TV implements this and what exactly it passes through.
Yes, but if the TV doesn't alter the signal, it's simple, elegant, and trouble free.

---

### Post by nickrout on 2012-05-03
> **anonymousdog said:**
> Yes, but if the TV doesn't alter the signal, it's simple, elegant, and trouble free.

But most do alter it, Sony for example omy sends stero out the spdif port.

---

