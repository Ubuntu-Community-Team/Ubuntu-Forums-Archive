---
title: "Uninstall a feral (g)mplayer"
date: 2012-05-16
forum: Multimedia Software
---

### Post by HerixFromParis on 2012-05-16
Hi there,

So it's been nearly six years since I first installed Ubuntu on this computer and we've been through many updates, uninstall and reinstall.

I'm currently undertaking some sort of cleanup.
Among other things, I have this MPlayer instance that I'd like to get rid of. It shows in the applications menu.
The binary is /usr/local/bin/gmplayer
Synaptic shows MPlayer as *not* installed. 
If I install it with Synaptic, install goes OK. The newly installed binary is in /usr/bin/gmplayer
but the existing menu still links to /usr/local/bin/gmplayer and no new menu is added.
Uninstall via Synaptic goes OK, and preexisting menu and binary remain.

I don't remember, but I guess I installed MPlayer from sources or something.

Now I guess I could just rm /usr/local/bin/gmplayer and the corresponding .desktop file, but I also feel that doing so would be somewhat unclean.

What would the correct uninstall procedure be ? Any other files that I should remove ?

[Xubuntu 10.4 64-bit, if this is relevant]

Thanks

---

### Post by shantiq on 2012-05-17
i was made aware of this line of code to Fully remove software


   ```
  sudo apt-get remove --purge PACKAGE NAME
```



maybe try that

---

### Post by enigma32 on 2012-05-17
The cleanest way would be to find the source you built it from and uninstall from there:

```
cd */directory/containing/original/source*
sudo make uninstall
```

Short of that, I'd try finding source for a version approximately the same as the one that's installed, building it (make), then running uninstall (make uninstall).

This is all assuming that makefile supports uninstall... that's not always the case.

---

### Post by SeijiSensei on 2012-05-19
Any associated files are likely to be in /usr/local/include, /usr/local/lib and /usr/local/etc.  Just browse around the directories below /usr/local for files with timestamps more or less identical to the one for /usr/local/bin/gmplayer.

You can just delete that file and ignore everything else.  Whatever else was installed won't interfere with the rest of the system, unless there's a specific problem that you've identified.

---

