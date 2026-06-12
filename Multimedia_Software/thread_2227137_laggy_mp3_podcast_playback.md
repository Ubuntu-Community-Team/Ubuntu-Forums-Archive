---
title: "laggy mp3 podcast playback"
date: 2014-05-30
forum: Multimedia Software
---

### Post by manthony121 on 2014-05-30
I collect several podcasts using "gPodder", on my laptop, running Ubuntu 14.04 LTS x86_64.  I listen to them in my car on my Sansa Clip Zip mp3 player.  The podcasts from one particular source, "Inquiring Minds", always takes several seconds to start when changing files.  None of the other podcasts do that.  It seems as if there is something different about the way that site encodes its podcast.  However,  each file gets processed, and re-encoded, before I copy it to my mp3 player, like this: after I download the mp3 files, I convert each one to a "wav" file, using "lame".  Each "wav" file is then sped up, using "soundstretch", then converted back into an mp3 file, again using "lame".  Finally, the original id3 tag is copied to the accelerated mp3 file using "id3cp".

I could understand why an mp3 file might behave differently from one source if I were playing it unchanged from the way it was downloaded.  However, since all the files go through the mp3 -> wav -> soundstretch -> mp3 processing, it seems they should all behave the same.  Is there something in the id3 tag that would cause the file to have a noticable lag?  Or, is there something in the original mp3 file that would be preserved through the processing I described?  I find it very puzzling.

---

### Post by tgalati4 on 2014-05-30
Play the original, unalterated file in *vlc* and open up the message terminal and see what it says while decoding the file.  As far as soundstrech, does the clip not have a speed setting buried in the menus?  I had an old Sansa player that had the ability to speed up or slow down tracks so no conversion was necessary to speed through a podcast.

---

