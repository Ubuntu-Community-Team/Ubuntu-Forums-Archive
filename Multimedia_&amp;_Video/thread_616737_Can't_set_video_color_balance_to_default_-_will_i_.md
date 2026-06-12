---
title: "Can't set video color balance to default - will i really have to re-install AGAIN ?"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by wladston on 2007-11-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/163660](https://bugs.launchpad.net/ubuntu/+bug/163660) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The video playback on the "Movie Player" was working perfectly, but on  I clicked the button to "reset to default" on the preferences dialog, color balance part.

that screwed my color/brightness/contrast settings and now I can't get it back to normal.

please, read the bug report I filled on launchpad ... I don't know what I can do anymore...

my last hope is to reinstall ubuntu yet again to revert this click ... if you have this bug also, pelase, report it on launchpad, so they might get it fixed faster!

thanks very much for the help!

---

### Post by Beaucephus on 2007-11-18
If the problem is just with one program you can remove it and reinstall with Synaptec. You will have to use the "remove completely" option which deletes config files too.  Reinstalling is rarely the (right) answer.  

Another option is to ditch the default movie player (I hate it) and install VLC.

---

### Post by wladston on 2007-11-18
I've marked Totem, totem-gstreamer and totem-mozilla for complete removal, and afterwards, I re-installed them.

Guess what happened ? Nothinhg!!! The problem was still there ...those settings should reside in a higher layer ...  ;-(

About VCL, I've had bad experiences with it on the past. The videos were running in a slighttly slower than normal rate, with really irritated me!

---

### Post by Beaucephus on 2007-11-19
Hmm...maybe I was wrong about "completely remove" actually getting rid of the config files with that  setting you want to revert.

I checked out where totem puts its files.  They seem to be in the directory

/home/username/.gconf/apps/totem/

Deleting these files should return it to it's default configuration.  Run this command from your home dir
```

sudo rm -rf .gconf/apps/totem/ 
```

Then try again.  If that doesnt work check out vlc.  It is a real nice full featured media player.  Heck, check out VLC even if it does work.  You might like it better. 
```
sudo apt-get install vlc
```

---

### Post by wladston on 2007-11-19
thanks!

actually I worked this problem out by removing my entire /home/user directory. X-(

lost all settings for everything .... if I just waited one day ...



I'm going to try vcl anyways, let's hope it is able to play my files normally this time.

---

### Post by Beaucephus on 2007-11-21
Removing your whole directory is pretty harsh, but still not as bad as reinstalling!  The lesson here is that everything in Linux is controlled by a file.  You just have to find it.

---

### Post by wladston on 2007-11-21
yeah! Thanks for the help! ;)

---

