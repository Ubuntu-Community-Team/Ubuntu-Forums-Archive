---
title: "firefox, realplay and mplayer"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by stevieb on 2006-11-19
you know, i've done this so often, you'd think i'd remember it one of these days...

(running edgy)when trying to play a realplayer file in firefox (at [www.tagesschau.de](www.tagesschau.de), for example), mplayer takes over.  i've made sure that nphelix is installed in the plugins directory, and that mplayer-in-rm or whatever it's called is removed.

i remember something about adding realplay to firefox's PATH, but forgot the specifics.  can someone help me?  I've got tomboy ready to write it down this time!

thanks,
steve

---

### Post by psycho78 on 2006-11-25
same prob here... :( want the same link.. [www.tagesschau.de](www.tagesschau.de) .... and more of course... nice idea with tomboy, I'll try this... or even better I will use evolution and sync it on my treo afterwards ;)

---

### Post by stevieb on 2006-11-25
try this:

in firefox, goto edit-prefs-content, hit "manage" under "file types", find the realplayer format and change it to use /usr/bin/realplay.

sagst bescheid, op's gelungen ist!
-steve

---

### Post by psycho78 on 2006-11-26
I deleted mozilla-mplayer and I could use real media. Under edit->pref.->content->filetypes was nothing to see except flash.... . I saw more before removeing mozilla-mplayer.
Now that I reinstalled mozilla-mplayer, there are more filetypes under edit->pref.->content->filetypes, but not real media. And when I try to play e.g. [www.tagesschau.de](www.tagesschau.de) mplayer jumps back in again and cannot play the stream.. :(  
I will try to remove the  mplayerplug-in-rm.so and mplayerplug-in-rm.xpt from /usr/lib/firefox/plugins and ~/.mozilla-firefox/plugins .... I already tried that before but I am clueless what else I could do...

---

### Post by stevieb on 2006-11-26
have you removed 'totem-mozilla' from your system?  that was another thing i had to do.  it will ask if you want to remove 'ubuntu-desktop' or something similar. this is safe to remove, it is only a pointer to other packages. (you can confirm this is safe by searching the forums for 'ubuntu-desktop'; several others have confirmed that it's safe)

-steve

---

### Post by psycho78 on 2006-11-27
yes  I did... , right now I only have realplayer and mozilla-plugin-vlc installed. This setup works with [www.tagesschau.de](www.tagesschau.de) ..... hmm but trying to watch the latest stream seems to be unsharp.. and using the external realplayer the screen flickers as hell... :(

Schei.....

---

### Post by malcolm1234 on 2007-01-11
[http://ubuntuforums.org/showpost.php?p=1938063&postcount=4](http://ubuntuforums.org/showpost.php?p=1938063&postcount=4)

---

