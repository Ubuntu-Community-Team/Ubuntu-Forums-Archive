---
title: "Sound on PC speakers, no sound on TV"
date: 2010-10-20
forum: Multimedia Software
---

### Post by chmmr on 2010-10-20
Before I upgraded to 10.10, I would hear sound on both my PC speakers and on my TV.

The speakers are connected via the standard speaker out, the TV was connected via the line-out, through a stereo to RCA adapter.  Video is supplied to the TV via HDMI.

Now that I've upgraded to Maverick, however, I no longer get sound on the TV.  This isn't the usual "sound stopped working completely on upgrade" issue, because I get flawless sound via the PC speakers just as before.  I've tried most of the debugging steps recommended in other threads about audio, with no improvement.

The weird thing about all this is, **when I plug other speakers or headphones into the same port, I hear audio.**

So I'm starting to suspect that the problem has to do with the HDMI audio out capability on my video card (an nvidia GT 240), which might have suddenly come alive (if not fully functional) with Maverick's new version of ALSA.  I don't know what signal(s) my TV thinks it's getting and have no way of troubleshooting things on that side, but it seems possible that the HDMI it's getting video through is also sending a null/silent audio stream, and that stomps the analog audio signal it's getting from my sound card.

I see two output devices in Sound Preferences, "Internal Audio" and "High Definition Audio Controller".  "Internal Audio", ie my onboard sound, is what's producing audio via the speakers.  HDMI has never produced any audio, and I don't really need it to if I can just make it work the way it did before.  I've tried completely disabling that device, even adding the "snd_hda_codec_nvhdmi" module to /etc/modprobe.d/blacklist - no change.

The solution for this could be one of two things: one, I could try to get the HDMI audio out working and let that be what my TV receives, two I try to make the audio setup work as before, with analog audio going to both speakers and TV.

Thoughts?  I'm leaning towards the latter, ie not bothering with the HDMI audio, as having another audio source would probably mean messing with PulseAudio which has otherwise worked 100% fine for me up until now.  If need be I can supply more details on hardware, CLI output etc.

For what it's worth, the line-out analog audio has *never* worked on my windows XP partition.

---

### Post by chmmr on 2010-10-24
My workaround (not fix!) for this, on the off chance someone else is having this exact problem:

I used a DVI cable, which doesn't carry an audio stream, to connect my video card to my TV, along with the analog audio, and used HDMI for the PC monitor.  At this point, the TV got sound.

HDMI audio out didn't work after trying a few of troubleshooting steps on these forums.  It did however work in winXP with an nvidia driver update.  So hopefully in a future (>10.10) version of Ubuntu (with new kernel/ALSA/nvidia driver) the HDMI audio will "just work" with the additional source.

---

### Post by chmmr on 2010-10-30
Documenting for the benefit of future searchers...

So the "switch DVI/HDMI outputs" workaround had other drawbacks.  I ended up disabling the use of EDID from xorg.conf, and specifying a custom modeline for the TV.  I now get sound on both outputs, because the TV isn't telling the video card things that make it send the empty audio signal.

There is another solution that involves hex-editing an EDID.bin file extracted from your monitor by nvidia-settings, but that seemed more risky to me so I went with the previous solution.

This was a giant pain, not an Ubuntu or even a Linux problem, so I'm going to implore Nvidia to do something about it - namely, give an option to easily disable HDMI audio (as I can think of several other situations besides mine a user would want to do that), if only from xorg.conf.

Threads that helped me scrape together this info and come up with the better workaround:

[http://support-us.samsung.com/cyber/popup/iframe/pop_troubleshooting_fr.jsp?idx=51469&modelname=LN-T4671F&modelcode=&session_id=MGTvDhZQWLGxGkGv2GdpT0v6VF5r0hqWhht4RK09F248GzZvcnG1!2061370641!1761676348!7501!-1!1573112582!1761676444!7501!-1!1287933487839](http://support-us.samsung.com/cyber/popup/iframe/pop_troubleshooting_fr.jsp?idx=51469&modelname=LN-T4671F&modelcode=&session_id=MGTvDhZQWLGxGkGv2GdpT0v6VF5r0hqWhht4RK09F248GzZvcnG1!2061370641!1761676348!7501!-1!1573112582!1761676444!7501!-1!1287933487839) - the Samsung support entry - they tell you to bug your video card maker
[http://www.nvnews.net/vbulletin/showthread.php?t=119446](http://www.nvnews.net/vbulletin/showthread.php?t=119446) - this person had almost my exact problem
[http://www.nvnews.net/vbulletin/showthread.php?t=121161](http://www.nvnews.net/vbulletin/showthread.php?t=121161) - same here
[http://mysettopbox.tv/phpBB2/viewtopic.php?t=20857&sid=251fae445671271659b8d405686ac60a](http://mysettopbox.tv/phpBB2/viewtopic.php?t=20857&sid=251fae445671271659b8d405686ac60a) - this person did too, but he/she figured out you could disable EDID and specify a custom modeline
[http://ubuntuforums.org/showthread.php?t=1003099&highlight=modelines&page=2](http://ubuntuforums.org/showthread.php?t=1003099&highlight=modelines&page=2) - how to find the right modeline to use
[http://blog.mymediasystem.net/my-media-system/solved-no-sound-via-stereo-jack-with-philips-lcd-tv/](http://blog.mymediasystem.net/my-media-system/solved-no-sound-via-stereo-jack-with-philips-lcd-tv/) - documentation of alternate, hex edit EDID solution

---

