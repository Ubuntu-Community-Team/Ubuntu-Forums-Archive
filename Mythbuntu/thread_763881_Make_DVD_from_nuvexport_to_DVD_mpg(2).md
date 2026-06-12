---
title: "Make DVD from nuvexport to DVD mpg(2)"
date: 2008-04-23
forum: Mythbuntu
---

### Post by sceo on 2008-04-23
I am trying to identify the best way to make a DVD from a movie I recorded on television for posterity.  I figured out how to do the cutlist, and I then used nuvexport to make an .mpg file (I chose "DVD" from nuvexport's menu).  This creates an .mpg file with mp2 video and mpeg1 audio.  

However, when I go into QDVDAuthor or ManDVD (programs I'm new to with this project), it doesn't seem to work.  QDVDAuthor won't pick up the audio (seems like it wants a separate file?) and ManDVD gets to the last step in setup but then won't transcode - I get a warning about the audio, but I don't know if that is always on that final screen or if that appears just in my case.

Should I nuvexport to separate audio and video files somehow?  Should I extract the audio from my mp2 into a separate file?

---

### Post by laga on 2008-04-23
Have you tried Mytharchive?

On KDE, I've sometimes used kmediafactory with acceptable results for my DVB recordings (which are handled differently from normal video files in kmediafactory).

---

### Post by sceo on 2008-04-23
> **laga said:**
> Have you tried Mytharchive?

Somehow, it took me till now to find it, but it's just perfect!  I have an .iso now, which I'm going to burn to disc and see if it works.  I may have a/v sync issues, but we'll see.

I also ran into that weird thing with transcoding where I had to delete my .ICEauthority file.  But then it seemed to work.  I didn't realize MythArchive existed, since I just upgraded to new Mythbuntu recently from Knoppmyth.

---

