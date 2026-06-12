---
title: "DVD playback - VLC not responding"
date: 2008-05-10
forum: Multimedia Software
---

### Post by silkstone on 2008-05-10
I've just done a fresh install of Hardy on an Acer laptop, and got Totem to play DVDs after installing various codecs etc. Under Feisty I preferred VLC, so installed that using part 4 of the guide...

[http://ubuntuforums.org/showthread.php?t=766683&highlight=vlc](http://ubuntuforums.org/showthread.php?t=766683&highlight=vlc)

When I try to play a DVD, VLC loads but the screen panel doesn't appear, and after a few seconds the title bar greys out and nothing works. If I click on the close button I get the message that VLC is not responding, and I have to kill it.

VLC appears to work with other types of media, but not DVDs. (DVDs still play with Totem.)

Any ideas? :)

---

### Post by silkstone on 2008-05-11
In case this helps...

If I start VLC and tell it to open the DVD disk, it plays with no problems.

If I edit /etc/gnome/defaults.list and change totem.desktop to vlc.desktop in the x-content/video entries, when a DVD is inserted VLC launches but then freezes.

---

### Post by Lifedeath on 2008-08-29
Exact same problem here.

---

