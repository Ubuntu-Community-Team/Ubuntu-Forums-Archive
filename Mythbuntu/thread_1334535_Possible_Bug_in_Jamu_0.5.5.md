---
title: "Possible Bug in Jamu 0.5.5"
date: 2009-11-22
forum: Mythbuntu
---

### Post by jmeads on 2009-11-22
Using Jamu version 0.5.5 and storing all meta data (and movies and tv series) on a windows home server mounted on my myth 0.22 server via cifs.

It appears that the ":" character is not valid, I get the following error after running ~/jamu -NMIV

-start----
Now processing video file (Terminator The Sarah Connor Chronicles.s01e02)(1)(2)


Entry exists in MythDB but category is 0 and year is 1895 (default values).
Updating (Terminator The Sarah Connor Chronicles.s01e02).
3-Added a poster for(Terminator The Sarah Connor Chronicles.s01e02)
3-Added a banner for(Terminator The Sarah Connor Chronicles.s01e02)
Traceback (most recent call last):
  File "/home/mythtv/jamu", line 6203, in <module>
    main()
  File "/home/mythtv/jamu", line 6188, in main
    process.processMythTvMetaData()
  File "/home/mythtv/jamu", line 5637, in processMythTvMetaData
    shutil.copy2(self.rtnAbsolutePath(tmp, graphicsDirectories[graphic_type]), newFilename)
  File "/usr/lib/python2.6/shutil.py", line 99, in copy2
    copyfile(src, dst)
  File "/usr/lib/python2.6/shutil.py", line 47, in copyfile
    raise Error, "`%s` and `%s` are the same file" % (src, dst)
shutil.Error: `/local/videos/metadata/Fanart - Terminator: The Sarah Connor Chronicles_fanart.jpg` and `/local/videos/metadata/Fanart - Terminator: The Sarah Connor Chronicles Season 1_fanart.jpg` are the same file
mythtv@lion:/local/videos/TV$ 
---end-------

Does anyone know if it's possible to blacklist certain characters from being used in the jamu script?


Thanks

---

### Post by jmeads on 2009-11-22
had a poke around at the code, the following patch appears to take care of the issue

diff jamu.py.20091122 jamu.py
219a220
>  # 0.5.6 Strip ":" char from names - may need to look at these too"<>:"/\|?*"
490c491,492
<     return 1<=len(name)<= NAME_MAX and "/" not in name and "\000" not in name
---
>     ##return 1<=len(name)<= NAME_MAX and "/" not in name and "\000" not in name
>     return 1<=len(name)<= NAME_MAX and "/" not in name and "\000" not in name and ":" not in name
500c502,503
< 	for char in u"/%\000":
---
> 	##for char in u"/%\000":
> 	for char in u":/%\000":

---

### Post by RDV on 2009-11-22
jmeads,
    I wrote Jamu and that error is weird. I used Jamu v0.5.9, removed all of my Terminator graphics and reran Jamu. There were no errors and images download with names like "Terminator: The Sarah Connor Chronicles Season 1_banner.jpg" and "Terminator: The Sarah Connor Chronicles Season 1_fanart.jpg". They also showed properly in MythVideo.

The solution you found will likely work but I think it is better to get rid of the odd combination of options (e.g. -sdtS PF) or disable those options in your jamu config file. Your stated command line options of "-NMIV" should be enough. 

When using Jamu with MythTV the extra options should be ignored. I had never seen an image file prefixed with a "Fanart - " when using the Jamu for MythTV before (-M option). There should not have been an abort with the python library "shutil". What Jamu passed as source and destination file names are not duplicates and are legit POSIX file names.

Please upgrade Jamu from 0.22+fixes and disable any un-needed options that are in your jamu.conf file. All Jamu command line options you would need with MythTV are documented in the wiki. [http://www.mythtv.org/wiki/Jamu](http://www.mythtv.org/wiki/Jamu)

This is all I can suggest right now.

---

### Post by williammanda on 2009-11-22
RDV
When are these issues going to be resolved?

[http://ubuntuforums.org/showpost.php?p=8360741&postcount=29]("http://ubuntuforums.org/showpost.php?p=8360741&postcount=29")

---

### Post by jmeads on 2009-11-23
RDV,
I assumed that I was running the latest version (running up to date mythbuntu) so will pull the latest version of the jamu script from svn and retest tonight.

I setup my config file as per the wiki, only changed the language and video ext (avi & mkv)

Regarding the &#8220;Fanart &#8211;&#8220; prefix, that&#8217;s what&#8217;s happening here - I set all the poster / fanart / banner storage groups to the same location...

BTW - I noticed the Janitor cron job wiped out the graphics on my system too - have removed the J option from this job.

Is there a preferred directory layout that would get the best results from Jamu?

---

### Post by RDV on 2009-11-23
jmeads and williammanda,

Just for the record the timing of the MythTV 0.22 release and the Mythbuntu 9.10 release caused Mythbuntu to have to include a release candidate of MythTV 0.22. Jamu had a bug which was fixed for the official MythTV 0.22 release.

You should keep Mythbuntu and MythTV 0.22+fixes up to date following these instructions. [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

The instructions above will get you up to date and and keep you up to date. It seems only prudent considering both sets of software are new.

There will be a patch for Jamu coming out in a few days that resolves an issue with the (-J) Janitor function erroneously removing graphics for people that use VIDEO_TS directories (copies of DVD files). It ONLY effected graphics related to those type of video directories. The coding is done but testing takes a while.

Having a prefix in the image file name "Fanart - " in general does no harm but is redundant with the "_fanart" suffix.

I have never tested where all the image storage groups are the same directory but will see if that causes the prefixing of the image file names. 

You may not know but if you create a 'Videos' storage group and NO image storage groups, the 'Videos' storage group will become the default directory for all images. When that scenario was tested, I still did not see a prefix on image file names.

jmeads: I will watch this thread to see after you have updated if you still get an abort with the "shutil" library.

---

### Post by jmeads on 2009-11-23
RDV,
Once again apologies for not running the latest versions - I'm now completely up to date using the weekly 0.22 fixes auto builds and I manually confirmed the jamu.py script is the latest revision.

I purged the Sarah Connor TV series from the database so that it would be repopulated...

delete 
videometadata.*, 
videometadatacast.*,
videometadatagenre.*
from 
videometadata, 
videometadatacast,
videometadatagenre
where 
videometadata.intid = videometadatacast.idvideo
and videometadatagenre.idvideo =  videometadatacast.idvideo
and videometadata.title = "Terminator The Sarah Connor Chronicles"

I then ran the jamu.py script to re-populate

~/jamu -MNIV

Unfortunately I get the same failure,

Now processing video file (Terminator The Sarah Connor Chronicles.s01e01)(1)(1)


Entry does not exist in MythDB.  Adding (Terminator The Sarah Connor Chronicles.s01e01).
3-Added a poster for(Terminator The Sarah Connor Chronicles.s01e01)
3-Added a banner for(Terminator The Sarah Connor Chronicles.s01e01)
3-Added fanart for(Terminator The Sarah Connor Chronicles.s01e01)
At least (rating) needs updating
Category added for (Terminator: The Sarah Connor Chronicles)(20)
1-At least (Terminator The Sarah Connor Chronicles.s01e01)'s value(rating) has changed new(TV Show)(<type 'unicode'>) old(NR)(<type 'unicode'>)
Updated Mythdb for video file(Terminator The Sarah Connor Chronicles.s01e01)

Now processing video file (Terminator The Sarah Connor Chronicles.s01e02)(1)(2)


Entry does not exist in MythDB.  Adding (Terminator The Sarah Connor Chronicles.s01e02).
3-Added a poster for(Terminator The Sarah Connor Chronicles.s01e02)
3-Added a banner for(Terminator The Sarah Connor Chronicles.s01e02)
Traceback (most recent call last):
  File "/home/mythtv/jamu", line 6434, in <module>
    main()
  File "/home/mythtv/jamu", line 6419, in main
    process.processMythTvMetaData()
  File "/home/mythtv/jamu", line 5848, in processMythTvMetaData
    shutil.copy2(self.rtnAbsolutePath(tmp, graphicsDirectories[graphic_type]), newFilename)
  File "/usr/lib/python2.6/shutil.py", line 99, in copy2
    copyfile(src, dst)
  File "/usr/lib/python2.6/shutil.py", line 47, in copyfile
    raise Error, "`%s` and `%s` are the same file" % (src, dst)
shutil.Error: `/local/videos/metadata/Terminator: The Sarah Connor Chronicles_fanart.jpg` and `/local/videos/metadata/Terminator: The Sarah Connor Chronicles Season 1_fanart.jpg` are the same file

And looking at the metadata storage group

-rwxr-xr-x 1 mythtv mythtv  149335 2009-11-23 20:01 Dexter Season 4_coverart.jpg
-rwxr-xr-x 1 mythtv mythtv  327763 2009-11-23 20:01 Dexter_coverart.jpg
-rwxr-xr-x 1 mythtv mythtv   42431 2009-11-23 20:01 Dexter Season 4_banner.jpg
-rwxr-xr-x 1 mythtv mythtv   42431 2009-11-23 20:01 Dexter_banner.jpg
-rwxr-xr-x 1 mythtv mythtv  381804 2009-11-23 20:01 Dexter Season 4_fanart.jpg
-rwxr-xr-x 1 mythtv mythtv  381804 2009-11-23 20:01 Dexter_fanart.jpg
-rwxr-xr-x 1 mythtv mythtv       0 2009-11-23 21:12 Terminator

(Note, the Dexter covers downloaded earlier fine)

Looks to me like the script is failing to save to the windows filesystem share due to the illegal character of ":" in the filename of the fanart and covers...

Please let me know if I can provide any further information

Thanks
Jonathan

---

### Post by RDV on 2009-11-23
jmeads,
    First it looks like the odd "Fanart -" prefix has gone away. I now understand the abort once you mentioned "...script is failing to save to the windows filesystem share...".

    Jamu's file name validation/sanitise logic is checking against the POSIX standard and not MS file system standards. Your addition of a ':' to the code would most likely need to include '\' as well.

    My approach will be to add a new config file variable so users can add additional characters that they want removed from the image file names. The "sanitiseFileName()" function will add any of that variables characters to the replaced with '_' list. This will have no negative effect in MythVideo but will mean the occasional images that are downloaded for the Watch Recordings screen will not show up. Nothing can be done with that situation .

Keep up to date and this change will be in the next patch released for Jamu (v0.6.0).

---

### Post by jmeads on 2009-11-24
RDV,
Thanks that would be excellent, very appreciated

---

### Post by RDV on 2009-11-24
jmeads,
The ability to add your file name filter characters has been released to 0.22+fixes and trunk. Jamu v0.6.0 see: [http://svn.mythtv.org/trac/changeset/22899](http://svn.mythtv.org/trac/changeset/22899)

These changes are available right now in 0.22+fixes and trunk but will take a day or two to be available for Mythbuntu daily updates. See: [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

See #6 of from the changes list below. The new jamu.conf variable "filename_char_filter" has the additional characters that need to be filtered for a MS-Windows file system. The variable is disabled in the jamu-example.conf file. There should be enough documentation in the example conf file for you to add and enable the new variable to your own jamu.conf file.

If you find that the changes has corrected the issues in this thread then please rename the thread as [SOLVED] so others can find the solution.

The release includes these changes:
1) Changed The Janitor -MJ option to deal with graphics associated with a VIDEO_TS directory.
2) Stopped Jamu from processing any video files in a "VIDEO_TS" directory as it was leading to multiple  MythVideo entires for *.VOB files. Jamu does not process multi-part videos. Use MythVideo to add metadata for VIDEO_TS directories.
3) Added the use of PID files to prevent two instances of the same Jamu -M options running at the same time. This deals with issues when a meta data source is off line for an extended period of time and Jamu runs as a cronjob. Options effected are (-M, -MW and -MG).
4) Change to have jamu use the TMDB Movie title as is done in MythVideo rather than the file name.
5) Fixed a bug when TMDB genres are filtered and none remain they were still being added. This bug was spotted and correct by Mathieu Brabant (thanks).
6) Added the ability for a user to filter additional characters from a file name this is important for users using MS-Windows file systems as a CIFS mount. See the jamu-example.conf "filename_char_filter" variable.

Doug

---

### Post by jmeads on 2009-11-30
RDV
Thanks, this fix (ver 0.6.0) works :p

---

