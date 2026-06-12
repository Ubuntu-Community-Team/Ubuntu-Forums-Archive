---
title: "Stereo, 5.1: finally... again"
date: 2024-11-15
forum: Multimedia Software
---

### Post by leodp on 2024-11-15
Hi, 
quick report on my audio adventures.
I have an old audio amplifier with analog clinches and optical S/PDIF connection. No HDMI. 
An Ubuntu machine and 5.1 speaker system are attached.

5.1 audio has always been a hassle, but found a way of having it working, 'till some years ago, when Ubuntu changed something in the sound architecture, alsa, pulseaudio, now pipewire.
'Till Ubuntu 24.04 I was unable/unwilling to move from a situation where there was only stereo output.

Now, with Ubuntu 24.10, I have 5.1 working again. 
Sharing it here in case somebody is in the same situation.

**Problem**: stereo (i.e. Youtube) has stereo output and does not upmix to 5.1
--> create a .conf file (e.g. 40-upmix.conf) in 
~/.config/pipewire/client.conf.d/ with this content:

```
# Enables upmixing
stream.properties = {
    channelmix.upmix      = true
    channelmix.upmix-method = psd
    channelmix.lfe-cutoff = 150
    channelmix.fc-cutoff  = 12000
    channelmix.rear-delay = 12.0
}

```

from [gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Guide-Upmixing]("https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Guide-Upmixing")


then restart pipeaudio:
```
systemctl --user restart pipewire.service
systemctl --user restart pipewire-pulse.service

```(not sure if both are necessary. Reboot works also)
from [URL="https://www.reddit.com/r/pop_os/comments/v3g2w9/is_there_a_cli_command_to_restart_pipewire/"]
cli_command_to_restart_pipewire/[/URL]



Then from "audio" utility you can rebalance front<->back with:
Back <- Fade  -> Front
or in alternative from "pavucontrol" (install it):
Output_devices -> press unlock
--> change every single channel amplification

As output device I used the analog clinches.
If I select the 5.1 Spdif digital IEC958/AC3 then I am not able to rebalance front/back fade, which I need in my setup and may be necessary for stereo sources.

**Question**: is it due to the passthrough of encoded audio or can it be changed with, say, a config file?
**Question2**: Why Does Ubuntu, which has a certain focus on ease-of-use, decide to leave muted some speakers in users' setups in case of, say, stereo source? Wouldn't it be more "default" to upmix sources that do not comply with the output system? I'm not focusing on the negative side of the question here, I'm sincerely interested on what are the reasons behind this decision.

Thanks & have a nice weekend.

---

### Post by TheFu on 2024-11-15
I can only guess that people want the input audio accurately reproduced in the output speakers. If it is stereo, then the output should be stereo. If it is 5.1, then the output should be 5.1.  In this way, they have a leg to stand on when someone wants something different for their personal taste.  

Being inaccurate is an abomination, after all, especially when it comes to audiophiles. 

I do have to wonder if your modification doesn't screw 5.1 audio output. Does it? You can use some test files found online for testing.  I use these:
```
AAC_5.1.mp4  Dolby_Atmos_E-AC-3_5.1.2.mp4  Dolby_Digital_AC-3_5.1.mp4  DTS_5.1.wav  FLAC_5.1.flac
``` They are each about 45 seconds and can be used to help tune outputs for your different speaker locations.  For example, my left channel is softer than I'd like, even though that speaker is closer to my ears.

But it is also great that you have a way to get the audio output you prefer.

---

### Post by leodp on 2024-11-15
Yes, inaccuracy is abomination.
And a distro with a reach makes a sin against its own principles if it supposes that everybody will be a configuration expert on systems that are chained together in a complex way that changes across releases & different distributions.
Anyhow, I close it here.

The modification does not seem to change the 5.1 output, I tested it already with various 5.1 audio test files.
Thansk, Leo

---

### Post by Yellow Pasque on 2024-11-15
> Why Does Ubuntu, which has a certain focus on ease-of-use, decide to leave muted some speakers in users' setups in case of, say, stereo source? 
Because that's a sane default. It would be nice if Linux had more audio options configurable in a GUI, but that's a general Linux problem, not specific to Ubuntu.

> I'm sincerely interested on what are the reasons behind this decision.
Again, I doubt Ubuntu made any discussion/decision on this. They probably just use whatever pipewire/wireplumber does.

> Wouldn't it be more "default" to upmix sources that do not comply with the output system?
No. Not to me.

---

