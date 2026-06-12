---
title: "Rythmbox won't import folders"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by muggins on 2006-10-29
I downloaded some music using the default bittorrent into a folder I named my music. Now rythmbox won't import any of the folders into the library so I can listen to it. I have read the help contents in rythmbox and also can not drag and drop any of the folders either. Don't know if its just me or what.

---

### Post by muggins on 2006-10-29
Installed amarok and it had no trouble importing files/folders. Why won't rythmbox, would unistalling and then reinstalling it be worth a shot?

---

### Post by sam81 on 2006-10-29
What kind of files are you trying to import? You might be missing some codecs, I think amarok and Rhytmbox use different libraries for dealing for example with mp3 files. Try to import some ogg files in Rythmbox, if that doesn't work then it's probably a Rhytmbox problem, otherwise you might be missing the codecs for gstreamer. Hope this helps!

---

### Post by muggins on 2006-10-30
> **sam81 said:**
> What kind of files are you trying to import? You might be missing some codecs, I think amarok and Rhytmbox use different libraries for dealing for example with mp3 files. Try to import some ogg files in Rythmbox, if that doesn't work then it's probably a Rhytmbox problem, otherwise you might be missing the codecs for gstreamer. Hope this helps!

Thanks for your reply, they were mp3 files. Installing Gstreamer fixed the problem, am now listening to my music. What can I use for an equalizer in rythmbox?

---

### Post by sam81 on 2006-10-30
> **muggins said:**
> Thanks for your reply, they were mp3 files. Installing Gstreamer fixed the problem, am now listening to my music. What can I use for an equalizer in rythmbox?

That's a feature I'm really missing in Rythmbox, maybe we should add it in the wishlist for the developers.

---

### Post by m_bridge on 2006-11-01
same problem, same solution.
The package i installed to make it work is gstreamer0.10-fluendo-mp3

---

