---
title: "Can't get YouTube browser plugin working in Movie Player (totem) in 12.10"
date: 2013-02-20
forum: Multimedia Software
---

### Post by GeekyAdam on 2013-02-20
ubuntu 12.10
totem 3.4.3

I've read in a bunch of places online that Ubuntu's default movie player, totem, has a plugin to browse YouTube videos. Here's one example post: [http://www.clickonf5.org/7557/watch-youtube-videos-ubuntu-lucid-media-player/]("http://www.clickonf5.org/7557/watch-youtube-videos-ubuntu-lucid-media-player/")

I think the newer version of totem doesn't include the YouTube browser by default, so I'm trying to add the plugin. I downloaded the plugin files and put them in /usr/lib/totem/plugins as I was supposed to...
```
adam@poseidon:/usr/lib/totem/plugins/youtubeh264$ ll
total 28K
-rw-r--r-- 1 adam adam 5.2K Mar 28  2008 youtubeh264.plugin
-rw-r--r-- 1 adam adam 8.8K Mar 28  2008 youtubeh264.py
-rw-r--r-- 1 adam adam 4.7K Mar 27  2008 youtubeh264.ui
adam@poseidon:/usr/lib/totem/plugins/youtubeh264$ 
```
...but the plugin still won't show up in the totem plugin options area.
I launched totem via command-line and got some errors:
```
adam@poseidon:~$ totem

(totem:30894): Gdk-CRITICAL **: gdk_error_trap_pop_internal: assertion `trap != NULL' failed

(totem:30894): libpeas-WARNING **: Could not find 'Module' in '/usr/lib/totem/plugins/youtubeh264/youtubeh264.plugin'

(totem:30894): libpeas-WARNING **: Error loading '/usr/lib/totem/plugins/youtubeh264/youtubeh264.plugin'
adam@poseidon:~$ 

```
Granted, the plugin I downloaded is probably the version for pre-12.04 versions of Ubuntu and/or previous versions of totem.

1. Does anyone have totem's YouTube browser plugin working on 12.04 or 12.10?
2. Any ideas why I'm getting those errors?

---

### Post by mc4man on 2013-02-20
where did you get the plugin from??

totem 3.4.x can get youtube thru a grilo plugin but you'd need to either build totem with grilo support or find a ppa that does that.
(I believe there may be a grilo ppa that has totem builds.

screen shows totem with grilo

There is also minitube (ver.2 now around) or smplayer's youtube player

---

### Post by GeekyAdam on 2013-02-20
I got the plugin from a link to one of the posts I found about totem's YouTube plugin. I noticed links in some of the other posts and all links went to the same source so I'm sure its the only place to get the YouTube plugin files.
I don't feel like re-building totem if necessary. I've used minitube, and it works well enough, I just wanted to get totem's plugin working to have one less package installed on my system. Guess I'll stick with minitube.
Thanks for info mc4man.

---

