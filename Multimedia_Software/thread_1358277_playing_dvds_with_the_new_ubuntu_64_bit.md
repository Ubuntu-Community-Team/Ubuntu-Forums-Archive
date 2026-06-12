---
title: "playing dvds with the new ubuntu 64 bit"
date: 2009-12-18
forum: Multimedia Software
---

### Post by clettier on 2009-12-18
Hello there!!!!
I just installed the latest version of ubuntu. Even though I saw the advertisement claiming that ubuntu was ready to play media and videos, I was sure that the damn limitation on dvds was still on.
However when I tried to overcome the problem I was unable. Somehing is changed.
Does anybody have an updated link where I can find the solution to thi annoying thing ?
Hence:
[B]How can I be able to play dvds with Ubuntu 9.10 64 bit?
[/B][COLOR=black]Cheers!!![/COLOR]

---

### Post by ajgreeny on 2009-12-18
I am sure a quick search would have found this for you, which gives everything you need.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by saltmore on 2009-12-18
What ajgreeny said. Be sure to grab gstreamer0.10-plugins-ugly . For some reason that does not automatically install, and will cause problems.

---

### Post by clettier on 2009-12-18
I did indeed. Too bad it is not working for me :P
I think the post is becoming a report of a bug then

---

### Post by saltmore on 2009-12-18
I do playback on my 64 bit os. So unless it is hardware specific bug. Dunno. I would reinstall it all from the mediabuntu repo.

---

### Post by mc4man on 2009-12-18
For totem it's the bad plug-in, vlc just needs libdvdcss2
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

If not sure about libdvdcss2 then run 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If still no go then it's something else, not libs or plug-ins (region setting, corrupt .dvdcss, rct.

---

### Post by clettier on 2009-12-18
> **saltmore said:**
> What ajgreeny said. Be sure to grab gstreamer0.10-plugins-ugly . For some reason that does not automatically install, and will cause problems.

That's it!!!!
Thanks a lot !!! Now it works!
cheers

---

### Post by saltmore on 2009-12-18
> **clettier said:**
> That's it!!!!
Thanks a lot !!! Now it works!
cheers

Glad could help. Enjoy!

---

