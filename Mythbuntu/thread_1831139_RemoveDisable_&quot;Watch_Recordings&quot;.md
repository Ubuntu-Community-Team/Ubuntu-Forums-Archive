---
title: "Remove/Disable &quot;Watch Recordings&quot;"
date: 2011-08-23
forum: Mythbuntu
---

### Post by SeanHagen on 2011-08-23
Hey folks.

I installed Mythbuntu about a month ago, and so far I'm loving it.

However, I don't have a TV capture card installed, and I don't have cable ( and I don't plan on getting cable or satellite in the foreseeable future ).

How do I disable the "Watch Recordings" in the Media Library? It's a feature I'm never going to use, as I'm never going to watch or record live TV using my MythTV setup.

I've done some Googling about to see if anybody else has tried this, but I can't seem to find anything.

Any help is much appreciated.

Cheers.

---

### Post by ian dobson on 2011-08-23
Hi,

Mythtv stores the menu structure in xml files, so all you need to do is find the xml file for the main menu and edit it with a text editor.

Here's part of the dvr mainmenu xml file
/usr/share/mythtv/themes/DVR/mainmenu.xml

```

<?xml version="1.0" encoding="UTF-8" ?>
<mythmenu name="MAIN">

    <button>
        <type>TV_WATCH_RECORDINGS</type>
        <text>Watch Recordings</text>
        <description>Play Recordings</description>
        <action>TV_WATCH_RECORDING</action>
    </button>

    <button>
        <type>TV_CONFLICTS</type>
        <text>Upcoming Recordings</text>
        <description>See what will be recorded next</description>
        <action>TV_FIX_CONFLICTS</action>
    </button>

    <button>
        <type>TV_SCHEDULE_RECORDINGS</type>
        <text>Schedule Recordings</text>
        <description>Pick shows to record</description>
        <action>MENU tv_schedule.xml</action>
    </button>
```

Note if you edit these files and then do an update, the update could well overwrite yor changes.

Hope this helps 
Regards
Ian Dobson

---

### Post by uteck on 2011-08-23
If you copy the file to your .mythtv directory and then edit it, you will not lose your changes when you update the system.  I did this when I added Hulu and Boxee menus.  Before I did this the file would get replaced during an update, but with the edited version in .mythtv the system reads that one first before looking for the one in /usr/share/mythtv/

---

