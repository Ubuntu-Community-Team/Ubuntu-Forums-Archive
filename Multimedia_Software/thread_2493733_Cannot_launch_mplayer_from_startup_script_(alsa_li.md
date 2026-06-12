---
title: "Cannot launch mplayer from startup script (alsa lib unable to open slave)."
date: 2023-12-22
forum: Multimedia Software
---

### Post by jons50 on 2023-12-22
Hi all.

[ This is my first post, so I hope I'm not stepping on any toes or violating protocol here.  My apologies if I am. ]

I've been struggling with the following issue for over an hour, and I'm stuck.

I've created a script that launches mplayer to stream some Christmas music.  When I login as myself (user "music") and run this script, everything works fine -- mplayer is able to open the audio driver and play the stream.  Life is good.

However, when I launch the script from a startup script (/etc/init.d/), mplayer runs but complains that it cannot open the audio driver (unable to open slave).  It looks like audio programs that are launched as root are unable to open the audio driver -- I say this because if I 'sudo bash' then try to run my script or run something like "speaker-test", I get the same error.

I've modified my init script to perform an "sudo -u music <path_to_my_mplayer_script>", and my mplayer script shows that it's being invoked as user "music", but alas, I still get the same audio driver error (it's as though the audio driver is still being opened as root instead of 'music').

Any ideas on how to get past this?

Thanks.

-Jon

---

### Post by andrew.46 on 2023-12-23
Perhaps use elevated privileges and run the following command:

```

mplayer -ao help

```

This should tell you the audio output devices available to MPlayer under root or sudo...

---

