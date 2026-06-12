---
title: "Select title in Blu-Ray in Mplayer?"
date: 2012-08-23
forum: Multimedia Software
---

### Post by Warmijwilf on 2012-08-23
Okay, so I've got a Blu-Ray disc. I've set up mplayer and the mount points and everything so when I type

mplayer -fs br:////mnt/blu/

it'll play the Blu-Ray back in Mplayer in fullscreen just fine, no stuttering or anything, selectable subtitles, etc. The only problem is it'll only play the first title on the Blu-Ray. This is a major problem. I can't seem to figure out how to switch titles whilst in the video (< and > do nothing).

on the Mplayer manual page on a website it says to try:

mplayer br://1 or br://2 or whatever to select the title number. Problem is, this doesn't work at all, it can't seem to figure out what br:// is referring to, and I need to manually enter the entire directory for the Blu-Ray disc (br:////mnt/blu/). However adding 1/2/whatever number to the end of that doesn't load the title any different. Nor does adding some -title switch.

I cannot for the life of me figure this out. I'd try SMPlayer, but that doesn't have an option to load the Blu-Ray disc anywhere at all.

Someone help?

---

