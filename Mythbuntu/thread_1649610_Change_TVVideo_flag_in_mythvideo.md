---
title: "Change TV/Video flag in mythvideo?"
date: 2010-12-20
forum: Mythbuntu
---

### Post by JamesNorris on 2010-12-20
I have mythvideo order show my files by TV series or film. This works great except for one episode of Star Trek Deep Space Nine, which insists it is a film and therefore doesn't show itself listed in the folder for the series. 

Is there any way to change this??

---

### Post by ian dobson on 2010-12-20
Hi,

The only may to do this would be to manually edit the SQL database. MythTV just uses the Title/Sub title to sort/group programms so it only needs one character wrong/an extra space in the title and the grouping breaks.

If you really feel happy about this then install/use myphpadmin to edit the required programm.

Regards
Ian Dobson

---

### Post by iamlindoro on 2010-12-20
Yikes.  No.  Please do NOT do that.

Television is defined as "Anything with a Season or episode number greater than 0."  If your DS9 stuff is being shown as Movies, it's because the filenames were an unparseable format when you added them.  See:

[http://www.mythtv.org/wiki/MythVideo_File_Parsing](http://www.mythtv.org/wiki/MythVideo_File_Parsing)

If you want your DS9 to appear in the Television view, then edit the metadata to correctly set the season and episode numbers for the items.  Highlight an item, press E to edit metadata, adjust the season number and episode.

Alternately, move the DS9 stuff out of your library, scan for changes, rename the files to use a supported naming format (such that season and episode are parseable), move them back into the library, rescan.

I'd randomly guess that you have named them something like "path/to/yourfiles/Star Trek: Deep Space Nine/Episodename" Which includes no parseable season or episode information.

---

### Post by ian dobson on 2010-12-21
Hi,

So is the recording showing up in "watch recordings" but not under the same Title as the rest of the DS9 episodes? If so my method will work.

I've manually edited the SQL table afew times, mainly when my EPG provider screws up the UTF8 encoding (öäüà replaced with a invalid character). When you go to the watch recordings screen the frontend issues a SQL query looking for all distinct program titles, it then fills the lefthand side of the watch recordings list. When you select a title from the lefthand side the frontend issues a sql query selecting all programs where the title is the same as the selected one.

iamlindoro on my system the episode number isn't even set in the recorded database but I still see my recodings sorted by title.

JamesNorris It's upto you, manually edit the database if you want, just make sure you have a backup before you start.

Regards
Ian Dobson

---

### Post by JamesNorris on 2010-12-21
> **iamlindoro said:**
> 
If you want your DS9 to appear in the Television view, then edit the metadata to correctly set the season and episode numbers for the items.  Highlight an item, press E to edit metadata, adjust the season number and episode.


Yes, that was it. For some reason it didn't have the season/episode number. Although they were all named DS9SxxExx when I ripped them from the DVDs...

Thanks!!

---

### Post by iamlindoro on 2010-12-21
> **ian dobson said:**
> 
iamlindoro on my system the episode number isn't even set in the recorded database but I still see my recodings sorted by title.

JamesNorris It's upto you, manually edit the database if you want, just make sure you have a backup before you start.


Ian,

He's not referring to recordings.  He's in MythVideo, and specifically talking about The TV/Movie Browse By mode.  His Star Trek: Deep Space Nine episodes were appearing under movies rather than TV, because season and episode were not set.

Please, please, please don't suggest that people manually edit the database.  I have lost countless hours that could have been spent improving MythTV helping people repair the damage they cause doing this.

Robert
MythVideo Maintainer/The Guy Who Wrote The Abovereferenced Code

---

