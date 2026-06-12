---
title: "DVD rip capabilities disappeared from Mythbuntu frontend menu"
date: 2010-09-03
forum: Mythbuntu
---

### Post by Nausser on 2010-09-03
I am running Mythbuntu 10.04. I've had only very minor hiccups in the past which were simple tweaks to my hardware. 
Mythbuntu recently did some upgrades and now the possibility of ripping DVDs is gone altogether. What I mean is the Optical Discs Menu, where you could import a DVD always was, is now not there at all. I checked the menu file in "/usr/share/mythtv/themes/defaultmenu/optical_menu.xml" and these are the contents that I found to confirm it is in fact gone.
```
<?xml version="1.0" encoding="UTF-8" ?>
<mythmenu name="OPTICAL_DISK">

    <button>
        <type>DVD_PLAY</type>
        <text>Play DVD</text>
        <description>Play a film on DVD</description>
        <action>JUMP Play DVD</action>
        <depends>mythvideo</depends>
    </button>

    <button>
        <type>VCD_PLAY</type>
        <text>Play VCD</text>
        <description>Play the video on a VCD</description>
        <action>JUMP Play VCD</action>
        <depends>mythvideo</depends>
    </button>

    <button>
        <type>ARCHIVE</type>
        <text>Archive Files</text>
        <description>Write video to a data DVD</description>
        <action>PLUGIN mytharchive</action>
        <depends>mytharchive</depends>
    </button>

    <button>
        <type>MUSIC_RIP</type>
        <text>Import CD</text>
        <description>Import music from an audio CD</description>
        <action>JUMP Rip CD</action>
        <depends>mythmusic</depends>
    </button>

    <button>
        <type>EJECT</type>
        <text>Eject media</text>
        <description>Eject CD or DVD from drive</description>
        <action>EJECT</action>
    </button>

</mythmenu>

```

I was then looking to make sure MTD(Myth Transcoding Daemon) is running and it isn't even installed! Worse yet, I can't even install it! It is supposed to be a part of mythDVD package or mythvideo package. I've re-installed those packages and still no prevail. 
I've checked to see if mtd is in my "/usr/bin" and it is not. The closest thing I have is mythtranscode which I believe is different.

If anyone has run into this one or can offer me your "/usr/share/mythtv/themes/defaultmenu/optical_menu.xml" file, I would be greatly appreciated. Everything may be just fine and I just need to add back that particular button. I just don't know where it would point exactly so that is why I could really use a sample.

Thanks!

**Update:**
I've installed the myth-frontend on a second machine and copy/pasted the missing button into my myth box. I now have the option there, however, when I select to import DVD, it does absolutely nothing. This is so frustrating that an update would do this! I have been happily and gradually importing my entire DVD collection and now I'm at a stand still.

---

### Post by petatkinson on 2010-09-04
Have you tried starting Mythbuntu Control Centre and ticking all the boxes to enable all the plugins.It might be worth a try.I reckon your solution lies in MCC.

---

### Post by Nausser on 2010-09-04
> **petatkinson said:**
> Have you tried starting Mythbuntu Control Centre and ticking all the boxes to enable all the plugins.It might be worth a try.I reckon your solution lies in MCC.

Sorry, I forgot to mention that one earlier. That is actually the first thing I tried. I even tried unchecking, executing, restarting and rechecking all plugin options in myth control centre with no change at all. From the myth control centre, I even removed the frontend role altogether, restarted, and re-issued its frontend role, of course with no prevail. 

On a slightly different, yet similar note, I see changes all over in the look or feel of things.  Other changes such as flash streaming suddenly doesn't work. Myth-frontend crashing while doing cut point edits which I never had an issue with before.
All this started with recent upgrades. I wish I knew exactly what they were. So be cautious of those recent updates. It seems they are sereious trouble! For me anyways.

---

### Post by kja999 on 2010-09-05
Ripping DVDs relies on mythvideo, so this really is the only plugin you should need to install to get it working.

Have you tried running mythfrontend from a terminal and checking for errors?
You may see a plugin initialisation error early on, or an error at point of using the menu option

---

