---
title: "Can't play Media Files"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by FreeSoul on 2007-01-05
Hello All,

    First I installed both gstreamer0.10-plugins-ugly and libxine-extracodecs from the ubuntu site with the GUI to no avail. Then installed both easyubuntu (nothing) and then automatix2 but still can't play audio (mp3) or video files.
It always says I don't have the required decoder (codecs?) in Totem. When I try playing mp3 files in Amarok it acts like it was succesfull as follows:
   Shows the songs name as a popup file for maybe 3 seconds and then it says "play list finished". My sound works fine in other programs, so that's not the issue.

Any suggestions?

I'm running a 5 year old Gateway 400sd4 P4 laptop 1.8GHz w/ 256mb ram.

Thanks,
FreeSoul

---

### Post by Gremlinzzz on 2007-01-05
Remove totem and its mozilla  plugin install  mplayer and its mozilla  plugin. Mplayer and its plugin has to be configured like this start mplayer click on the screen- click preferences then click video tab choose X11/XV then click the Codecs & demuxer tab. click audeo codec family choose w32/acm/decoders- now to configure the plugin for video streaming .go to a site where u use it click on the screen choose X11 and alsa. then click ok== done hope this helps ya.

---

### Post by FreeSoul on 2007-01-05
> **Gremlinzzz said:**
> Remove totem and its mozilla  plugin install  mplayer and its mozilla  plugin. Mplayer and its plugin has to be configured like this start mplayer click on the screen- click preferences then click video tab choose X11/XV then click the Codecs & demuxer tab. click audeo codec family choose w32/acm/decoders- now to configure the plugin for video streaming .go to a site where u use it click on the screen choose X11 and alsa. then click ok== done hope this helps ya.

Hey Gremlinzzz, Thanks for your time. I did what you stated but it still doesn't play the video file. It says "Cannot find codec mismatching selected - vo and video format Ox33564D57"

But, I can sort of play audio. 25% there.
I can play the file by clicking on the mp3 and saying open with Mplayer and it gives me this message "decoder preinit failed". But the file still plays a second after the message. If I just double click on the mp3 it opens Mplayer (a larger version that says Xfmedia but it doesn't do anything. Didn't try the streaming yet...

Any suggestions?

Thanks,
FreeSoul

---

### Post by Gremlinzzz on 2007-01-05
Did you install w32codecs if not get them from here [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)  hope this helps

---

### Post by FreeSoul on 2007-01-05
> **Gremlinzzz said:**
> Did you install w32codecs if not get them from here [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)  hope this helps

Seems to be working. Thanks for your time and help bro. I'll stick with these players for a while ant later on try to get Amorak working (just easier to manage/play my collection. 

Thanks again,
FreeSoul

---

