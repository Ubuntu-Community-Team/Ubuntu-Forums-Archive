---
title: "A media player that can configure subtitles (encoding, position)?"
date: 2011-12-18
forum: Multimedia Software
---

### Post by siriusbg on 2011-12-18
Hello! I tried watching some avi file that comes with subtitles under VLC player. It all went well until the subtitles were displayed - they were in the video region. Now, for some years I've used The KMPlayer, which is the best media player to my view. There I had an option to draw the subtitles outside the video region - in the black space beneath. I studied VLC forums for quite some time and apparently there is no such option here. 
Can someone come up with a suggestion how to handle this situation? Many of the players I tried had a really minimalistic design and didn't offer making such a tweak. Some didn't even recognize Cyrillic subtitles (totem and xine for example). 
Thanks in advance!

---

### Post by stumpalump on 2011-12-18
Try xbmc. I'm not sure about Cyrillic subs but I know you can set the subtitle position through the settings.

---

### Post by SeijiSensei on 2011-12-19
It depends on how the subtitles are encoded.  If they are "hard" subs, they have been imprinted on top of the video and cannot be altered.  AVI files generally have hard subs because the container technology wasn't designed to handle subtitle streams.  In some cases soft subtitles for AVI files are distributed as a separate file with a .sub or .srt extension.  Files in the Matroska (.mkv) format usually include the "soft" subtitles as a "stream" in the container.

You can't do anything to alter the appearance of hard subs.  With soft subs you have a lot more control over location and appearance.  I recommend giving **smplayer** a try.  It provides an excellent GUI interface to manage subtitles; it uses mplayer as the engine.

---

### Post by Keith_ on 2012-09-29
I know this thread is a few months old, but when I was searching for a way to re-position my subtitles in VLC Media Player this is one of the pages I found. At first it seems to me also there was no way to re-position subtitles, but after more digging I found it is possible. I'm also using VLC Media Player version 2.1 from the nightly updates.

I'm on a Mac, so maybe it's a little different in Ubuntu, but I found it by going into Preferences > Show All > Video > Subtitles / OSD > "Force subtitle position". I also found reference on how to do this [here]("http://www.cyberkey.in/2012/06/how-to-change-position-of-subtitles-in.html"), but I'm not sure when it was posted nor the OS it is running on.

---

