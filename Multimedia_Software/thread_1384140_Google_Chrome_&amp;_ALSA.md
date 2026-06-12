---
title: "Google Chrome &amp; ALSA"
date: 2010-01-18
forum: Multimedia Software
---

### Post by ahmedsaieed on 2010-01-18
OK I've been having lots of problems with sound since my upgrade to Karmic and now I really don't like pulseaudio. It seems like I could fix most of the sound problems except for those with Google Chrome.

Anyway, the problem goes as follows:
I open youtube.com or any flash audio/video website. I watch the video, but I get no audio at all. I go to System > Administration > Sound > Applications, to find this flickering (yes flickering) sound volume controller for the application:
```
ALSA plug-in [chrome]
```
The controller is set at maximum sound but I still can't really understand why it's flickering.

After some Googling, [bturrie on the Debian forums]("http://forums.debian.net/viewtopic.php?f=6&t=45396") inspired me to think that it's an authorization problem, so I ran Google Chrome as sudo. Guess what? I got sound! And the whole volume controller flickering thing disappeared!

Now I'm really not happy with running my browser as sudo! 

So, do you have any idea how can I give Google Chrome the required authority to perfectly run the ALSA plugin (or any other supported sound plugin) with no need for sudo?

Notes:
1. HTML5 content work perfectly.
2. I tried various versions of flash players and the problem is repeated.

Thanks! :)

---

### Post by tubbygweilo on 2010-01-26
I seemed to have a problem much like yours and found the solution at posting #6 of [No Sound in Google Chrome]("http://ubuntuforums.org/showthread.php?t=1349572") the link holding the information is [how-to-make-google-chrome-browser-play]("http://happyubuntu.blogspot.com/2009/12/how-to-make-google-chrome-browser-play.html"). Hope this helps.

---

### Post by ahmedsaieed on 2010-02-15
not working :(

---

### Post by ahmedsaieed on 2010-02-15
Oh now it works!
Had to rename the old plugins folder before creating the symlink to firefox's :)

Thank you!

---

