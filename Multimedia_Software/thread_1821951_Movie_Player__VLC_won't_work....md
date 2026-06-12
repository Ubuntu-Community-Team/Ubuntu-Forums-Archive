---
title: "Movie Player / VLC won't work..."
date: 2011-08-09
forum: Multimedia Software
---

### Post by insanekat on 2011-08-09
Running Natty Narwhal. 

So a while ago my Movie Player stopped working since I didn't have the proper MP3 plugin, computer tried searching with no luck, made sure all the restricted extras etc were installed, tried various other fixes through Google searches also without results. Although MP3s play fine on all other things, just can't play avis or anything like that in Movie Player.

I had VLC media player installed so I've just been using that without trouble. However, today there were software updates, some for Movie Player I believe, and now VLC only plays audio with no video. 

This is what I get when I try to run an avi file through the terminal in VLC:
```
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x89cf914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1313500902)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2524): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
[0x8a6ac94] signals interface error: signal 17 overriden (0x12174c0)
[0x8a6ac94] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x8a6ac94] signals interface error: Caught Interrupt signal, exiting...

```

Help with both or either of these problems would be great! I will be happy to provide you with any other information. Thanks.

---

