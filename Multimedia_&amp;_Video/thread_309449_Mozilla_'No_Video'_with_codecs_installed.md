---
title: "Mozilla 'No Video' with codecs installed"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by mistermax on 2006-11-29
I have installed the restricted formats codecs, have tried using totem and gstreamer and also VLC but I cannot watch the rails screencasts -
[http://media.rubyonrails.org/video/flickr-rails-ajax.mov](http://media.rubyonrails.org/video/flickr-rails-ajax.mov)

about:plugins reports that I have-

Shockwave Flash
VLC multimedia plugin
Totem Web Browser Plugin 2.16.2
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
Windows Media Player Plug-in 10 (compatible; Totem)
DivX® Web Player
QuickTime Plug-in 7.0 (compatible; Totem)
QuickTime Plug-in 6.0 / 7
RealPlayer 9
Windows Media Player Plugin
mplayerplug-in 3.31
Java(TM) Plug-in 1.5.0_08-b03
MozPlugger 1.7.3 handles QuickTime Windows Media Player Plugin
mplayerplug-in 3.31
MozPlugger 1.7.3 handles QuickTime Windows Media Player Plugin

(and, yes it does list MozPlugger twice..)

Initially I had followed the steps I used before, from the Ubuntu hacks book. This didn't seem to set up the video in mozilla for me though, so I tried out the Automatix installer.

I can watch wmv files, for instance in VLC, so am I missing something out?

---

### Post by crane on 2006-12-12
I seem to be getting the same thing. As far as I know everything is installed. Still looking though. Any input would be most helpful.

---

### Post by nabdan on 2006-12-12
Hi all,

Same here, no way to play windows media streaming but everithing works locally.

If someone have an idea :confused: 

Bye.

---

### Post by ciscosurfer on 2006-12-12
I can view the Flickr-Rails-Ajax.mov just fine.

Perhaps try installing Automatix2 and then installing from it the AUD-DVD codecs, Multimedia Codecs/Apps, Swiftfox and Swiftfox Plugins (the plugins being the key here), as well as Mplayer and it's plugins.  If you are so inclined and able to do so, install the non-free codecs as well (which I believe is the AUD-DVD package).  If you have Automatix2 installed, remove them and then reinstall again.  That's helped me in the past.

My 2 cents. (and it's a cool movie taboot)

---

### Post by mcduck on 2006-12-12
works fine for me with totem plugin (I also have mplayer-plugin & flash 9 and together they seem to hande every video I can find from the web)

(and no, I have never used Automatix. I rather learn to do things myself ;) )

---

### Post by eggdeng on 2006-12-12
No problems visualising the ruby stuff. In fact I've yet to come across a file I can't reproduce. I'm using firefox 2.0 with the following plugins.

libflashplayer.so
libnullplugin.so
mplayerplug-in-gmp.so
mplayerplug-in-qt.so
mplayerplug-in-rm.so
mplayerplug-in-wmp.so
mplayerplug-in.so
nphelix.so (real)
nppdf.so (adobe)

Noticed that the Mplayer plugins you are using are a lower version than mine (3.25). I used Automatix2 & would recommend it with no reservations. Another possibility is that you may have the wrong plugin set to open a certain type of file. You can fix that in Preferences -> Content -> File Types.

---

