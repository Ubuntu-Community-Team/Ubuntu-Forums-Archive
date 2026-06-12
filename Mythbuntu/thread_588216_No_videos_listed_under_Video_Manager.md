---
title: "No videos listed under Video Manager"
date: 2007-10-23
forum: Mythbuntu
---

### Post by mungewell on 2007-10-23
Hi,
Tried out Mythbuntu 7.10 (release) last night on a test machine and it appears to mostly work. I like the new theme... good job!

However I noticed that of the few video files placed into '/var/lib/mythtv/videos' none are listed in the Video Manager, so I am unable to enter information about them into the database.

At first they would not play either, but installing the codecs appears to have fixed that. Even then they are not listed.....


One thing to note is that this test machine does not have a capture card, and is used for pre-recorded material only. So that might be an issue.

Cheers,
Simon.

---

### Post by tgm4883 on 2007-10-23
In order for the videos to show up you first have to go to

Utilities/Setup > Video Manager

That will scan the dir for new videos

Then just go back into the watch videos screen and they should be there

---

### Post by mungewell on 2007-10-23
> **tgm4883 said:**
> In order for the videos to show up you first have to go to

Utilities/Setup > Video Manager

That will scan the dir for new videos

Then just go back into the watch videos screen and they should be there

Just to be clear this is what I did, and got the report that no videos were found.

From (failing)  memory isn't the 'Video Manager' supposed to be where I can edit the details of the video files to tag them with Name, Director, Plot, Poster image, etc....?

Sort of like:
[http://www.mythtv.org/wiki/index.php/Image:VideoManagerIMDB.jpg](http://www.mythtv.org/wiki/index.php/Image:VideoManagerIMDB.jpg)

Simon.

---

### Post by napsilan on 2007-10-23
That's correct. I would look through the setup options for a couple tickboxes that say "browse files in video manager" and "browse files in video gallery".  Try activating those two and see if it helps.

---

### Post by mungewell on 2007-10-24
Those are both selected (depressed), as are all the options on the that config page, but still no listings under video manager.

I'll try a default install (had done custom) and see if that magically makes it work.

Simon.

---

### Post by superm1 on 2007-10-24
> **mungewell said:**
> Those are both selected (depressed), as are all the options on the that config page, but still no listings under video manager.

I'll try a default install (had done custom) and see if that magically makes it work.

Simon.

Did you move around your directories?  As in you aren't using standard locations for your videos and recordings and such?

---

### Post by mungewell on 2007-10-24
> **superm1 said:**
> Did you move around your directories?  As in you aren't using standard locations for your videos and recordings and such?

Nope, I'm using standard directories. The few video files (.avi) are present in the 'watch video' menu and can be played/watched.

They just don't appear under the 'video manager' menu.
Simon.

---

