---
title: "Splitting large MP3 file into tracks - seems impossible!"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by jdolan on 2007-06-07
Hello, 

I'm slowly moving my day to day computer usage over to Ubuntu and (up to this point) it has succeeded. However, I have recently acquired 7 large MP3 files (each file containing 10 - 15 tracks). I also acquired .cue files along with these MP3's. (One cue file per large MP3 file). I understand that the .cue files help a mounting device to isolate each of the tracks from within the MP3's. 

I have tried:

**K3B** but (despite having installed all the appropriate MAD mp3 decoder libraries and plug ins) it still informs me that they are not installed.)

**X-CD-Roast** but I do not have the first clue regarding how to use this software to burn my MP3's to disc (using the CUE files to ensure the tracks are isolated).

**I've also tried using a Windows application called Slice (under the WINE emulator), however, this does not work as it splits the tracks at the incorrect points as some tracks have moments of silence in them and it assumes these are track ends**.

**I've tried MagicISO and Daemon Tools** from within Windows to just try to mount the cue files but they both say the .cue files are inaccessible. I know the .cue files are not corrupt as their contents are fine.

**I've tried manually splitting the tracks using Audacity ** but when re-encoded the tracks suffer from a massive lack in quality.

**I've also tried mounting the cue files through Linux to no avail.**

[SIZE="4"]My question is this! -[/SIZE] How do I split / mount / burn these MP3 files (using the CUE files) so that the MP3's are individual files. 

Thanks!
Jord

---

### Post by dannystaple on 2007-06-08
Hi Jdolan,
Frustrating - for getting K3B to do its thing, I probably could not recommend enough reading the Ubuntu Guide - [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_K3b_.28CD.2FDVD_burning_software.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_K3b_.28CD.2FDVD_burning_software.29).

However, you would still end up with a CD with one big track anyway.

To split them up, audacity was a step in the right direction, but then you need to check the parameters that you re-encode with. It is this encoding bitrate and encoding quality that means everything. In the preferences, look at file formats, MP3 Export Setup, Quality. and then set this value nice and high!

---

### Post by jdolan on 2007-06-11
Thanks for your help. It is indeed very frustrating and a little dissapointing that the issue has not been programmatically resolved (to my knowledge) as of yet. If any developer has the time or inclination - a piece of equipped software would be exceptionally appreciated!

---

### Post by TravMan63 on 2007-06-12
In Audacity did you check the quality output?
 (edit/preferences - bit rate)

or try exporting as ogg quality 10? (if that format works for your application)

----
um - looks like jdolan suggested this also :KS - guess that's now 2 votes for Audacity... 
----
Audacity has been a good performer for my task (editing and compressing mp3's for web publishing)

For streaming audio, (in windows) - I've used stream ripper with winamp - don't think that will work for you though.

---

### Post by timcredible on 2007-06-12
audacity will do that.  it'll also save in any format you want.  i've used it to do all sorts of stuff, including pulling stuff off of vinyl and tape and it has no problems with quality.

---

### Post by Gavin77 on 2007-06-12
Mp3DirectCut works flawlessly under Wine, grab it from [http://mpesch3.de1.cc/mp3dc.html](http://mpesch3.de1.cc/mp3dc.html)
Make sure you download mpglib.dll also, it's on the main page.

---

### Post by diskotek on 2007-06-23
are there any other cue splitter for linux?

---

### Post by diskotek on 2007-06-23
well, i've already find a small app for that for .ogg & . mp3

[http://mp3splt.sourceforge.net/mp3splt_page/home.php](http://mp3splt.sourceforge.net/mp3splt_page/home.php)


here is an example for this cli programme. 
you have a file diskotek.cue & diskotek.mp3

```
 mp3splt -c diskotek.cue diskotek.mp3
```

---

### Post by lagartoflojo on 2007-07-08
> **diskotek said:**
> well, i've already find a small app for that for .ogg & . mp3

[http://mp3splt.sourceforge.net/mp3splt_page/home.php](http://mp3splt.sourceforge.net/mp3splt_page/home.php)


here is an example for this cli programme. 
you have a file diskotek.cue & diskotek.mp3

```
 mp3splt -c diskotek.cue diskotek.mp3
```

I've been looking for something like this, thanks!
By the way, it's in the repos, so you can install it wil Synaptic/aptiitude.

---

### Post by robinkjeld on 2007-11-14
Thanks a lot! :-D

---

