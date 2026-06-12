---
title: "Audio output failed: The audio device &quot;default&quot; could not be used: Connection refused"
date: 2017-10-24
forum: Multimedia Software
---

### Post by linuxyogi on 2017-10-24
Hi, VLC is not playing any sound no matter which output module I select. I have tried all available modules.  Any ideas ?

---

### Post by TheFu on 2017-10-24
Kill and restart pulse-audio.  I've seen this issue about 5x a day since loading 16.04.  Everything is fine, provided I don't change programs that output sound.  If I switch from a browser to a video player - bam - no sound from either anymore until pulse audio subsystem is restarted.

Lubuntu doesn't use pulse, so if you are running that, manually fixing alsa is necessary.

---

### Post by linuxyogi on 2017-10-24
> **TheFu said:**
> Kill and restart pulse-audio.  I've seen this issue about 5x a day since loading 16.04.  Everything is fine, provided I don't change programs that output sound.  If I switch from a browser to a video player - bam - no sound from either anymore until pulse audio subsystem is restarted.

Lubuntu doesn't use pulse, so if you are running that, manually fixing alsa is necessary.

Thanks for your reply.

```
$ pulseaudio --check
corei3@corei3 ~ $ pulseaudio -k
corei3@corei3 ~ $ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.

```

Now I getting sound from vlc. Is there a permanent fix ?

---

### Post by TheFu on 2017-10-24
> **linuxyogi said:**
> Thanks for your reply.

```
$ pulseaudio --check
corei3@corei3 ~ $ pulseaudio -k
corei3@corei3 ~ $ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.

```

Now I getting sound from vlc. Is there a permanent fix ?

Sure. Convince Canonical to dump pulse audio and put their efforts into a sound subsystem that actually is stable.
My fix is to have those commands in a script and run them whenever sound breaks.

---

### Post by linuxyogi on 2018-01-28
Upgraded to 18.04. Problem solved.

---

### Post by TheFu on 2018-01-28
Actually, I found a solution too. Mine was to disable shared-memory for Pulse communications.  Let me see if I can find the setting.

In ~/.config/pulse/client.conf, put 1 line:
```
enable-shm = no
```

Since doing that, it hasn't crashed once.

---

