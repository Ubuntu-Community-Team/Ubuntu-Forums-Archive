---
title: "Video Manager"
date: 2009-03-20
forum: Mythbuntu
---

### Post by tbaca on 2009-03-20
I am running 8.10 with fixes.

Last night I noticed that when I go into the Video Manager to update meta data, the screen opens up with the "Enter IMDB #" window on top of the listing and no matter what I do it does not go away.

Tony

---

### Post by entourage on 2009-03-24
I've got the same issue.  Can't do anything about the window.  Then when I try to type something in and hit ESC it crashes the Frontend...

---

### Post by newlinux on 2009-03-24
I have no idea what this is, but try running a repair on the DB... you can use phpmyadmin, I think MCC, or there are a couple of scripts. The following should do it

```

mysqlcheck -u root -p  --repair mythconverg

```

Other than that, you will probably want to post your frontend logs from when this happens.

---

### Post by entourage on 2009-03-25
I first decided to try changing Themes because I've had other issues where the particular theme didn't have the updated info.
Now, I don't have the "Enter IMDB #" window overlay, but I still can't input the number.  Here's a copy of the relevant portion of my mythfrontend.log:

**BTW, this is before I switched the theme...
```
2009-03-24 16:22:43.103 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/video-ui.xml
2009-03-24 16:22:43.429 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-03-24 16:24:32.416 MythVideo: VideoManager : Failed to get entertmdb object.
MythThemedDialog.o: something is requesting a screen update of zero size. A widget probably has not done a calculateScreeArea(). Will redraw the whole screen (inefficient!).
Starting mythfrontend.real..
2009-03-24 16:25:10.277 New DB connection, total: 2
2009-03-24 16:25:10.278 Connected to database 'mythconverg' at host: localhost
2009-03-24 16:25:10.280 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-24 16:25:10.281 Enabled verbose msgs:  important general
2009-03-24 16:25:11.760 No theme dir: /home/trulockam/.mythtv/themes/Mythbuntu-8.04-wide
2009-03-24 16:25:11.762 Primary screen 0.
2009-03-24 16:25:11.763 Using screen 0, 1920x1080 at 0,0
2009-03-24 16:25:11.764 No theme dir: /home/trulockam/.mythtv/themes/Mythbuntu-8.04-wide
2009-03-24 16:25:11.765 Switching to wide mode (Mythbuntu-8.04-wide)
2009-03-24 16:25:11.847 Using the Qt painter
2009-03-24 16:25:11.848 JoystickMenuClient Error: Joystick disabled - Failed to read /home/trulockam/.mythtv/joystickmenurc
2009-03-24 16:25:11.850 lirc init success using configuration file: /home/trulockam/.mythtv/lircrc
2009-03-24 16:25:14.926 Specified base font 'medium' does not exist for font clock
2009-03-24 16:25:14.926 Specified base font 'medium' does not exist for font small
2009-03-24 16:25:14.926 Specified base font 'medium' does not exist for font medium
2009-03-24 16:25:14.926 Specified base font 'medium' does not exist for font large
2009-03-24 16:25:14.927 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2009-03-24 16:25:15.066 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-24 16:25:15.115 Registering Internal as a media playback plugin.
2009-03-24 16:25:15.466 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-24 16:25:15.644 Failed to run 'cdrecord --scanbus'
2009-03-24 16:25:15.650 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-24 16:25:15.655 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-24 16:25:15.676 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-03-24 16:25:15.787 No theme dir: /home/trulockam/.mythtv/themes/Mythbuntu-8.04-wide
2009-03-24 16:25:25.363 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/video-ui.xml
2009-03-24 16:25:25.647 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-03-24 16:25:41.890 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/video-ui.xml
2009-03-24 16:26:14.160 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/video-ui.xml
2009-03-24 16:28:42.302 MythVideo: VideoManager : Failed to get entertmdb object.
MythThemedDialog.o: something is requesting a screen update of zero size. A widget probably has not done a calculateScreeArea(). Will redraw the whole screen (inefficient!).
Starting mythfrontend.real..
2009-03-24 16:29:27.311 New DB connection, total: 2
2009-03-24 16:29:27.312 Connected to database 'mythconverg' at host: localhost
2009-03-24 16:29:27.315 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-24 16:29:27.316 Enabled verbose msgs:  important general
2009-03-24 16:29:28.098 No theme dir: /home/trulockam/.mythtv/themes/Mythbuntu-8.04-wide
2009-03-24 16:29:28.101 Primary screen 0.
2009-03-24 16:29:28.102 Using screen 0, 1920x1080 at 0,0
2009-03-24 16:29:28.103 No theme dir: /home/trulockam/.mythtv/themes/Mythbuntu-8.04-wide
2009-03-24 16:29:28.104 Switching to wide mode (Mythbuntu-8.04-wide)
2009-03-24 16:29:28.130 Using the Qt painter
2009-03-24 16:29:28.130 JoystickMenuClient Error: Joystick disabled - Failed to read /home/trulockam/.mythtv/joystickmenurc
2009-03-24 16:29:28.133 lirc init success using configuration file: /home/trulockam/.mythtv/lircrc
2009-03-24 16:29:30.542 Specified base font 'medium' does not exist for font clock
2009-03-24 16:29:30.542 Specified base font 'medium' does not exist for font small
2009-03-24 16:29:30.542 Specified base font 'medium' does not exist for font medium
2009-03-24 16:29:30.542 Specified base font 'medium' does not exist for font large
2009-03-24 16:29:30.543 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2009-03-24 16:29:30.641 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-24 16:29:30.669 Registering Internal as a media playback plugin.
2009-03-24 16:29:30.725 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-24 16:29:30.759 Failed to run 'cdrecord --scanbus'
2009-03-24 16:29:30.764 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-24 16:29:30.769 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-24 16:29:30.790 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-03-24 16:29:30.839 No theme dir: /home/trulockam/.mythtv/themes/Mythbuntu-8.04-wide
2009-03-24 16:29:58.381 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/video-ui.xml
2009-03-24 16:29:58.724 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-03-24 16:30:10.503 Video Search: Executing '/usr/share/mythtv/mythvideo/scripts/imdb.pl -M tv=no;video=no Scrubs My Musical'
2009-03-24 16:30:11.918
2009-03-24 16:30:11.918 GetVideoList returned 0 possible matches
2009-03-24 16:30:22.125 MythVideo: VideoManager : Failed to get entertmdb object.
MythThemedDialog.o: something is requesting a screen update of zero size. A widget probably has not done a calculateScreeArea(). Will redraw the whole screen (inefficient!).
Starting mythfrontend.real..
2009-03-24 16:31:07.421 New DB connection, total: 2
2009-03-24 16:31:07.422 Connected to database 'mythconverg' at host: localhost
2009-03-24 16:31:07.425 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-24 16:31:07.425 Enabled verbose msgs:  important general
2009-03-24 16:31:08.141 No theme dir: /home/trulockam/.mythtv/themes/Mythbuntu-8.04-wide
2009-03-24 16:31:08.144 Primary screen 0.
2009-03-24 16:31:08.144 Using screen 0, 1920x1080 at 0,0
2009-03-24 16:31:08.146 No theme dir: /home/trulockam/.mythtv/themes/Mythbuntu-8.04-wide
2009-03-24 16:31:08.147 Switching to wide mode (Mythbuntu-8.04-wide)
2009-03-24 16:31:08.173 Using the Qt painter
2009-03-24 16:31:08.174 JoystickMenuClient Error: Joystick disabled - Failed to read /home/trulockam/.mythtv/joystickmenurc
2009-03-24 16:31:08.176 lirc init success using configuration file: /home/trulockam/.mythtv/lircrc
2009-03-24 16:31:10.748 Specified base font 'medium' does not exist for font clock
2009-03-24 16:31:10.748 Specified base font 'medium' does not exist for font small
2009-03-24 16:31:10.749 Specified base font 'medium' does not exist for font medium
2009-03-24 16:31:10.749 Specified base font 'medium' does not exist for font large
2009-03-24 16:31:10.749 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2009-03-24 16:31:10.848 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-24 16:31:10.876 Registering Internal as a media playback plugin.
2009-03-24 16:31:10.932 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-24 16:31:10.964 Failed to run 'cdrecord --scanbus'
2009-03-24 16:31:10.969 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-24 16:31:10.975 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-24 16:31:10.996 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)

```
Basically this is after 3 failed attempts to enter the IMDB number and when I hit ESC, it crashed the frontend each time and I then restarted it.  Does that help at all?

---

### Post by newlinux on 2009-03-25
did you try repairing your database? I doubt that's the problem though, but it doesn't hurt. I run repair and optimize scripts daily,

these messages seem to indicate part of the problem:

"videolist.cpp: getVideoListMetadata: index out of bounds: 0"
and 
"GetVideoList returned 0 possible matches"

Did this used to work and all of sudden stopped working? Can you still get to these videos in your filesystem? Have you changed any permissions on disk or filetype settings or the anything about the video scan directory in myth?

---

### Post by entourage on 2009-03-25
Honestly I haven't tried the repair yet.  This is just something I noticed recently and in all honesty doesn't affect me that much.  I've actually never used it before but I just figured that if it wants me to enter the # and then crashes...something isn't right.  I don't store a lot of videos, but I know people who do, who would benefit from this.

Fortunately changing the theme seems to have stopped the crashing and I can watch the few videos that I have without problems.

I'll try the repair tonight...

---

### Post by tbaca on 2009-03-25
I did try the repair and that did not fix the problem.  I'll try switching themes and see if that does anything.

---

### Post by mike_hurley_1 on 2009-03-26
I have this same problem after upgrading my Mythbuntu Jaunty alpha install without changing my videos.
I'll check my logs tonight.

I'm using the default Mythbuntu theme.

---

### Post by tbaca on 2009-03-26
Only had a few minutes last night.  Changing themes does not help.

---

### Post by azmyth on 2009-03-26
I'm seeing this as well. I get a segfault and it says entermdb object not found. I suspect something is missing in the theme as I'm using MePo. Usually GANT is the fall back one I try and this gave the same fault. Must be something new that needs updating in the theme.

---

### Post by silverdulcet on 2009-03-26
I'm also experiencing this issue. The other problem is that I am unable to automatically or manually add covers to videos. When I go to the edit menu within Video Manager and check the cover files box I should be presented with a list of cover files within 
```
~/.mythtv/MythVideo
```

Instead I get "No Files Found"

Not sure if its related, but I noticed it the first time I encountered the "Enter IMDB" box.

---

### Post by jeefm on 2009-03-27
same here, if you guys have solved your problem, let me know.

---

### Post by tbaca on 2009-03-28
> **newlinux said:**
> did you try repairing your database? I doubt that's the problem though, but it doesn't hurt. I run repair and optimize scripts daily,

these messages seem to indicate part of the problem:

"videolist.cpp: getVideoListMetadata: index out of bounds: 0"
and 
"GetVideoList returned 0 possible matches"

Did this used to work and all of sudden stopped working? Can you still get to these videos in your filesystem? Have you changed any permissions on disk or filetype settings or the anything about the video scan directory in myth?

I get the one error "videolist.cpp: getVideoListMetadata: index out of bounds: 0", not the other.  Mine has worked for sometime, but I can not say exactly when it stopped because I don't go into the video manager too often.

---

### Post by Jove on 2009-03-30
Similar symptoms here. Video Manager displays all videos, but I see "Enter IMDB #" box immediately. When I select a video and hit "I", I get the "Select action" menu. "Search" then attempts to retrieve the correct info with the correct IMDB number, but then hangs mythfrontend at "retrieving..." screen.  mythfrontend.log shows:

"Video Data Query: Executing '/usr/share/mythtv/mythvideo/scripts/imdb.pl -D 41737'" as the last line before the hang.

Running imdb.pl -D ##### from the command line correctly retrieves and displays IMDB info on the terminal.

Help! :)

---

### Post by silverdulcet on 2009-04-08
Just wanted to reiterate that I haven't found a solution to this "Enter IMDB #" box in the Video Manager menu. The only error in my mythfrontend.log is this:
```
2009-04-08 18:57:54.234 videolist.cpp: getVideoListMetadata: index out of bounds: 0

```

I've run the suggested mysql scan's and fixes and it has not gotten rid of the box. 

My earlier problem with the cover files I did fix. My artwork directory was set to the incorrect path.

---

### Post by jimmyjimjim on 2009-04-14
This problem has been bugging me for a long time too and I just figured out a workaround.

The problem appears to be with this line...
MythVideo: VideoManager : Failed to get entertmdb object.

The video-ui.xml for the theme has
 <container name="enterimdb">... </container>

I manually changed enterimdb to entertmdb for the theme I'm using and it's working correctly now.

I doubt this is the correct long term fix but it's a workaround until the code that's calling the wrong object is fixed.

---

### Post by utar on 2009-04-15
The issue has just appeared for me as well.  It happened after I installed jyavenard's vdpau build of myth, and so must be linked to something that has been updated.


Utar

---

### Post by silverdulcet on 2009-04-21
> **jimmyjimjim said:**
> This problem has been bugging me for a long time too and I just figured out a workaround.

The problem appears to be with this line...
MythVideo: VideoManager : Failed to get entertmdb object.

The video-ui.xml for the theme has
 <container name="enterimdb">... </container>

I manually changed enterimdb to entertmdb for the theme I'm using and it's working correctly now.

I doubt this is the correct long term fix but it's a workaround until the code that's calling the wrong object is fixed.

Did you change the video-ui.xml file for your theme under:
```
/usr/share/mythtv/themes/
```

I tried changing that line in under the Mythbuntu-8.04-wide, ProjectGrayhem-wide, and glass-wide. None of those changes made the box go away. I also tried changing that file under the default and default-wide directories. 

I also noticed that when set to the metallurgy-wide theme the box no longer appears. So the box is showing up on certain themes and not on others.

---

### Post by kal on 2009-04-21
Hi,

Same issue here :(
I guess someone should open a bug ticket...

Cheers,
Kal

---

### Post by jeremycobert on 2009-05-04
has anyone followed up on this issue ? I just installed 9.04 and using the blue-tube wide i also get the IMDB popup box when I enter the video manager.

---

### Post by elgordo123 on 2009-05-04
Just checked launchpad.  It has been "Confirmed" 
[https://bugs.launchpad.net/mythbuntu/+bug/339880](https://bugs.launchpad.net/mythbuntu/+bug/339880)

We'll probably get a fix shortly.

---

### Post by rha7dotcom on 2009-05-19
I followed the 'make it disappear fix' at [https://bugs.launchpad.net/mythbuntu/+bug/339880](https://bugs.launchpad.net/mythbuntu/+bug/339880), which comments out the enterimdb section at video-ui.xml at /usr/share/mythtv/themes/<you-theme>/video-ui.xml....

Et voila!

It started complaining that it couldn't get the "entertmdb" object!

Guessing I renamed the section to "entertmdb" and it works.

So, in your /usr/share/mythtv/themes/<you-theme>/video-ui.xml
Change the line
    <container name="entertmdb">
to
    <container name="entertmdb">
or
    <container name="entermdb">

whichever works ....

And in case it doesn't, just comment it completely (surround it with < !-- and -- >) and run mythfrontend -v all from the console, go to the menu (M key) and choose "Manually enter video #" and go back to the console and see what mythtv complains about, then change the above line to whatever it was.

Hope this works for you guys.

Later
Rha7

---

### Post by jyavenard on 2009-05-23
> **azmyth said:**
> I'm seeing this as well. I get a segfault and it says entermdb object not found. I suspect something is missing in the theme as I'm using MePo. Usually GANT is the fall back one I try and this gave the same fault. Must be something new that needs updating in the theme.

The issue occurs as the packages now use tmdb rather than imdb.

You need to edit the default theme (blue) and add the entertmdb entry.

I just became aware of this issue today.
I've made a patch fixing the default theme and the MePo theme...

---

### Post by Archmage on 2009-06-05
Sorry, I'm running 9.04 and I'm quite confused. Is there any way to make it run?

At the moment I can't enter the movienumbers for my videos having blank icons and no summary at all. :(

---

### Post by klc5555 on 2009-06-05
> **Archmage said:**
> Sorry, I'm running 9.04 and I'm quite confused. Is there any way to make it run?

At the moment I can't enter the movienumbers for my videos having blank icons and no summary at all. :(

The fix requires editing one single keystroke in the affected file.

Just follow rha7dotcom's instructions from earlier in this thread. The only even mildly tricky part is correctly identifying the theme you're running. Then examine your theme's copy of the video-ui.xml file, and where it says: 

<container name="enterimdb">

(correcting rha7dotcom's inadvertant typo.)
edit this to read:

<container name="entertmdb">

Where the "i" in "imdb" is to be changed to "t" ("tmbd"). Save, and it's done.

Thanks to rha7dotcom for figuring this one out! :)

---

### Post by elgordo123 on 2009-06-05
Here is a command from the Bug forum that will fix it:  Taken from David Valentine on the Bug tracker. 

```
find /usr/share/mythtv/themes/ -name "video-ui.xml" -print | xargs sudo sed -i 's/enterimdb/entertmdb/g'
```

---

### Post by aussiedini on 2009-06-05
> **elgordo123 said:**
> Here is a command from the Bug forum that will fix it:  Taken from David Valentine on the Bug tracker. 

```
find /usr/share/mythtv/themes/ -name "video-ui.xml" -print | xargs sudo sed -i 's/enterimdb/entertmdb/g'
```

Thanks guys, just a note to say it worked for me. 

:p

---

