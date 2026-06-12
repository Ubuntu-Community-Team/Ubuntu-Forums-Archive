---
title: "How can you make Firefox use Realplayer instead of Mplayer for real media?"
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by mzuverink on 2006-12-21
I am not happy with the way Mplayer plugin for Firefox handles Real Media streams, and would like to have Real Player handle all its Real streams.  
Is it possible to do this without uninstalling Mplayer?

---

### Post by obsidion on 2006-12-26
> **mzuverink said:**
> I am not happy with the way Mplayer plugin for Firefox handles Real Media streams, and would like to have Real Player handle all its Real streams.  
Is it possible to do this without uninstalling Mplayer?


  Assuming stock install of firefox and mplayer ie from the repos.
Open a terminal and cd to /usr/lib/firefox/plugins and sudo rm any mplayerplugin that has rm or helix in it.
You will now need to symlink the nphelix.xpt and nphelix.so files from where they are in realplayer. Without knowing how you installed that I can't advise you fully sorry.

---

### Post by Dies on 2006-12-27
After you get rid of the mplayer rm plugins.

Real Player should do that for you, just open the player go to Help>Reset Player, a wizard should come up.
Just OK through the wizard and it should set up up the symlinks for you.

---

### Post by NobodySpecial on 2006-12-27
The following worked for me.

Edit the mplayer plugin file:
```
gedit ~/.mplayer/mplayerplug-in.conf
```

Change as needed to:
```
enable-rm=0
enable-smil=0
enable-helix=0
```

Now when you click on a realplayer file, it will ask you what to open it with, and you can click Realplayer and use the external player.

---

### Post by sgla1 on 2007-01-07
Thanks for the tip.  After editing mplayerplug-in.conf and re-running RealPlayer > help > reset I can now play realplayer files with realplayer instead of mplayer.

---

