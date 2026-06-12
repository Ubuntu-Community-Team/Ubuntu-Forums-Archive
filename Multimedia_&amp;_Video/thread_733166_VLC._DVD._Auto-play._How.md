---
title: "VLC. DVD. Auto-play. How?"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by Roasted on 2008-03-23
What steps must I take in order to play a DVD automatically using VLC? When I put a DVD in, it'll make VLC pop up. When I hit play, it prompts me with what to open.

I want it to automatically boot up the DVD and go right into the movie. How do I do that?

p.s. - I've changed the settings under system - removable drives and media and put "vlc" in the box next to DVD playback.

---

### Post by jdgiotta on 2008-03-23
If you entered the command VLC, it won't be enough.
Its possible you'll just launch VLC and nothing will begin to play.

I suggest you check [http://www.videolan.org/doc/play-howto/en/ch04.html]("http://www.videolan.org/doc/play-howto/en/ch04.html") for command line know-how. I think you may need to do
```
vlc dvd://
```

---

### Post by Roasted on 2008-03-23
That worked.

What about for audio CDs?

---

### Post by _godbout_ on 2008-03-23
Hi,

I join the topic because I had a bit of the same problem, but actually mine is that VLC doesn't start at all.

I read everywhere that under the Multimedia tab, there is a "DVD Playback" settings, but I don't have it :confused:

---

### Post by Roasted on 2008-03-24
Where exactly are you when you're trying to find the DVD Playback setting?

---

### Post by jdgiotta on 2008-03-24
For audio CDs its:
```
vlc cdda://
```

---

### Post by Roasted on 2008-04-12
I magically started getting this error when I insert a new DVD. Before it worked. Now it doesn't. I changed nothing.


Unable to open 'dvd://'

---

### Post by jdgiotta on 2008-04-16
New as in blank or new as in DVD you've tried to play for the first time?

---

### Post by Roasted on 2008-04-22
It's not a blank DVD. My apologies, I should have specified. It's a store-bought live concert DVD version of Pearl Jam in concert. It's the kind of DVD you'd throw in a DVD player and watch on a big screen. Ya know, nothing different from a DVD movie.

---

