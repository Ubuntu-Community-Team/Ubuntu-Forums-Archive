---
title: "Last.fm player won't start in Ubuntu 8.10"
date: 2009-03-09
forum: Multimedia Software
---

### Post by BOBSta on 2009-03-09
Today, I tried to start Last.fm player on my Ubuntu 8.10 system and it won't start.  Very confused by this as it's always worked in the past - I've been running it since 7.10 on the same PC.

When I select it from Applications > Sound & Video > Last.fm, the application icon appears in the panel for about 10 seconds, then disappears and leaves me with no player! This has never happened before.

My system is fully up to date as of this morning when I did a full update, then rebooted.

I've since tried removing and re-adding Last.fm via Add/Remove and it still doesn't work.

In the Launcher properties, the command is "/usr/bin/lastfm".  I checked the file in terminal and it has these permissions:

ls -lha lastfm
-rwxr-xr-x 1 root root 120 2008-09-21 21:42 lastfm

Have searched the web and forums, but most people previously reporting problems are using Rythmbox (I don't) or have problems with no sound after 1 second of a song playing - I can't even get the app to start.

Can anyone provide help?

Regards,
Rob.

---

### Post by woodenbrick on 2009-03-09
Try running the program from the terminal and see if it gives you any error messages.

---

### Post by BOBSta on 2009-03-09
Hey, thanks for the fast response! :o

/usr/bin$ ./lastfm
/usr/lib/lastfm/last.fm: symbol lookup error: /opt/project-neon/lib/libQtDBus.so.4: undefined symbol: _Z13qFlagLocationPKc

Hmm... Is it conflicting with the KDE 4.2 desktop nightly build that I installed last week?

I'm currently logged in to GNOME desktop and haven't used KDE since Tuesday (was just trying it out). When I removed and re-installed just now, I was in GNOME and thought that would have fixed it.  Some dependency issue?

Rob.

---

### Post by gdonwallace on 2009-03-09
Something that I found that works pretty good for Last.fm is the plug-in for Firefox.

No dependency issues, and with runs in your browser.

---

### Post by BOBSta on 2009-03-09
Sure, but I'd like to get the main application working if possible.  Thanks.

---

### Post by BOBSta on 2009-03-09
Just to satisfy my curiosity, I logged off GNOME and went into KDE.  I'm currently running Version 4.2.63 (KDE 4.2.63 (KDE 4.3 >= 20090212)).

Last.fm player wont run from the K menu or via command line here either.  From command line I get same error as in GNOME:

/usr/bin$ ./lastfm
/usr/lib/lastfm/last.fm: symbol lookup error: /opt/project-neon/lib/libQtDBus.so.4: undefined symbol: _Z13qFlagLocationPKc

---

### Post by woodenbrick on 2009-03-09
> **BOBSta said:**
> 
Hmm... Is it conflicting with the KDE 4.2 desktop nightly build that I installed last week?
Rob.

Looks like it, the last.fm program depends on the libqt, and it must be using the unstable one from project neon.  I don't really know much about it, is this last.fm package from the project neon project too?

Looking at my system I have 1:1.5.1.31879.dfsg-1ubuntu3 of the lastfm software installed.

---

### Post by BOBSta on 2009-03-09
No, I think it is the main ubuntu release of last.fm player as it was installed some time ago from Add/Remove Software within GNOME desktop, before I installed KDE.

As I can't start last.fm player I don't know the exact version, but if memory serves, it was *similar* to your version.  I tried running this on command line:

./lastfm -version

but got that same symbol lookup error again.

Is it possible to patch a config file to point to a different lib file, or do I need to un-install KDE?

---

### Post by woodenbrick on 2009-03-09
To be honest, I have no idea. Installing the old versions of libqt should work though.

---

### Post by BOBSta on 2009-03-09
Thanks!  Does anyone know how I can point the app to use a different libQt file and how I install that without breaking anything else?


Bug logged:
I've tried to log this with bugs.kde.org, but as the player isn't a KDE app, so I can't.

I did log it on the last.fm client support forum.  Will post any updates from them here.

Rob.

---

### Post by BOBSta on 2009-03-09
**_Issue resolved!_**

I did an Ubuntu Software update with the KDE nightly-build repository enabled this time, and I now have KDE Version 4.2.65 (KDE 4.2.65 (KDE 4.3 >= 20090226)).

After rebooting PC, the Last.fm player is working again under both GNOME and KDE!

My player is Version 1.5.1.31879.

I'm happily listening to music again, so all is well.

Rob.

---

