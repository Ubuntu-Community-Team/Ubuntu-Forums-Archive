---
title: "mplayer problems"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by logos34 on 2006-11-21
Can't seem to get Mplayer to work in 6.10 Edgy.  I carefully followed the multimedia install instructions on the Restricted Formats page.  I get two types of error messages: a "fatal error" concerning "video_out (-vo)" and one that reads "Can't resolve name for AF_INET6: grm33gstreamos.com" (trying to play a quicktime movie trailer).  On the rare occasions I can get it to start up it quits halfway thru the clip.  It even froze my desktop today -- had to restart.  I tried one suggestion of changing the mplayer.conf file to read "xv=true" or something like that (didn't work -- set it back to default "vo=xv") and I've fiddled in vain with the video settings in mplayer prefs-- set it to recommended X11/xv, tried frame dropping, etc, etc.  All the codecs (including QT) are in so far as I can tell from the codecs tab.  I have the mozilla-plugin installed and Media Connectivity add-on.  (The latter works fine on my windows partition).  

I am also having problems--like many--getting Realplayer10 to work as advertised (low-bandwidth BBC streaming video is about all it can handle).  Green screens, stuttering, choppy playback (particularly with commercials).  Totem-xine, on the other hand, handles streaming wmv video fine.  DVD playback working in Totem, Kaffeine, Gxine.  Flashplayer 9 beta works pretty well.  

Any help appreciated.

---

### Post by sizzam on 2006-11-22
Here is the fix that works for me for "Error opening/initializing the selected video_out (-vo) device." :

Go to Preferences in Mplayer, click the Video tab, and select "x11" in the list.

and here is the fix that works for me for "Can't resolve name for AF_INET6: grm33gstreamos.com" :

Open the file ~/.mplayer/config
and add the following line to the bottom:

```
prefer-ipv4 = yes
```

---

### Post by logos34 on 2006-11-22
> **sizzam said:**
> Here is the fix that works for me for "Error opening/initializing the selected video_out (-vo) device." :

Go to Preferences in Mplayer, click the Video tab, and select "x11" in the list.

and here is the fix that works for me for "Can't resolve name for AF_INET6: grm33gstreamos.com" :

Open the file ~/.mplayer/config
and add the following line to the bottom:

```
prefer-ipv4 = yes
```

 
I modified the mplayer config and the gstreamer errors no longer pop up.  X11setting doesn't seem to help.  I did discover, though, that gxine does a perfect job with Quicktime trailers -- look and sound great.  So now that's my default qt file player.  Ideas, anyone, on how to get mplayer to work?

---

### Post by drphilngood on 2006-11-22
This [how2]("http://ubuntuforums.org/showthread.php?t=76946") should get you sorted.

---

