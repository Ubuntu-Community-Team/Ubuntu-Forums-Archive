---
title: "Subtutles Help!!!"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by jehozadakk on 2007-03-12
I need help getting subtitles to work correctly in Ubuntu Edgy Eft.  I am using Kaffeine (though I tried other installed players as well).  The subtitle file is an .srt file.  Kaffeine recognizes the file and tries to render the subtitles, but it doesn't seem to be recognizing the font or maybe the color.  An example of what subtitles look for me:

<font color ="#ffffff">The bright sun blinded her</font>
<font color ="#ffffff">and erased her memory.</font>

So while I can still read the words, it is making it very difficult to read them fast enough and sort through the junk that is on the screen as well.  Any suggestions would be welcome.

I should also mention that I used this same subtitle file from windows media player and it recognized and rendered the file perfectly, so I don't believe the file is corrupt.

THanks

---

### Post by chewearn on 2007-03-12
I used VLC player, and has no problem with the subtitles.  I don't think the <font> attribute is supported.  But srt file is simply a text file, you can remove all those crap by find-replace using a text editor.

You can also change the default subtitles rendering, by going to:
  Settings -> Preferences -> Video -> Subtitles/OSD

Example, to change color, go to "Text renderer".  You can also add a background color to the subtitle, so it is "highlighted".

---

### Post by panch0 on 2007-03-12
Try with KPlayer. It has File - Load Subtitles command, and so far all subtitles I tried worked fine. KPlayer uses MPlayer as the backend.

---

### Post by shirilover on 2007-03-12
Most of the player available do not support stylized subtitles.
I happen to use MPlayer, which I compile from SVN myself, and I have no problems with subtitles.

---

