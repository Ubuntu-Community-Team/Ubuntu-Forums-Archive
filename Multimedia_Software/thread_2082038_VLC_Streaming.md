---
title: "VLC Streaming?"
date: 2012-11-08
forum: Multimedia Software
---

### Post by PDA1 on 2012-11-08
Here's what I want to do;

Copy any video I watching while on the web- particularly the Youtube video at this link;

[http://www.youtube.com/watch?v=nEwSpfs1Sw8&feature=related](http://www.youtube.com/watch?v=nEwSpfs1Sw8&feature=related)

Of course that's not really the video I want but I want to figure out how to watch video, streaming, using VLC player. 

Using the VLC Media------>"streaming" and entering the http address doesn't do anything- no video is streamed.

Any ideas from those of you who actually have done this sort of thing?

---

### Post by evilsoup on 2012-11-08
This is actually my standard way of watching internet videos.

The easy way - this works for Youtube, Vimeo, and Dailymotion links - is to install the Firefox add-on [open with]("http://www.darktrojan.net/software/addons/openwith"), and set up VLC (to get at the settings, once you have the add-on, point firefox to about:openwith). You'll have to right-click on links and select 'Open Link with VLC media player'.

If you open VLC on the commandline with a youtube (or Dailymotion/Vimeo) link it'll play the video
```
vlc [http://www.youtube.com/watch?v=nEwSp...eature=related]("http://www.youtube.com/watch?v=nEwSpfs1Sw8&feature=related")
```should work perfectly fine.

You can take advantage of this by creating a keyboard shortcut. You'll need to install [xclip]("apt://xclip"); then, go to keyboard shortcuts and set something to
```
vlc $(xclip -selection clipboard -o)
```Then you can ctrl+c copy (or right-click 'copy link location') a youtube or whatever link, and then hit the keybinding to activate that scrap of script (I use ctrl+alt+x, but that's arbitrary). The advantage of this over the Open With version is that you can also view embedded videos: just right-click the video and select 'copy video URL'...

There are only a few websites that VLC can 'read' for videos; for others you need a direct link to the video. Fortunately, another Firefox add-on comes to the rescue: [DownloadHelper]("http://www.downloadhelper.net/") can let you copy the direct URLs of a page's media, which of course feeds into the keyboard shortcut method described above.

Also, in VLC's advanced preferences, under 'Input/Codecs', you can choose your preferred quality of video streams. By default it's 'highest possible' IIRC, not suitable for lower-end machines.

---

