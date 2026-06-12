---
title: "How to make Xine as default dvd player?"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by vrod74 on 2006-12-30
Hello,

What command can I put in "Removable Drives and Media Preferences" to make Xine the default player for movies when I pop in a movie DVD? 

Right now it says: totem %m

What's the right command for Xine? Any help will be appriciated. Thanks.

vrod74

---

### Post by taurus on 2006-12-30
Try to replace that with **xine %m**!!!

---

### Post by vrod74 on 2006-12-30
That's what I did but it gives me the following error:

-Xine engine error-

There is no input plugin available to handle 
'<?xml version ="1.0"?>'.

Maybe MRL Syntax is wrong or file/stream source doesn't exist.

---

### Post by taurus on 2006-12-30
Remove the %m at the end then.  And login out and back in doesn't hurt, either!

---

### Post by vrod74 on 2006-12-30
Ok I found how to fix it...  I had to go through the xine --help command in order to figure this out. 

The command I used is 

xine -pd

"-p" for autoplay and option "d" is for retrieving a play list from the DVD. In this case the first .vob file. 

Now when i pop in a DVD it just auto plays.  


vrod74


.

---

### Post by PaulRay on 2008-03-22
Thanks so much! That was an easy fix.
Again, I am reminded why I'm a dyed-in-the-wool ubuntu user.
 The community :guitar:

---

### Post by davidgypsy on 2008-03-22
> **vrod74 said:**
> Ok I found how to fix it...  
The command I used is 
xine -pd 
Now when i pop in a DVD it just auto plays.  
vrod74
.

Wow! Thanks! Been wondering about this for a while.

---

### Post by mvaniersel on 2008-03-24
I'm trying out the new ubuntu 8.04 Beta
However, there is no DVD section in the removable drives & media dialog anymore.

Any idea how to change this preference in ubuntu 8.04?

---

### Post by acron1 on 2008-04-15
> **mvaniersel said:**
> I'm trying out the new ubuntu 8.04 Beta
However, there is no DVD section in the removable drives & media dialog anymore.

Any idea how to change this preference in ubuntu 8.04?

Same here any ideas?

---

### Post by ubuntu-freak on 2008-04-15
Removed and new post made.

---

### Post by einnar on 2008-04-26
We used to be able to run a script when a DVD was inserted under the old version of ubuntu. Any idea how to get it to do the same in 8.04?

Thanks

---

### Post by ubuntu-freak on 2008-04-26
> **einnar said:**
> We used to be able to run a script when a DVD was inserted under the old version of ubuntu. Any idea how to get it to do the same in 8.04?

Thanks

 
A lot of code has been rewritten in GNOME. If Totem Xine or Gxine don't show up in Places>Computer>Edit>Preferences>Media>DVD Video, then use the instructions in my  [how-to](http://ubuntuforums.org/showthread.php?t=766683), but modify them to your needs (totem-xine.desktop instead of vlc.desktop).
 
Hope that helps.
 
Nathan

---

