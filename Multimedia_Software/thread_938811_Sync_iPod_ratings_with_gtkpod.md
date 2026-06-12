---
title: "Sync iPod ratings with gtkpod?"
date: 2008-10-05
forum: Multimedia Software
---

### Post by Breepee on 2008-10-05
I'm seeing if I can somehow synchronize the ratings I gave to songs on my iPod to the songs on my PC and vice versa. As there's no real standard to save these ratings in tags, I wonder if gtkpod (or any app that syncs with the iPod) can upload the ratings from my pod to the pc. Anyone know more about this?

---

### Post by Breepee on 2008-10-07
Anyone an idea?

---

### Post by grittyminder on 2008-12-02
I can say that I have been able to sync my ipod ratings with my local music library using gtkpod. That is the good news. The bad news is that I have been unable to figure out a way to do this consistently (sometimes the ipod ratings do not sync; sometimes all the ratings on my ipod are overwritten). So in short, there seems to be a way to sync ipod ratings using gtkpod (I've been able to do it twice); however, it is not intuitive, and I am not even 100% sure how to do it myself ;)  I don't want the ratings on my ipod to be overwritten again so I am loathe to do any more experimenting.

I've been experimenting with various alternatives to gtkpod, such as Exaile and Amarok, and have had zero success with regards to syncing the ipod ratings. I've got to say--this has become a really, really frustrating issue for me (I've probably wasted 3 entire weekends on this!). If anybody knows of a way to reliably sync ipod ratings with a local music library (any software is fine) please help!

---

### Post by Breepee on 2008-12-23
Ha, nice to see I'm not the only one!

BTW, I just discovered your other thread: [http://ubuntuforums.org/showthread.php?t=898952](http://ubuntuforums.org/showthread.php?t=898952)
It looks things have changed since then?

I'd in fact prefer it if I could sync the ratings to a certain tag on the music files on my PC. That's way I'm sure they always travel with the file, in case the database is lost or the filename/location is changed.

---

### Post by grittyminder on 2008-12-23
I found a solution--don't use gtkpod. ;)  Well, more specifically, use Songbird. I just started using Songbird recently and it is great. It syncs ratings easily. It is fast (it scanned my music library faster than Amarok. BTW, I was never able to figure out how to get Amarok to display ratings from my iPod. Nor Exaile. Banshee would quit about 1/10 of the way through when scanning my music library). The GUI is far, far more intuitive than gtkpod. And there are some very useful plugins as well.

It wasn't easy transferring my gtkopod ratings to Songbird, but with some time and persistence I was able to do it. What I did was create a playlist in gtkpod containing all the songs in my music library with ratings attached to them. I divided these songs into batches (about 10 batches in all with each batch being aproximately the same size as my ipod disk drive). I then transfered a single batch to my ipod. In Songbird, I created a new blank temporary playlist in my local music library (the purpose of this playlist is only to sync ratings--it can be deleted later), then copied all the tracks on my ipod to the playlist. Songbird automatically synced the ipod ratings to the local database without any input or intervention from me. After Songbird finished syncing the ratings I deleted all the songs in the temporary playlist and repeated the above steps for the next batch. It works. Now I am a happy Ubuntu/iPod user!

---

### Post by Breepee on 2008-12-25
Thanks for the info! Some more question though: with Songbird, do you actually need to use those playlists (I normally don't)? And do you know of a way to backup the Songbird library, so that I could transfer my ratings around (without the iPod)?

---

### Post by grittyminder on 2008-12-25
> **Breepee said:**
> with Songbird, do you actually need to use those playlists (I normally don't)? And do you know of a way to backup the Songbird library, so that I could transfer my ratings around (without the iPod)?

The gtkpod playlist is only necessary for identifying the songs that you have already rated in your music library. That way you can ignore the songs that have not yet been rated. It's just a temporary playlist--it can be deleted later (that is, if you ever decide to use gtkpod again!) ;) 

You need only create one temporary playlist, one time only, in Songbird for the purpose of syncing your ipod ratings--this playlist can be deleted later after your have transferred all your ratings. 

As far as backing up the Songbird library, I'm not so sure about how to do that. If you ever find out, I'd be interested in knowing as well! :)

---

