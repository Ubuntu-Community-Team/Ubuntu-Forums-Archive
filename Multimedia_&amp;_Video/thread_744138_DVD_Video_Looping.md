---
title: "DVD Video Looping"
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by mip on 2008-04-03
I've created a VOB file using [dvd-slideshow]("http://dvd-slideshow.sourceforge.net/wiki/Main_Page"). I'd like to burn this to a DVD so that the video loops continuously. 

Does anyone know how I can do this?

Cheers.

---

### Post by mc4man on 2008-04-03
How is it structured? menu? 1 title with chapters, 1 title w/ 1 chapter, multiple titles , ect.

---

### Post by mip on 2008-04-03
I have just a single VOB file. No Menus, titles etc.

---

### Post by mc4man on 2008-04-03
Without trying out dvd-slideshow I couldn't really say. With a 'normal' dvd movie structure i'd use PgcEdit to edit the post command or use a JumpVTS_TT.
You could post a query here [https://forum.doom9.org/forumdisplay.php?f=50](https://forum.doom9.org/forumdisplay.php?f=50)  (5 day wait from registering to posting)
I use the win. version in wine, there is a linux version but the gui is not as good.
It is not a very intuitive app for advanced operations
It would be interesting to try I'll give it a shot over the weekend and post back if you haven't found a solution

---

### Post by mip on 2008-04-04
bump.

---

### Post by mc4man on 2008-04-04
basically very easy to do _after_ turning your 1 .vob into a proper dvd structure (VIDEO_TS)
dvd-slideshow is a real pita to use (at least for me) took a couple of hours to figure out and resolve some of the errors - 1st. with ffmpeg and then with dvd-menu
What you need to do is either use dvdauthor or the built -in dvd-menu to create a video_ts. I gave up on trying to get dvdauthor to accept the .xml created by dvd-slideshow and also on having a dvd menu at all - dvd-menu would always error out at end. This is what did work and should be suitable for what you have. Assuming you didn't delete .xml that dvd-slide created (same directory as .vob was created in ) in terminal
```
doug@doug-desktop:~$ dvd-menu -f /home/doug/tests.xml -o /home/doug -nomenu
```
adjust paths and names as needed  -f = path to .xml,  -o =path to output new VIDEO_TS
Once you have a video_ts it's very simple to create loop in PgcEdit
You would use open dvd tab and browse to your video_ts ,it may want to correct substream error - let it
Highlight VTST 1,1 in left box, in right box there will be 1 post command - 1 Exit  (or if multi title last VTST - the one with 1 Exit as post command)
highlight it, press spacebar and a dialog box will pop up - command editor
At top pick >jump to > First-Play PGC > CallSS-Fp, choose that,  then click ok, your post command should now be changed to 1 (CallSS) Call the First Play PGC, resume cell 1
Now in left box double click  VTST 1,1 and a cell table will be built. Scroll to the last cell and in the middle are 2 white boxes - the one on left will probably have a number (255), just highlight it and change to 0. (all of those boxes should be 0 for all cells) Click save and your done
The reason for changing 255 to zero is the last cell is set to a runtime+infinite pause - you need it to end so playback at cell 1 can resume
While this is very easy to do I'd make a copy of the VIDEO_TS first just in case

edit; the above pgcedit method will work on any reauthored Video_TS, ie. no menu - with menu procedure will be different
tested with vlc and dvd-rw on standalone - audio sounds surprisingly decent - wav>AC3

---

### Post by mip on 2008-04-05
Many thanks. I'll give this a try.

---

### Post by mc4man on 2008-04-05
if you need any help with pgcedit let me know - just installed linux version on another box - the gui is better than i remembered - should be  a piece if cake
[http://download.videohelp.com/r0lZ/pgcedit/](http://download.videohelp.com/r0lZ/pgcedit/)

---

### Post by mip on 2008-04-07
I followed your instructions carefully and everything seemed to go well. However, the video is not looping. Is there something I can post so you can check that I have completed the process correctly?

Also, throughout the process (except with the dvd-menu command which complained when I tried to use -w) I have specified widescreen. When I play the DVD on my DVD player the TV does not automatically revert to a widescreen display as with other DVDs. I have to manually select widescreen. Is there something I can do so that the DVD player will detect the video is 16:9 and send the relevant signal to the TV?

---

### Post by mc4man on 2008-04-07
rather than post some screenshots yet open the video_ts in pgcedit, close out the bov scan and in the view tab choose show log - save as .txt and post. That won't show why it's not looping but will show the structure and we'll take it from there. i retested the dvd-rw in 3  standalones (sony, pioneer, cyperhome ) works fine which would seem to eliminate standalone incompatibility.
As far as AR it shouldn't be a problem to change - post log first.
To show as ex. I didn't have any jpg's so i used what was in OO to make slideshow
on left set to 16:9 letterbox, on right orig  (screenshots from vlc, using default ar - will reburn and test on standalone0)
dvd-menu is a somewhat whacked app - should be able to work around it's shortcomings.

---

### Post by mip on 2008-04-08
Here's the log:

```
Reading DVD "/home/user/test/dvd_fs/VIDEO_TS"

>>> Reading VMG IFO.
Reading VMG IFO.
Reading "/home/user/test/dvd_fs/VIDEO_TS/VIDEO_TS.IFO" (translation: binary, seek: 0)
Computing start and end addresses of the VMG tables.
Extracting VMGM_MAT.
Extracting VMG_TT_SRPT.
Extracting VMGM_PGCI_UT.
Extracting VMG_PTL_MAIT.
Extracting VMG_VTS_ATRT.
Extracting VMG_TXTDT_MG.
Extracting VMGM_C_ADT.
Extracting VMGM_VOBU_ADMAP.
Parsing VMG IFO.
Found 1 VTSs
Parsing FP-PGC.
Found 1 pre, 0 post and 0 cell commands.
Parsing PGCI_UT (VTS 0).

Reading VTS 1 IFO.
>>> Reading VTS 1 IFO.
Reading "/home/user/test/dvd_fs/VIDEO_TS/VTS_01_0.IFO" (translation: binary, seek: 0)
Computing start and end addresses of the tables.
Extracting VTSI_MAT.
Extracting VTS_PTT_SRPT.
Extracting VTS_PGCI.
Extracting VTSM_PGCI_UT.
Extracting VTS_TMAPTI.
Extracting VTSM_C_ADT.
Extracting VTSM_VOBU_ADMAP.
Extracting VTS_C_ADT.
Extracting VTS_VOBU_ADMAP.
Parsing VTS 1 IFO.
Parsing VTS_PGCI.
Parsing PGC 1
Found 0 pre, 1 post and 0 cell commands.
Found 76 cells in Cell playback table.
Found 76 cells in Cell position table
Parsing VTS_PTT_SRPT (VTS 1)
Processing TTU 1.
Parsing PGCI_UT (VTS 1).

Parsing VMG_TT_SRPT table.
Found 1 Titles.

Reading menu button informations in VOBs...
Scanning menu VOB of VTS 0...
Note: No Subpic stream in IFO
No Cells in menu domain
Scanning menu VOB of VTS 1...
Note: No Subpic stream in IFO
No Cells in menu domain
>>> Found a total of 0 menu buttons in menu domain.

DVD loaded OK.

MsgBox "Verify number of streams (in whole DVD)" -> yes to all
>>> Fix Streams:  Fixed 1 / 1 discrepancies.
>>> DVD Opened OK.  1 VTS loaded.
>>> DVD Opened OK.  1 VTS loaded.   Found a total of 0 BOVs.
>>> Creating backup...
Create Backup: Creating directory "/home/user/test/dvd_fs/VIDEO_TS/PgcEdit_backup"
Create Backup: Copying "/home/user/test/dvd_fs/VIDEO_TS/VIDEO_TS.IFO" to "/home/user/test/dvd_fs/VIDEO_TS/PgcEdit_backup".
Create Backup: Copying "/home/user/test/dvd_fs/VIDEO_TS/VTS_01_0.IFO" to "/home/user/test/dvd_fs/VIDEO_TS/PgcEdit_backup".
>>> Saving buttons information...
>>> /home/user/test/dvd_fs/VIDEO_TS/PgcEdit_backup/menubuttons.but not created: no menu buttons or BOVs in DVD.
>>> Backup created OK.
Reading "/home/user/.PgcEdit/mru.cfg" (translation: auto, seek: 0)
Saving data to "/home/user/.PgcEdit/mru.cfg" (mode: write).
Reading "/home/user/.PgcEdit/mru.cfg" (translation: auto, seek: 0)
>>> Building PGC editor window...
>>> Building cell table...
>>> Writing VMG IFO.
Saving data to "/home/user/test/dvd_fs/VIDEO_TS/VIDEO_TS.IFO" (mode: write).
>>> Writing VTS 1 IFO.
Saving data to "/home/user/test/dvd_fs/VIDEO_TS/VTS_01_0.IFO" (mode: write).
>>> Fixing VTS sectors.
Reading "/home/user/test/dvd_fs/VIDEO_TS/VIDEO_TS.IFO" (translation: binary, seek: 0)
Saving data to "/home/user/test/dvd_fs/VIDEO_TS/VIDEO_TS.IFO" (mode: write).
>>> Copying BUP files.
PgcEdit: Write DVD: Copying "/home/user/test/dvd_fs/VIDEO_TS/VIDEO_TS.IFO" to "/home/user/test/dvd_fs/VIDEO_TS/VIDEO_TS.BUP".
PgcEdit: Write DVD: Copying "/home/user/test/dvd_fs/VIDEO_TS/VTS_01_0.IFO" to "/home/user/test/dvd_fs/VIDEO_TS/VTS_01_0.BUP".
>>> DVD saved OK!  VTS sectors (standard method) OK!
MsgBox "PgcEdit: Save DVD" -> ok



```

---

### Post by mc4man on 2008-04-08
your log looks ok in terms of there is 1 post command - you want to make sure it's the right one. I'll attach 2 screenshots (hope you can see.) If the post command is the same as i show then open cell tables again (d. click on VTST1,1) and make sure the last cell looks like screenshot.( zeros in 2 white boxes) If the cell flag is 2 try setting to 8 - click on box (red arrow) and choose seamless and uncheck STC,  if it's 10 just uncheck STC
You should test in vlc - the other players won't respect post comm.
For 16:9 highlight VTST1,1 , click on domain, choose d. stream attributes and choose 16:9 letterboxed (other screenshot )
If you messed with this to much delete your backup ,make a new one and try again

---

