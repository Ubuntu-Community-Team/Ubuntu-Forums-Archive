---
title: "Firefox crashing with Flash/You Tube"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by steveneddy on 2007-06-05
I posted this [here]("http://ubuntuforums.org/showthread.php?p=2787287#post2787287"), but will post it here so it is on top for people searching for this issue and to get it resolved.

This isn't a total fix for everyone, but the three steps outlined here did the trick for me when Firefox would crash while watching Flash videos on You Tube.

[HTML]I first made sure that I using the flashplugin-nonfree that is available in Synaptic and then followed advice from here that addressed the sound issue in Firefox causing the crash and not actually Flash.

It tell you how to install alsa-oss and how to get Firefox to use it correctly.

I had sound already but did it anyway. This along with another hint did it for me.

The third hint is from this post that deals with adding a line to the /usr/bin/firefox file.

Here is a copy of that post:

HTML Code:

1. Open the firefox file...

    Ubuntu users: sudo gedit /usr/bin/firefox

    Kubuntu users: sudo kate /usr/bin/firefox

2. Add the following line as last but one line of the file:

    export XLIB_SKIP_ARGB_VISUALS=1

3. Restart Mozilla Firefox

Adding the line in the firefox bin file and changing the Firefox default sound app to alsa-oss helped me.

I was crashing ALL THE TIME - usually after 3-4 videos. I just did that and went to YouTube and watched almost 30 minutes of video with no crash. I started them in the middle, closed the tab while playing and started a new video in the moddle of one that was already playing. I opened three tabs and played video in all three tabs with no crash.

I did also open firefox in terminal to see what the error code was when it crashed, but like I said, no crashes.

1. Use the correct driver
2. Download alsa-oss and tell Firefox to use it.
3.Add the line in /usr/bin/firefox
[/HTML]

If this helps you, please tell others.

-SE

EDIT:

After much testing I have found another quick fix if you are using Flash9, and that is to right click and let YouTube or Google, or whatever flash video site you are having problems, store 'unlimited" cache. I will continue testing. I assume there is a problem dealing with the memory, maybe.

I started Firefox in terminal but when it crashed i can't get even the terminal to give me output because it is unresponsive also.

EDIT:

This is so frustrating - it will work well for an hour, then I close out to look at google or something, go back and it crashes on the first video.

More research needed.

---

### Post by NiGHTS7041 on 2007-06-06
I followed your guide and I got the same results, youtube worked but once exited it would not work agian. I agree with you though, this situation is completely frustrating. I have made posts about this before and so far you are the only one who has actually responded. 

I do believe it is a sound issue though, rather than a flash issue. Right now my sound isn't working so youtube isn't either.

EDIT

---

### Post by roscoetuff on 2007-06-13
I'm having a similar problem: Youtube freezes. Great. Now I was able to see Will Farrell's "The Landlord" just fabulously on funnyordie, but for some reason Youtube is an issue. 

Same hardware using Mepis 6.5 worked Youtube just fine. But Mepis was running an older version of Firefox.
I've seen the suggestion to remove Flashplayer from FIrefox and re-install it. I haven't seen where to do this.... it doesn't show under package manager... so I'm a little puzzled, too.

Maybe someone in Ubuntu land will respond?

---

### Post by arjanito on 2008-03-31
Hi there.completely remove Gnash and Flash Player.Then install Flash Player again .Works fine for me.

---

### Post by sav74sac on 2008-04-25
This didn't fix it for me.

Firefox still crashes on Youtube (or flash videos) about a 20% of the time.

---

### Post by steveneddy on 2008-05-04
> **sav74sac said:**
> This didn't fix it for me.

Firefox still crashes on Youtube (or flash videos) about a 20% of the time.

This thread is almost a year old and I think that Flash is working better in Hardy and if you are using Gutsy, try the Flash in the repos.

---

