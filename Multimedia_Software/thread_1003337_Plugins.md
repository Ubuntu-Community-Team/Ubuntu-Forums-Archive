---
title: "Plugins"
date: 2008-12-06
forum: Multimedia Software
---

### Post by Achilles124 on 2008-12-06
I cannot watch realplayer stream in firefox. Can somebody take a look at the installed plugins? Maybe that is the problem.

> Shockwave Flash

    Bestandsnaam: libflashplayer.so
    Shockwave Flash 9.0 r124

Shockwave Flash

    Bestandsnaam: libflashplayer.so
    Shockwave Flash 10.0 r12

MIME-type 	Beschrijving 	Achtervoegsels 	Actief
application/x-shockwave-flash 	Shockwave Flash 	swf 	Ja
application/futuresplash 	FutureSplash Player 	spl 	Ja

DivX Browser Plug-In

    Bestandsnaam: mplayerplug-in-dvx.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

QuickTime Plug-in 7.4.5

    Bestandsnaam: mplayerplug-in-qt.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

RealPlayer 9

    Bestandsnaam: mplayerplug-in-rm.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

mplayerplug-in 3.55

    Bestandsnaam: mplayerplug-in.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Java(TM) Plug-in 1.6.0_10-b33

    Bestandsnaam: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_10


GCJ Web Browser Plugin 0.96.1

    Bestandsnaam: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.



---

### Post by Achilles124 on 2008-12-10
I am trying to figure out how everything works. I have mozilla-plugin-vlc installed. When I have to select what extension should be opened with what program within Mozilla Firefox, which should I choose?

/usr/share/bug/mozilla-plugin-vlc
/usr/share/doc/mozilla-plugin-vlc
/var/lib/dpkg/info/mozilla-plugin-vlc.list
/var/lib/dpkg/info/mozilla-plugin-vlc.md5sums


from these four?

thanks beforehand.

---

### Post by Achilles124 on 2008-12-10
Okay, I have figured it out.

[http://www.linuxquestions.org/questions/linux-newbie-8/firefox-mplayerplugin-no-video-334055/]("http://www.linuxquestions.org/questions/linux-newbie-8/firefox-mplayerplugin-no-video-334055/")

Last post:
" I was having this problem and finally got it to work. In Firefox, click on a video. When the mplayer window opens, I saw the video url in the screen (no video) but could hear the audio. I right-clicked on the mplayer window and selected "Configure". When the configuration window opens, the "Video Output" box was empty. I selected "X11" and I now have video.
Oddly, there is nothing selected for "Audio Output" and yet audio woks just fine...."

that is what worked with me.

---

