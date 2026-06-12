---
title: "BBC video clips"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by Bloch on 2007-01-01
I am trying to play the video news clips from the BBC site
[http://news.bbc.co.uk/](http://news.bbc.co.uk/)

The mplayer plugin appears to start but freezes. Firefox freezes and has to be forced to close. (This also happens with many, but not all sites with embedded contoent where the mplayeer plugin is started)

The video links on the BBC site offer a choice of windows media player or real player. mplayer starts in each case, but freezes. mplayer works on such sites as boreme.com and others. When it doesn't work it freezes Firefox completely.

Can anyone get the clips on the BBC site to work? With some other sites I can copy the streaming URL and paste it into the "open location" field on Totem or Realplayer, but for this site I can't get the streaming URL.

---

### Post by obsidion on 2007-01-01
[QUOTE=Bloch;1956042]I am trying to play the video news clips from the BBC site
[http://news.bbc.co.uk/](http://news.bbc.co.uk/)

The mplayer plugin appears to start but freezes. Firefox freezes and has to be forced to close. (This also happens with many, but not all sites with embedded contoent where the mplayeer plugin is started)

The video links on the BBC site offer a choice of windows media player or real player. mplayer starts in each case, but freezes. mplayer works on such sites as boreme.com and others. When it doesn't work it freezes Firefox completely.


   It works fine with real player, I suggest you install that and its plugins and remove the mplayer plugins.

---

### Post by Bloch on 2007-01-01
Realplayer is installed - how do I install the plugins extra?

Do you mean the plugins in listed in /usr/lib/mozilla/plugins ?

nphelix.so and nphelix.xpt are listed there - I understand Realplayer is based on what is called the Helix engine, so does this mean I have the realplayer plugins?

Is there any way to temporarily disable the mplayer plugins - I think I may need them for other sites.

When you say remove the mplayer plugins do you mean to simply move all the files named mplayerplug-in-rm.so etc fromthis foider?

I use Dapper Drake.

---

### Post by obsidion on 2007-01-01
[QUOTE=Bloch;1956164]Realplayer is installed - how do I install the plugins extra?

Do you mean the plugins in listed in /usr/lib/mozilla/plugins ?

nphelix.so and nphelix.xpt are listed there - I understand Realplayer is based on what is called the Helix engine, so does this mean I have the realplayer plugins?

  Yes it does and this is probably the root of your problem, you have two sets of real media plugins installed.

Is there any way to temporarily disable the mplayer plugins - I think I may need them for other sites. 

 I only mean the real player ones.

When you say remove the mplayer plugins do you mean to simply move all the files named mplayerplug-in-rm.so etc fromthis foider?

   That would work fine, I suspect you are getting a conflict by having both sets of rm plugins installed. Personally I just delete them.

---

### Post by obsidion on 2007-01-01
Quick thought make sure there are symlinks to the nphelix files in /usr/lib/firefox/plugins, if not symlink them to the ones in mozilla/plugins

---

### Post by koki on 2007-01-01
FWIW, BBC video clips play here using the mplayer FF plugin.

---

### Post by Bloch on 2007-01-01
Success!

Thank you all for your replies.
I "removed" mplayerplug-in-rm.so and mplayerplug-in-rm.xpt from the /usr/lib/mozilla/plugins folder (in fact I just renamed them in case I might need them later)

That was all, the Realplayer plugin (which in the folder is the file named nphelix.so and nphelix.xpt) then started on the BBC clips instead of the mplayer plugin. It worked fine.

koki, you say the mplayer plugin worked fine for you on the BBC clips. For the sake of clearing up the issue, do you have the realplayer plugins installed (in which case my problem may have been a clash of plugins)?
Or do you hvae a more up to date version of Firefox / mplayer plugin?
I have the default Dapper 6.06 Firefox, with the mplayer plugins as installed by automatix several months ago.

It was suggested that the presence of two plugins (specifically mplayerplug-in-rm.so  and nphelix.so) to handle realplayer content might be causing the problems.
I tested this by removing the nphelix.so and nphelix.xpt files from the /usr/lib/mozilla/plugins folder, and trying the mplayer plugin alone. This still caused Firefox to crash. Removing the mplayerplug-in-rm.so and mplayerplug-in-rm.xpt files and leaving only the  nphelix.so and nphelix.xpt files solves the problem.

The mplayer plugins often cause Firefox to freeze for me. Do I need to update them? Are they not updated automatically?

---

### Post by obsidion on 2007-01-01
[QUOTE=Bloch;1956265]Success!

Thank you all for your replies.
I "removed" mplayerplug-in-rm.so and mplayerplug-in-rm.xpt from the /usr/lib/mozilla/plugins folder (in fact I just renamed them in case I might need them later)


It was suggested that the presence of two plugins (specifically mplayerplug-in-rm.so  and nphelix.so) to handle realplayer content might be causing the problems.
I tested this by removing the nphelix.so and nphelix.xpt files from the /usr/lib/mozilla/plugins folder, and trying the mplayer plugin alone. This still caused Firefox to crash. Removing the mplayerplug-in-rm.so and mplayerplug-in-rm.xpt files and leaving only the  nphelix.so and nphelix.xpt files solves the problem.

  That was probably the problems


The mplayer plugins often cause Firefox to freeze for me. Do I need to update them? Are they not updated automatically

  I'm not a big fan of mplayer and have had similar problems when I have used it in the past even without the extra clash of plugin problems. I tend to use aviplay to play my other media files as a standalone called from firefox.

---

