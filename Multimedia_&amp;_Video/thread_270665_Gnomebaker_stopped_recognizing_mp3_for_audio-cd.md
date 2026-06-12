---
title: "Gnomebaker stopped recognizing mp3 for audio-cd??"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by warjowuch on 2006-10-03
Hi there,
A few days ago, gnomebaker upgraded to 0.6.0. I happy, new shiny stuff. But now I wanted to burn an audio-cd from mp3. This worked before. But it just does not show the mp3-files in the file-browser, so I cannot add them. The filetype-indicator on the right only says 'audio-files'. But I thought, if mp3 is not an audio-file, then what is it??

So, does anyone recognize this problem or has anyone got an idea how to fix this?

---

### Post by warjowuch on 2006-10-04
*bump*

---

### Post by warjowuch on 2006-10-05
Can't anyone help me with this? Does anyone have this problem too?

---

### Post by endorfin on 2006-10-09
with me it works just fine. i think it didn't at first, but now it does anyway...

---

### Post by sKuarecircle on 2006-10-10
Having the same problem, can someone shed light on this?

---

### Post by koshari on 2006-10-16
i can confirm this to.

as of gnomebaker 0.6.0 the audio files type control box in the audio cd dialog is broken, 

not a good trade off IMHO for some flash new icons :-(

looks like i will need to use serpintine untill the package is apdated.

---

### Post by koshari on 2006-10-16
it seems as though it is not exclusive, as the mp3s are visable on another installation of gnomebaker 0.6.0 i have on a another PC. 

the pulldown button still doesnt give an option to change files however??


very interesting, 

i wonder if there is a workaround as there are very limited options in the preferences.

on the other PC i downgraded back to 0.5.1 and the mp3s showed up in mp3 view, though there is no option button in 0.5.1 so the upper panel doesnt descriminate between mp3 ect.

i will see if dragging the files in from nautilas is an option, brings up "mp3 plugin not installed, hmm looks like this new baby uses a different mp3 engine, gstreamer 10 ian guessing as the old one still relied on gstreamer8 mad or ugly...

yep added the gstreamer bad and ugly packages and were back in buisness,

---

### Post by Jallu59 on 2006-10-17
There was a bug in gnomebaker 0.6.0.unbuntu1.:rolleyes:  Now (yesterday, monday 16th of October) they have released 0.6.0.ubuntu2, in which the bug is announced to have been repaired. I haven´t tested yet. My patch was to force the previous version 0.5.x.x to use (forcing can be found in some of Synaptic:s menus).

Yours 

Jallu59
an elder ICTpro, but a linux newbie(9 months);)

---

