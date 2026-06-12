---
title: "using mythtv to organise video file (tv shows)"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by geneticmod72 on 2007-01-04
hey guys,

I'm looking for a solution to my current situation, I have a lot of dvds of tv shows (i'm from australia, seriously our tv sucks so i have to buy dvds) that i have ripped and encoded that are now stored on an external harddrive. I'm looking for a way to access them from the tv media centre style and i thought mythtv was the way to go. but sadly mythtv doesn't seem to deal with anything other than movies (i.e. you can't add the necessary metadata like show name, season and episode number). Does anyone know of any way I can do this? 

I have been using it on a mac and using itunes and front row to do it but that's no longer an option as i need to access them from a Linux box in a similar manner (not to mention the fact that front row doesn't let you see any info on the show before you play it)

---

### Post by tagra123 on 2007-01-04
> **geneticmod72 said:**
> hey guys,

I'm looking for a solution to my current situation, I have a lot of dvds of tv shows (i'm from australia, seriously our tv sucks so i have to buy dvds) that i have ripped and encoded that are now stored on an external harddrive. I'm looking for a way to access them from the tv media centre style and i thought mythtv was the way to go. but sadly mythtv doesn't seem to deal with anything other than movies (i.e. you can't add the necessary metadata like show name, season and episode number). Does anyone know of any way I can do this? 

I have been using it on a mac and using itunes and front row to do it but that's no longer an option as i need to access them from a Linux box in a similar manner (not to mention the fact that front row doesn't let you see any info on the show before you play it)

Are the dvd's, iso's or mpgs?

MythTV is sooo close to being right -- its frustrating. 

In any case I 've use nuvexport -- assume you have too.

I export to dvd mpeg.

The filename are a pretty good starting point as to what the show and episode is. Granted, you don't have the episode number or Season but the other info is good.

Here's a plus ---

If myth recorded it its most likely all that important stuff is still in the database.

Using PhpMyAdmin you can browse the database ( RecordedProgram Table)

That should make it a little easier to get the data.


The videos is supposed to be able to do most of this but you are right -- it seems to be lacking.

This might be a good idea.  Export the recorded program table.  Create a new Mysql Database  MyMyth Videos and import the recorded programs data.  Assign a "DVD" number or use the MPG's  and path that is what you are working with in an added column.

A perl or python script could access and open the video you choose. It does sound useful. I too have over 200 dvd's of TV.  Maybe I'll look into this when I get some free time.

---

### Post by Nelson-Ray on 2007-01-04
MythVideo can do want you want. You can also edit the metadata to your heart's content. Basically make a video directory and set that as your video folder in MythVideo and then you can browse your files via MythVideo and launch it when you wish. You can edit the metadata and add thumbnails if you wish.

---

### Post by geneticmod72 on 2007-01-04
is there something extra i need to do? mythvideo only seems to do metadata for movies and doesn't have options for season number or episode number

---

### Post by Nelson-Ray on 2007-01-04
I am away on vacation so I can't access my mythbox to check out the exact metadata options but this is a thought.

Why not a have a root folder called Video

inside that folder have a folder for each tv series you like. Example would be TV SHOW A, TV SHOW B, TV SHOW C

then inside each TV SHOW folder have a folder for SEASON 1, SEASON 2, SEASON 3 etc.

then have each video episode inside the the seperate Season folders?

Seems like that would be an easy way to browse your tv show collection and have it orgranized well.  Use a program like VLC to capture a thumbnail for each tv episode you have and place it in the metadata for each tv show..if you wish. Also when using MythVideo have it set to browse your video folder by folders...I forget the exact name but you have like 3 choices...i think it might be gallery mode?

---

### Post by lokimon on 2007-01-09
> **Nelson-Ray said:**
> I am away on vacation so I can't access my mythbox to check out the exact metadata options but this is a thought.

Why not a have a root folder called Video

inside that folder have a folder for each tv series you like. Example would be TV SHOW A, TV SHOW B, TV SHOW C

then inside each TV SHOW folder have a folder for SEASON 1, SEASON 2, SEASON 3 etc.

then have each video episode inside the the seperate Season folders?

Seems like that would be an easy way to browse your tv show collection and have it orgranized well.  Use a program like VLC to capture a thumbnail for each tv episode you have and place it in the metadata for each tv show..if you wish. Also when using MythVideo have it set to browse your video folder by folders...I forget the exact name but you have like 3 choices...i think it might be gallery mode?

it's eeire, you just described my setup.

---

