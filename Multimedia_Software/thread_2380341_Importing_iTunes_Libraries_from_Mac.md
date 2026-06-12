---
title: "Importing iTunes Libraries from Mac"
date: 2017-12-16
forum: Multimedia Software
---

### Post by paulakreuzer on 2017-12-16
I know similar questions have been asked before but I couldn't find a recent post describing how to move an iTunes library from a Mac to Ubuntu, which didn't refer to an App or script that doesn't seem available anymore.

So here is the situation:
I have a MacBook with multiple iTunes Libraries - one for Music, one for Movies, one for TV-Shows and one for Audiobooks, Podcasts & Co.

I'd like to import them all to my brand new Ubuntu Laptop - either to one App that can have multiple Libraries and handle all the kinds of Media I mentioned above, or to different Apps.

What's essential to me is that I don't loose:
[LIST]
[*]Metadata 
[*]Ratings (with half Stars) 
[*]Play Counts 
[*]Last Played 
[/LIST]
as well as that - at least the App that handles Music - is capable of complex intelligent Playlists, Playlist Folders and intelligent Playlists that refer to a folder.

What's also important, but not essential is that I can import all my intelligent Playlists. This will spare me hours of work trying to recreate them.

Bonus would be:
[LIST]
[*]a Play-Next-Playlist like iTunes' old DJ (not the crappy "Next" it has now) which I can feed from an intelligent Playlist, which refreshes automatically so it never ends and which displays the last few played songs along with the upcoming songs so I can rate them. 
[*]the ability to sync a Playlist with my Android (Lineage OS) Fairphone via USB (not via Cloud). 
[*]the ability to play formats common to Mac (like aac), so I don't have to convert them first. 
[/LIST]

I'm thankful for any tips.

---

### Post by yancek on 2017-12-17
What have you tried?  Do you have hfsprogs installed?  Which versin of Ubuntu are you using?  You would at least need to install hfsprogs to access the Mac from Ubuntu using the command below:

> sudo apt-get install hfsprogs

I'm not sure your expectations are realistic but you might try Rhythmbox or Amarok for your music.  Apple software and operating systems are extremely closed/proprietary by design and that makes it difficult to access them from other operating sysems.  That combined with the fact that Apple computers make up a very small % of computers used by home users means there isn't much incentive to Linux developers.

I recently purchased my first Apple device, Iphone 7 and have no problem accessing and copying data from it to Ubuntu.

---

### Post by paulakreuzer on 2017-12-18
Thanks for the answer.
What I tried so far was searching the web for similar questions asked before (most of the posts I found were 3+ years old) and tried to download the scripts or apps that were suggested there (but all the links were broken).

So next I downloaded and played around with different audio players for ubuntu to see which would come closest to my needs. I found that complex intelligent playlists like with iTunes will probably not be possible anywhere, but I did find that Banshee has a built in import-iTunes-Library-(+ratings+play counts+playlists)-option, so I'm trying that right now. I'm simpy moving the whole iTunes library to my new Laptop via USB, so no need for hfsprogs.

I rekon I will loose many playlists, AACs won't be imported, I'll loose half-stars-ratings and some other things will probably go wrong or get lost. But it will all be compensated by the warm feeling of finally being free from Apple.

So let's hope it will go reasonably well, if not I'll report back.

---

### Post by speartip on 2017-12-18
Depending on the size of the collection you are talking about, I would just download my whole Library to an external Hard Drive, then copy across to my Ubuntu Install using something like rsync.
Also why do you say AACs won't be imported? Ubuntu plays AACs fine.

---

### Post by paulakreuzer on 2017-12-18
Ok so it took me until now to move the iTunes Library around - it's now on my Ubuntu's second internal drive (that's what a HDD is for right?).

So then I tried Banshee's import-from-iTunes option, but it only lead to errors. For some reason the iTunes Library xml file pointed to a wrong location for all files (.../iTunes/Music/... instead of .../iTunes/iTunes Media/Music/...).
So I moved the Music folder out of the iTunes Media folder and now it's importing.

It's currently at 17% with 3200 errors. I think many of them might be long-deleted duplicates that somehow still were mentioned in the xml file. Others may be bought AAC files (yeah sorry, normal AAC files shouldn't be a problem. That was just my pessimism). I'll check that later.

Anyways intelligent Playlists are not imported at all and half-star-ratings are gone, but I expected that by now.


**PS:** The process ended with more errors than files actually imported.
I went through some of the errors and they had minor inconsistencies in the file path (e.g. different file extension).
I suspect iTunes doesn't actually keep the .xml file up to date but uses the .itl file instead.

So here is what I'm trying now:

1. I'm using PowerTunes to make a copy of my iTunes Music Library and hope it will come with a updated .xml file.
2. I'll change all ratings to full-star-ratings.
3. I'll let Banshee try to import that new Library and see what happens.

---

### Post by paulakreuzer on 2018-01-06
Ok, it took me a while but now I'm almost there.

So here is what I did (after some failed tries):

On my Mac:
[LIST]
[*]Changed all ratings to full stars
[*]With PowerTunes created a new iTunes Library placed on my USB Hard Drive (This process took a few days)
[/LIST]
On my Ubuntu:
[LIST]
[*]Moved the new iTunes Library onto my Ubuntu's HDD drive
[*]With imported the Library into Banshee, which I set to copy the files into the Music folder on my SSD (This imported about 90% of 38.000 tracks and put out 10% errors)
[*]Did another round of importing, this time with only 1000 errors.
[*]Made 39 screenshots of the errors.
[*]Downloaded a community plugin for Banshee to remove duplicates (files successfully imported at both rounds).
[*]It took me 2 days to remove the duplicates as you have to select every second track in the list of duplicates manually.
[/LIST]

What I still have to do:
[LIST]
[*]Find and export the 1000 failed songs from my iTunes library to try and import them again.
[*]rename all of them which contain â, à, á, ä or similar symbols in the tilte, album title or artist name as none of such files were successfully imported
[*]import these files and keep copying down all errors and retrying these files until I got them all
[*]**find a way to move files that are in the banshee library but were for some reason not moved into the Music folder (about 300 files)**. Then I can remove the iTunes Library from the HDD.
[*]Manually transfer the play counts and ratings of about 100 songs which data got lost during the import.
[/LIST]

And one more thing I'd then like to be able to do (but maybe that's better placed in a new thread) is to convert all the files to ogg so I can store the play counts and ratings in the files as metadata. But if I just convert the files how can I let banshee know they are the same tracks as the mp3 files they came from?

---

### Post by Yellow Pasque on 2018-01-06
[https://superuser.com/questions/273797/convert-mp3-to-ogg-vorbis](https://superuser.com/questions/273797/convert-mp3-to-ogg-vorbis)
Keep in mind that converting lossy audio to another lossy audio format is not good for the audio quality.

I prefer ogg metadata over id3 tag too, but I'm not sure I'd do a mass conversion. Maybe something like this exists for Banshee? [https://github.com/shatterhand19/RhythmboxPOPM](https://github.com/shatterhand19/RhythmboxPOPM)
Can Banshee write play count directly to ogg? That's nice if it can. It's a shame Banshee isn't actively developed anymore.

---

### Post by Habitual on 2018-01-07
[How to move your iTunes library to a new computer]("https://support.apple.com/en-us/HT204318")
Published Date: Nov 30, 2017

Good Luck!

---

### Post by paulakreuzer on 2018-01-07
> **Temüjin said:**
> [https://superuser.com/questions/273797/convert-mp3-to-ogg-vorbis](https://superuser.com/questions/273797/convert-mp3-to-ogg-vorbis)
It's a shame Banshee isn't actively developed anymore.

It isn't? Oh no. I guess that's why the official website won't open. I thought it was some privacy-browser-addon blocking it for some reason.

So I guess I'll have to find another Audio Player that can import the Library from Banshee.
If all my files were already oggs with the playcount and rating stored in them I'd just need another Player that can do the same and find a way to batch-change the "RATING:BANSHEE" and "PLAYCOUNT:BANSHEE" ogg tags to however the new Player stores them.

---

