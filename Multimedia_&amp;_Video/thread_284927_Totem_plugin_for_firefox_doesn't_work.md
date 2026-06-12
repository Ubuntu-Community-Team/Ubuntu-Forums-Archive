---
title: "Totem plugin for firefox doesn't work"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by michaeljb2005 on 2006-10-26
For some reason the totem plugin is not working in firefox for me. I tried reinstalling the plugin but that doesn't seem to do anything. As far as what happens when I try to play files the area the video should be is just blank. I understand this could be due to an incorrect link somewhere, but I'm not sure how it should link to the plugin. I fresh installed edgy but used the same home directory from dapper to edgy. Could that cause some problem? I have all necessary codecs to play video outside of the browser so that is not a problem.  Help would be appreciated. Thanks.

edit:  I'm on edgy, it worked on dapper, but is not working on edgy.

---

### Post by tommcd on 2006-10-27
I have the same problem. I can download the videos and watch them with either vlc or totem or mplayer, but I can't stream them directly in firefox on edgy. It all worked fine in dapper. I am searching for a solution. I hope you will do the same. If I find an answer I'll post it here. Please do the same.
I don't think the same /home directory is the problem. I can play all my .avi files from my home directory just fine with vlc.

---

### Post by gerowen on 2006-10-27
The mozilla-mplayer plugin package works wonderfully, but for some reason I cannot get it to take precedence over the totem mozilla plugin.  If you guys can figure it out let me know, the mplayer browser plugin rocks, even lets you save movies.

---

### Post by tommcd on 2006-10-27
Are yo on edgy? I got the mozilla-mplayer plugin and I can't get streaming video to work.

---

### Post by gerowen on 2006-10-27
Do you have your win32 codecs installed?  By default none of the players support mp3, wmv, wma and other proprietary codecs, and you have to install them yourself.  There's a topic in here somewhere explaining where to get them.

Yeah I'm on edgy, what did you do to make it use the mplayer plugin instead of the totem one?

---

### Post by michaeljb2005 on 2006-10-27
I have all the necessary codecs to play the file outside of the browser so I would assume if it worked correctly it should be able to play in.

---

### Post by dolphinholmer on 2006-10-27
Navigate to /usr/lib/firefox/plugins and delete the libtotem plugin links (need to be root to do this) Other compatible plugins that are installed will then be used

---

### Post by michaeljb2005 on 2006-10-27
So effectively, by telling me to do this, you're saying the totem plugin does not work?

---

### Post by dolphinholmer on 2006-10-27
well i can't get it to work either. wouldn't want to say anything so definite as 'it *doesn't* work.'

---

### Post by michaeljb2005 on 2006-10-27
Why wouldn't uninstalling the plugin simply fix the problem instead of deleting it?

Edit:  Nevermind, you can't uninstall it because it is a dependency for other packages.

---

### Post by michaeljb2005 on 2006-10-27
> **dolphinholmer said:**
> Navigate to /usr/lib/firefox/plugins and delete the libtotem plugin links (need to be root to do this) Other compatible plugins that are installed will then be used'

This method seems to work as it reverts to mplayer.  Thanks a lot.

---

### Post by tommcd on 2006-10-27
I tried removing the libtotem plugin links, and I stll can't seem to stream video. I have w32codecs, mozilla-player. Before doing this I messed around with file types preferences in firefox under edit>preferences>content>manage (under file types). My download optios box in firefox looks like this:

SPL SPL file..............open with shokwave flash
QTL QTL file..............opens with Quicktime plugin
WM WM file...............opens with WMP plugin
WVX WVX dike.............opens with WMP plugin
FLI FLI file..............opens with mplayer plugin3.31
AU Basic uLaw audio.......opens with mplayer plugin 3.31

Am I missing something? What does your download options box look like?

---

### Post by michaeljb2005 on 2006-10-27
Tommcd I'm not at home right now but when I do get there i'll answer your post.

---

### Post by tommcd on 2006-10-27
Thanks Michael, I will be heading off to work soon. I will have to pick up with this tomorrow. I think I am probably just missing a plugin or something, not sure. Anyway, thanks for any help you can provide. Please list all the firefox plugins you currently have.

---

### Post by michaeljb2005 on 2006-10-28
Tommcd my download options look like yours.  Make sure you deleted all the libtotem files, and then try reinstalling the mplayer plugin.

---

### Post by tommcd on 2006-10-29
Michael, thanks for getting back. I have since discovered that it is only MPEG videos that I can't stream. With MPEG, all I get is a black window that says (no video). WMV videos stream fine. I can download MPEG videos and watch them. I just can't stream them. about-plugins in firefox show that I have MPEG enabled for vlc and mplayer. Also, in about-plugins, I have 2 listings for mplayerplug-in 3.31, with slightly different sets of codecs listed. 
Also, the WMV videos will stream in movie-player (not mplayer) with or without those libtotem links deleted. (I backed them up to my home folder, so I could easily replace them if needed, and for troubleshooting purposes). Do your videos stream in mplayer? Am I missing a codec for streaming MPEG?

---

### Post by gerowen on 2006-10-29
I finally got mine working.  I used [Automatix](http://www.getautomatix.com/) to install the AUD/VID codec package and now even totem picks up all the codecs, so I just left it alone, no use in installing 3 or 4 media players when the default one works.

---

### Post by michaeljb2005 on 2006-10-29
> **marcusdean.adams said:**
> I finally got mine working.  I used [Automatix](http://www.getautomatix.com/) to install the AUD/VID codec package and now even totem picks up all the codecs, so I just left it alone, no use in installing 3 or 4 media players when the default one works.

I had all the codecs from Automatix, the problem was the libtotem plugin.  But if yours works, then great!

---

### Post by michaeljb2005 on 2006-10-29
> **tommcd said:**
> Michael, thanks for getting back. I have since discovered that it is only MPEG videos that I can't stream. With MPEG, all I get is a black window that says (no video). WMV videos stream fine. I can download MPEG videos and watch them. I just can't stream them. about-plugins in firefox show that I have MPEG enabled for vlc and mplayer. Also, in about-plugins, I have 2 listings for mplayerplug-in 3.31, with slightly different sets of codecs listed. 
Also, the WMV videos will stream in movie-player (not mplayer) with or without those libtotem links deleted. (I backed them up to my home folder, so I could easily replace them if needed, and for troubleshooting purposes). Do your videos stream in mplayer? Am I missing a codec for streaming MPEG?

I would consider getting the codecs through automatix if I were you just to be sure you have all the codecs.  If after that, you have a problem, then it is probably a problem with how they are installed.

---

### Post by gerowen on 2006-10-29
If you don't want to use the totem plugin, you can install the mozilla-mplayer package and delete all of the totem plugin files from /usr/lib/firefox/plugins .  This is safe to do, if you change your mind you can just open Synaptic, lookup totem-mozilla (I think that's it) and mark it for re-installation.

---

### Post by tommcd on 2006-10-30
Thanks Marcus. I have the mozilla-mplayer package and I deleted all libtotem plugins. I even reinstalled mozilla-mplayer after deleting them as Michael suggested. I still can't stream mpegs, but I can download them and watch them that way.
about-plugins in FF shows no totem plugins whatsoever. This is my only problem with Edgy. I think I am probably just missing something, but I just can't figure it out. Searching the forums I have found nothing about streaming problems in Edgy. If you have any other ideas, please reply. And thanks for the assistance.

---

### Post by gerowen on 2006-10-30
When you have the mplayer-mozilla package installed and have removed the totem plugin files, can you see an mplayer media control box at all in pages with embedded media?  If you can, right click it and go to configure and check those options, it may not be set to stream it right away or something.  Just a thought, sorry I can't be of any more help.

---

### Post by tommcd on 2006-11-18
Fixed!! 
I can now stream video in firefox.
 I was able to play any video (wmv, mpeg, quicktime, avi) that I downloaded to my home folder, I just could not stream them directly in firefox. The way I "fixed" it was to install the excellent firefox extension 'media player connectivity':
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
This allows you to easily select which media player will open which type of file. It then plays the file in a seperate window. It seems to work pretty well in FF 2.0. I use xine for video, as I would get an error message with mplayer (the video still played though).
If anyone else can't stream video (but can play video from your home folder) give it a try.

---

### Post by YODAR on 2007-12-23
The  day before Christmas eve I see your post. It looks like Firefox takes the plugin without complaint

Thank you Thank you Thank you 

yodar in O'do

---

