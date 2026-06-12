---
title: "Default media player in Google Chrome"
date: 2010-10-19
forum: Multimedia Software
---

### Post by voutasaurus on 2010-10-19
Hi there.

I'm running Ubuntu 10.04 Desktop, and I'm using Google Chrome as a browser.

Every time I open any video file in the browser, it automatically uses the Totem Movie Player plugin to play it. I would prefer it to use the VLC plugin as a default (I do have the plugin installed). I've tried to find the option in Chrome's preferences, and I checked my plugins, and when I disable the Totem plugin, videos don't play in the browser at all.

I figure it should be simple, so I figure maybe I'm missing something.

Any help would be appreciated. Thanks. :)

---

### Post by sohlinux on 2010-10-19
Right click on the video file and select Properties. then Choose the Open With, go to other then go to applications - sound and video and select VLC Player.  tick remember application association. done!

---

### Post by voutasaurus on 2010-10-19
Okay, ignore Chrome for a second.

Within Nautilus, I right clicked on an avi file and opened it with vlc and ticked the box for "Remember this application for "AVI video" files". I open the file a second later and it opens with Totem. mp4s open with vlc every time, and wmvs open with Totem, even if I do the same thing as with the avi file.

Is there a file somewhere which overrides these preferences which I could edit?

---

### Post by sohlinux on 2010-10-19
> **voutasaurus said:**
> Okay, ignore Chrome for a second.

Within Nautilus, I right clicked on an avi file and opened it with vlc and ticked the box for "Remember this application for "AVI video" files". I open the file a second later and it opens with Totem. mp4s open with vlc every time, and wmvs open with Totem, even if I do the same thing as with the avi file.

Is there a file somewhere which overrides these preferences which I could edit?

easiest would be to remove Totem if you dont use it then VLC will become default

---

### Post by mc4man on 2010-10-19
> Within Nautilus, I right clicked on an avi file and opened it with vlc and ... 
To change the default for a mimetype use r. click -** properties** - open with

If you installed the vlc mozilla plugin then remove the totem-mozilla plugin - you should only have 1 browser plugin installed at a time

---

### Post by Chipzzz on 2010-12-09
I recently solved a similar problem with Chrome and mms streams this way:

Open: Applications/System Tools/Configuration Editor
Go to: desktop/gnome/url-handlers/mms
Right click, Edit, and change: 'totem "%s"' to 'vlc "%s"'

All done!

This should work similarly for any file or stream type.

Good luck :)

---

### Post by nathan.f77 on 2012-02-25
Awesome, thanks Chipzzz, your solution worked for me. 

But instead of "Open: Applications/System Tools/Configuration Editor", just go to Terminal and type "gconf-editor".

---

