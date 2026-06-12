---
title: "Embedded WMV Cnn Videos"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by crazyarlo on 2006-11-10
I cannot get embedded videos on CNN to play.  I finally got Quicktime, Youtube, and even MSNBC WMV files to play, but the Mplayer plugin for Firefox just acts like it is loading forever and never plays, and the Totem gives me a "you may not have permission" error.

I am running Xubuntu 6.10 on a Dell C400 laptop (it's awesome!) and have  updated all my repositories, installed and run both Automatix2 AND Easy Ubuntu, installed Mplayer and the plug in's, checked to make sure every darn gstreamer file was installed, installed the W32 codecs ... everything on every forum I could find.

Any thoughts from anyone?  

Arlen Owens II
Belpre,  Ohio

---

### Post by space42 on 2006-11-10
I am having the exact same issue since I upgraded to edgy.
I also cannot play the streams on gametrailers.com.  It acts like its loading / buffering but it just sits there forever.
I wish I had a solution.

---

### Post by thomasaaron on 2006-11-10
I'm having the same problem on Dapper.
I downloaded everything Automatix had to offer, but no dice.
I can play about half of my wma files.
But nothing from cnn.com's video selection.
It just loads and loads. Sometimes it looks like it might want to try to play. Then it croaks.

T

---

### Post by scotty2hott2k on 2006-11-10
same here, with edgy, mplayer and gamespot.com

---

### Post by Absurd on 2006-11-10
I too am having a problem with embedded WMV's **in general**; even with the totem plugin for firefox (perhaps it isn't meant to work with 2.0?).

---

### Post by space42 on 2006-11-11
This looks like a problem with Firefox 2.0.
I installed regular Mozilla and tested the same streams.  They all play fine under mozilla using mplayer-plugin.

Should this be filed as a bug?

---

### Post by rpkehoe on 2006-11-11
has anyone tired this with opera 9?  I am getting the same result as with FF 2.  Opera is also using a mplayer plugin

---

### Post by thomasaaron on 2006-11-12
I'm not sure its a problem just with firefox. I can't play the cnn.com streams with Mozilla either.

---

### Post by Ipsissimus on 2006-11-16
The funny thing is that I cannot play ANY video from cnn.com on my windows partition because I don't have Windows Media Player installed :) (I use Media Player Classic on windows).  But on ubuntu cnn.com plays perfectly. How? I use mplayer. Just:

```
apt-get install mplayer mozilla-mplayer w32codecs
```

And maybe some other codes packages I'm forgetting. But that should get you started. I also had a problem with 'totem-mozilla' package being installed, with breaks mplayer. Just uninstalled it and mplayer plays ANY internet streaming videos, on every site I've encountered.

You may also want to check this out for more info: []("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox")

Hope that helps,
-- Ipsissimus

---

### Post by triplehelix3 on 2006-11-16
Im running dapper.
I've followed the dapper ubuntuguide.org to the letter.
For mplayer firefox plugin, that is.
I havent got totem-mozilla or flash 9 beta installed.
I do have  mplayer mozilla-mplayer w32codecs installed, as per ubuntuguide.org.

And I have the same problem with unable to play from such as cnn
Has anyone found a solution?

---

### Post by evaldas on 2006-11-16
I can't play videos in firefox on Edgy. I followed this wiki [Playing Streaming Video from the Internet]("https://help.ubuntu.com/community/RestrictedFormats#head-e25afe1552d3a818f60e64143931b2d8e0522267"). It suggests to install **totem-gstreamer-firefox-plugin** package (and it worked on Dapper). But the thing is, that there is no more such a package for Edgy Eft :(  If you search repositories you'll find that there's this package for Dapper Drake, but not for Edgy Eft :confused:

---

### Post by Ipsissimus on 2006-11-16
Follow this wiki and install mplayer and mozilla-mplayer and w32codecs and you can see videos in firefox on Edgy:

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox")

Hope that works for you.

---

### Post by Cronjob on 2006-11-19
Yep, I have the same problem on Dapper. Both playing in Firefox 1.5 and downloading the files and watching them (from GameSpot, for example), which results in audio but no video. Same with most embedded videos.

Just suddenly stopped working. I presumed that the rest of the world might be encoding in a new version of some codecs that hadn't been updated in my gstreamer/mplayer/xine/vlc stuff, but that doesn't seem to be the case.

---

### Post by space42 on 2006-11-20
I found a resolution for my issue.  I changed mplayer plugin to use the gl setting for video out instead of xv (right click on the video window to change).

I can now stream video where I could not before.  Hope this helps someone else.

---

### Post by PARO on 2006-11-20
I have firefox 2.0 on Edgy and can see cnn.com embedded wmv videos by using firefox's media player connectivity plugin found [here]("https://addons.mozilla.org/firefox/446/") with VLC media player. If that helps anyone.

---

### Post by elephant007 on 2007-03-12
> **Ipsissimus said:**
> The funny thing is that I cannot play ANY video from cnn.com on my windows partition because I don't have Windows Media Player installed :) (I use Media Player Classic on windows).  But on ubuntu cnn.com plays perfectly. How? I use mplayer. Just:

```
apt-get install mplayer mozilla-mplayer w32codecs
```

And maybe some other codes packages I'm forgetting. But that should get you started. I also had a problem with 'totem-mozilla' package being installed, with breaks mplayer. Just uninstalled it and mplayer plays ANY internet streaming videos, on every site I've encountered.

You may also want to check this out for more info: []("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox")

Hope that helps,
-- Ipsissimus


Worked for me!  Thanks!

---

### Post by mocha on 2007-03-17
> **space42 said:**
> I found a resolution for my issue.  I changed mplayer plugin to use the gl setting for video out instead of xv (right click on the video window to change).

I can now stream video where I could not before.  Hope this helps someone else.

Hey that worked!  Thanks.

Now the big question is how do you get wmv, asf, etc working in Opera?  All I get is a grey screen where the mplayer plugin would normally pop up in Firefox.

---

### Post by FernandoGonzalez on 2007-03-24
How did you uninstall totem-mozilla? ubuntu-desktop seems to depend on it.

I'm also concerned on hindering the process of upgrading to Feisty.

I'm configuring the vlc/MediaPlayerConnectivity plugin. I'll tell you how it pans out.

---

### Post by Ipsissimus on 2007-03-24
> **FernandoGonzalez said:**
> How did you uninstall totem-mozilla? ubuntu-desktop seems to depend on it.

I'm also concerned on hindering the process of upgrading to Feisty.

I'm configuring the vlc/MediaPlayerConnectivity plugin. I'll tell you how it pans out.

You can uninstall the 'ubuntu-desktop' package with no ill effects. If you look at the details of the package you'll see its just a placeholder package. No other packages depend on it, and it does nothing.

---

### Post by sdowney717 on 2007-03-28
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

you might try this.

I can watch embedded video with mplayer plugin.

BUT, after I upgrading to feisty beta, its not working very well. sometimes it plays after a long time of sitting there. 
BUT, it used to work great with edgy.
I am hoping it is fixed.
you still have to do this with about:config

I also played with totem plugin and managed to watch one cnn embedded video.
If you install all the mms support, you will be able to do this if you right click the totem plugin to open in stand alone player.

---

### Post by sdowney717 on 2007-03-28
a few picture of embedded cnn video
Just to show anyone that it is possible to do

Embedded videos are becoming more critical to potential adopters of linux. If sites dont work, people will say linux does not work. 

Video on the web is the future. making it work easily and well should be made a priority. Most potential adopters of linux could never figure this out without a lot of help. right now its just too hard.

---

### Post by sdowney717 on 2007-03-28
I decided to download the source for 3.40 mplayer plugin and compile it myself.

[http://ubuntuforums.org/showthread.php?t=352282](http://ubuntuforums.org/showthread.php?t=352282)

This thread will show you everything you need to do to compile from source.

After you are done in about:plugins you should see 3.40 version installed.

It eventually plays the cnn videos for me, but for some reason it delays displaying the video for a long long time.
Should come up quickly!
Now, why is that?

---

### Post by mocha on 2007-03-28
Why doesn't the mplayer plugins work in Opera?

---

### Post by sdowney717 on 2007-03-29
I had a cnn grease monkey script running. It all works great now.
I think the key for me was compiling mplayerplugin from source version 3.40
When I was using edgy it worked fine, but when I switched to feisty, the mplayer plugin installed by synaptic 3.31 did not work anymore in firefox 2.0.0.3
.

---

### Post by Colonel Kilkenny on 2007-03-29
> **mocha said:**
> Why doesn't the mplayer plugins work in Opera?

It does work in certain conditions (version, compiled with --enable-x, etc.).
But it is made for mozilla so...
Anyway, at the moment I'm using mozplugger and xineplugin. Xineplugin (I compiled it myself) seems to be able to play wmv's and mozplugger all the rest. The thing is they can't get along with each other and if I load both of them nothing works. I'll try to solve this on weekend.

---

