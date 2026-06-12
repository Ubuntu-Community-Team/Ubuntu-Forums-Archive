---
title: "Mythvideo Issues"
date: 2008-10-04
forum: Mythbuntu
---

### Post by ttabbal on 2008-10-04
Mythbuntu 8.04 x64

It's working pretty well. However, I can't add file types to Mythvideo and I can't do per-file command lines in the Video Manager. I can delete file types, but adding them doesn't take. It would be really nice to be able to experiment without dropping out of Mythfrontend to do it. 

No odd errors in the logs, nothing looks to be throwing errors, it just doesn't seem to want to let me do this.

---

### Post by newlinux on 2008-10-04
Can you post your frontend log when you do this? And just to confirm, you are hitting the "done" button not escaping out after making changes?

---

### Post by ttabbal on 2008-10-04
Wow newlinux, you're all over the forum. :) 

```

2008-10-04 09:37:56.263 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2008-10-04 09:38:16.340 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
```


I doubt it's helpful. That seems to be the message I get when I enter the File Types menu. 

I select "New", type an extension "mkv". Select "Create New Extension" from the dialog. It shows up now. If I select "Done" and come back in, "mkv" is not an option. I've tried it with different extensions, no change. I can, however, delete options from the menu, and that sticks. 

Using the custom command option from the Video manager just doesn't give me the option to use that field. I can see it on the screen, but I can't get to it with keyboard or remote. I get this log entering the Video Manager.

```
2008-10-04 09:43:22.493 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2008-10-04 09:43:22.493 Unable to find image file: /usr/share/mythtv/themes/Mythbuntu/vidgallerybackg.png
2008-10-04 09:43:22.493 UIImageType::LoadImage() - Cannot find image: vidgallerybackg.png
Container: background already exists
2008-10-04 09:43:22.510 Failed to parse a container. Ignoring.
2008-10-04 09:43:22.825 videolist.cpp: getVideoListMetadata: index out of bounds: 0
```

Obviously, something's up with that index out of bounds error. The UI skips over the "unique player command" option like it's not there. I can see it, but I can't use it.

---

### Post by newlinux on 2008-10-04
That is really weird, and I haven't ever heard of this problem. Maybe a DB problem? Try repairing your database. You can do this from mythweb or using the optimize_mythdb.pl script which should be in:

/usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl
```

perl /usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl

```

would run it.

Are there any other weird looking (DB or otherwise) errors in your front or backend log not directly related to when you try to change this?

---

### Post by ttabbal on 2008-10-06
I ran the optimize script. It completed without errors. 

I checked the DB directly with the mysql command line client. It looked OK to me, so I added a test record. Loading the File Types GUI in the frontend, it could see the new test record. So I added a couple more. It seems to cache the data, I had to exit the frontend and re-load it, but it could see those records as well. So I can add to the DB manually and it seems to see the settings. I'll try messing around in there a little. I'm very familiar with SQL, so I shouldn't mess anything up doing this. I can always restore the backup if I have to. Here's the current table, let me know if you see anything it shouldn't like in there. 
```

mysql> select * from videotypes;
+-------+-----------+-------------+----------+-------------+
| intid | extension | playcommand | f_ignore | use_default |
+-------+-----------+-------------+----------+-------------+
|     2 | log       |             |        1 |           0 |
|     3 | mpg       | Internal    |        0 |           0 |
|     4 | avi       |             |        0 |           1 |
|     5 | vob       | Internal    |        0 |           0 |
|     6 | mpeg      | Internal    |        0 |           1 |
|     7 | VIDEO_TS  | Internal    |        0 |           0 |
|     8 | iso       | Internal    |        0 |           0 |
|     9 | img       | Internal    |        0 |           0 |
|     1 | txt       |             |        1 |           0 |
|    10 | nzb       |             |        1 |           0 |
|    11 | sfv       |             |        1 |           0 |
|    12 | nfo       |             |        1 |           0 |
|    13 | mds       |             |        1 |           0 |
+-------+-----------+-------------+----------+-------------+
13 rows in set (0.00 sec)
```

---

### Post by newlinux on 2008-10-06
I don't see anything wrong with that table -- looks pretty much like mine. I'm glad you have a workaround, because I really have no clue about why you can't edit it from the frontend. It seems it is connecting to the DB just fine if there aren't any meaningful errors in mythfrontend and it reads newly inserted types, videos, etc.

Yeah, I've noticed the caching when I change this info on one frontend it doesn't automatically show up on other frontends.

A shot in the dark, but maybe a different theme. I've seen problems where people can't access or use certain parts of myth due to errors in the theme they were using...

---

### Post by ttabbal on 2008-10-06
Thanks for the info. I'll try another theme and see if that helps.

---

### Post by ttabbal on 2008-10-07
No joy on the theme change. I was running the old 7.x Mythbuntu theme. I changed to the current one and it's still not working in the UI. No idea why. For now, I guess I'll do it in the database directly. Not ideal, but at least it works.

---

### Post by mcuerdo on 2008-10-19
i've got the same problem, can't add a new file type in mythvideo

---

### Post by ttabbal on 2008-10-20
> **mcuerdo said:**
> i've got the same problem, can't add a new file type in mythvideo

The only fix I found is to edit the database directly, then restart MythFrontend. If you don't know what that means, or what the query above means, don't attempt it. You can seriously screw up your database if you don't know what you're doing with SQL. 

I'm about ready to just buy a couple Popcorn Hour boxes. :)

---

