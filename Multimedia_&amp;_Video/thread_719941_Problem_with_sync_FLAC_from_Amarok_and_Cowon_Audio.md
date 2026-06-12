---
title: "Problem with sync FLAC from Amarok and Cowon Audio 7"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by fabietto0102 on 2008-03-09
Hello,

I use Amarok to sync my ogg, mp3 and flac music collection to a Cowon Audio7. The Amaork plugin is "generic audio player" and it successfully transfers mp3s, but it fails with flacs and oggs, although I went to the "configure media device" menu and added flac and ogg to the "transferring files to media device" pane.

Oddly, the filetypes are written "&flac" and "&ogg", and when I close the window, try and fail to transfer my flacs and oggs to the media player and go back to the setting window, "&flac" and "&ogg" are gone from the pane.

I don't get how come mp3, which is licenced, works ok, and ogg and flac which are free do not! Also, I don't think the audio player makes a difference, as I can, by drag&drop through Nautilus, transfer files to the Audio7. The problem IMHO lies with Amarok.

Please help!!
Fabio

---

### Post by fabietto0102 on 2008-03-10
Solution found: [http://amarok.kde.org/forum/index.php/topic,14717.0.html](http://amarok.kde.org/forum/index.php/topic,14717.0.html)

//QUOTE//
-Open ~.kde/share/condig/amarokrc
-Do a find for ogg; you'll see it as &ogg
-Delete the & and save it

You should be able to transfer oggs now.  If that doesn't take, just try opening that same file, and look for the line that reads "supportedFiletypes."  It'll probably say something like

supportedFiletypes=mp3

Make it look like:

supportedFiletypes=mp3 ogg

Then save, close, and try it again.
//UNQUOTE//

---

