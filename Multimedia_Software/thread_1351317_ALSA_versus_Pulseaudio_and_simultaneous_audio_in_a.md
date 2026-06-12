---
title: "ALSA versus Pulseaudio and simultaneous audio in apps"
date: 2009-12-10
forum: Multimedia Software
---

### Post by laeg_ on 2009-12-10
Since upgrading to 9.10 I have had a lot of problems with sound but now they seem all but resolved.

Initially sound on all media, flash, mp3, video etc was gradually fading out completely over 20 or 30 seconds until there was none whatsoever.

I fixed this by following these instructions:

> I think this issue is linked to the following bug:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/279478](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/279478)

The following comment seems to confirm this:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/279478/comments/45](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/279478/comments/45)

Please try this workaround procedure for the sound fading issue:

1. copy-paste the following command into the Terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

2. In gedit editor, scroll down and add these lines to the end of the */etc/modprobe.d/alsa-base.conf* file:

```
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=3stack
```

3. Then navigate to System>Preferences>Sound and change everything to ALSA

4. copy-paste the following command into the Terminal:

```
gksudo gedit /etc/group
```

5. replace the following line (or something very similar to it):

```
audio:x:29:pulse
```

with this line:

```
audio:x:29:laeg,pulse
```

6. reboot and retest sound

7. In the Mixer control panel, make sure to unmute all channels and increase the volume on all channels, including Master, PCM and Center.

If relevant even though I have ALSA selected in *gstreamer-properties* I was unable to complete step 3 by selecting ALSA in *System >> Preferences >> Sound* because there's no option for it in any of the tabs or on the drop down menu - please see screenshots below:

[IMG]http://i49.tinypic.com/2q06bf7.jpg[/IMG]
[IMG]http://i47.tinypic.com/24yy3is.jpg[/IMG]
[IMG]http://i49.tinypic.com/2nkp8qd.jpg[/IMG]

Following the steps stopped the sound fading out but now I have a problem playing sound in simultaneous apps. To allow sound in Firefox and VLC at the same time I had to manually change the latter's *Tools >> Preferences >> Audio >> Output >> Type* - from Default to ALSA audio output.

Do I have to configure every app that uses sound in this way? I used not to on 9.04.

Why doesn't the default just work, whether it's Pulseaudio or ALSA and how do I check that?

I plan to install WINE again soon and I know that sometimes there are issues with this and Pulseaudio so should I remove it?

---

