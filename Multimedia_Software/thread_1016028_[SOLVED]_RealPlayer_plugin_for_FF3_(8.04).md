---
title: "[SOLVED] RealPlayer plugin for FF3 (8.04)"
date: 2008-12-19
forum: Multimedia Software
---

### Post by afeasfaerw23231233 on 2008-12-19
I think I posted it in a wrong place. So I post it here again. Sorry for double posting.

Real player plugin for firefox (32-bit)8.04
I've downloaded and installed realplayer and it works fine while playing rmvb from my local disk. But how can I get a realplayer plugin for firefox so that I can listen to radio? 

Also I've just installed ubuntu 8.04 AMD64. I cannot find real player + real ff3 plugin on the real website or in synaptic to install. Where can I get it? Many Thanks!

---

### Post by wolfen69 on 2008-12-19
i use mozilla-mplayer plugin for firefox, and most streaming content works. i also remove totem-mozilla first, but that's optional i believe. i just like using 1 plugin at a time.

---

### Post by gandaran on 2008-12-19
> **afeasfaerw23231233 said:**
> I think I posted it in a wrong place. So I post it here again. Sorry for double posting.

Real player plugin for firefox (32-bit)8.04
I've downloaded and installed realplayer and it works fine while playing rmvb from my local disk. But how can I get a realplayer plugin for firefox so that I can listen to radio? 

Also I've just installed ubuntu 8.04 AMD64. I cannot find real player + real ff3 plugin on the real website or in synaptic to install. Where can I get it? Many Thanks! 
the plugin comes with realplayer 11 gold, you have to run some commands  to get it to work and you have to have the totem plugin for firefox too, it won't work if you using another firefox plugin like mplayer or vlc, the real player plugin will only handle real audio and video files totem does the rest.
personally I think the  real player plugin is limited and not needed, you can get the best results for firefox online streaming with having both mplayer-plugin and totem-plugin installed, mplayer handles real video and audio just as good as realplayer + many other codecs
follow these instructions,[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin) run all those commands for firefox plugin integration

about the 64-bits realplayer I don't know anything, maybe there isn't one!

---

### Post by afeasfaerw23231233 on 2008-12-19
Thanks for quick replies. I've followed this link [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin) and reinstall realplayer again. In my about:plugins these things show up: 
```
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
File name: libtotem-complex-plugin.so
The Totem 2.22.1 plugin handles video and audio streams.
MIME Type
Description
Suffixes
Enabled
audio/x-pn-realaudio-plugin
RealAudio document
rpm
Yes

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
File name: nphelix.so
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4434 built with gcc 3.4.6 on Oct 1 2008
MIME Type
Description
Suffixes
Enabled
audio/x-pn-realaudio-plugin
RealPlayer Plugin Metafile
rpm
Yes
```

But Mplayer plugin instead of Realplayer runs everytime I play live radio or radio/video archives. And Mplayer fails to play any video &#8211; it only shows &#8220;Stop&#8221;. While Mplayer is playing radio archives I cannot skip the playing time on the bar, and the quality seems a bit strange and bad. I cannot get BBC radio live being played too.

Please see my screenshots.

How can I get them played properly? The Realplayer plugin in 7.10 just play audio/video on all sites perfectly. So I would preferred Realplayer. Thanks for help!

The link of my local radio video programme archive example
[http://www.rthk.org.hk/asx/rthk/tv/30thgoldsongs/20080122.asx](http://www.rthk.org.hk/asx/rthk/tv/30thgoldsongs/20080122.asx)
radio archive
[http://www.rthk.org.hk/smi/rthk/radio3/peterking/20081217.smi](http://www.rthk.org.hk/smi/rthk/radio3/peterking/20081217.smi)

---

### Post by gandaran on 2008-12-20
> How can I get them played properly? The Realplayer plugin in 7.10 just play audio/video on all sites perfectly. So I would preferred Realplayer. Thanks for help!
thats exactly the one thing I don't like mplayer too much, it some times has difficulty connecting, it just stops! but if you insist a lot it will work and some days it just works nicely! thats why I still prefer the totem plugin for most video streaming and mplayer for real and quicktime video only.
has I have said before it won't work if the mplayer-plugin is installed, you have to remove the mplayer plugin and just keep the totem-plugin installed and maybe run those real player firefox integration commands again, the real player plugin is system linked to the totem-plugin and works every-time you find a web-page with real or audio video

---

### Post by afeasfaerw23231233 on 2008-12-28
Realplayer plugin of firefox works after removing totem and mplayer plugins from Synaptic. Thanks for help

---

