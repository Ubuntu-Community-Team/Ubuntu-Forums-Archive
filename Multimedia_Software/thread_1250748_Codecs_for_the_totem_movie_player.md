---
title: "Codecs for the totem movie player"
date: 2009-08-26
forum: Multimedia Software
---

### Post by Nyhus on 2009-08-26
Hi.
I need codecs for the totem media player. When i play a movie with the program it wont run smoothly, so i have to use VLC. I guess a lot of people wonder why i wont just use VLC, and the answer is simple. The VLC "menu" is'nt attached to the screen where the movies are show like it is in windows, and this really bothers me. Also there is no fullscreen menu. Thats not a problem whit the totem. I've used it before with no problem, but this time it wont work the way it should.
I've googled a little and installed the codecs i could find, with no resault. I've also installed restricted extras.

---

### Post by kerry_s on 2009-08-26
sounds like you just need to mess with the preferences.

---

### Post by Yellow Pasque on 2009-08-27
This command will allow you to tweak gstreamer video playback (totem uses gstreamer):
```
gstreamer-properties
```

As for codecs, search for 'gstreamer' in Synaptic. Make sure you have gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly installed.

---

### Post by wildnfree on 2009-08-27
> **Nyhus said:**
> Hi.
I need codecs for the totem media player. When i play a movie with the program it wont run smoothly, so i have to use VLC. I guess a lot of people wonder why i wont just use VLC, and the answer is simple. The VLC "menu" is'nt attached to the screen where the movies are show like it is in windows, and this really bothers me. Also there is no fullscreen menu. Thats not a problem whit the totem. I've used it before with no problem, but this time it wont work the way it should.
I've googled a little and installed the codecs i could find, with no resault. I've also installed restricted extras.

Hello Nyhus,

If you upgrade to the latest version of VLC which is 1.1.0 you will find that it is a lot better with the menu attached to the screen.

I believe this is also in the slightly earlier version 1.0.1 in Karmic.

---

