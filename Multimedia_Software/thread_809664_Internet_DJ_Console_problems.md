---
title: "Internet DJ Console problems"
date: 2008-05-27
forum: Multimedia Software
---

### Post by Korijn on 2008-05-27
I having a weird problem with my Ubuntu 8.04 setup. First a good description, then the question.

I followed the steps in this guide: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) so those sound card problems are at least fixed.

I installed IDJC from the Add/Remove program Ubuntu offers. When I run it I get a message saying I need to run JACK sound server (instead of PulseAudio?). So I run the command suggested:

```
jackd -d alsa -r 44100 -p 2048
```

I have to leave the terminal open for the JACK sound server to continue to run, so I do. I then start IDJC again and it shows me the main panel. I fill in all the details in the server panel and set it to ShoutCast server (which is running properly, because I can connect from windows machines). The problem: the "server connect" button is greyed out. And there's apparently nothing I can do about it just googling/foruming.

What do I do?

---

### Post by StephenF on 2008-05-27
> **Korijn said:**
> I installed IDJC from the Add/Remove program Ubuntu offers. When I run it I get a message saying I need to run JACK sound server (instead of PulseAudio?). So I run the command suggested:

```
jackd -d alsa -r 44100 -p 2048
```

I have to leave the terminal open for the JACK sound server to continue to run, so I do. I then start IDJC again and it shows me the main panel. I fill in all the details in the server panel and set it to ShoutCast server (which is running properly, because I can connect from windows machines). The problem: the "server connect" button is greyed out. And there's apparently nothing I can do about it just googling/foruming.

What do I do?
The Ubuntu build of IDJC lacks support for mp3 streaming. This leaves only Ogg/vorbis as an option and only to Icecast servers. If you need mp3 to Shoutcast you'll have to either compile your own IDJC from source or use one Steveway's unofficial builds.

---

### Post by Korijn on 2008-05-28
And is there something to do about having to keep the JACK-terminal open? Isn't there some kind of way to make it all happen automatically?

Thanks alot by the way. :D

---

### Post by Korijn on 2008-05-28
```
checking for JACK... configure: error: Package requirements (jack >= 0.98.1) were not met:

No package 'jack' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables JACK_CFLAGS
and JACK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I consistently get this error, even though I've definitely installed all jack packages (jack-tools + dependencies and all other packages listed on the idjc's site). I've also set JACK_LIBS to /usr/lib/jack but that doesn't help either.

---

