---
title: "hda_intel, 1/2 second sound lag EXCEPT in Quake 4"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by KrakensDen on 2006-08-25
Moin, I use the snd_hda_intel driver. In all applications, mplayer, vlc, Totem, Tremulous, there is a half-second or less lag between when the sound is supposed to happen and when it does. As you can imagine, this is fairly distracting when watching movies or trying to shoot aliens ;).

There is, however, an interesting exception to this. Quake 4 plays all sounds when they are supposed to be played. This perplexes me. According to its logs, it uses ALSA just like everything else that's laggy.

The canonical solution for slow sound,
```

echo "tremulous 0 0 direct" > /proc/asound/card0/pcm0p/oss

```

DOES NOT work. And yes, the output is

```

$cat oss
tremulous 0 0 direct

```

lspci output:
```

0000:00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```

Another interesting bit of information about this particular soundcard is that no one seems to be able to get it to its full volume. If anyone has any ideas, please post :).

---

### Post by KrakensDen on 2006-08-25
Well, I finally got it working. The problem seems to be that the default period size is too large. For future reference:

```

pcm.hda-intel {
   type hw
   card 0
}

ctl.hda-intel {
   type hw
   card 0
}

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024 	# The magic number
buffer_size 8192	# If it's lower you get skipping

rate 48000
}
bindings {
0 0
1 1
}
}

```

---

