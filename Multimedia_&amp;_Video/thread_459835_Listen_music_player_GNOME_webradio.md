---
title: "Listen music player GNOME webradio"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by Tomasnrsk on 2007-05-31
Hi all,
I need to help with playing webradios in Listen music player, It just doesnt work. I choose Webradio - SHOUTcast then for example Top 25 Streams and some radio, click to play and I cant hear any sound.

/usr/lib/listen/widget/tray.py:45: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  try: import egg.trayicon
-> [http://www.shoutcast.com/directory/?numresult=25&startat=0&sgenre=TopTen](http://www.shoutcast.com/directory/?numresult=25&startat=0&sgenre=TopTen)
Stream OEF 1 False
-> [http://www.shoutcast.com/directory/?numresult=25&startat=0&sgenre=TopTen](http://www.shoutcast.com/directory/?numresult=25&startat=0&sgenre=TopTen)
Stream OEF 1 False
Found web radio:  24
I:Radio Playlist:Uri choosen: [http://222.122.131.29:22000](http://222.122.131.29:22000)
I:Radio Playlist:Uri choosen: [http://222.122.131.29:22000](http://222.122.131.29:22000)

And I forgot that I am using Ubuntu Feisty with Python 2.5.1, gstreamer 0.10 and Listen 0.5. All other sounds work fine in Listen only this webradio doesnt play.

---

### Post by Tomasnrsk on 2007-05-31
I did it, i needed to have installed gstreamer bad and gstreamer bad mutiverse variant...

---

