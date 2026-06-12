---
title: "Online media problems"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by rgraves on 2006-11-16
I keep getting error messages like the one below at certain web sites. I used Automatix to install all available codecs, I thought. Error says I need to install additional plugins.

I'm running Ubuntu Edgy and Firefox 2.0. I've tried changing prefs in Firefox to use but it doesn't give me the option to change plugins for different types of media files, although I have several installed. (quciktime, mplayer, windows media player)

Appreciate any help.

Thanks,
Bob


Totem could not play 'mmsh://wms.scripps.com/networkad/house/hammered-dp.wmv?MSWMExt=.asf'.

Video codec 'Windows Media Video 9' is not handled. You might need to install additional plugins to be able to play some types of movies

---

### Post by encompass on 2006-11-17
You don't have the proper codec installed...
look up restricted formats ubuntu in google.

---

### Post by billstei on 2006-11-23
Here is what I did to resolve the "Totem could not play mmsh ..." problem:

Using Add/Remove Applications:

1) Installed MPlayer Plugin for Mozilla
2) GStreamer extra plugins (might not need this but I did)

Using Synaptic Package Manager:

3) Installed gstreamer0.8-mms (mms plugin for gstreamer)

Using Terminal:

4) Disabled the mozilla totem plugin(s):
cd /usr/lib/mozilla-firefox/plugins
sudo mkdir disabled-plugins
sudo mv libtotem* disabled-plugins

Seems like there should be an easier way to disable mozilla plugins, but I can't find one.  Or maybe a way to change file type (protocol type?) handling in Firefox.

Hopefully I got everything needed written here.  If not let me know and I'll see if I can figure out what I missed.

Bill

P.S. Hey devs, how about including the gstreamer0.8-mms in the "GStreamer extra plugins" Add/Remove package?

---

