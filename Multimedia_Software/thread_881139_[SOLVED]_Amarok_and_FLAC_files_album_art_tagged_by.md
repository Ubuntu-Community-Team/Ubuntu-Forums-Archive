---
title: "[SOLVED] Amarok and FLAC files album art tagged by MediaMonkey"
date: 2008-08-05
forum: Multimedia Software
---

### Post by hardy-newbie on 2008-08-05
Hi to all,

Before my recent switch to Ubuntu, I used MediaMonkey, a Windows only media player, to administer my music collection; I also used MM to tag my music collection. (This collection consists of a lot of FLAC files, each tagged with the respective album art.) Now I gave Amarok a try, although I use Gnome. (Since my collection is pretty big, I liked Amarok' s optional use of MySQL.)

So far, so good: I can add my music to the Amarok collection, and Amarok also recognizes most of the tags. There is only one big drawback: Amarok doesn't show the album covers of my files. Does anybody know how to fix this? Has it something to do with the album tag version? (After having encountered the problem, I tried to fool around with EasyTag and some Amarok settings -- unfortunately to no avail.)

Any help is highly appreciated, thanks in advance!

Edit: EasyTag recognizes the album art.

---

### Post by CuteUsagi on 2008-08-05
I also use amarok and easy tag for my music collection needs!  I have found that in easy tag, although it may "recognize" the album art, I have to tell it directly where that album art is located in the tagging process for amarok to display properly.  In the pictures tab of the tag, next to the picture should be some info.  Just make sure that next to "Description:" there is something like filename.jpg.  If the field next to "Description:" is blank, then the tag isn't pointing directly to a file.

If you save your album art to your computer, you might consider putting each album's art in the album's folder just for ease of use.  Often times, whether an album has been tagged in easy tag or not, if a single .jpg or .png file resides in the album's directory, Amarok will automatically pair it with the album.

Hope this helps!!!!

---

### Post by hardy-newbie on 2008-08-06
Hi CuteUsagi,

Thanks a lot for your reply! I tried to create some albumart.jpg files and to save them in the respective album folders -- and it worked like a charm: Amarok recognized them.

The only problem remaining is how to create all the albumart.jpg files (and how to get them in the respective folders). Currently, the album art is somehow stored in the FLAC tags. (I.e.: I dont have any albumart.jpg files.) I can manually save them as .jpg files by using EasyTag, but doing so for my entire collection would mean a lot of work. Therefore, I will have to look for an automated way of extracting them. (Maybe the CopyCover script is a solution, but I rather don't think so, since Amarok doesn't recognize the album art embedded in the files.)

---

### Post by hardy-newbie on 2008-08-06
For anyone who has the same problem I had: I was able to extract the album art with (Windows only) MediaMonkey and the MediaMonkey script "Album Art Tagger". (I used "Album Art Tagger" v. 4.2; I guess there is a similar script / program for Ubuntu boxes, but I didn't find one so far.). This script gets the album art from the music (in my case: FLAC) files and saves it as albumart.jpg files to the respective folders. (There is one caveat: Don't mark all files of an album before using "Ablum Art Tagger", but only one file per album - otherwise MediaMonkey will crash.)

Amarok now recognizes the albumart.jpg files stored in my music folders -- and displays them correctly.

---

