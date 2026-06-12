---
title: "Avidemux: &quot;Can't identify subtitle format&quot;"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by berliita on 2007-10-18
Whenever i try to get Avidemux to add SRT subtitles to a movie, the following error message pops: "Can't identify subtitle format". The file fi use contains no letter outside the ASCII character set, and i have no trouble rendering the subtitles using mencoder.  I use Avidemux 2.3.0 on a Feisty Fawn. Has anyone encountered a similar problem? Does anyone have an idea how to solve this problem?

---

### Post by Mud.Knee.Havoc on 2008-01-12
I remember having this problem a long time ago.  I believe I avoided it in some cases by downloading another .srt file (from divxstation or any number of other sites), and also by modifying the .srt file in a notepad.  I can't remember exactly what the problem was, but it was that the .srt wasn't exactly what avidemux was expecting.  I think the subs started off at 1 when it expects 0 or something like that (I had to make a dummy sub in order to get it to work).  Sorry I can't be of any help, but hopefully this will jog somebody else's mind or give you a place to start searching...

---

### Post by mpm on 2008-07-08
> **Mud.Knee.Havoc said:**
> I remember having this problem a long time ago.  I believe I avoided it in some cases by downloading another .srt file (from divxstation or any number of other sites), and also by modifying the .srt file in a notepad.  I can't remember exactly what the problem was, but it was that the .srt wasn't exactly what avidemux was expecting.  I think the subs started off at 1 when it expects 0 or something like that (I had to make a dummy sub in order to get it to work).  Sorry I can't be of any help, but hopefully this will jog somebody else's mind or give you a place to start searching...

In my case, I tried renaming and got no results.  When I erased the 0 subtitle (complete with the number, time stamps, and subtitles) and the new .srt file started with 1, it worked fine.
Thanks

---

