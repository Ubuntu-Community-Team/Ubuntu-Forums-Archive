---
title: "Menu &quot;Delete Recordings&quot; goes to screen &quot;Watch Recordings&quot;"
date: 2009-12-02
forum: Mythbuntu
---

### Post by korgman on 2009-12-02
This used to work, but sometime recently, probably after an upgrade, when I select "Delete Recordings" from the Manage Recordings section, it takes me to the "Watch Recordings" screen.  Exiting takes me back to the Manage Recording menu where the cursor is still selected on delete recordings.

Frontend log entering manage recording and then selecting delete
```
2009-12-02 16:07:22.371 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//manage_recordings.xml
2009-12-02 16:07:32.068 Loading window theme from /usr/share/mythtv/themes/Mythbuntu-9.10/recordings-ui.xml

```

---

### Post by nickrout on 2009-12-02
I take it you are using 0.22? Thats how it works now, use one of the menu buttons (M or I) to bring up a menu allowing you to delete the recording.

---

### Post by uncle hammy on 2009-12-02
I don't think that's what he's referring to. 

MEDIA LIBRARY>WATCH RECORDINGS and MANAGE RECORDINGS>DELETE RECORDINGS takes you to the same "page"...Watch Recordings (even the title is the same).  

IOW Delete Recordings does not seem to exist anymore, which for some people is annoying, because the delete recordings page had the file sizes and the total usage graph on it.

---

### Post by nickrout on 2009-12-02
> **uncle hammy said:**
> I don't think that's what he's referring to. 

MEDIA LIBRARY>WATCH RECORDINGS and MANAGE RECORDINGS>DELETE RECORDINGS takes you to the same "page"...Watch Recordings (even the title is the same).  

IOW Delete Recordings does not seem to exist anymore, which for some people is annoying, because the delete recordings page had the file sizes and the total usage graph on it.

You are right, it doesn't exist any more, which is why it goes to the screen where you CAN delete files.

And yes it is sometimes annoting not to have the old screen. c'est la vie.

---

### Post by ian dobson on 2009-12-02
Hi,

I have found the same problem. In the end I linked the Red button on my remote to the "i" key. This brings up the old delete/transcode menu.

Regards
Ian Dobson

---

### Post by nickrout on 2009-12-03
> **ian dobson said:**
> Hi,

I have found the same problem. In the end I linked the Red button on my remote to the "i" key. This brings up the old delete/transcode menu.

Regards
Ian Dobson

'i' has always been a useful button, but in 0.22 it is more so!

---

### Post by t3chn0b0y on 2009-12-03
> **uncle hammy said:**
> I don't think that's what he's referring to. 

MEDIA LIBRARY>WATCH RECORDINGS and MANAGE RECORDINGS>DELETE RECORDINGS takes you to the same "page"...Watch Recordings (even the title is the same).  

IOW Delete Recordings does not seem to exist anymore, which for some people is annoying, because the delete recordings page had the file sizes and the total usage graph on it.


I agree with you completely, it is annoying.. I like to know
what the file size are etc.. whats the use in digging farther into
the menu to get to the same place as watch recordings.. it makes
no sense the way it is layed out now.. and if its going to stay
the way it is.. the delete recordings should be removed from the
menu all together.

---

### Post by nickrout on 2009-12-03
> **t3chn0b0y said:**
> I agree with you completely, it is annoying.. I like to know
what the file size are etc.. whats the use in digging farther into
the menu to get to the same place as watch recordings.. it makes
no sense the way it is layed out now.. and if its going to stay
the way it is.. the delete recordings should be removed from the
menu all together.

we look forward to your contributed themes :)

---

### Post by uncle hammy on 2009-12-03
> **nickrout said:**
> we look forward to your contributed themes :)
You really are a broken record with that attitude, aren't you?  Tell me, exactly what you think you're accomplishing with that?  All you're doing in promoting the notion that Linux Fan Boys are unapproachable, arrogant, elitist a-holes, who always fall back to the "What do you want, it's free" or "Feel free to fix it yourself if you don't like it" playbooks.

Do you REALLY think that people who don't have the technical knowledge to code don't have anything to contribute to the project?

Remember this thread? [http://ubuntuforums.org/showthread.php?t=1337733](http://ubuntuforums.org/showthread.php?t=1337733) 

Guess what, I haven't submitted to "mailing list" or "trak".  Know why?  BECAUSE I DON'T KNOW WHAT EITHER OF THEM ARE, AND YOU COULD BE BOTHERED TO EVEN POST A LINK.  I searched around to try and figure it out, check the "Sticky" posts for FAQs and Where to get help.  Couldn't find a mention or either, got fed up and left it.  Thanks to your "help", I still don't know what either of them are.

---

### Post by nickrout on 2009-12-03
> **uncle hammy said:**
> You really are a broken record with that attitude, aren't you?  Tell me, exactly what you think you're accomplishing with that?  All you're doing in promoting the notion that Linux Fan Boys are unapproachable, arrogant, elitist a-holes, who always fall back to the "What do you want, it's free" or "Feel free to fix it yourself if you don't like it" playbooks.

Do you REALLY think that people who don't have the technical knowledge to code don't have anything to contribute to the project?

Remember this thread? [http://ubuntuforums.org/showthread.php?t=1337733](http://ubuntuforums.org/showthread.php?t=1337733) 

Guess what, I haven't submitted to "mailing list" or "trak".  Know why?  BECAUSE I DON'T KNOW WHAT EITHER OF THEM ARE, AND YOU COULD BE BOTHERED TO EVEN POST A LINK.  I searched around to try and figure it out, check the "Sticky" posts for FAQs and Where to get help.  Couldn't find a mention or either, got fed up and left it.  Thanks to your "help", I still don't know what either of them are.

I won't respond to your more hysterical ranting, but I will clarify the 'mailing list' and 'trac' (which I misspelled in the thread you point to.)

The main supports for mythtv are the mailing lists which you can access from the mythtv.org web site, specifically here:

[http://www.mythtv.org/support/](http://www.mythtv.org/support/)

They really are a great resource and have an excellent searchable archive here:

[http://www.gossamer-threads.com/lists/mythtv](http://www.gossamer-threads.com/lists/mythtv)

trac is the web front end to the development effort. You can get access to the code and also post "tickets" describing a bug.

[http://svn.mythtv.org/trac/](http://svn.mythtv.org/trac/)

I actually thought that someone who posts here as often as you would have known at least about the main mythtv support route, the mailing lists. Sorry for that assumption. 

The post in the other thread was accurate, but I'll be clearer. Feature requests go to the mailing lists, unless you actually have code (in the form of a patch file) to submit to implement the request, in which case you can post it on the trac/svn system. 

Bug reports go to trac, prefereably with a patch to fix it, but not necessarily. As for the difference between a 'bug' and a 'feature request' - well thats sometimes in the eye of the beholder :)

Last point, most of the developers do not read this forum, but they are often active on the mailing list.

---

### Post by t3chn0b0y on 2009-12-03
> **nickrout said:**
> we look forward to your contributed themes :)

I will be more than willing to create a patch to remove the
deletion of recordings from the menu which takes one too
the watch recordings menu..

But as for contributing themes.. the two themes I have created
haven't completely been brought over to the new gui as of yet,
and they are Holiday based, by the time I get them done no one
would be interested in them until next Christmas. I haven't
distributed those themes, on the basis that I figured the majority
of people probably wouldn't be interested in them and considering
they are not wide screen, and I haven't as of yet had the hard cash
to run out and buy a wide screen display, I figure the 4:3 themes
would be of little interest to the majority either.

And I am use to being told to get in there and fix the bugs and the problems, on a regular basis.. But I at least expect a version that is stable to run as my back-end/front end.. When it comes to  complaining about instability, I am flat out told to become more unstable.
so if and when that spare computer drops in my lap with a wide screen display..  I am not willing to fully deal with a media center
that might not run for days, sacrificing every recording I have scheduled.
I am not one of those developers that have businesses like IBM landing million of $$$ into my lap... as some developers do.. Or people willing to send me the hardware to do so.... which they also receive. granted not all do..

---

