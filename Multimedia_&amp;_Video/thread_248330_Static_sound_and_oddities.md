---
title: "Static sound and oddities"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by KageKeeper on 2006-08-31
Hi all,

I have just installed Dapper and am having some issues with sound.

I am using a SB Live 24 bit which is being detected as CA0106.

I have followed the comprehensive sound guide as well as a few others. After unmuting with alsamixer I get no sound whatsoever unless I unmute the SPDIF and then the sound is staticy and awful.

I am unsure exactly where to go at this point so any help would be welcome and appreciated.

Thanks so much. :confused:

---

### Post by butterman on 2006-09-09
I have the SB Audigy LS but with the same driver, and the same problem.  Maybe we can help each other.  This link describes the same problem, but the solution didn't help me.  I don't have any digital options in alsamixer, only analog and spdif.

[URL="http://www.ubuntuforums.org/showthread.php?t=108160&highlight=spdif+static"]http://www.ubuntuforums.org/showthread.php?t=108160&highlight=spdif+static
[/URL]
In my panel, the speaker icon for the volume control applet has a red slash through it.  Does yours?

Did you try testing your sound in root?

```
sudo /usr/bin/speaker-test
```

Can you hear the speaker test through the static?  I can't.  I hear only static.

---

