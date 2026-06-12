---
title: "TV Series on DVD"
date: 2012-07-05
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-07-05
I have searched, but have not found a good way to have MythVideo parse files that are a result of ripping a TV series from DVD to ISO files.  Before I get too far I should explain that I do not want to rip the episodes into individual files, because then I lose the menus, subtitles, etc., so I would like to leave them as the ISO image.  However, when you do this, the metadata grabber very much does not like the end result, and comes up with nothing.  

Questions:

1- Is there a way to enter an IMDB number any more, like I used to be able to do?

2 - What is the solution in these cases, in order to pull down the proper graphics, series descriptions, etc.?

I renamed them for now, placing in S01E01, in each of the ISO files, but that is clearly not going to work, as this makes it look like each ISO is just episode one of the series, but at least it is the right graphics.

Any ideas?  Am I the only one with this seemingly simple grabber paradox?

Thanks...

---

### Post by tgm4883 on 2012-07-05
> **jlp_engineer said:**
> I have searched, but have not found a good way to have MythVideo parse files that are a result of ripping a TV series from DVD to ISO files.  Before I get too far I should explain that I do not want to rip the episodes into individual files, because then I lose the menus, subtitles, etc., so I would like to leave them as the ISO image.  However, when you do this, the metadata grabber very much does not like the end result, and comes up with nothing.  

Questions:

1- Is there a way to enter an IMDB number any more, like I used to be able to do?

2 - What is the solution in these cases, in order to pull down the proper graphics, series descriptions, etc.?

I renamed them for now, placing in S01E01, in each of the ISO files, but that is clearly not going to work, as this makes it look like each ISO is just episode one of the series, but at least it is the right graphics.

Any ideas?  Am I the only one with this seemingly simple grabber paradox?

Thanks...

I just rip the Episodes to individual files. To answer your questions though

1) You would use the [theTVDB]("http://www.thetvdb.com/") number, not IMDB. It's put in the same place that you use to put the IMDB number (I think it might still say IMDB in some places)

2) IDK, you are probably one of a few that leave episodic content in the ISO. Everyone else puts episodes in separate files.

---

### Post by nickrout on 2012-07-05
> **jlp_engineer said:**
> I have searched, but have not found a good way to have MythVideo parse files that are a result of ripping a TV series from DVD to ISO files.  Before I get too far I should explain that I do not want to rip the episodes into individual files, because then I lose the menus, subtitles, etc., so I would like to leave them as the ISO image.  

Personally I loath DVD menus, they are usually annoying and juvenile IMHO. 

Why would you lose subtitles when ripping?

---

### Post by tgm4883 on 2012-07-05
> **nickrout said:**
> Personally I loath DVD menus, they are usually annoying and juvenile IMHO. 

Why would you lose subtitles when ripping?

I somehow missed that part as well. Why would you lose subtitles when ripping? I know my bluray rips have subtitles using makemkv, I'd imagine my dvd rips do as well.

---

### Post by jlp_engineer on 2012-07-05
OK, perhaps I missed something then.  How does one retain the ability to either turn on or off subtitles, but not have the DVD style menus?  Does Mplayer or the integrated player in MythTV have the ability to yank subtitles out of an AVI or MPG file, if properly formatted.  If so, how is this done, or is the process automatically done by most ripping software?

There are other reasons I want to retain the DVD menus and the ISO format...  Just to name a few:

1 - So that I retain as much of the DVD viewing experience as possible, and so that WAF is high?  If it is complicated, my spouse will never use it and I will be called to the TV at all times of the day or night.

2 - So I can make backup discs from the ISO's in case the original is lost or damaged.  This has happened already.

3 - So I can watch the special features, and not have to load 50 different individual AVI's or MPG, etc.

4 - So that I can select different audio tracks while viewing the movie.

There are others, but I think you get the point - I want to keep my ISO's....

---

### Post by tgm4883 on 2012-07-05
> **jlp_engineer said:**
> OK, perhaps I missed something then.  How does one retain the ability to either turn on or off subtitles, but not have the DVD style menus?  Does Mplayer or the integrated player in MythTV have the ability to yank subtitles out of an AVI or MPG file, if properly formatted.  If so, how is this done, or is the process automatically done by most ripping software?


makemkv puts the subtitles in the mkv file, along with the video, and however many audio tracks you want. The internal MythTV player has the capability to switch between these during playback without needing the unnecessary DVD menus.

> **jlp_engineer said:**
> 
There are other reasons I want to retain the DVD menus and the ISO format...  Just to name a few:

1 - So that I retain as much of the DVD viewing experience as possible, and so that WAF is high?  If it is complicated, my spouse will never use it and I will be called to the TV at all times of the day or night.


Not sure why you think this way is better for WAF. Putting them in separate files (and then placing the files in subdirectories) allows you to separate by show > season > episode and it looks and works similar to the recordings interface. 

> **jlp_engineer said:**
> 
2 - So I can make backup discs from the ISO's in case the original is lost or damaged.  This has happened already.


This doesn't make sense to me. Rip it to the hard drive, then store the disk in a safe place. Just FYI, if you lose the original, you legally (in the US anyway) have to destroy the copy.

> **jlp_engineer said:**
> 
3 - So I can watch the special features, and not have to load 50 different individual AVI's or MPG, etc.


Yea that would be bad, but how often do you watch the special features anyway? Even if you do watch them a lot, you could feasibly rip just the extras to a single ISO file and name it appropriately.

> **jlp_engineer said:**
> 
4 - So that I can select different audio tracks while viewing the movie.


See my comment above about multiple audio tracks in mkv files.

> **jlp_engineer said:**
> 
There are others, but I think you get the point - I want to keep my ISO's....

If you must keep your ISO's, then there isn't a better way that I know of to name them for metadata.

---

### Post by jlp_engineer on 2012-07-06
OK,

Had to switch themes in order to view all the metadata settings correctly.  Mythbuntu theme seems to have the labels formatted incorrectly, or something.  Makes them hard to read.  Other themes are fine.

So I then began looking up the number for one of the TV series I have DVD sets for, and then placed that in the appropriate space.  However, it pulled the TMDB data, not the TVDB data.  Is there a way to specify which source it will pull data from?  Given the stubbornness that I have toward keeping the ISO's of the DVD's intact, entering the number is a more than acceptable work-a-round.  But if I can't get MythTV to pull from the correct source, I am back to square one.  ](*,)

Also, I am assuming since the MKV container is the only one that has been recommended, that this container is handled by MythTV appropriately and that any imbedded audio tracks or subtitles are available to be viewed or not on demand by the integrated player???  Are there any other video container files that have this capability that MythTV also supports.

I guess I am not totally opposed to breaking up the DVD's into their individual episodic files, but doing so also seems like a lot more work than just ripping the disk to an ISO.  :-k

---

### Post by tgm4883 on 2012-07-06
> **jlp_engineer said:**
> OK,

Had to switch themes in order to view all the metadata settings correctly.  Mythbuntu theme seems to have the labels formatted incorrectly, or something.  Makes them hard to read.  Other themes are fine.

So I then began looking up the number for one of the TV series I have DVD sets for, and then placed that in the appropriate space.  However, it pulled the TMDB data, not the TVDB data.  Is there a way to specify which source it will pull data from?  Given the stubbornness that I have toward keeping the ISO's of the DVD's intact, entering the number is a more than acceptable work-a-round.  But if I can't get MythTV to pull from the correct source, I am back to square one.  ](*,)


In order for it to pull from TheTVDB instead of TMDB, it needs to detect that the file is a show rather than a movie (that means season and episode number). It looks like TheTVDB has an option for doing extra's content by doing a season 0 according to [http://www.mythtv.org/wiki/MythVideo_File_Parsing](http://www.mythtv.org/wiki/MythVideo_File_Parsing)

> **jlp_engineer said:**
> 
Also, I am assuming since the MKV container is the only one that has been recommended, that this container is handled by MythTV appropriately and that any imbedded audio tracks or subtitles are available to be viewed or not on demand by the integrated player???  Are there any other video container files that have this capability that MythTV also supports.

I guess I am not totally opposed to breaking up the DVD's into their individual episodic files, but doing so also seems like a lot more work than just ripping the disk to an ISO.  :-k

It's a little more work. I stick the DVD in, open makemkv, tell it which tracks to rip (usually 4 per disk), then come back when it's finished and rename the files.

---

