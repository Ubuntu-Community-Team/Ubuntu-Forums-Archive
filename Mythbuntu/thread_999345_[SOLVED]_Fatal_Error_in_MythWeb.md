---
title: "[SOLVED] Fatal Error in MythWeb"
date: 2008-12-01
forum: Mythbuntu
---

### Post by Weidbrewer on 2008-12-01
I had been using MythWeb with no problems for a while, and then I dove back in for some updates the other night.  I noticed that a lot of things had changed in there, but now I'm getting an error I never got before.  Some of the listings that I click on the left side of the screen give me this error:

```
Fatal error: Call to a member function fetch_col() on a non-object in /usr/share/mythtv/mythweb/modules/video/handler.php on line 251
```

The strange thing is that it's only happening on one string of folders.  Now, this folder happens to have parenthesis in the title - is this what the error is referring to, and what is causing the subordinate folders to have issues as well?   Any one got any ideas?

---

### Post by Weidbrewer on 2008-12-08
I guess I stumped everyone.  :p

I ended up sussing it out, and I figured since there were some page views, some others might be curious.

I was right - it was because I had () in part of the file title.  Taking them out was simple, but then there was the matter of the MythTV database.  Since files in MythTV run on absolute path, changing this would wipe out all the metadata for all the files in this folder and sub folders (about 200.)  

To solve this, you just need to back your DB up, then go in and do a find/replace all on it.  Find all instances of the original folder name and change to the new one.  That's it.  Quick, simple and everything is still maintained in Myth.

---

