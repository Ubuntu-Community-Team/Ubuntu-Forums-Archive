---
title: "Kaffeine / xine skips on srt subtitles"
date: 2008-09-04
forum: Multimedia Software
---

### Post by mainstreetexile on 2008-09-04
When I try to watch a movie in Kaffeine that uses SRT subtitles, the video skips or hiccups whenever kaffeine puts up a new subtitle.

I've tried looking at the xine subtitle settings and I've tried clearing out my ~/.kde/share/apps/kaffeine settings but I haven't had any luck fixing this problem.

This happens with all movies w/ srts I've tried so it seems like it's not a bad video or bad srt problem. Also, VLC player renders the subtitles fine without any skips, but I prefer to use Kaffeine (I like it's sub rendering & I have it set up with my remote via lirc/irkick).

I haven't found any related threads via google or on these forums, anybody have any ideas?  Thanks for any help!

---

### Post by mainstreetexile on 2008-09-07
bump? nobody's seen this issue or has any ideas?

---

### Post by belecubration on 2009-04-14
I have the same problem, still no solution?

---

### Post by mainstreetexile on 2009-04-14
I never heard back from anybody but i was able to fix it myself a little while after I posted this.

In Kaffeine, under Settings -> xine Engine Paramaters -> video -> beginner options/videodriver  I had it set to one of the specific codecs. I'm not sure why/how I had specified one there, but when I changed it back to the default of 'auto' it worked fine.

If yours is already on auto, maybe try out a couple of the specific codecs to see if you get any better results.

---

### Post by Nat90 on 2009-05-02
Mine was already on auto and it still skips a couple of frames every now and then. But when I try to change it to one of the others, an error message comes on saying that can't be done.

Has anyone found another solution?

---

### Post by Nat90 on 2009-05-02
That's it, I'm going back to gnome

---

### Post by rohandhruva on 2009-06-19
I have the same problem :( I hope someone is able to find a solution to this.

I was talking to a kaffeine developer (hftom) - he got me to compile kaffeine without xcb support, disabling audio drivers etc, but we couldn't figure out the problem. This happens in Ubuntu 9.04, and Fedora 11, but not in Ubuntu 8.04 or Debian 5. I am assuming the new X infrastructure might be the cause of the problem.

I hope a solution is found soon, kaffeine is my favourite player!

---

