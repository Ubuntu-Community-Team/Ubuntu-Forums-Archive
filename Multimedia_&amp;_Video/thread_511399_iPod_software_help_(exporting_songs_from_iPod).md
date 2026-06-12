---
title: "iPod software help (exporting songs from iPod)"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by yeah, okay on 2007-07-27
(I hope this is the right forum) 

I recently reinstalled Ubuntu but didn't back up my music to an external drive or discs, and I'd like to know if and what software is available that could transfer my music from my iPod back to my computer. I use GTKpod for iPod support and GTKpod can export songs, BUT I want them exported as folders (band -> album, something like that), not just one folder filled with all the mp3s together, which would happen if I went that route with GTKpod. I use Rhythmbox as well, but that doesn't seem to do it. 

Help?

---

### Post by cometdog on 2007-07-28
Actually, gtkpod has a really nice facility for exporting songs just like you want.

[LIST=1]
[*]Select your ipod in the playlist column on the left so your music shows up on the right.
[*]Make sure all your music is selected by clicking on All in every sort tab.
[*]Right-click in one of the sort tab lists and choose "Copy tracks to filesystem."
[*]Navigate to the base folder where you want your music.
[*]Let your mouse pointer hover over over the filename format box for a description of how to enter your desired directory / file structure.  I used %a/%A/%T - %t which is <artist>/<album>/<track number> - <title>.  You can even specify different organization for different file types by appending extensions like .mp3.
[/LIST]

Depending on how new you are to linux in general, it may help to inform you that the forward slash "/" indicates a directory.

Hope this helps.

---

### Post by doclivingston on 2007-07-28
> **yeah, okay said:**
>  I use GTKpod for iPod support and GTKpod can export songs, BUT I want them exported as folders (band -> album, something like that), not just one folder filled with all the mp3s together, which would happen if I went that route with GTKpod. I use Rhythmbox as well, but that doesn't seem to do it. 

Rhythmbox should be able to do it. If you go to the preferenced (Edit->Preferences), there should be options for the Library Location and Library Structure on one of the tabs, check that these are set up how you want.

Click on the iPod source that should be the the sidebar, and select all the tracks (Edit->Select All). Then either drag then over to the Library source in the sidebar, or use Edit->Copy, click on the Library source, and Edit->Paste. If everything is working right, it should start copying them all to the place specified by your library settings.

---

### Post by jkirby on 2008-07-08
Thank you Cometdog.  Your filename format tip finally allowed me to restore the songs from my iPod in the way I wanted.

---

