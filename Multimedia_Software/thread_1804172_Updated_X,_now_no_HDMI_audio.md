---
title: "Updated X, now no HDMI audio"
date: 2011-07-14
forum: Multimedia Software
---

### Post by Coogan on 2011-07-14
Ran apt-get last night on my nVidia ION media center (running XBMC).  Apt showed several updates to various X packages, all updated successfully.  I shut the system down for the night.

Started it up this morning, and the resolution has been bolluxed, down to 640x480, but I can easily fix that later; XBMC still ran fine.  Loaded up a cartoon for my toddler to watch, and found the audio was not working.  Checked the settings in XBMC and nothing had changed.  The little guy was getting antsy so I sent him upstairs to watch cartoons while I did some basic checks.  Logged into my profile, went to Sound, and after some checking, found that none of the audio devices output any sound.  I loaded up alsamixer and verified that none of the sound cards had been muted.

I'm pretty sure this is a fairly easy fix, but I'm not sure where to start.  Aplay -l and lspci -v are normal; nothing has changed from before the update.  I'm not sure if the snd-hda-intel module got unloaded, or if maybe an X configuration file got reset to default, or what.

What are a few things I can check?

Coog

---

### Post by Coogan on 2011-07-14
Anything?  I got the resolution fixed, but the audio problem persists.  It was working fine before the update.

Here's the alsa info:

[http://www.alsa-project.org/db/?f=4bcc3755549257b802f2788d8b81b3ad53b0a051]("http://www.alsa-project.org/db/?f=4bcc3755549257b802f2788d8b81b3ad53b0a051")

Coog

---

### Post by Coogan on 2011-07-14
Well I know the audio to the headphone jack work.  I'm close to getting it working, but I'm not sure what to check next.

Coog

---

