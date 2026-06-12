---
title: "New to Mythbuntu"
date: 2008-04-13
forum: Mythbuntu
---

### Post by temujin77 on 2008-04-13
I'm new to Mythbuntu; actually, new to MythTV *and* new to Ubuntu, thought I had some experience with SuSE and Red Hat from a few years ago, thought not recently.  I just got Mythbuntu installed on a Dell box with Nvidia 7200GS video card.  I was able to get it to install, but have a few questions.

1. With the S-Video, I got output signals to my TV, but something is off -- the signals being displayed on the TV screen is just random static/jumbled colors.  Does anyone know what's wrong?  I'm not really sure how to start fixing it.

2. Since things seems to be working on the regular VGA output, I thought I'd continue testing things.  I found that commercial DVDs cannot be played.  It shows the initial screen, like "20th Century Fox" or "Artisan" or something, and then stops.  Is it a plugin I need to get?

3. Finally (for now), I have lots of home videos, my collection of CDs (ripped to MP3s of course), etc. I want to play with this new Mythbuntu box.  Does anyone know how to load them into the index so that I can use the MythTV interface to index and play them?  I noticed if I just copy the files to the /var/something/mythtv/videos etc. folders, the frontend doesn't see them, so I guess some kind of indexing needs to take place.

Thanks!  Hope it's not too many questions at once :)

---

### Post by volkswagner on 2008-04-13
> **temujin77 said:**
> I'm new to Mythbuntu; actually, new to MythTV *and* new to Ubuntu, thought I had some experience with SuSE and Red Hat from a few years ago, thought not recently.  I just got Mythbuntu installed on a Dell box with Nvidia 7200GS video card.  I was able to get it to install, but have a few questions.

1. With the S-Video, I got output signals to my TV, but something is off -- the signals being displayed on the TV screen is just random static/jumbled colors.  Does anyone know what's wrong?  I'm not really sure how to start fixing it.

2. Since things seems to be working on the regular VGA output, I thought I'd continue testing things.  I found that commercial DVDs cannot be played.  It shows the initial screen, like "20th Century Fox" or "Artisan" or something, and then stops.  Is it a plugin I need to get?

3. Finally (for now), I have lots of home videos, my collection of CDs (ripped to MP3s of course), etc. I want to play with this new Mythbuntu box.  Does anyone know how to load them into the index so that I can use the MythTV interface to index and play them?  I noticed if I just copy the files to the /var/something/mythtv/videos etc. folders, the frontend doesn't see them, so I guess some kind of indexing needs to take place.

Thanks!  Hope it's not too many questions at once :)

1. You may have to install restricted drivers, and enable.  This can be done from mythbuntu-control-centre.  If you already performed this, can you access Nvidia settings (under MCC>Restricted drivers)?
2.  You will have to enable propriatory codecs, also from MCC.
3.  If you added the music to the correct directory, you can go to setup>media setings>music tools>scan for music (within mythtv frontend).

---

### Post by temujin77 on 2008-04-13
volkswagner, thanks so much!  #1 and #2 are RIGHT ON!

Your #3 instructions doesn't seem to work, but I'm still working on it.  I'm wondering if the MP3 album I have isn't in a format MythTV can read?  I dug up the original purchased CD of the same album and I'm ripping it with MythTV right now to see if I have better luck...

---

### Post by temujin77 on 2008-04-13
I think my issue is with a lack of understanding of playlists... hmmm

---

### Post by volkswagner on 2008-04-13
What happens when you scan for new music?

Check logs for errors.  

Make sure mythtv has permission to read and write to the directory for your music.
There are some settings of interest.  
In music general settings for tree sorting I have "directory"
                    File name format I have "GENRE/ARTIST/ALBUM/TRACK_TITLE"

In music playback settings I select "show entire music tree"

If you are just seeing playlist, go to music tools>select music> I have all my music checked.

One other thing.  If you have transferred these files from windows, file name may contain spaces.  Linux does not like spaces in a file name.  To see if this is the problem, create a new directory under music, put one mp3 file there.  Then go back to select music and choose just that new directory.  If it shows up you may have to rename some files to eliminate spaces.

---

### Post by temujin77 on 2008-04-13
> **volkswagner said:**
> What happens when you scan for new music?

Check logs for errors. 

It ended up that all is well; the only thing is that I didn't know how to set up the playlist, that's why it seems nothing was added.  The playlist management seems cumbersome in MythTV; I hope it can be streamlined in a future release.  I am VERY impressed with MythTV as I played with it all day, so this is not so much of a turnoff, but still would be nice if it can be improved.  I suppose I'm spoiled by iTunes on both of my Macbook and Windows desktop environments :)

Thanks so much for your advice; it was vital even though it turned out trivial ^_^

> **volkswagner said:**
> One other thing.  If you have transferred these files from windows, file name may contain spaces.  Linux does not like spaces in a file name.  To see if this is the problem, create a new directory under music, put one mp3 file there.  Then go back to select music and choose just that new directory.  If it shows up you may have to rename some files to eliminate spaces.

Many of the files contain space, but that doesn't seem to cause any problems...

---

