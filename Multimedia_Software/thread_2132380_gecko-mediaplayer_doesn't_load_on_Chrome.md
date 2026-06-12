---
title: "gecko-mediaplayer doesn't load on Chrome"
date: 2013-04-04
forum: Multimedia Software
---

### Post by monkeybrain2012 on 2013-04-04
I wonder if others have had any success in using gecko-mediaplayet in Chrome? I have been getting "unable to load mplayer plugin" since gecko-mediaplayer 1.04 in Precise to 1.08 in quantal (installed via ppa) and have tried all versions of gecko-mediaplayer in between. However, at least 1.07 is working in Fedora (the only version I have used in Fedora 17) so it doesn't seem to be an upstream problem. It works perfectly on Firefox though.

In the meantime I am using totem plugin on Chrome but it doesn't work on some sites that require the Windows Mediaplayer plugin while I know gecko-mediaplayer would work by accessing the same sites on Firefox.

Any thought or suggestion? Thanks.

---

### Post by monkeybrain2012 on 2013-04-05
Hellp?? Anyone?? No one tries to access media other than flash on Chrome or no one experiences this problem? I find that strange.

---

### Post by monkeybrain2012 on 2013-04-06
gecko-mediaplayer 1.06 doesn't load in Chrome in Ubuntu 12.10 (as said since 1.04 no version works in Chrome on ubuntu) but it does load in Chrome in Debian SID

---

### Post by monkeybrain2012 on 2013-04-11
Bump!

---

### Post by gordintoronto on 2013-04-11
Give us a site which requires gecko-mediaplayer! Have you looked at the top of the page for a message "needs your permission to run"?

This might help: [https://bbs.archlinux.org/viewtopic.php?id=113548](https://bbs.archlinux.org/viewtopic.php?id=113548)

---

### Post by monkeybrain2012 on 2013-04-11
For example [http://www.ciut.fm/](http://www.ciut.fm/)

Or, I use viewtube instead of flash for Youtube and a few other sites [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011) (have to be install with a plugin called tampermonkey, a chrome version of greasemonkey)
It works in FF with gecko-mediaplayer, but not in Chrome (with totem is ok)
I have gone to about://plugin and checked "always allowed" for gecko-mediaplayer so there is no permission issue, the error message is "Chrome cannot load mplayer plugin" . If it were a permission issue it would ask whether you allow it to run, "always or only on this site"

---

### Post by gordintoronto on 2013-04-12
I went to this page:
[http://www.caribbean-radio.com/ciut/ciut.asx](http://www.caribbean-radio.com/ciut/ciut.asx)

First time, I got the permission message, then the music played. On later visits, the music did not play. Puzzling.

---

### Post by monkeybrain2012 on 2013-04-13
Which version of gecko-mediaplayer and gnome-mplayer is that? Does it work on FF? I think the windows media player plugin  for some versions of gnome-mplayer (1.06 and 1.07 ?) doesn't work (load to about 19% and stops).. You can download the asx file and try to play it gnome-mplayer and see if that works. Which Ubuntu are you using?

Link works for me on FF (gecko-mediaplayer1.08b) but plugin doesn't load on Chrome. Ubuntu 12.04 here.

---

### Post by gordintoronto on 2013-04-13
Gecko-mediaplayer 1.0.4-2, gnome-mplayer 1.0.5-1. At the time of this testing I am using Mint 13, equivalent to Ubuntu 12.04 but with the cinammon DE. (I have several versions of *buntu and Mint installed on various partitions or flash drives.)

I right-clicked in Chrome and selected "movie player," and that worked exactly one time. Same results in Firefox. It shows the pattern as if it is going to play, but doesn't.

It plays fine in VLC: "Open Network Stream" and paste in the URL from my previous message. And it works again and again.

---

### Post by monkeybrain2012 on 2013-04-14
> **gordintoronto said:**
> Gecko-mediaplayer 1.0.4-2, gnome-mplayer 1.0.5-1. At the time of this testing I am using Mint 13, equivalent to Ubuntu 12.04 but with the cinammon DE. (I have several versions of *buntu and Mint installed on various partitions or flash drives.)

I right-clicked in Chrome and selected "movie player," and that worked exactly one time. Same results in Firefox. It shows the pattern as if it is going to play, but doesn't.

It plays fine in VLC: "Open Network Stream" and paste in the URL from my previous message. And it works again and again.

There are two issues here

1) window media plugin for gecko-mediaplayer (actually gnome-mediaplayer) doesn't work. You can check if this is the case if you download the .asx file and try to open it with gnome-mediaplayer.It seems that window media plugin for gnome-media-player has not been working since version 1.06 (quantal)  but it is working again with 1.08 ( installed from ppa) But I remember 1.04 used to work in Precise. 

In FF my work around is to simply disable window media plugin and just use vlc to open those links. In Chrome you may have to actually download the asx file.

2) the problem reported in this flag. Gecko-mediaplayer doesn't load at all in Chrome. This seem to start since version 1.05 or 1.06 and it seems to be specific to Ubuntu, as I have tested some versions that don't load (in Chrome) in Ubuntu but they work in Fedora and Debian. so maybe Mint doesn't have the problem either.

---

### Post by gordintoronto on 2013-04-14
Now you have enough information to file a bug report. [smile]

Mint is so close to Ubuntu that I am very surprised to see a difference in how Chrome behaves.

---

### Post by gordintoronto on 2013-04-15
Just for yucks, I tried some experiments in Xubuntu 12.10. By default, gecko... and the other program are not installed. CUIT would not play in either FF or Chrome. However, 680News, which also uses a Windows media format, played the live stream just fine in both. (I had installed the Restricted Extras the same day I installed the OS.)

I installed the two programs. Firefox played the live stream beautifully, and it was repeatable. Chrome said, "Couldn't load plug-in." That was the first time I saw that message. Both programs were version 1.0.6-1.

---

### Post by monkeybrain2012 on 2013-04-15
Yeah both 1.06 and 1.07 don't work for CIUT and a few other sites that use the window media plugin. And those plus 1.08 and 1.05 don't load in Chrome (at least for Ubuntu)

---

