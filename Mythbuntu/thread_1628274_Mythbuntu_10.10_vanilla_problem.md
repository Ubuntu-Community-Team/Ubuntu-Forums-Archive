---
title: "Mythbuntu 10.10 vanilla problem"
date: 2010-11-22
forum: Mythbuntu
---

### Post by Keary on 2010-11-22
Noob here so please be kind.

I have down loaded the Mythbuntu 10.10 disk and created the cd.  Used it to create a simple setup - front and back end on same machine.  Leaving all things as default.

Can rip and play CDs.

Ripping DVDs seems to work i.e. I can find the files and run them using VLC but nothing appears in the MythTV Videos menu - says no files found.

Question: where do I start to trouble shoot?

Just point me in the right direction and I should be okay.  Thanks. 

Keary

---

### Post by superm1 on 2010-11-22
Welcome!

After ripping the DVD, try hitting the menu button in mythvideo and telling it to "scan for changes"

---

### Post by Keary on 2010-11-23
> **superm1 said:**
> Welcome!

After ripping the DVD, try hitting the menu button in mythvideo and telling it to "scan for changes"

Many thanks for this.  Just the fact that you mentioned a menu button (m) that I was not aware of helped me solve this.  Brilliant.

What I needed to know was this:


[LIST=1]
[*] On the backend to host the videos, stop the backend process and run mythtv-setup.
[*] In Storage Group configuration, set up directories for each of the following: **Videos, Trailers, Fanart, Banners, Screenshots, and Coverart**.
[*] *Optional Step:*  If you would like to use a combination  of Storage Group and locally hosted video, you can do the following.  On  the frontends, go to Utilities/Setup->Setup->Media  Settings->Video Settings->General.  Change "Directories that hold  videos" to point at a directory that is **not the same** as the one  the Storage Group points at.  If the local video setting and the Storage  Group setting point at the same path, MythVideo will prefer the Storage  Group path and ignore the local one.
[*] Enter MythVideo.  Press the "M" (MENU) key and choose "Scan For Changes."
[/LIST]
Just went into the storage group settings int he frontend and changed the directory to nothing and it now works.  Fantastic.

Where do I find the documentation dor MythTV o I can do this for myself?

Keary (and very happy now)

---

### Post by superm1 on 2010-11-23
> **Keary said:**
> Many thanks for this.  Just the fact that you mentioned a menu button (m) that I was not aware of helped me solve this.  Brilliant.

What I needed to know was this:


[LIST=1]
[*] On the backend to host the videos, stop the backend process and run mythtv-setup.
[*] In Storage Group configuration, set up directories for each of the following: **Videos, Trailers, Fanart, Banners, Screenshots, and Coverart**.
[*] *Optional Step:*  If you would like to use a combination  of Storage Group and locally hosted video, you can do the following.  On  the frontends, go to Utilities/Setup->Setup->Media  Settings->Video Settings->General.  Change "Directories that hold  videos" to point at a directory that is **not the same** as the one  the Storage Group points at.  If the local video setting and the Storage  Group setting point at the same path, MythVideo will prefer the Storage  Group path and ignore the local one.
[*] Enter MythVideo.  Press the "M" (MENU) key and choose "Scan For Changes."
[/LIST]
Just went into the storage group settings int he frontend and changed the directory to nothing and it now works.  Fantastic.

Where do I find the documentation dor MythTV o I can do this for myself?

Keary (and very happy now)
Great, glad you figured it out.

[http://www.mythtv.org/wiki](http://www.mythtv.org/wiki)
and
[http://mythbuntu.org/wiki](http://mythbuntu.org/wiki)

---

