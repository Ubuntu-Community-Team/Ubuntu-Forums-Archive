---
title: "HOWTO Patch Mplayer SVN to stop Gnome Screensaver"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by mikeym on 2008-01-15
Hi, 

I recently had to patch mplayer for compiz support following this guide ([HOWTO: Download/Configure/Make/Install MPlayer from SVN w/ patch for compiz fusion]("http://ubuntuforums.org/showthread.php?t=571556")) which didn't completely work for me on it's own so I combined it with this guide on compiling compiz ( [[Howto] Successfully install the svn mplayer + gmplayer + all the codec]("http://ubuntuforums.org/showthread.php?t=558538")s). 

It worked but I found that the GNOME screensaver wasn't being disabled. I tried looking for fixes and found that there were patches but none appeared to work with the SVN version. (I also found the following fix -  [HOWTO disable screensaver and powermanager while mplayer or other apps are running]("http://ubuntuforums.org/showthread.php?t=284804") - but I wanted mplayer to behave without another program running.) So I found the ubuntu fix for their sources and tried to make it work with the SVN.

I ended up with this patch. Probably bet to apply it by extracting the patch file to the SVN mplayer directory and run:

```

patch -p1 < mplayer-svn-gnome-screensaver.patch

```

---

### Post by mikeym on 2008-01-19
I just found an issue with mplayer and the Firefox/Epiphany/etc plugin.  To re-install this plugin:

```
sudo apt-get install mozilla-mplayer
```

You can then edit the confiuration file:

```
sudo gedit /etc/mplayerplug-in.conf
```


There are some tips on how to set this up for the BBC player [here]("http://ubuntuforums.org/showthread.php?t=540412"). Also if you've installed mplayer with the compiz plugin add this line because the '*xv*' video output no longer works in the plugin.

```
vo=x11
```

---

