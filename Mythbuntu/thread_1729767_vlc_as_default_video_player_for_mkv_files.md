---
title: "vlc as default video player for mkv files"
date: 2011-04-15
forum: Mythbuntu
---

### Post by ian dobson on 2011-04-15
Hi,

I have several "troublesome" mkv files that don't play very well with the mythtv video player or mplayer (both using vdpau). The mkv's play OK with vlc on one of my windows PC's, so it there a way to hez mythtv to use vlc in full screen, no user interface etc.

I've tried editing the default player option but vlc only starts in a window and doesn't load the correct video file and my ir remote doesn't work.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-04-16
Hi,

OK I've found that it's easier to create a simple script that calls vlc with the correct parameters and tell mythtv to use this script.

```
#!/bin/sh

CMD="/usr/bin/vlc --spdif --no-video-title-show -f --video --mouse-hide-timeout 500  --extraintf lirc"

echo $CMD "$@" vlc:quit
exec $CMD "$@" vlc:quit

```

And in mythtv I just set the default play to "mythvlc.sh  file://%s". It's almost working, some keys in LIRC work, audio output over HDMI works, but vlc still shows a menu and I haven't found out how I can select the audio track (Language).

Regards
Ian Dobson

---

### Post by 4romany on 2011-04-17
Ian, how does VLC does as far as off-loading x264 movies to the Nvidia card (aka vdpau)?  I've been pretty happy with mplayer but I would like to look at VLC.  Being able to bring up the dialog feature is a must though...

---

### Post by ian dobson on 2011-04-17
Hi,

vlc doesn't use vdpau. Which is a good idea for me as all vdpau based players that I've used on ubuntu show exactly the same problems at exactly the same point in the videos.

vlc uses about 50-70% cpu (Core2Duo 2500GHz) when playing back a very large mkv file (10Gb/Hr).

Regards
Ian Dobson

---

### Post by ian dobson on 2011-04-20
Hi,

OK I've now got the script up and running (OK I'm not using storage groups). The key mapping in lirc isn't the same for mythtv and vlc but that's a small problem that I'll need to solve in lirc.

Here's the script

```

#!/bin/sh

CMD="/usr/bin/vlc --spdif --no-video-title-show --aout-rate=48000 -f --video --mouse-hide-timeout 500 --intf dummy --extraintf lirc --audio-language=en,eng,de,deu"

echo $CMD "$@" vlc:quit
exec $CMD "$@" vlc:quit

```

and Just set the default player to mythvlc.sh file://%s

Hope this helps someone.

Regards
Ian Dobson

---

### Post by nickrout on 2011-04-20
Have you tried increasing vdpaubuffersize? it did the trick for me.

---

### Post by ian dobson on 2011-04-21
Yep.

vlc seems to be able to play anything I throw at it without any need for tweaking, and I'd rather be watching my mkv's than playing with my computer.

Regards
Ian Dobson

---

### Post by nickrout on 2011-04-21
> **ian dobson said:**
> Yep.

vlc seems to be able to play anything I throw at it without any need for tweaking, and I'd rather be watching my mkv's than playing with my computer.

Regards
Ian Dobson

you need to post samples of the files for the myth devs to fix whatever is wrong. if people don't alert the devs, there is nothing they can or will do to fix it.

---

### Post by ian dobson on 2011-04-21
> **nickrout said:**
> you need to post samples of the files for the myth devs to fix whatever is wrong. if people don't alert the devs, there is nothing they can or will do to fix it.

OK, when I find a sample that I can post without getting in trouble, I'll post a link to it.

Regards
Iam Dobson

---

