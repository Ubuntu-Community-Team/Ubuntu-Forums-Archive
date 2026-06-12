---
title: "Flash sound suddenly gone"
date: 2008-05-02
forum: Multimedia Software
---

### Post by olavjunior on 2008-05-02
I installed Hardy from scratch yesterday. I used the none free flashplugin, and everything was working great. I watched movies with sound, but today, the sound is gone. I see on the forums that this is a bug with the none free plugin not sending it's sound to pulse audio. But what I really don't get is why I had sond in the first place!??

---

### Post by Zorael on 2008-05-02
If you kill the pulseaudio server, does Youtube play sound again? Then perhaps pulse is (somehow) getting exclusive access to the soundcard (sink).
```
$ pulseaudio -k
```
To restart it:
```
$ pulseaudio -D
```
To set pulse up to be the default ALSA output device (which, I think, should fix the issue itself), check **/etc/asound.conf** and make sure that the contents look something like this. Else, open it up in a text editor, such as gedit, with superuser permissions. (Alt+F2, '**gksu gedit /etc/asound.conf**')
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

---

### Post by olavjunior on 2008-05-02
I don't have any asound.conf

I read your reply on a nother thread, and made the asound.conf¸restarted firefox, but still no sound. 

So I've installed libflashsupport for now, and I think I'll just see how much these firefox crashes will annoy me. Hope they'll fix it soon!

EDIT: I've actually not had any crashes! sweet

---

### Post by Ulsak on 2008-05-02
Yeah, killing pulseaudio was a useful tip for my problem also. I had the problem with streaming videos at youtube, the videos stopped playing after two seconds thus the buffering went on. One could drag the progresshandle to watch the oncoming scenes as stills. But no  motion or sound output were possible to get.
Anyway. I'm happy with this tip, but I have to investigate this further.

---

### Post by Zorael on 2008-05-02
Doh, forgot libflashsupport across all posts. >.<

Check Known Issues over at [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) if this doesn't work.

---

### Post by olavjunior on 2008-05-02
:) But I'm getting terrilble many clicks and ticks in the audio when playing music with Rhythmbox. this happens when I open/close apps and windows... another bug maby? Has prb nothing to do with libflashsupport

---

