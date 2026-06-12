---
title: "Sound form MPD disappears if I change the volume"
date: 2018-08-21
forum: Multimedia Software
---

### Post by marek-campus on 2018-08-21
Hi,

I'm using MPD and Cantata for music on my desktop machine, and want the mpd visible to network clients so that I can control it from my phone. It all works save for a odd behaviour with volume. This is probably a pulse audio configuration issue, I suspect.

Key MPD configuration options:
- music_directory is set to a subfolder of /home/
- mpd user is "mpd"
- bind_to_address is "localhost"
- port is 6600
- output is :
audio_output {
        type            "pulse"
        name           "MPD_Pulse"
}

When I open cantata and hit "play" I get sound, and I can change the volume of the music *within* the application. However, if I use the media volume control keys on my keyboard, or the volume widget in the panel (I'm running plasma as my desktop), the music is muted, though the song keeps playing and the in-application volume indicator isn't affected.

I've tried a number of different wikis on mpd configuration, but nothing I've tried so far seems to help much.

Appreciate any pointers.

---

### Post by marek-campus on 2018-08-22
Got things working by taking a different approach. 

Using the daemon basically wasn't working - couldn't get it working with pulse properly.

Purged everything, started afresh following the mpd parts of this tutorial: [https://ubuntu-mate.community/t/how-to-install-and-setup-mpd-mpdscribble-ncmpcpp/8439](https://ubuntu-mate.community/t/how-to-install-and-setup-mpd-mpdscribble-ncmpcpp/8439)

Once mpd was configured, cantata took no effort. End result - working cantata with pulse audio, and remote control through M.A.L.P. available through my phone - hurray!

---

