---
title: "Rhythmbox cover art not showing after enabling plugin"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by timzak on 2007-07-16
I have a couple of computers with Rhythmbox running.  One (with Ubuntu 7.04) shows album art like it is supposed to.  The other (with Xubuntu 7.04) does not show the album art.  I see the picture of the jewel case with the gnome logo with toes moving like it's trying to retrieve, but nothing ever shows.  Any ideas as to why it won't load?  Both computers are on the same network, attached to the same router.  Could there be some missing dependency on the Xubuntu machine?

Bonus question:  I can't get Rhythmbox (on the same Xubuntu machine) to play an internet radio station that streams with .m3u and .asx.  I get a message about a missing plugin when I try to play the station (yes, I installed all the gstreamer plugins).  The station is [www.kwve.com](www.kwve.com).  I tried both the itunes/mp3 stream and the Windows Media stream.

Thanks.

---

### Post by timzak on 2007-07-16
bump...any ideas?

---

### Post by timzak on 2007-07-16
One last bump.  Any ideas why the cover art isn't loading on the Xubuntu machine?  I can live without it, but I don't understand why it works on the Ubuntu machine and not the Xubuntu machine.  The Xubuntu machine has a working internet connection, but for some reason Rhythmbox isn't downloading the album art.

Thanks.

---

### Post by bensode on 2008-01-13
Was looking for ways to manually add what the plugin couldn't find on it's own and stumbled on your post.  I found this link that shows how to add it manually when it can't be found.  Yeah it's like 8 months after the fact you posted but maybe it will help someone else

[http://philbull.livejournal.com/42080.html](http://philbull.livejournal.com/42080.html)

Manually adding missing album art in Rhythmbox
I wrote these instructions in response to a comment on a blog post from a while ago. The commenter was wondering how they could get missing album art to appear in Rhythmbox:

   1. Using Firefox, find the album on Amazon.com and click on it.
   2. Right-click the picture of the album cover and select 'Save Image As...'

   3. In the box marked Name, type ~/.gnome2/rhythmbox/covers/Artist Name - Album Name.jpg. You have to type the artist name and album name *exactly* as they appear in Rhythmbox, including punctuation and spaces e.g. John Frusciante - To Record Only Water For Ten Days.jpg

   4. Press Save.

   5. Go back into Rhythmbox and double-click on a song from the album that was missing the album art. The album cover should now be displayed if you typed the name correctly. You may have to close and then open Rhythmbox sometimes for this to take effect.

---

### Post by timzak on 2008-01-14
Thanks for posting this.  I no longer need the info, but someone else might.  The reason I don't need the info is that the computer I was having this problem with had Xubuntu 7.04.  I've since replaced that computer with a slightly more powerful system running Ubuntu 7.10.  I never had this problem in regular Ubuntu.

Take care.

---

