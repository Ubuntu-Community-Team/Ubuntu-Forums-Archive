---
title: "&quot;Play to&quot; function similar to windows 7?"
date: 2010-05-23
forum: Multimedia Software
---

### Post by mehepsk on 2010-05-23
Is it possible to add a "play to" menu in the context menu in nautilus like in windows 7? 

For those of you who don't know what I'm talking about:

When you right click a media file (avi/mp3/mkv etc) in windows 7, it lets you select "Play to" and then lists all upnp/dlna devices on the network, and the amazing thing is that when you select a device, the media file is actually played on that device! It would be so much easier to select a file and then "play to" my xbmc htpc, than to move the video to the htpc and then index it and then browse for it on the htpc and then remove it after I've seen it... 

I couldn't find anything about a feature like that...? There must be someone else, beside me, that would love a feature like that?


I know I can install ushare and stream that way, but the big difference is that the movie is started from my computer and not on the xbox, htpc, tv, av-reciever or what you use to watch movies over the network! It would make it so much easier! Setting up sharing, and then adding them to what you use for playback and then finally browse to your movie and selecting play is just not worth it when you know how much easier it can be done using "play to" for a few movies...


Is there anything like this for ubuntu?

---

### Post by sgosnell on 2010-05-23
Right-click, and select Open With...  That will list all the possible devices Ubuntu knows about.  The default Open should open it with whatever player you have set as default.  It doesn't say "Play to", but it does the same thing.

---

### Post by mehepsk on 2010-05-24
I don't find any of my upnp/dlna devices in the "open with" menu, only my applications... Is it supposed to list upnp/dlna devices in the "open with" menu? I don't think dlna devices is supposed to show up in the open with menu..

---

### Post by sgosnell on 2010-05-24
Sorry, I misread your post.  I've never tried to do what you want, because I don't have any devices connected other than a printer/scanner.  Maybe someone will be along who does that...

---

### Post by iceman_89 on 2010-11-01
Hello,

Different ideas:
1. [http://ubuntu.allmyapps.com/apps/install-gupnp-tools-upnp-av-control-point](http://ubuntu.allmyapps.com/apps/install-gupnp-tools-upnp-av-control-point)
2. sudo apt-get install upnp-inspector
   Right-click on device --> control MediaRenderer

For more infos see:
[http://jorgenmodin.net/index_html/archive/2009/12/26/list-of-open-source-dlnaupnp-av-software-devices](http://jorgenmodin.net/index_html/archive/2009/12/26/list-of-open-source-dlnaupnp-av-software-devices)

---

### Post by nithinphilips on 2010-11-29
I tried iceman_89's suggestion and it works! There is no Nautilus integration, but it shouldn't be terribly difficult to write a script to make that possible.

My setup has a [Mediatomb server]("http://mediatomb.cc/"), [GUPnP AV Control Point]("http://www.gupnp.org/"), and a Samsung  LNxxC6xx series TV with AllShare/DLNA. Windows 7's 'Play To..' is basically Mediatomb+GUPnP AVCP. When you click 'Play To..', the file is added to the Windows Media Player library (and the media share) and then the URL is pushed to the device. My mediatomb server runs on a remote computer (a local installation should work the same) and the GUPnP AVCP runs on my laptop. I can browse the mediatomb share from the laptop and select and play media. The TV's media browser interface is very slow and browsing a large share is nearly impossible, so this works great for me. As an added benefit, once you start playing media (from a remote UPnP/mediatomb server), you can turn off your laptop and the media will continue to play.

One downside is that there is no playlist support in GUPnP AVCP. But if you want to just play music, [Leia]("http://leia.sommerfeldt.f-m.fm/") has playlist support, but it won't let you play video files. There is also another control point program, [KinskyDesktop]("http://oss.linn.co.uk/trac/wiki/KinskyDesktop"), it has a lot of features, but the linux ui is just awkward.

To install the programs:
```

sudo apt-get install [mediatomb]("apt://mediatomb")
sudo apt-get install [gupnp-tools]("apt://gupnp-tools")

```

---

