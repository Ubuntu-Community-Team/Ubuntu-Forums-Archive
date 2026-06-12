---
title: "Codec not working for xvid mpeg-4"
date: 2010-07-18
forum: Multimedia Software
---

### Post by digitalis_46613 on 2010-07-18
When I had Ubuntu 8.10 video worked fine.  When I upgraded to 9.04, 9.10, etc, I haven't been able to play anything .AVI.  Any ideas?  I tried to reinstall the codec, but it says no codec found.  I use Windows to watch AVIs now....
HELP!

---

### Post by mc4man on 2010-07-18
I would try this

Open synaptic, search ffmpeg and mark for complete removal **all installed** ffmpeg libs, libavcodec[COLOR="Blue"]XX[/COLOR], libavformat[COLOR="Blue"]XX[/COLOR] ect. (scroll down to get all - last one is libswscale[COLOR="Blue"]X[/COLOR]

you will lose a player and gstreamer-plugin or two, no matter, you can reinstall after.

When done run this to restore the basic gstreamer plugins and then re-install any lost players ( synaptic -> File -> history will show

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly

```

Later if needed you can install the multiverse gstreamer plugins if needed and upgrade your ffmpeg libs to the 'extra' versions (mainly needed for encoding, not decoding

---

### Post by digitalis_46613 on 2010-07-18
ok, I removed all those, and pasted the code in terminal.  I went straight to run an avi, and it says (after searching for plugins) "No Packages with the requested plugins found" "DivX MPEG-4 Version 5 Decoder"
I added ffmpeg back in, installed my removed software, and added xine.
It still has the same error as when I started. 
It almost seems as if my sources are old?  Maybe it's searching the wrong place for the plugins?
I have no ideas...

---

### Post by mc4man on 2010-07-18
Not sure - xvid or divx doesn't take anything out of the ordinary to decode.
Is there anyway to get a sample of your problem file?

Have you tried in a non gstreamer player (vlc, mplayer, ect.?

Here are a couple of similar type files,(right click save link as), can you play them?

cats.avi
[http://samples.mplayerhq.hu/V-codecs/DX50-DivX5/](http://samples.mplayerhq.hu/V-codecs/DX50-DivX5/)
ayan....avi
[http://samples.mplayerhq.hu/V-codecs/DIV5/](http://samples.mplayerhq.hu/V-codecs/DIV5/)
green.avi (no audio
[http://samples.mplayerhq.hu/V-codecs/XVID/old/](http://samples.mplayerhq.hu/V-codecs/XVID/old/)

While not needed for xvid, in lucid i like to use the latest gstreamer plugins, from this ppa

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by Yellow Pasque on 2010-07-19
EDIT: These plugins are available in gstreamer0.10-plugins-bad-multiverse package

---

### Post by mc4man on 2010-07-19
> plugins are available in gstreamer0.10-plugins-bad-multiverse package

While I've never found it necessary to have the multiverse plugin(s) installed to decode xvid/divx/MPEG-4 *, being that the ffmpeg plugin should handle , it certainly would be a good idea to install.

> ~$ gst-inspect plugin xvid
Plugin Details:
  Name:			xvid
  Description:		XviD plugin library
  Filename:		/usr/lib/gstreamer-0.10/libgstxvid.so
  Version:		0.10.18
  License:		GPL
  Source module:	gst-plugins-bad
  Binary package:	GStreamer Bad Multiverse Plugins (Ubuntu)
  Origin URL:		[https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad-multiverse0.10](https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad-multiverse0.10)

  xvidenc: XviD video encoder
  xviddec: XviD video decoder

  2 features:
  +-- 2 elements


Edit: I'm still not to convinced that plugin (xvid) is used for playback, though gstreamer at times remains a bit of a mystery to me
For all such files I see this in a verbose output

> GST_PLUGIN_LOADING gstplugin.c:800:gst_plugin_load_file: plugin "/usr/lib/gstreamer-0.10/libgstffmpeg.so" loaded
 GST_ELEMENT_FACTORY gstelementfactory.c:363:gst_element_factory_create: creating element "ffdec_mpeg4"

---

