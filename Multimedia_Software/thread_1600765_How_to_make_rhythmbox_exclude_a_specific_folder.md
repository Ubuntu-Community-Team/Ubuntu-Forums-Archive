---
title: "How to make rhythmbox exclude a specific folder?"
date: 2010-10-19
forum: Multimedia Software
---

### Post by Sylchat on 2010-10-19
hi,

This question can be found on the internet and on this forum but either there is no response or the advice is to move the folder to exclude on another path (in case of using a subfolder for ripped/downloaded mp3). 

But in my case my music is on a SAN and I access it through CIFS. So every time I delete a file or folder it goes to the Trash, in a folder called #recycle, which Rhythmbox indexes as well. So I have to delete this folder to avoid duplicates...

Is there any configuration in Rhythmbox to exclude a folder?

I only see a configuration for multiple folders in gconf-editor:
/apps/rhythmbox/library_locations

Any idea welcomed!
Syl

---

### Post by Sylchat on 2010-10-19
Ok I think I have found my own workaround:
- When I hit SHIFT+DEL, the file/folder goes in #recycle/
- When I hit DEL or right click > Move to Trash (holding SHIFT or not), it goes in .Trash/

.Trash gets emptied by Emptying the Trash, but not #recycle...

So the w/a is to not SHIFT+DEL (I was thinking this is to bypass Trash / perma-delete)

Syl.

---

### Post by Sylchat on 2010-11-18
Also: when changing tags in Rhythmbox, it puts the old tagged file in #recycle as well.

Finally I did:
```
chmod a-w #recycle
```

Tags can still be renamed AFAIK

---

