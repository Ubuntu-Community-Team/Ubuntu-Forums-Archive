---
title: "mythtv 0.22-trunk and VDPAU??"
date: 2009-08-19
forum: Mythbuntu
---

### Post by mbobak on 2009-08-19
Hi,

I'm running myth 0.22 trunk from the Mythbuntu weekly builds on Ubuntu 9.04.

I was previously running myth 0.21 with VDPAU patch backported, and had no problems.

With 0.22, I can't seem to get VDPAU working. As a result, my CPU gets hit pretty hard, and when things get busy, I get some skips and dropouts, etc.

Is anyone else running 0.22 trunk? Got VDPAU working?

I created a new Video Playback profile, and all it has is:

if rez > 0 0 -> vdpau & vdpau

and, I still get no VDPAU on playback.

Any thoughts or suggestions are welcome.

Thanks,

-Mark

---

### Post by superm1 on 2009-08-19
Make sure you have a fairly current NV driver loaded with it, 185 or higher probably...

---

### Post by mbobak on 2009-08-19
Not at home now, but it's the latest NVIDIA driver, 180.44, I think.  It's whatever is current for Jaunty.  I don't think it's the 185.* series.

Whatever the driver is, it worked w/ 0.21-fixes and JAvenard's VDPAU patch.  VDPAU was running great on that.  I bumped up to 0.22-trunk, cause I hope to pick up an HD-PVR soon, but, I want to first make sure it's stable, and that I can get VDPAU working.

Thanks,

-Mark

---

### Post by mbobak on 2009-08-19
I'm at home now.  I just confirmed that my NVIDIA driver is at 180.44, which is the most up-to-date driver available in Jaunty right now.

-Mark

---

### Post by jyavenard on 2009-08-20
> **mbobak said:**
> I'm at home now.  I just confirmed that my NVIDIA driver is at 180.44, which is the most up-to-date driver available in Jaunty right now.

-Mark

running mythfrontend.real -v playback

what does it show when starting playback ?

Normally upgrading from 0.21-fixes with my backport to 0.22 with trunk requires no modification to the video profile ; it's fully compatible.

However, I've seen cases where it wouldn't be recognised. The easy fix is simply deleting the profile and recreating one.

---

### Post by mbobak on 2009-08-20
> **jyavenard said:**
> running mythfrontend.real -v playback

what does it show when starting playback ?

Normally upgrading from 0.21-fixes with my backport to 0.22 with trunk requires no modification to the video profile ; it's fully compatible.

However, I've seen cases where it wouldn't be recognised. The easy fix is simply deleting the profile and recreating one.

Hi Jean-Yves,

Actually, I should have been clearer.  For unrelated reasons, I did a complete O/S re-install between 0.21-fixes and 0.22-trunk.

So, there were no remnants of the old 0.21-fixes stuff anywhere.

I did, however, use your guidelines at:
[http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html](http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html)

to help me define the profile.  I have a 9500GT, so, as it outlined, I did:
if rez > 0 0 -> vdpau & vdpau

Any other thoughts?

Thanks,

-Mark

---

### Post by jyavenard on 2009-08-20
> **mbobak said:**
> Hi Jean-Yves,

Actually, I should have been clearer.  For unrelated reasons, I did a complete O/S re-install between 0.21-fixes and 0.22-trunk.

So, there were no remnants of the old 0.21-fixes stuff anywhere.

I did, however, use your guidelines at:
[http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html](http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html)

to help me define the profile.  I have a 9500GT, so, as it outlined, I did:
if rez > 0 0 -> vdpau & vdpau

Any other thoughts?

Thanks,

-Mark

Then post the result of mythfrontend.real -v playback when you start playback of a recording...
to see what's happening.

---

### Post by mbobak on 2009-08-21
> **jyavenard said:**
> Then post the result of mythfrontend.real -v playback when you start playback of a recording...
to see what's happening.

Will do, as soon as I get home.  Had a LUG meeting last night, got home late, forgot to do that.  I'll be sure to do it tonight!

-Mark

---

### Post by mbobak on 2009-08-22
Well, ok, either I'm an idiot, or I changed something without realizing it.  VDPAU playback seems to be fine now.....

Sorry I bothered you all.

I did notice, though, that with the default level of logging, mythfrontend shows:
2009-08-22 01:03:16.358 AFD: Opened codec 0xb461030, id(MPEG2VIDEO) type(Video)

which is what I used to see in 0.21, when VDPAU was broken.
(In 0.21, when VDPAU was working, I'd see something like "(MPEG2VDPAUVIDEO)", or something like that.

In 0.22, when running w/ '-v playback', I was able to see lots of VDPAU related log messages, but with default logging, there's no trace that VDPAU is enabled.

Also, CPU usage is way down, and playback is much smoother as a result, so I definitely have VDPAU working now, and I'm fairly certain it was not working as recently as Wednesday.

Anyhow, guess we can consider this closed, even if I don't know what actually resolved it.

Thanks,

-Mark

---

### Post by hades_wi on 2009-08-23
Hi [[COLOR=#76482C]**superm1**[/COLOR]]("http://ubuntuforums.org/member.php?u=44239"), I'd be interested to know how I can have 185 series of nvidia drivers with mythbuntu weekly builds (trunk)?

VDPAU for my video card (zotac ION) does not appear to work with the 180 series. Problem is that then I try to apt-get mythtv-frontend, it wants 180 series drivers, not 185 and hence will not install.

Wayne

---

### Post by jyavenard on 2009-08-23
> **mbobak said:**
> Well, ok, either I'm an idiot, or I changed something without realizing it.  VDPAU playback seems to be fine now.....

Sorry I bothered you all.

I did notice, though, that with the default level of logging, mythfrontend shows:
2009-08-22 01:03:16.358 AFD: Opened codec 0xb461030, id(MPEG2VIDEO) type(Video)

which is what I used to see in 0.21, when VDPAU was broken.
(In 0.21, when VDPAU was working, I'd see something like "(MPEG2VDPAUVIDEO)", or something like that.


That's how the newer ffmpeg works.
Previously, mythtv was based on an early ffmpeg patch released by nvidia. They created a different video codec for all vdpau accelerated codecs.
so MPEG2VIDEO had a corresponding MPEG2VIDEOVDPAU

The latest mythtv trunk used the official ffmpeg vdpau support, it doesn't have that distinction anymore ; all codecs have the same name (no more vdpau specific codecs)

You do get however in the log, some traces that vdpau is being used, not the same one as the 0.21 backport however where it was very clear.

---

### Post by mbobak on 2009-08-24
Thanks for the explanation, Jean-Yves.

Now that I've got 0.22 stable and VDPAU working, I'm just waiting for Dell (or someone) to discount the HD-PVR and I can say good bye to my annoying Comcast DVR.

-Mark

---

