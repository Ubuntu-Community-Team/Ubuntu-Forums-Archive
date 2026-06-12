---
title: "Why not Realplayer in Firefox?"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by popatopalous on 2008-02-29
Ubuntu/Kubuntu have for quite a while had a problem with Realplayer. I don't have it in Synaptic???  Canonical and third party repos ARE enabled so why isn't it there? Strange. How do I get Realplayer and get it to work in Firefox???

Ok, ok, I know I can and just did install Realplayer from it's own website although there is an Ubuntu trick. There is a package you have to install to install Realplayer. But it's a secret... And I positively know Realplayer will not have sound. Realplayer hasn't had sound upon install for me since the beginning or Ubuntu [Breezy for me]. This HAS to be an unfixed bug.

```
$ cd /usr/lib/firefox/plugins
:/usr/lib/firefox/plugins$ ls
flashplugin-alternative.so  mplayerplug-in-dvx.xpt  mplayerplug-in-rm.xpt   mplayerplug-in.xpt
libjavaplugin.so            mplayerplug-in-qt.so    mplayerplug-in.so       nphelix.so
libunixprintplugin.so       mplayerplug-in-qt.xpt   mplayerplug-in-wmp.so   nphelix.xpt
mplayerplug-in-dvx.so       mplayerplug-in-rm.so    mplayerplug-in-wmp.xpt
```

```
$ cd   /usr/lib/mozilla/plugins
:/usr/lib/mozilla/plugins$ ls
flashplugin-alternative.so  mplayerplug-in-qt.so   mplayerplug-in.so       nphelix.so
libjavaplugin.so            mplayerplug-in-qt.xpt  mplayerplug-in-wmp.so   nphelix.xpt
mplayerplug-in-dvx.so       mplayerplug-in-rm.so   mplayerplug-in-wmp.xpt
mplayerplug-in-dvx.xpt      mplayerplug-in-rm.xpt  mplayerplug-in.xpt
```

Ok so there are the appropriate plugins listed but the DO NOT appear in Firefox in 'about:plugins'. What's wrong?

---

### Post by puneit on 2008-02-29
According to UbuntuGuide for Gutsy there is a plugin. I don't use my machine to play media so I haven't tried this. You can have a look 
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins)

---

### Post by popatopalous on 2008-03-01
> **puneit said:**
> According to UbuntuGuide for Gutsy there is a plugin. I don't use my machine to play media so I haven't tried this. You can have a look 
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins)

Thanks but:

```
~$ sudo apt-get install mozilla-helix-player
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mozilla-helix-player
```

As far as I know it isn't possible to get Realplayer to work in firefox in Kubuntu AMD64. Damn shame too.

Edit: [http://ubuntuforums.org/showthread.php?t=587953](http://ubuntuforums.org/showthread.php?t=587953)

---

### Post by popatopalous on 2008-03-07
Ok here is what I did. I installed RealPlayer from their website. I currently have 3 Firefox plugins IcedTea Java, Flash non-free, and MPlayer. I finally remembered something. An application doesn't have to be listed in 'about:plugins' to be used by embedded media in Firefox. First you have to edit >Edit>Preferences>Content>File Types>Manage so the appropriate file types point to Realplayer [in my case /usr/local/RealPlayer/realplay] and then remove the mplayer rm plugins:

```
/usr/lib/firefox/plugins$ sudo rm -v mplayerplug-in-rm.so
removed `mplayerplug-in-rm.so'
/usr/lib/firefox/plugins$ sudo rm -v mplayerplug-in-rm.xpt
removed `mplayerplug-in-rm.xpt'
```

Then when I select something in RTE I get the dialog box with the option 'Open with /usr/local/Realplayer/realplay'. In BBC you have to select 'launch in stand alone player' and you will get same dialog box. You can also select 'Do this automatically from now on'.

How can I undo the 'do this automatically from now on' part if I want to?     :confused:

---

