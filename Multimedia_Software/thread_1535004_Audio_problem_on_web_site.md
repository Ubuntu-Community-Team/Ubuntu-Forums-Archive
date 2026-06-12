---
title: "Audio problem on web site"
date: 2010-07-20
forum: Multimedia Software
---

### Post by unix1980 on 2010-07-20
A rare audio problem for me on Lucid.  Can you play the audio on this page?  

[http://www.sheetmusicplus.com/look_inside/16299702/audio/56411](http://www.sheetmusicplus.com/look_inside/16299702/audio/56411)

There should be a player at the bottom of the page.  I get a "Loading audio clip..." message and nothing.  This site changed something recently and now my computer must be missing something to handle the change.

thanks in advance!

---

### Post by themusicalduck on 2010-07-20
For some reason mp3s won't play for me in a browser either, not sure why.

I found a rough workaround to help you though. On that page, right click in empty space and click View page source. On line 22 there is a URL - [http://cdn-origin.sheetmusicplus.com/soundclips/16299702_20.mp3](http://cdn-origin.sheetmusicplus.com/soundclips/16299702_20.mp3) which is the link to the mp3 you want to play.

With this URL you could either paste it into the address bar and see if it plays, or if not open Movie Player in the Sound menu, go to Movie > Open Location and paste the URL into there, click Open.

If you want to download it, open a terminal, type ```
wget http://cdn-origin.sheetmusicplus.com/soundclips/16299702_20.mp3
``` and it'll download the file to your homespace.

Hope this helps a bit.

---

### Post by unix1980 on 2010-07-21
Thanks, that's exactly how I was working around the problem.  Chrome and Opera have the same problem as Firefox.  What's puzzling me is that when I reboot into 9.10, Firefox handles this page correctly and the embedded player shows up and the audio works as expected.  I have not been able to determine what is different in 10.04.

---

### Post by lidex on 2010-07-23
Do part 2 on this page:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

You may want to do part 1 if that doesn't do it.

---

### Post by unix1980 on 2010-07-23
> **lidex said:**
> Do part 2 on this page:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

You may want to do part 1 if that doesn't do it.

Thanks, I tried that and it didn't work.  But, something happened because I no longer have the problem!  Maybe a re-boot is required, not just re-starting Firefox.  Or maybe the web site changed something.  I suspected a Flash problem all along, especially since many people seem to have Flash problems on 10.04, but now I guess I'll never know.  At least the problem is gone (for now).

---

