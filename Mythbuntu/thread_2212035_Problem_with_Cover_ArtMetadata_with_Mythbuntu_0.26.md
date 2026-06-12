---
title: "Problem with Cover Art/Metadata with Mythbuntu 0.26 and 0.27"
date: 2014-03-19
forum: Mythbuntu
---

### Post by prof3205 on 2014-03-19
Hi All,

Have a problem that's causing me fits.  I'm trying to get the movie art from inside of Mythbuntu (running .27, but it also appears in .25 and .26).

I'm testing with three movies, Shrek, The Incredibles and Monster's, Inc.  When I run the details update (using "i") I can get the art for Monster's Inc., but not the other two.  The front end log shows no entries found:

Mar 18 22:09:12 HTPC mythfrontend[4764]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb3.py -l en -M Shrek
Mar 18 22:09:13 HTPC mythfrontend[4764]: I CoreContext videodlg.cpp:3263 (customEvent) No results found for Shrek 0 0

But when I run the script from the command line ... python tmdb.py -l en -M "Shrek"

The film is found in the TMDB:

<?xml version='1.0' encoding='UTF-8'?>
<metadata>
  <item>
    <title>Shrek</title>
    <tagline>The greatest fairy tale never told.</tagline>
    <description>It ain't easy bein' green -- especially if you're a likable (albeit smelly) ogre named Shrek. On a mission to retrieve a gorgeous princess from the clutches of a fire-breathing dragon, Shrek teams up with an unlikely compatriot -- a wisecracking donkey.</description>
    <inetref>808</inetref>
    <homepage>http://www.shrek.com/</homepage>
    <releasedate>2001-04-21</releasedate>
    <userrating>6.700000</userrating>
    <popularity>5.25790104462</popularity>
    <year>2001</year>
    <runtime>90</runtime>
    <images>
      <image url="http://image.tmdb.org/t/p/original/wBG4kHfhwm3bLwKUFNRByXXv4r2.jpg" type="fanart" thumb="http://image.tmdb.org/t/p/w300/wBG4kHfhwm3bLwKUFNRByXXv4r2.jpg"/>
      <image url="http://image.tmdb.org/t/p/original/140ewbWv8qHStD3mlBDvvGd0Zvu.jpg" type="coverart" thumb="http://image.tmdb.org/t/p/w92/140ewbWv8qHStD3mlBDvvGd0Zvu.jpg"/>
    </images>
  </item>
  <item>



Any clue what might be going on????  Any help would be greatly appreciated.

---

### Post by blm-ubunet on 2014-03-19
The frontend is running a different script (tmdb3.py) to you (tmdb.py).
(But the script tmdb.py is probably a backported version of tmdb3.py)

You have different parameters as well.
The frontend seemed to have passed the parameters series & episode "0 0".
You have used quotes "" around the title.

/usr/share/mythtv/metadata/Movie/tmdb.py -v
/usr/share/mythtv/metadata/Movie/tmdb3.py -v

Should be version 0.3.7..

I'm fairly sure tmdb3.py is the latest script but I haven't got artwork for movies lately (last 6 months)..

edit: Well my problem was the file /home/"FE-user"/.mythtv/cache/pytmdb3.cache did not exist..

---

### Post by prof3205 on 2014-03-19
Thanks for the quick reply.  I tried the command from Terminal with both quotes and no quotes, and they both return values.  You need to have the quotes in the command line if the title has spaces.  I have the same code in each of the files.  I've updated the TMDB.py from the TMDB3.py code.

But, I think I might be onto something ... turns out that when there's only one movie with the name (I assume it parses the filename and treats it like a search term), then it doesn't return anything, but if there's only one name, then it picks up the metadata just fine.  If that's the case, I read that there should be a listing of found files and you can select the one you want.

---

### Post by blm-ubunet on 2014-03-19
You can interactively choose the matching movie in the FE if there is more than one.

For items in "recordings" group:
You can do this easily before it is recorded (scheduled recordings- pick-an-entry <enter>/ edit recording rule/metadata options).

The hard way is after recording has finished. You have to use (<m>/Edit recording schedule/**/metadata options).
** - if there is no future recording scheduled then metadata option is blocked out so you change this to record any.
(This metadata lookup is for a future recording not the existing one)
You can select artwork etc but you must remember the inetref number..save exit..
Select recording (<m>/Recording options/change recording metadata) then enter the inetref. done..

Easy eh..

For items in "Videos" it is much more straight forward..

---

### Post by prof3205 on 2014-03-19
Yeah.  Easy ... maybe.

But, I was trying to do this for "Videos".  I've already got the videos (in MP4) in the /var/lib/mythtv/videos folder and I'm while I'm in the FE/Watch Videos section, I tried using the "M" and "I" menus to get the file details.  That's when the issue occurs.  So, can you help me with the "Videos", I would REALLY appreciate it!

So, if "tmdb.py" finds only one match in it's metadata lookup I can get the artwork, but it appears that if there's more than one, rather than giving me a choice of which one, it doesn't find any matches.

Is this something that I'm doing wrong, forgot to set or just missing?  I really appreciate your help.

(I'm teaching a Community College class in residential networking, and I'm showing them how cool it is to have a MythTV FE/BE for a home theater environment and this was driving us crazy in our class last week.  It would be great to show them that it works.)

---

### Post by blm-ubunet on 2014-03-20
There are reasons why metadata for recordings is more complicated, the fact that each item can have series/episode details & has unique artwork & descriptions is big part of that...

Your post prompted me to go & fix the inetref/artwork for a several items in Videos..
 
First thing with Videos collection/group is that you need to "scan for changes" after adding/moving things around or adding folder artwork (manually).

Some of this could be theme dependent..assuming mythbuntu wide (& from memory)..
In Videos:
- select a candidate with wrong/no metadata
- hit <i>
- select edit video details.
- if inetref = "000000" ( or v similar) then delete it
- set/correct series & episode numbers if possible.
- click on "search artwork" (2nd column of buttons) this triggers the search.
The 1st column of buttons searches in local cache or folders (inc. DIY images).
 - Pick the correct artwork (& description) from the list & then the inetref will be populated.
- click on the other 2nd column buttons to find/select any candidates for banners/trailers/etc.

I think the <W> key might trigger search as well.
Possibly, any of the 2nd column buttons trigger a inetref lookup..
You can find the inetrefs directly from the 2 main online DBs.
The only trick (that I know) is if the inetref  is "0000000" then a metadata lookup previously failed & a new lookup will not occur.
I think a weakness of mythtv metadatalookup is that movies  are searched on one DB & "TV show"s (series/episode) on another. I have movies that can only be found on the "TV show" DB.
HTHs & YMMV..as always ACNR.

---

### Post by prof3205 on 2014-03-20
THANKS blm-ubunet!!!!! :p

Looks like manually finding the "inetref" number from the TMDB, putting it into the video details, manually setting the coverart and fanart and then using the "i" option to retrieve the rest of the details works!

I'm still curious as to what's going on inside of Mythbuntu.  If there's more than one entry in the database I thought all of the items would be displayed in a list and you could select the one you want as opposed to finding nothing.  Am I missing something?

Anyway, it's probably a pain in the butt to go through this process manually, but at least it works.

If you have any clue how to make this more automated (perhaps a more exact way of naming a file) let me know.

A big shout out to you!

---

### Post by blm-ubunet on 2014-03-21
Clearly there is something broken in the code ..
In mythtv master, the metadatalookup (run automatically by BE) fails with no data but the exact same query from terminal returns correct results..
The user should not have to run the same script query in terminal or browse some website to find the inetref!

Videos with no inetref:
- The "edit video details" GUI does search & find some correct artwork but not all.
I think this artwork "choice" should populate the inetref..but it does not..

Videos with inetref:
- works well

Folders & filenames:
This naming convention was noted in the old mythvideo (as a plugin) page
[http://www.mythtv.org/wiki/MythVideo_File_Parsing](http://www.mythtv.org/wiki/MythVideo_File_Parsing)
This page is not *linked to* in the "new" mythvideo but I think it is still relevant.

There are clues about filenaming in the mythvidexport script
[http://www.mythtv.org/wiki/Mythvidexport.py](http://www.mythtv.org/wiki/Mythvidexport.py)

---

### Post by slavo.fabian on 2014-03-22
I have the exactly same problem wth 0.25 version + updates.

It looks like this script needs to be repaired or changed.

I tried other similar systems for home video and imdb handling and they funcion without problems - MediaPortal - will give you choice of selection, if it find more then one name, plex - no problem, ...

I have found also a lot of similar question on different forums. 

It would be perfect if somebody will repair it.

I have found an old script for automatization of imdb, but it was only for older version. 

Maybe it helps for the beginning, if script will find more results for one name, it will use only the first and do not stop as it is today.

useful links: 

[https://pypi.python.org/pypi/tmdb3](https://pypi.python.org/pypi/tmdb3)

[https://github.com/wagnerrp/pytmdb3](https://github.com/wagnerrp/pytmdb3)

---

### Post by blm-ubunet on 2014-03-22
Both the OP & myself are running that script directly in terminal with success, albeit a roundabout solution..

The script does seem to work..the problem seems to be that when mythmetadatadownload.cpp calls the grabber script it either:
- times out too soon
- fails to get any stdout (return result)
- fails to stick the xml stdout into a tmp file
- fails to parse the xml in file.

The metadatalookup does (seem to) work for scheduled & upcoming "Recordings".

The script can only return the results & not be interactive with user. MythTV can't be interactive when metadatalookup is run automatically for bulk (on mass) updates.

What is broken is the interactive process (in MythTV code) "let-the-user-choose-the-right-one" part..

The inetref value/string = "000000" seems to be treated as equivalent to "" empty string

---

### Post by dkgiles on 2014-09-21
I was experiencing a similar issue, in my case no metadata scanning was working for any movies.  I was able to get things working by creating the file pytmdb3.cache in /home/<FE-user>/.mythtv/

ie. touch pytmdb3.cache

Movie metadata scanning immediately started working.

---

