---
title: "HOWTO: VIA 8237 SPDIF output"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by Phophos on 2007-01-31
Hi all,

Up until about 30 minutes ago I couldn't get the SPDIF on my VIA 8237 chip to work at all. Well, I think I've worked it out.

I'm not a technical Linux user, just a desktop user, so if there are issues with this, don't shoot me. This is how I got the thing to work.

I've noticed there are a few similar problems to this, so I'll outline what I did. If this is in the wrong place, please could a moderator shift it.

Firstly, you have to make sure the soundcard is installed. Just check on your normal volume control that it's selected as the device, then in an application check something is playing. I used ubuntu_sax.ogg running in loop in the background.

[LIST=1]
[*]Make sure alsamixer is installed
[*]Enter a terminal and type alsamixer
[*]Check that IEC958 is not muted. Sometimes it is!
[*]Change the IEC958 Playback Source to Analog1
[*]Alter the volume settings using VIA DXS 2 (none of the others make a difference) and PCM.
[*]Voila! Perfect sound!
[/LIST]

I hope that helps somebody. It sure helped me.

---

### Post by loswr86 on 2007-03-01
> **Phophos said:**
> 
[*]Change the IEC958 Playback Source to Analog1


How?

---

### Post by Phophos on 2007-03-16
Use the left/right arrows to scroll to IEC958 Playback Source, and the up/down arrows to scroll through the list of available sources.

I must say on reviewing this thread that this was a highly unsatisfactory solution to the issue. The sound quality is appalling on my SPuDIFf system (beefy Yamaha home entertainment system). 

Once I solved the issue by following this method, then one day proper sound started working again...I did nothing to it except try switching back to PCM on the IEC95 Playback Source. 

After this I reverted back from Edgy 64 to Dapper 32 to resolve RT61 issues. It stopped working again, so I solved it once more by compiling from the ALSA website's source and binaries. Then something broke it again, by which time I was fed up and decided to apt-get dist-upgrade to Edgy 32, which miraculously worked.

So there you go. This is okay as a quick fix solution, but for decent quality sound, compile from source! Or don't use SPDIF...

---

