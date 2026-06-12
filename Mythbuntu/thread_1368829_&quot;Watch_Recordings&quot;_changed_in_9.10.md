---
title: "&quot;Watch Recordings&quot; changed in 9.10?"
date: 2009-12-31
forum: Mythbuntu
---

### Post by storyid on 2009-12-31
Hello,
I must be losing my mind here - just upgraded to 9.10 and not only is the project grayhem theme gone (any idea if that works with 9.10 / myth .22?  I figure it was removed for a reason)...but also the functionality seems different/worse (maybe this was just a function of project grayhem as a theme)...

In the old days (ie, this morning ;) when I was on 9.04, if I would go to watch a recording and press right arrow, it would popup a menu asking if I wanted to watch from the beginning, from a bookmark, delete the show, etc...now, no matter what I do, it always starts playing the show, no menu, nothing... :(  Needless to say, that is a pain for me as now I'd have to setup a key on my remote to be "d" to "delete" shows, and there's no apparent way to watch from the beginning, etc.  Further, it seems like when I'm watching a show, what used to skip ahead and back now do fast forward and rewind.

Thinking it was just a problem with my lirc configuration, I copied over the old one (from dd of the entire drive that I make to a duplicate drive before I upgrade for just this sort of thing) but that seemed to be no help.  No matter what theme or menu I use, it seems like the old functionality is just gone.  

So, if anyone out there has an idea as to how to bring this back (theme, some setting that I'm missing, some keymapping or something, etc.), please reply...am going crazy and seriously considering going back to 9.04 just to have my old way of doing things and old menus, theme, etc. back... :(

---

### Post by SiHa on 2009-12-31
9.10 incorporates MythTV 0.22. This comes with a completely new UI engine, which supports horizontal scrolling lists. The effect of this is that the old right-key actions don't work any more. I agree that this seems a backwards step, and am surprised that it couldn't accommodate both, but hey, I'm not a dev.

The new UI means all the themes need to be re-done. I don't believe Project Grayhem has been yet. 10.04 will, incorporate 0.23 which should have more themes. It's due out in March / April.

The right-arrow menu can now be found on 'I'. It has both the 'Delete' option, and 'Watch From...'

FF/RW: In the Frontend setup, TV Settings -> Playback (Seeking 7/9) there's an option called 'Sticky Keys'. With this ensabled, it will FF/RW. Without, it will skip back / forwards.

---

### Post by storyid on 2009-12-31
Thanks SiHa, a couple of thoughts/comments below:

> **SiHa said:**
> 9.10 incorporates MythTV 0.22. This comes with a completely new UI engine, which supports horizontal scrolling lists. The effect of this is that the old right-key actions don't work any more. I agree that this seems a backwards step, and am surprised that it couldn't accommodate both, but hey, I'm not a dev.  The right-arrow menu can now be found on 'I'. It has both the 'Delete' option, and 'Watch From...'

Yep, am sad to see that gone, as now even that I know it's the "I" key (I had stupidly turned on numlock on my media keyboard which made the "I" be a "5" when I was pressing all the keys), I have to remap another key to it on my remote...would sure be nice if you had the choice of making "Enter" EITHER just play it or bring up the menu with more options (the "I" menu).  Thanks for the tip though on that.

> **SiHa said:**
> The new UI means all the themes need to be re-done. I don't believe Project Grayhem has been yet. 10.04 will, incorporate 0.23 which should have more themes. It's due out in March / April.

I wish I'd known that (my fault, I'm sure it is somewhere out in the wiki), or had known that a bunch of the themes were gone, might have waited or thought harder about upgrading...that said, the new theme is growing on me I guess...really don't love the widescreen (as the fonts are HUGE, some of the options "wrap" (ie you're choosing different settings for a recording like for matching duplicates, and the selection wraps to the next category of choices), etc)...like you said, hopefully 0.23 will have more variety, not less...hopefully it makes the cut for Mythbuntu 10.4, pending the timing... :)  I have a feeling some of the old themes won't make the cut, I wonder if they're even being actively worked on...looks like Grayhem is pretty dormant, most of the links on the web to it are dead, etc...

> **SiHa said:**
> 
FF/RW: In the Frontend setup, TV Settings -> Playback (Seeking 7/9) there's an option called 'Sticky Keys'. With this enabled, it will FF/RW. Without, it will skip back / forwards.

That fixed it, and sure enough my old one wasn't checked, so now at least that feature is back.  

Thanks again!

---

