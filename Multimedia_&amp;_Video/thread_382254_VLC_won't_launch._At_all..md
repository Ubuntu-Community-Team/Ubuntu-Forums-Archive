---
title: "VLC won't launch. At all."
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by Spike-X on 2007-03-11
I've searched the forums, but haven't found an answer, so here we go:

When I first installed Ubuntu (Edgy), I used Automatix2 to install the VLC Player. I realise now that wasn't the best way to do it, but hey, I was new...

It all worked fine up until a few days ago, when the Software Updates thingy told me there were some updates for VLC. I installed them, and ever since then, I can't get VLC to launch. If I right-click on a .wmv file and ask it to open with VLC - nothing. I try to launch it from Applications > Sound & Video > VLC media player - nothing.

I've uninstalled and reinstalled with Automatix2. I've uninstalled (complete removal, including configuration files) and reinstalled with Synaptic - nothing.

I tried launching it from a Terminal just now, and this is what I got:

```
spike-x@spike-x-desktop:~$ vlc
VLC media player 0.8.6 Janus
[00000020] main interface error: no interface module matched "hotkeys,none"
[00000020] main interface error: no suitable interface module
[00000001] main private error: interface "hotkeys,none" initialization failed
[00000021] main interface error: no interface module matched "screensaver,none"
[00000021] main interface error: no suitable interface module
[00000001] main private error: interface "screensaver,none" initialization failed
[00000022] main interface error: no interface module matched "any"
[00000022] main interface error: no suitable interface module
[00000001] main private error: interface "(null)" initialization failed
spike-x@spike-x-desktop:~$ 
```

Heeeeeeeeeeeeeeeeeeeelp!!!

---

### Post by Spike-X on 2007-03-11
Fixed it!!

I found the following solution in response to a different problem, and it worked for the one I was having!

Go into your home folder, view-show hidden folders
rename or delete the .vlc folder
then restart vlc to to get back the default settings

---

