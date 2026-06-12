---
title: "Firefox on Ubuntu 9.10 can't play Quicktime Streaming"
date: 2009-11-01
forum: Multimedia Software
---

### Post by Juno Ubun2 on 2009-11-01
I'm new to Ubuntu and I got the latest release which is Karmic Koala. Being a long time Windows user at work and Apple user at home, I really like Ubuntu so far and I'm quite positive I'll get to like it more in the days to come.

Just one problem though, Firefox can't play Quicktime streaming video. I've tried quite a lot of suggested fixes but no luck so far.

Maybe the experts here can help out a newbie. Thanks.


Juno

---

### Post by lovinglinux on 2009-11-01
[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Juno Ubun2 on 2009-11-02
Thanks :D

---

### Post by andrew.46 on 2009-11-02
Hi Juno,

> **Juno Ubun2 said:**
> Just one problem though, Firefox can't play Quicktime streaming video. I've tried quite a lot of suggested fixes but no luck so far.

Do you mean the Apple trailers for example? These will work with the gecko-mediaplayer + Firefox.

Andrew

---

### Post by Juno Ubun2 on 2009-11-02
Andrew,

Yes, I just tried the Apple Trailers a while ago and it didn't work. I'll try what you suggested and I hope it will work this time.

Thanks.

---

### Post by Juno Ubun2 on 2009-11-02
Andrew,

I installed Gecko-Mediaplayer using Synaptic Package Manager but I still can't view Quicktime Streaming video. May I request for further assistance?

Thanks.

---

### Post by Juno Ubun2 on 2009-11-02
Andrew,

I can already view clips from Apple Trailers but I still can't view MPEG4 & H.264 streaming video from a digital video recorder based CCTV.

---

### Post by Juno Ubun2 on 2009-11-10
Anyone?

---

### Post by jeffmings on 2010-01-27
Hi!

   Here's how I got Firefox 3.5 to play Apple's iPad quicktime video:
-Closed Firefox
-Deleted the plugins registry file.  That should be in your ~/.mozilla/firefox/<profile (like xxxxxxxx.default)> folder, where ~/.mozilla is generally /home/<yourname>/.mozilla.  Delete the file pluginreg.dat, which firefox will recreate when it starts.
-Using Synaptic Package Manager, ensure that the multiverse repository is enable.
-I removed the totem mozilla plugin named totem-mozilla.
-I installed gecko-mediaplayer, which automatically installed all of the mplayer goodness as well.
-Also ensure that firefox 3.5 gnome-support is installed.

I think that's it - the main issue seemed to be replacing totem with the better gecko-mediaplayer/mplayer combo.

Aloha,
-Jeff Mings

---

### Post by quimkaos on 2010-01-27
> **jeffmings said:**
> Hi!

   Here's how I got Firefox 3.5 to play Apple's iPad quicktime video:
-Closed Firefox
-Deleted the plugins registry file.  That should be in your ~/.mozilla/firefox/<profile (like xxxxxxxx.default)> folder, where ~/.mozilla is generally /home/<yourname>/.mozilla.  Delete the file pluginreg.dat, which firefox will recreate when it starts.
-Using Synaptic Package Manager, ensure that the multiverse repository is enable.
-I removed the totem mozilla plugin named totem-mozilla.
-I installed gecko-mediaplayer, which automatically installed all of the mplayer goodness as well.
-Also ensure that firefox 3.5 gnome-support is installed.

I think that's it - the main issue seemed to be replacing totem with the better gecko-mediaplayer/mplayer combo.

Aloha,
-Jeff Mings

Not working for me in U9.10 with FF 3.5.7 neither with mozilla-mplayer nor with gecko-mediaplayer plugins in synaptic

any thoughts in solving this?

---

### Post by quimkaos on 2010-01-27
this seams to work now:

```

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-plugin-vlc totem-mozilla xine-plugin

sudo apt-get install mplayer mozilla-mplayer
```tho i can see the news on [www.apple.com]("http://www.apple.com") like: [http://www.apple.com/ipad/#video](http://www.apple.com/ipad/#video)
i can't see any of the trailers in [http://www.apple.com/trailers/](http://www.apple.com/trailers/)

---

### Post by buck2825 on 2010-01-28
> **jeffmings said:**
> Hi!

   Here's how I got Firefox 3.5 to play Apple's iPad quicktime video:
-Closed Firefox
-Deleted the plugins registry file.  That should be in your ~/.mozilla/firefox/<profile (like xxxxxxxx.default)> folder, where ~/.mozilla is generally /home/<yourname>/.mozilla.  Delete the file pluginreg.dat, which firefox will recreate when it starts.
-Using Synaptic Package Manager, ensure that the multiverse repository is enable.
-I removed the totem mozilla plugin named totem-mozilla.
-I installed gecko-mediaplayer, which automatically installed all of the mplayer goodness as well.
-Also ensure that firefox 3.5 gnome-support is installed.

I think that's it - the main issue seemed to be replacing totem with the better gecko-mediaplayer/mplayer combo.

Aloha,
-Jeff Mings

works great thanks!!!!!

---

### Post by scottro on 2010-02-14
This method works for me on Lucid.  Thank you for sharing it.

---

### Post by mc4man on 2010-02-14
> ....on Lucid.

I actually find the totem-mozilla plug-in to be superior to the gecko one for quicktime - particularly on sites like apple trailers. 
Now totem-mozilla buffers the complete video very quickly - about 1 - 1.5 MB/sec here 
(the same as you would typically see for flash on youtube ect., buffered fully to /tmp

---

### Post by scottro on 2010-02-14
Was this on Lucid?  For me, the particular movie that didn't work was a little thing on Apple's site, dealing with the iWork Pages program


[http://www.apple.com/iwork/pages/](http://www.apple.com/iwork/pages/)

If I clicked on any of the links that begin with "Show me" which open Quicktime movies, I would get a message that I needed to download Quicktime. 

Following Jeffmings' suggestions, however, enabled me to do so. 

Note that I hadn't tried any other Quicktime movies prior to that.  

Also, if you're not referring to Lucid, then perhaps the difference in what we're experiencing is simply due to Lucid being in Alpha at this point.

---

### Post by kart2go on 2010-02-26
This is my first post here. I've just switched back to Linux after many years and must say I'm quite impressed with Ubuntu 9.10. Everything just worked right out of the box. Well almost everything. And thats why I'm here. After reading this thread, I got Quicktime streams to work from the Apple site. However, there is one site I just cant seem to be able to play with any plugin. Any Quicktime streams from beeline.tv don't work. The mplayer plugin says buffering and then says stopped. I've played around with cache and other settings in the plugin, but that didn't seem to work. Can anybody try and see if they get the same problem. Here is a direct link:

```
http://www.mysteryfree.tv/unicast_embed/AFTVMysteryH264500.html
```

---

### Post by bcgrown on 2010-03-02
> **jeffmings said:**
> Hi!

   Here's how I got Firefox 3.5 to play Apple's iPad quicktime video:
-Closed Firefox
-Deleted the plugins registry file.  That should be in your ~/.mozilla/firefox/<profile (like xxxxxxxx.default)> folder, where ~/.mozilla is generally /home/<yourname>/.mozilla.  Delete the file pluginreg.dat, which firefox will recreate when it starts.
-Using Synaptic Package Manager, ensure that the multiverse repository is enable.
-I removed the totem mozilla plugin named totem-mozilla.
-I installed gecko-mediaplayer, which automatically installed all of the mplayer goodness as well.
-Also ensure that firefox 3.5 gnome-support is installed.

I think that's it - the main issue seemed to be replacing totem with the better gecko-mediaplayer/mplayer combo.

Aloha,
-Jeff Mings

After following these instructions I can play embedded WMVs but not embedded Quicktime.  On a Quicktime page nothing ever happens if I press play.  Ubuntu 9.10 64-bit here, with all the latest updates applied.

---

### Post by f1champ on 2010-03-19
> **jeffmings said:**
> Hi!

   Here's how I got Firefox 3.5 to play Apple's iPad quicktime video:
-Closed Firefox
-Deleted the plugins registry file.  That should be in your ~/.mozilla/firefox/<profile (like xxxxxxxx.default)> folder, where ~/.mozilla is generally /home/<yourname>/.mozilla.  Delete the file pluginreg.dat, which firefox will recreate when it starts.
-Using Synaptic Package Manager, ensure that the multiverse repository is enable.
-I removed the totem mozilla plugin named totem-mozilla.
-I installed gecko-mediaplayer, which automatically installed all of the mplayer goodness as well.
-Also ensure that firefox 3.5 gnome-support is installed.

I think that's it - the main issue seemed to be replacing totem with the better gecko-mediaplayer/mplayer combo.

Aloha,
-Jeff Mings

I've done that, now instead of showing me to get quicktime, it appears to start to play, but it keeps saying connecting. Any idea?
I'm on 9.10 netbook remix with firefox 3.6

---

### Post by f1champ on 2010-03-19
> **f1champ said:**
> I've done that, now instead of showing me to get quicktime, it appears to start to play, but it keeps saying connecting. Any idea?
I'm on 9.10 netbook remix with firefox 3.6

bump it back down to 3.5.8 and it's working now.

if anyone has solution for 3.6, please post. Thanks!

---

### Post by dannyboy1121 on 2010-04-03
> **jeffmings said:**
> Hi!

   Here's how I got Firefox 3.5 to play Apple's iPad quicktime video:
-Closed Firefox
-Deleted the plugins registry file.  That should be in your ~/.mozilla/firefox/<profile (like xxxxxxxx.default)> folder, where ~/.mozilla is generally /home/<yourname>/.mozilla.  Delete the file pluginreg.dat, which firefox will recreate when it starts.
-Using Synaptic Package Manager, ensure that the multiverse repository is enable.
-I removed the totem mozilla plugin named totem-mozilla.
-I installed gecko-mediaplayer, which automatically installed all of the mplayer goodness as well.
-Also ensure that firefox 3.5 gnome-support is installed.

I think that's it - the main issue seemed to be replacing totem with the better gecko-mediaplayer/mplayer combo.

Aloha,
-Jeff Mings

Many thanks for this. Appreciated. ;)

---

### Post by ibexslam on 2010-08-31
Not working for me on Firefox 3.6.8. The player says "stopped." When I press play, it says "connecting" for a split second then says "stopped" again.

I.

---

