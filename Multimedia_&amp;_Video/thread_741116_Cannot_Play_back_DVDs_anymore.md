---
title: "Cannot Play back DVDs anymore"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by forceofnature on 2008-03-31
I have posted my initial issue here [http://ubuntuforums.org/showpost.php?p=4620599&postcount=669](http://ubuntuforums.org/showpost.php?p=4620599&postcount=669)

Since that time I have reinstalled the libdvdcss2 1.2.5, I have removed all vlc components and reinstalled everything.  I also prevented update to libdvdcss2.

I looked in to my .vlc directory and found vlcrc file with this info for dvd playback

[dvdread] # DVDRead Input (DVD without menu support)

# DVD angle (integer)
#dvdread-angle=1
# Caching value in ms (integer)
#dvdread-caching=300
# Method used by libdvdcss for decryption (string)
#dvdread-css-method=

Should there be a dvdread-css-method in there, or does the # symbol mean that is just a comment at this time? I dont want to have to use an unspeakable OS,  but playback of DVDs is important when traveling.

---

### Post by mrpixels0 on 2008-03-31
from looking at your other post I would Venture a guess that if it is a recent DVD it might be using a new form of Encryption than Libdvdcss2 or 1 were built to handle. 

 if it is a homemade DVD (I.E. a converted rip) then it may have had errors during the burning process or may have corrupted during processing

that would be my guess as to how to fix it some where on the forums there is a link to a patched version of VLC player that fixes a problem similar to yours, other than that I do not know.

hope that helps.

MP0

---

### Post by forceofnature on 2008-03-31
I have tried both new and old DVD's for playback and nothing.

---

### Post by Prefix100 on 2008-03-31
I had a similar problem - check this thread and see if it helps you,
[URL="http://ubuntuforums.org/showthread.php?t=739636"]
http://ubuntuforums.org/showthread.php?t=739636[/URL]

---

