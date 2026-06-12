---
title: "Multi-play problem of sound in pulseaudio"
date: 2008-12-23
forum: Multimedia Software
---

### Post by mrcrazyani on 2008-12-23
Hi, I've got some problem about between pulseaudio and soundcard, so I want to ask you how I can fix the problem.

My setting of computer is:

AMD Athlon64X2 5200+
ASUS M3A/H HDMI
2G DDR SDRAM
ATI 3870
MAYA 5.1 MK-II(Soundcard)

First, I didn't hear any sound in ubuntu, so I set all sound settings "ICEnsemble ICE1724 IEC1724 IEC958 (ALSA)" at "System - Preference - Sound, then problem occured.

My first problem is that I can't hear any sound in Youtube, and second is that I can hear only one sound of an application. For example, if I hear music in with rythembox, then I can't hear any sound with other application.

So I found solution first: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

But I couldn't fix the problem.

I found that my problem correspond to:

> The application does plays audio and does not list an entry in the Playback tab;
- the application is either accessing your sound card directly or playing sound via ALSA's dmix device. This will prevent PulseAudio from working correctly & cause audio mixing errors.

and

> The application does not play audio and does list an entry in the Playback tab;
- the application is using PulseAudio but there is a problem, such as: a bug in PulseAudio, a problem with your ALSA kernel module or libraries, or your PCM/Master volume is muted.

First, If I set all settings of sound to ICEnsemble ICE1724 IEC1724 IEC958(ALSA), an application plays sound, but does not list an entry in the playback tab. Second, If I set all settings of sound to Autodetect, it does list an ectry in the playback tab, but I can't hear any sound.

So I checked all process, and I found it : $ alsamixer -Dhw

If I type that in terminal, then "HDA ATI HDMI" occurs. It is device of ASUS M3A/H HDMI, motherboard. I killed sound device of motherboard at Bios setting, but my default setting of sound device is "HDA ATI HDMI".

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97415&stc=1&d=1230089006[/IMG]

I don't know how to change the setting. And I can't confirm and fix contents of /proc/asound/. If I try, then I see only this :

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97416&stc=1&d=1230089249[/IMG]

How can I fix this problem?

---

### Post by 2hot6ft2 on 2008-12-23
Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

There are more but this gives you some alternatives that are being used.

---

