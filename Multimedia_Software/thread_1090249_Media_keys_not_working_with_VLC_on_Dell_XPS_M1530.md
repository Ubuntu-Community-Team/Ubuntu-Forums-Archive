---
title: "Media keys not working with VLC on Dell XPS M1530"
date: 2009-03-08
forum: Multimedia Software
---

### Post by blakeoxx on 2009-03-08
My next, previous, stop, and play/pause buttons are not working with VLC media player 0.9.4 in Ubuntu 8.10. I am using a Dell XPS M1530. I have tried going to System > Preferences > Keyboard Shortcuts and setting hotkeys from there. It recognizes that I am pressing the keys and sets them correctly, but they are not affecting VLC for some reason. I also tried setting the hotkeys in VLC itself, but VLC does not recognize the media keys.

Any suggestions? I found some seemingly outdated solutions for older Ubuntu versions, but nothing current.

---

### Post by vdoki on 2009-03-10
I have tried to set it too without any success :(

---

### Post by blakeoxx on 2009-04-08
Bump. Any help?

Edit: I found out the media keys work with Rhythmbox. So, this is apparently an issue with VLC.

---

### Post by tgalati4 on 2009-04-08
Run vlc in a terminal and look for keybinding errors:

>vlc --debug

---

### Post by blakeoxx on 2009-04-10
That causes an error:

> vlc: unknown option or missing mandatory argument `--debug'

---

### Post by Pithikos on 2010-12-24
same problem here. anyone solved this? *--debug *is not an acceptable flag for VLC.

---

