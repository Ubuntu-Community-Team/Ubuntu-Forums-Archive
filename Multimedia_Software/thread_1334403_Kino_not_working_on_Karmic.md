---
title: "Kino not working on Karmic"
date: 2009-11-22
forum: Multimedia Software
---

### Post by ukuli on 2009-11-22
Hello, 

Kino used to work well on Ubuntu.

However, when I updated to Ubuntu 9.10 it started to act really strange.

Everything goes ahead like I am fast forwarding the video.

Does anybody know how to fix this?

---

### Post by nigels on 2009-11-22
Same problem here.
I'm going to try building from source.

I suspect it has something to do with pulse audio - I get lots of messages on the console:
```

Could not open ALSA device "/dev/dsp": No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
```

---

### Post by ukuli on 2009-11-22
I get that audio error message too, but it is also fast forwarding the video.

---

### Post by nigels on 2009-11-22
I built and installed **kino-1.3.4** from source - same problem.  There are lots of libfoo-dev packages required to do that.  I noticed if I close Banshee Media Player, a wait a while (30 seconds perhaps) kino will play normally.  But if I press stop/play it will go back to playing quickly and silently again.

I'm not quite willing to nuke pulse-audio from this machine, but it might be worth a try if you don't mind the risk.

- Nigel

---

### Post by nigels on 2009-11-22
There are some suggested workaround mentioned on the Kino site: [http://www.kinodv.org/article/view/173/1/13/](http://www.kinodv.org/article/view/173/1/13/)

The first of these doesn't work for me: "try setting the Audio Device to plughw:0,0"

The second works, but the audio is choppy: run Kino using the "padsp kino" command.

So is pulse audio here to stay, or has it been declared some big terrible disaster already?

- Nigel

---

### Post by ukuli on 2009-11-22
Thanks! I will try these...

---

### Post by nigels on 2009-11-22
Here is a workaround that works well for me.

At the command line: ```
pasuspender kino
```

Which suspends pulse audio and provides direct audio hardware access to kino.

Rejoice and be happy.

- Nigel

---

### Post by ukuli on 2009-11-22
Thanks! That did it! Now both video and audio are ok!

---

### Post by Spectre5 on 2009-11-22
> **ukuli said:**
> Thanks! That did it! Now both video and audio are ok!

Please remember to mark the thread as solved.  Select "Thread Tools" and then Solved.  Thanks.

---

### Post by tomdkat on 2009-12-02
Sweet!  I'm having this issue right now so I'll give the above a try. 

Thanks!  :)

EDIT:  Using "padsp kino" works beautifully!  Thanks again!

Peace...

---

