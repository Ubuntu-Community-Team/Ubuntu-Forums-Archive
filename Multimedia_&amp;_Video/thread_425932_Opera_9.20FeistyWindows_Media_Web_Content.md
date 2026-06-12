---
title: "Opera 9.20/Feisty/Windows Media Web Content"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by carney1979 on 2007-04-28
How do I get opera to play Windows Media files such as the videos on CNN.com?

David

---

### Post by reclusivemonkey on 2007-04-28
Sorry I don't use Opera, but I can play the videos in Firefox. I use the mplayer plugins.

You have to install mplayer & mozilla-mplayer. I then remove all the totem plugins from /usr/lib/firefox/plugins. IMHO, the mplayer plugins for firefox are the best solution for multimedia on the web in Linux.

---

### Post by carney1979 on 2007-04-28
I can view the content in Firefox. I'm just trying to make it work in Opera.

David

---

### Post by reclusivemonkey on 2007-04-28
> **carney1979 said:**
> I can view the content in Firefox. I'm just trying to make it work in Opera.

What steps have you already taken?

---

### Post by carney1979 on 2007-04-28
I've tried "isolating" the plugins by limiting which plugins Opera "sees" by telling it to only look in /usr/lib/opera/plugins.

Then I tried moving or linking plugins to that folder. 

So far I got (or almost got) results with the mplayer plugin. CNN asked if I wanted to upgrade my player and I told it no. It tried to play the video but all I got was a blank screen where the video should be.

The reason I'm "shuffling" plugins is I thought maybe I was getting a conflict between one or more plugins.

David

---

### Post by someguyouknow on 2007-04-28
[http://www.opera.com/linux/docs/plugins/install/](http://www.opera.com/linux/docs/plugins/install/)
Those are directions to install mplayer in Opera. I have tried many times and was only able to do it once long ago... kinda difficult for a noob like me. I just stick with the Kaffeine plugin.

---

### Post by reclusivemonkey on 2007-04-29
> **carney1979 said:**
> I've tried "isolating" the plugins by limiting which plugins Opera "sees" by telling it to only look in /usr/lib/opera/plugins.

Then I tried moving or linking plugins to that folder. 

So far I got (or almost got) results with the mplayer plugin. CNN asked if I wanted to upgrade my player and I told it no. It tried to play the video but all I got was a blank screen where the video should be.

The reason I'm "shuffling" plugins is I thought maybe I was getting a conflict between one or more plugins.

David

What does 

```

ls -l /usr/lib/opera/plugins

```

give?

---

### Post by carney1979 on 2007-04-29
> **reclusivemonkey said:**
> What does 

```

ls -l /usr/lib/opera/plugins

```give?

This:

```
david@n1zhe:~$ ls -l /usr/lib/opera/plugins
total 200
lrwxrwxrwx 1 root  root     41 2007-04-29 02:53 kaffeineplugin.a -> /usr/lib/mozilla/plugins/kaffeineplugin.a
lrwxrwxrwx 1 root  root     42 2007-04-29 02:53 kaffeineplugin.la -> /usr/lib/mozilla/plugins/kaffeineplugin.la
lrwxrwxrwx 1 root  root     42 2007-04-29 02:53 kaffeineplugin.so -> /usr/lib/mozilla/plugins/kaffeineplugin.so
lrwxrwxrwx 1 root  root     42 2007-04-29 02:53 libflashplayer.so -> /usr/lib/mozilla/plugins/libflashplayer.so
lrwxrwxrwx 1 root  root     39 2007-04-29 02:54 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
-rw-r--r-- 1 david david 97332 2007-04-09 11:16 libnpp.so
lrwxrwxrwx 1 root  root     47 2007-04-29 02:53 mplayerplug-in-dvx.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root  root     45 2007-04-29 02:53 mplayerplug-in-qt.so -> /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root  root     46 2007-04-29 02:53 mplayerplug-in-qt.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root  root     45 2007-04-29 02:53 mplayerplug-in-rm.so -> /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root  root     46 2007-04-29 02:53 mplayerplug-in-wmp.so -> /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root  root     47 2007-04-29 02:53 mplayerplug-in-wmp.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root  root     38 2007-04-29 02:54 nphelix.so -> /usr/local/RealPlay/mozilla/nphelix.so
lrwxrwxrwx 1 root  root     39 2007-04-29 02:54 nphelix.xpt -> /usr/local/RealPlay/mozilla/nphelix.xpt
lrwxrwxrwx 1 root  root     50 2007-04-29 02:54 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
-rwxr-xr-x 1 root  root   7056 2007-04-09 11:16 operaplugincleaner
-rwxr-xr-x 1 root  root  88788 2007-04-09 11:16 operapluginwrapper
david@n1zhe:~$ 

```I moved a few more around and tried kaffeine (didn't work either).

David

---

### Post by risidoro on 2007-04-29
Hi,
i think i've tried EVERY media player's plugin out there with my opera browser so i can say i'm quite an expert on the subject ;)

This were my findings:

- totem-plugin: doesn't work

- mplayer-plugin (in repository): doesn't work

- mplayer-plugin (compiled by me without gtk support): **works** but you have no controls so you can't play/stop/volume-up/volume-down/etc...etc

- gxine plugin: doesn't work

- vlc plugin: doesn't work

- Gecko-media-player (GNOME Media player's plugin): doesn't work (PLS note: the author declares it opera compatible so maybe it was my fault if it didn't work. Pls, let me know if you'll try it and succeed)

- kaffeine-plugin: **works** but it plays videos in a separate window (instead of embedded in the browser). I prefer the separate window so kaffeine is fine for me BUT it is a KDE app and i'm now a GNOME user 

- mozplugger 1.73 (in repository) OR mozplugger 1.81 (compiled by me): **works**, plays everything, can show the video embedded in pages or, by modifying /etc/mozpluggerrc, even in separate windows. You can associate different video formats to different applications so, for example, you can open .wmv and .avi with totem-xine and .mov with mplayer (totem-xine doesn't play apple.com/trailers but mplayer does)

So, i can say i've found the best i could desire: mozplugger.
PS: i have found no differences at all between mozplugger 1.73 and 1.81 but i've installed the latter 'cos i've always believed in the 'more recent is better' philosophy... well at least until Windows Vista came out :D
If you want i can send you the mozplugger 1.81 package i compiled (the package has been created with checkinstall and will install only in /usr/lib/opera/plugins so firefox is not affected)

Bye

---

### Post by deadlines on 2007-04-30
Interesting, I'm using mozplugger in Opera and it does NOT play Windows media content properly (at least not newer Windows media files such as those hosted on cnn.com)  Oddly enough, using the Opera [plugins check page]("http://people.opera.com/byberg/media/index.htm") the WMV test video seems to work, but again, I'm pretty sure this has to do with what version of Windows Media Player the file was created with.

---

### Post by risidoro on 2007-04-30
> **deadlines said:**
> Interesting, I'm using mozplugger in Opera and it does NOT play Windows media content properly (at least not newer Windows media files such as those hosted on cnn.com)  Oddly enough, using the Opera [plugins check page]("http://people.opera.com/byberg/media/index.htm") the WMV test video seems to work, but again, I'm pretty sure this has to do with what version of Windows Media Player the file was created with.

Mozplugger doesn't play anything by itself, it is only a wrapper to external applications (by default it uses mplayer or totem). If you're having problems with cnn.com videos, it is not a mozplugger fault but a mplayer or totem one.
In my pc i've associated (in /etc/mozpluggerrc) all the videos to totem (including wmv) and .mov movies to mplayer (totem won't open them). 
Totem plays wmv (even cnn.com ones) videos without problems.

BTW: i'm using totem-xine with libxine-extracodecs and w32codecs (from medibuntu repository) installed.

If you're still unable to plays wmv with totem you can install mplayer (and w32codecs if you haven't done it yet). Mozplugger will use mplayer by default (instead of totem) if it is installed in your pc.

Hope that helps and sorry for my awful english :frown: 
Bye.

---

### Post by deadlines on 2007-05-01
Yes I understand it calls other apps, that still doesn't really explain why some Windows media content will play in Mplayer and others won't.  Nonetheless, thanks for the tip on associating mozplugger with totem, I was able to at least get that working in Firefox but still no love in Opera for some reason.

Cheers

---

### Post by Colonel Kilkenny on 2007-05-02
I use Gecko-media-player and it seems to be the best solution.
It needs to be compiled (and requires compiled gnome-mplayer) but it's worth it.

---

### Post by deadlines on 2007-05-02
Cheers again to risidoro for the tip on associating mozplugger with totem for WMV, after digging around a little I discovered there was a hidden mozpluggerrc file in ~/.opera, so once I copied my modified /etc/mozpluggerrc over it everything worked like a champ.  I just yanked the mplayer-wmp plugin out of /usr/lib/opera/plugins/ just to make sure there was no conflict should I ever need to detect some new plugins for Opera.

Anyways long story short, Windows media player content playing in Opera so I'm now a happy camper.  Despite the fact that Firefox has some very nice extensions, it still doesn't come close to handling sessions as elegantly as Opera does imho, and Opera's features tend to be more polished.  Not to mention Opera renders HTML much faster than any other browser out there. so I was really hurting to get this working.  Thanks again mate!

---

### Post by risidoro on 2007-05-03
> **deadlines said:**
> Cheers again to risidoro for the tip on associating mozplugger with totem for WMV, after digging around a little I discovered there was a hidden mozpluggerrc file in ~/.opera, so once I copied my modified /etc/mozpluggerrc over it everything worked like a champ.  I just yanked the mplayer-wmp plugin out of /usr/lib/opera/plugins/ just to make sure there was no conflict should I ever need to detect some new plugins for Opera.

Anyways long story short, Windows media player content playing in Opera so I'm now a happy camper.  Despite the fact that Firefox has some very nice extensions, it still doesn't come close to handling sessions as elegantly as Opera does imho, and Opera's features tend to be more polished.  Not to mention Opera renders HTML much faster than any other browser out there. so I was really hurting to get this working.  Thanks again mate!

I'm really happy you succeeded :)
I didn't tell you of the hidden .mozpluggerrc in  .opera because I DON'T HAVE ONE. It's really strange! I have only the one in /etc and when i change it and restart opera i have my changes applied.
Anyway, it worked in the end so you can be happy :)

TIP: if you want to load your videos in separate windows, remove 'swallow(totem)' from your mozpluggerrc file! I prefer separate windows 'cos i can see the movies full screen.

Bye

---

### Post by deadlines on 2007-05-03
Question, have you noticed any problems playing Quicktime content?  For some odd reason I'm now unable to play Quicktime movies reliably, I have mozplugger calling mplayer to handle .mov files, everything loads up and begins to play fine only to later lock up in the middle of playing the videos.  I've tried setting & changing the cache in mplayer but with no luck, I thought perhaps there might be a setting I could tweak in the mozpluggerrc that passes an option to mplayer when it is called to fix this.

**Update:** Nevermind I fixed this issue, it turns out I needed to get the latest version of Mozplugger and start from scratch again.  This fixed the problem I was running into with mplayer hanging playing Quicktime movies.

---

### Post by phinn on 2007-05-08
Yea mplayerplug-in is definitely the best

[http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)

It works on almost everything flash doesn't.

The main downside with apt-getting it is as with a lot of stuff the apt-get repositories are outdated by months and months with that kind of stuff. Thats that main disappointment with Ubuntu for me

---

