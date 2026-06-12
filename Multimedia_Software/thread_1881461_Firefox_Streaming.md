---
title: "Firefox Streaming"
date: 2011-11-15
forum: Multimedia Software
---

### Post by data2005 on 2011-11-15
Hello,

is there any way to hinder Firefox to start downloading a mp3-stream (and therefore never finishing) and instead DIRECTLY pass the file/url to a specified external application?

Here is a mp3-stream for testing:

[http://demovibes.de/necta192.mp3]("http://demovibes.de/necta192.mp3")

Any method known?

---

### Post by An Sanct on 2011-11-15
Welcome to the forums!

If you go to Edit>Preferences then select the Applications button on top of the newly opened window. There you can find the MP3 (Streamed) or whatever media type you want to manipulate and choose an option.

---

### Post by dniMretsaM on 2011-11-15
Or you could use a plugin like VLC ([FONT=Courier New]mozilla-plugin-vlc[/FONT] in the repos) or Gecko ([FONT=Courier New]gecko-mediaplayer[/FONT] in the repos) if you want to just play it within Firefox (Gecko works with other browsers as well).

---

### Post by data2005 on 2011-11-15
Hello An Sanct!

(I was active in this forum before (2 years ago), not sure why none of my old posts are listed anymore?!)

Anyway, i did try this option to set the file-association for .mp3/.mp3-stream/etc. to QMMP, but that doesn't change the odd behaviour that firefox still tries to download the .mp3 first (try clicking on the link above, which is a mp3-stream) before it would add it to QMMP... since firefox cannot finish downloading an endless stream file, QMMP never gets invoked to play the stream.

So maybe there is another option or trick to "skip the download part" and/or directly hand the file over to QMMP (or another external player able to stream the file)?

---

### Post by data2005 on 2011-11-15
> **dniMretsaM said:**
> Or you could use a plugin like VLC ([FONT=Courier New]mozilla-plugin-vlc[/FONT] in the repos) or Gecko ([FONT=Courier New]gecko-mediaplayer[/FONT] in the repos) if you want to just play it within Firefox (Gecko works with other browsers as well).

While that is certainly possible, I'm looking for a solution to use an external player.
Of course one could "right-click-and-copy" the mp3-link location and then paste it manually over to the mediaplayer, but a simple click on a provided mp3-stream-link to make firefox do that for me would be very nice (and what I would expect when setting .mp3-file-association in firefox).

---

### Post by dniMretsaM on 2011-11-15
> **data2005 said:**
> While that is certainly possible, I'm looking for a solution to use an external player.

I realize this, I was just stating another option (for if perhaps you didn't know it was possible). Anyway, as for importing the link directly into an external program, I don't really know if that's possible. You could try something like a macro, but other than that I'm not sure.

---

### Post by data2005 on 2011-11-15
Do you know how to possibly solve it with a macro?
Any directions where to look or get an idea how such a macro might work?

---

### Post by An Sanct on 2011-11-15
Well, I tried all the possible options and -no fun-...

Note, that if you go to the root of that folder ([http://demovibes.de/](http://demovibes.de/)) you have m3u files there, they could be are a good start.

Sorry, I know this is not the solution, but here are the results of my little search.
At first I disabled my VLC plugin, that handled mp3-s and "played" them from inside FF (actually it never played, as it never finished to download). So I set every "audio" in the list to "Ask what to do" and than selected "Play in [movie player]", which again, never played - as FF handles the file over after it has downloaded it and it never does (the point of streaming...)

So, I downloaded the ***m3u*** file and selected "open it". As this is the only correct way to play streaming audio (radios etc.)

-------
Edit: I also discovered this *Tools>manage content plugins*, where you can modify how content is handled ... PS. I couldnt, I'm on an Nightly Alpha rv:11.0a1 64Bit, it seems broken here =)

---

### Post by data2005 on 2011-11-16
Thanks An Sanct for trying to find a solution, those steps were exactly what I did too (to no avail...).

So what exactly is this "Tools>manage content plugins"?

---

### Post by An Sanct on 2011-11-16
It should provide you with a windows, containing a list of file-types - by mime (style: x-application/whatever) and the way, FF handles them....

As said, this functionality seems broken in the nightly FF11a, and I cannot even find it in FF7 (under Windows)

---

### Post by data2005 on 2011-11-16
Where did you see this "Tools" then? :)

---

### Post by An Sanct on 2011-11-16
here :)

Note, that the forum resized the images, that where larger than 1024*768

---

### Post by data2005 on 2011-11-16
Alright, so this looks very much like the "Applications"-Tab under "Preferences", where you choose the default actions for file/mime-types.

BTW.: I like how you setup your panels (very much like I used to do under windows-xp) :)

---

### Post by dniMretsaM on 2011-11-16
Not available on 7.0.1.

---

### Post by An Sanct on 2011-11-16
> **data2005 said:**
> Alright, so this looks very much like the "Applications"-Tab under "Preferences", where you choose the default actions for file/mime-types.

BTW.: I like how you setup your panels (very much like I used to do under windows-xp) :)

Hmmm ... Well, FireFox is changing rapidly :) ... maybe you could resolve this issue with some addon.

PS. about the BTW comment ... yes, I prefer bottom panels and right top (min/max/close) buttons

---

