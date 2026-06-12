---
title: "XMMS right click menu"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by mello__yello on 2006-12-05
Hey,

I am almost complete my conversion from Windows.

I was wondering how I can Add to my right click drop down menu an option to Enque in XMMS to add songs to the  que as so.  It is quite convenient in Winamp.


Thanks in advance

---

### Post by gschoper on 2006-12-05
This is how I did it under gnome/edgy.

cd into your nautilus scripts directory:
```

cd ~/.gnome2/nautilus-scripts
```

create a file
```
gedit enqueue-in-xmms
```

with the following contents:
```

#!/bin/bash
xmms -e $NAUTILUS_SCRIPT_SELECTED_URIS

```

save it, and make it executable:
```

chmod +x enqueue-in-xmms
```

restart nautilius
```
killall nautilus
```


Now, right click on an mp3 in nautilus and select scripts-->enqueue-in-xmms and your song will be queued.

HTH,

gschoper

---

### Post by SpanishFranks on 2006-12-05
Hi
I use beep which is an XMMS clone. 
i tried your solution, but the song names appear in the playlist filled with %20 symbols instead of spaces. beep converts %20s to spaces like XMMS.

Any ideas?

---

### Post by mello__yello on 2006-12-06
Thanks,

Worked like a charm

---

### Post by gschoper on 2006-12-06
> **SpanishFranks said:**
> Hi
I use beep which is an XMMS clone. 
i tried your solution, but the song names appear in the playlist filled with %20 symbols instead of spaces. beep converts %20s to spaces like XMMS.

Any ideas?

I've never used beep before. Sorry.

gschoper

---

### Post by gschoper on 2006-12-06
> **mello__yello said:**
> Thanks,

Worked like a charm


Glad I could help.

gschoper

---

### Post by La muerte del DIos on 2007-06-24
Works perfect, thank you very much.

---

### Post by erthian on 2007-07-16
awesome.  works great.killall nautilus

---

### Post by euchrid on 2007-07-23
Brilliant - thanks for this. It was the only thing annoying me about Amarok (that I couldn't add to playlist/enqueue with a right click). Changing 'xmms' to 'amarok' in your instructions worked beautifully! 

I'm loving Linux more and more every time I get something like this working.

---

### Post by miatawnt2b on 2007-12-29
this is excellent.  however, I have 2 issues.  First is the playlist doesn't clear after you close xmms and try to open another folder, so the new encue is listed after my old playlist.

Second, it doesn't seem to atuostart.  I have to click play to begin playing the songs.

thanks all!
-J

---

### Post by miatawnt2b on 2007-12-29
duhhhh... i should have looked up the xmms switches before I posted.  I just created another script to play-in-xmms using the -p switch instead of the -e.

Thanks all!

-J

---

