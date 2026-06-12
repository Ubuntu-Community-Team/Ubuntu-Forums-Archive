---
title: "Banshee/Rhythmbox Stop Playback Intermittently In 12.04"
date: 2012-04-28
forum: Multimedia Software
---

### Post by linux4me on 2012-04-28
I did an upgrade of 11.10 to 12.04 Beta 2 using the Alternate CD as soon as Beta 2 came out. The upgrade went smoothly, but I noticed that Rhythmbox would intermittently stop playback of a playlist of FLAC songs that I had imported from a Banshee playlist.

I installed Banshee, which I had used with the same playlist in 11.10 without any problems, and it too stopped playback intermittently.

In syslog, I see:
```
pulseaudio[1889]: [alsa-sink] protocol-native.c: Failed to push data into queue
```

With Rhythmbox, clicking on the progress indicator slider restarts playback, but it may stop again at the beginning of the next song or continue playing for some time before again stopping. The song files themselves appear to be fine because I can play them individually. 

There are a few different bugs reported on Launchpad regarding similar issues, including [this one]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/978604") that seems the most like what I'm encountering.

One person in that thread confirms the bug in a clean install.

I would think there would be a lot more people reporting problems if it weren't something particular to my install and the few other people reporting the issue, either in something that came along with the upgrade or in my home directory.

Sound is working fine in other respects. My installation of 12.04 is up-to-date now since the final release, but the problem persists.

I'm posting here to see if there are others experiencing this, and hopefully, to see if there is a fix.

TIA

---

### Post by jongkind on 2012-04-28
Same problem and same error message in Debian Wheezy.

I moved to Clementine as music player, which works like a charm.

grtz, Herman

---

### Post by linux4me on 2012-04-28
I hate to abandon Rhythmbox if it's going to be the default player in 12.04, but that's good information that Clementine works. If I start to get too crazy from Rhythmbox cutting out it will be worth a try.

---

### Post by kostkon on 2012-04-28
Try running rhythmbox in debug mode and see if you'll get anything useful. Just save the output in a file for easier inspection, i.e.
```
rhythmbox -d > ~/Desktop/rhythmbox_output.txt
```

---

### Post by linux4me on 2012-04-29
I'll give it a try.

---

### Post by linux4me on 2012-04-29
I tried running Rhythmbox in debug mode with the output to a file and didn't get anything at all when Rhythmbox spontaneously stopped playback, but when I shut down Rhythmbox I got the following:
> found device path /dev/sda1 for mount /boot
device /dev/sda1 has no ID_MEDIA_PLAYER tag in udev
/boot is already a mount point
override file /boot/.is_audio_player not found on mount /boot

I did install Clementine and it does work without any playback interruptions using the imported playlists from Rhythmbox.

---

### Post by kostkon on 2012-05-03
> **linux4me said:**
> I tried running Rhythmbox in debug mode with the output to a file and didn't get anything at all when Rhythmbox spontaneously stopped playback, but when I shut down Rhythmbox I got the following:


I did install Clementine and it does work without any playback interruptions using the imported playlists from Rhythmbox.
Have you tried purging and then reinstalling Rhythmbox?

---

### Post by linux4me on 2012-05-03
Yes, that was the first thing I did. It seemed there were so few complaints about similar behavior in Launchpad that I figured some setting had followed me from an earlier version and was causing the issue; however, the purge and reinstall didn't help.

---

