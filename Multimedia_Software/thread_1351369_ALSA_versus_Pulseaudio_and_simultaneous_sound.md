---
title: "ALSA versus Pulseaudio and simultaneous sound"
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

### Post by l-x-l on 2009-12-10
Sound is the only consistent issue I've had with 9.10. 

```
Following the steps stopped the sound fading out but now I have a problem playing sound in simultaneous apps. To allow sound in Firefox and VLC at the same time I had to manually change the latter's Tools >> Preferences >> Audio >> Output >> Type - from Default to ALSA audio output.
```

This hack helps with VLC & FF/Chrome. But unfortunately Totem doesn't have the ability to select.

---

### Post by VertexPusher on 2009-12-11
> **laeg_ said:**
> I was unable to complete step 3 by selecting ALSA in *System >> Preferences >> Sound* because there's no option for it in any of the tabs or on the drop down menu
That's because the instructions refer to Ubuntu 9.04, not 9.10. The old configuration panel and the old mixer applet are gone. They have been replaced with a tool that is unable to configure any ALSA-related properties. Furthermore, the asoundconf tool to select the default sound card has been removed, too. It seems that the developers' goal is to cripple ALSA as much as possible to make PulseAudio look good in comparison. Of course this doesn't magically fix any of PulseAudio's bugs.

However, it's still possible to remove PulseAudio from Ubuntu 9.10 and make sound work as it should. All you need to do is install some packages from the repository and remove some others.

These are the packages that need to be installed:

gstreamer0.10-alsa
gnome-alsamixer

These are the packages that need to be removed:

gstreamer0.10-pulseaudio
vlc-plugin-pulse
pulseaudio

This solution has been confirmed to work on a vanilla install of Ubuntu 9.10. See if it works for you. If it doesn't, you can easily revert the changes and continue waiting for PulseAudio fixes.

---

### Post by laeg_ on 2009-12-11
> **VertexPusher said:**
> 
These are the packages that need to be installed:

gstreamer0.10-alsa
gnome-alsamixer

These are the packages that need to be removed:

gstreamer0.10-pulseaudio
vlc-plugin-pulse
pulseaudio

Thank you very much, that worked just fine although I did have to set Audacious2 to use ALSA instead of Pulseaudio which it must have autoconfigured itself to. That said I didn't have to do the same for Exaile Music Player, probably because I'd never used it before?

---

### Post by VertexPusher on 2009-12-12
> **laeg_ said:**
> I did have to set Audacious2 to use ALSA instead of Pulseaudio which it must have autoconfigured itself to. That said I didn't have to do the same for Exaile Music Player, probably because I'd never used it before?
Each application seems to handle this in a different way. For example, GStreamer-based applications share a common tool (gstreamer-properties) to configure audio input and output. Others (Avidemux, Skype, Pidgin ...) have their own control panels to do that. But they all support ALSA because that is the only sound system guaranteed to be available across all Linux distributions.

---

### Post by yester64 on 2009-12-12
> **VertexPusher said:**
> That's because the instructions refer to Ubuntu 9.04, not 9.10. The old configuration panel and the old mixer applet are gone. They have been replaced with a tool that is unable to configure any ALSA-related properties. Furthermore, the asoundconf tool to select the default sound card has been removed, too. It seems that the developers' goal is to cripple ALSA as much as possible to make PulseAudio look good in comparison. Of course this doesn't magically fix any of PulseAudio's bugs.

However, it's still possible to remove PulseAudio from Ubuntu 9.10 and make sound work as it should. All you need to do is install some packages from the repository and remove some others.

These are the packages that need to be installed:

gstreamer0.10-alsa
gnome-alsamixer

These are the packages that need to be removed:

gstreamer0.10-pulseaudio
vlc-plugin-pulse
pulseaudio

This solution has been confirmed to work on a vanilla install of Ubuntu 9.10. See if it works for you. If it doesn't, you can easily revert the changes and continue waiting for PulseAudio fixes.

If i select gstreamer0.10-pulseaudio for removal, the system wants to remove ubuntu-desktop. why is that?
I have 9.10 64 running and try to get the sound working with wine/crossover. None of the games work due pulseaudio. so annoying.:(

---

### Post by VertexPusher on 2009-12-13
> **yester64 said:**
> If i select gstreamer0.10-pulseaudio for removal, the system wants to remove ubuntu-desktop. why is that?
It's because ubuntu-desktop is an empty package that depends on all the packages that make up the default Ubuntu desktop. As soon as you remove one of those packages, ubuntu-desktop has to go, too.

This is useful because if you ever want to restore the default setup, all you need to do is install ubuntu-desktop again. This will pull back in any other packages that you have removed.

---

### Post by bakinsoda on 2010-09-25
I uninstalled PulseAudio in my Ubuntu 10.04 and indeed I get simultaneous sound.  However, whenever ubuntu starts up I no longer have the sound applet in the taskbar.  Clicking Sound in System > Preferences, I get the error "Waiting for Sound System to respond."  Googling this I find suggestions of removing ~/.pulse and reinstalling Pulse Audio.  .pulse gets created everytime I start the system.  I also tried unchecking Pulse Audio in "Startup Applications."

Anyone get this issue?  Any way to resolve?

---

