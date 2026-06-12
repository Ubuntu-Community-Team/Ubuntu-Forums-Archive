---
title: "So um.. how can I get this video to work? (link)"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by Roasted on 2008-03-30
[http://www.wgal.com/video/15732105/index.html](http://www.wgal.com/video/15732105/index.html)

It's a video, yet I can't play it. What can I do to get it to play?

Also - When I full screen youtube videos, it's pathetic. Very choppy, laggy, and just bad. How can I fix that?

---

### Post by wolfen69 on 2008-03-30
```
sudo apt-get install mozilla-mplayer
```
if that doesnt work, you will need to uninstall totem. go to synaptic and search for totem and completely remove every instance.(totem can conflict with mplayer) but first go to system>admin>software sources and make sure all boxes are checked. close and reload. you might want vlc to replace totem. ```
sudo apt-get install vlc
```
you also might want Medibuntu repos for even more stuff to download.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
for DVD playback:
```
sudo apt-get install libdvdcss2
```

---

### Post by LeoSolaris on 2008-03-30
Isn't Silverlight the new Microsoft codec? It's fairly new, or so I thought, and rather proprietary. Sort of like MS's answer to flash.

---

### Post by warp99 on 2008-03-30
> **LeoSolaris said:**
> Isn't Silverlight the new Microsoft codec? It's fairly new, or so I thought, and rather proprietary. Sort of like MS's answer to flash.

You are correct. Silverlight is a MS product only, but they have a legacy player available and that is a flash player. I was able to view the video without any problems using Flash for Linux r115.

Do you have the latest version of Flash from Adobe? Just type [HTML]about:plugins[/HTML] in the url line of Firefox and read the version of Flash. Is it the following:

```
File name: libflashplayer.so
Shockwave Flash 9.0 r115
```

If not you need to download and install the current version. First remove the old version:

```
sudo apt-get remove flashplugin-nonfree
```

then download the file direct from Adobe for r115:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) 

Choose the .tar.gz version (install_flash_player_9_linux.tar.gz) and download the file:

Open a console and go to the directory the file in then do the following:

```
tar -xvf install_flash_player_9_linux.tar.gz && cd install_flash_player_9_linux
```

No need to install the file libflashplayer.so, just copy it to your plugins directory of Firefox:

```
sudo cp libflashplayer.so /usr/lib/firefox/plugins
```

Run Firefox and check to see that you have r115 installed.

---

### Post by Roasted on 2008-03-30
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r115

Yep, I got it.

Is it supposed to auto-play? Or am I just stupid?

Oh, and about the flash thing to take all totem instances away. I did that and restarted firefox, but it's still laggy on full screen.

---

### Post by warp99 on 2008-03-30
> **Roasted said:**
> 
Or am I just stupid?

I don't know? You tell me. :rolleyes:

BTW here is the stream to the video:

```
mms://a1995.v12877a.c12877.g.vm.akamaistream.net/7/1995/12877/v0001/vod.ibsys.com/2008/0328/15730939.200k.wmv
```

The mplayer plugin can't seem to extract the stream from the .asx file. You can use a Firefox extension called MediaConnectivity that will allow you to view embedded media when the plugins for mplayer fail to do so:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

If you don't want to load the extension you can use the -dumpstream parameter with mplayer from the command line if you have access to the stream. The url of the stream is in the .asx file

FYI Flash loaded and played some Dulcolax commercial so I didn't go beyond the commercial because it appeared everything was working correctly. 

You'll also be happy to know that the dog the fire department rescued in the video is doing fine. ;)

---

### Post by Roasted on 2008-03-30
The Add-on worked. How did you find out about this?

edit - k it looks like it didn't work. I can play the advertisement, but after the ad it just says, ahh, you suck, can't play. Sorry suckaaaa. :(

---

### Post by warp99 on 2008-03-30
It does work with the MediaConnectivity extension, but you need to use a different player. This is how I got it to work:

Make sure you have the mplayer plugins for Firefox installed. These are needed to trick the website into thinking the Windows Media plug-in is loaded, then it gives us the .asx file:

```
sudo apt-get mozilla-mplayer
```

Next you need to install the vlc player which is in universe repostories so it needs to be enabled:

```
sudo apt-get vlc
```

You already have the MediaConnectivity extension installed so go into the configure section and change the Windows Media type from mplayer to vlc. Click apply, then OK. Reload the page for the legacy player. Click on the play icon in the square box, wait about 5 seconds and a commerical will play followed by the video.

Sometimes the video will not load, but if use a vlc skin with an embedded window you can click on the links to reload the .asx file and you can also click past the commercials. I use the Dalin Media Player skin since this does have an embedded window to view the files:

[IMG]http://www.videolan.org/vlc/skins2/Dalin_Media_Player.jpg[/IMG]

[http://www.videolan.org/vlc/skins.php](http://www.videolan.org/vlc/skins.php)

Other then these little changes everything seems to work great. You gotta love Microsoft for their embedded media crap. :lolflag:

---

### Post by Roasted on 2008-03-30
VLC is installed.
Mozilla-mplayer is installed. 

:confused:

---

### Post by warp99 on 2008-03-31
You're using the legacy player at the website:

[http://www.wgal.com/video_legacy/15732105/index.html](http://www.wgal.com/video_legacy/15732105/index.html)

Because it works with the legacy player. I was able to watch the videos using VLC and the MediaConnectivity plug-in, but I did use a different VLC skin because some of the links would not autoplay and had to be clicked again in the embedded window of VLC.

---

