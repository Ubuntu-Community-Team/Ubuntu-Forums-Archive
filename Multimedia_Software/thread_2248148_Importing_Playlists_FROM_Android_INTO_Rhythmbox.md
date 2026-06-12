---
title: "Importing Playlists FROM Android INTO Rhythmbox"
date: 2014-10-12
forum: Multimedia Software
---

### Post by John_Wedgeworth on 2014-10-12
Hey guys!

I just recently converted my Acer Netbook from Windows 7 to Ubuntu 14.04 LTS (running Unity, though I may try installing a few other GUIs and messing with them.)

As part of the "moving in" process, I needed to import all my music and all my playlists from the default Music player app on my Samsung Galaxy Note 3 into my Ubuntu music player (I'm using Rhythmbox). Well, getting the music files from the phone to RB was a cinch! But now I'm trying to import the playlists, and am running into major headaches. I've changed the file types of the playlists on the Linux HD copy from .m3u to .pls (I'm keeping the ones on the Android side .m3u, of course, so they'll keep working). I can "Load from File" the playlist into Rhythmbox, but it's completely empty. I have one working playlist, but I had to go in and manually select the tracks to add. That's gonna take me absolutely forever with as many, as big, and as spread out my playlists are.

I've seen a ton of threads and websites dedicated to either  going FROM Rhythmbox TO Android, or to/from Windows to Rhythmbox, or  Apple to/from Rhythmbox, but after about an hour of fruitless searches, I  found absolutely zero resources dedicated to going FROM Android TO  Rhythmbox.

Is there either a script I can plug into terminal, or else, a file format I should use to get Rhythmbox to just take the playlist without me having to rebuild them from scratch? Alternately, are there any "midpoints" I can send the playlists to, and then send them into Rhytmbox from there?

You guys were a HEEEUUUUGE help with me getting my email clients set up last week, and I'm hoping you'll be able to "save my life" yet again. :)

Thanks a bazillion!!

-J

---

### Post by John_Wedgeworth on 2014-10-12
I pulled up both the working playlist I created in Rhythmbox as well as the non-working equvalent that came directly from the Galaxy in gedit. They should both be identical in terms of what tracks are and are not there, as well as in terms of what order they play in, so the only difference should be in formatting of the playlist for Rhythmbox consumption. The playlist is for the soundtrack to Cosmic Carnage for the Sega 32X - yes, video game music. :)

---------------------------------------------------------------------------------------------------------------------------------------

Here's a copy/paste of the NON-WORKING version (works fine on the Android):

---------------------------------------------------------------------------------------------------------------------------------------

#EXTM3U 
#EXTINF:126,Cosmic Carnage - 32X - Intro 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Intro.mp3 
#EXTINF:10,Cosmic Carnage - 32X - Title 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Title.mp3 
#EXTINF:176,Cosmic Carnage - 32X - Character Select 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Character Select.mp3 
#EXTINF:162,Cosmic Carnage - 32X - Naruto 1 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Naruto 1.mp3 
#EXTINF:212,Cosmic Carnage - 32X - Naruto 2 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Naruto 2.mp3 
#EXTINF:199,Cosmic Carnage - 32X - Zena Lan 1 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Zena Lan 1.mp3 
#EXTINF:202,Cosmic Carnage - 32X - Zena Lan 2 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Zena Lan 2.mp3 
#EXTINF:177,Cosmic Carnage - 32X - Cylic 1 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Cylic 1.mp3 
#EXTINF:194,Cosmic Carnage - 32X - Cylic 2 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Cylic 2.mp3 
#EXTINF:137,Cosmic Carnage - 32X - Tyr 1 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Tyr 1.mp3 
#EXTINF:160,Cosmic Carnage - 32X - Tyr 2 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Tyr 2.mp3 
#EXTINF:212,Cosmic Carnage - 32X - Talmac 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Talmac.mp3 
#EXTINF:156,Cosmic Carnage - 32X - Deamon 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Deamon.mp3 
#EXTINF:193,Cosmic Carnage - 32X - Naja 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Naja.mp3 
#EXTINF:167,Cosmic Carnage - 32X - Yug 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Yug.mp3 
#EXTINF:228,Cosmic Carnage - 32X - End Credits 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - End Credits.mp3 
#EXTINF:9,Cosmic Carnage - 32X - Game Over 
../Music/JaySeeDoubleYou/JaySeeDoubleYou_s Album/Cosmic Carnage - 32X - Game Over.mp3

-------------------------------------------------------------------------------------------------------------------------------

And here's the version that DOES work in Rhythmbox:

-------------------------------------------------------------------------------------------------------------------------------

[playlist]
X-GNOME-Title=Cosmic Carnage.pls
NumberOfEntries=16
File1=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Intro.mp3
Title1=Cosmic Carnage - 32X - Intro
File2=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Title.mp3
Title2=Cosmic Carnage - 32X - Title
File3=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Character%20Select.mp3
Title3=Cosmic Carnage - 32X - Character Select
File4=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Naruto%201.mp3
Title4=Cosmic Carnage - 32X - Naruto 1
File5=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Naruto%202.mp3
Title5=Cosmic Carnage - 32X - Naruto 2
File6=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Zena%20Lan%201.mp3
Title6=Cosmic Carnage - 32X - Zena Lan 1
File7=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Zena%20Lan%202.mp3
Title7=Cosmic Carnage - 32X - Zena Lan 2
File8=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Cylic%201.mp3
Title8=Cosmic Carnage - 32X - Cylic 1
File9=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Cylic%202.mp3
Title9=Cosmic Carnage - 32X - Cylic 2
File10=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Tyr%201.mp3
Title10=Cosmic Carnage - 32X - Tyr 1
File11=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Tyr%202.mp3
Title11=Cosmic Carnage - 32X - Tyr 2
File12=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Talmac.mp3
Title12=Cosmic Carnage - 32X - Talmac
File13=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Deamon.mp3
Title13=Cosmic Carnage - 32X - Deamon
File14=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Naja.mp3
Title14=Cosmic Carnage - 32X - Naja
File15=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20Yug.mp3
Title15=Cosmic Carnage - 32X - Yug
File16=file:///home/jayseedoubleyou/Music/JaySeeDoubleYou/JaySeeDoubleYou_s%20Album/Cosmic%20Carnage%20-%2032X%20-%20End%20Credits.mp3
Title16=Cosmic Carnage - 32X - End Credits

----------------------------------------------------------------------------------------------------------------------------------

Looking at these, if I were to just go the "text edit" route, it'd take me even longer to change all the text than it would to just rebuild the playlists from scratch. My hope is that someone here will know of either a utility, a script, or a file format that will make this work. This playlist is VERY short compared to some of them. And of course, the longer playlists are the ones I use most, so I'm REEEALLLY hoping to find a way to avoid having to just redo them all.

Any help would be super awesome!

Thanks!

---

