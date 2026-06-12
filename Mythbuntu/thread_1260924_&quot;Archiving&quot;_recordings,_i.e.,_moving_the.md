---
title: "&quot;Archiving&quot; recordings, i.e., moving them to video directory"
date: 2009-09-08
forum: Mythbuntu
---

### Post by dsbw on 2009-09-08
I've been searching for answers to this one but I think I'm hampered by "archiving" having a specific meaning to a lot of Myth folks (putting on DVD?).

I've recorded some things that I now want to save permanently. I know that I can keep them from auto-expiring in the recordings area, but I'd rather move them to my video directory.

Obviously I can copy them by hand. It'd be cool to have a menu option for a recording that allowed you to move it to the video directory, however, with an appropriate name change. (Also to do that with a whole set of titles, e.g., for a TV show.)

It's so cool, I find it hard to believe it hasn't been done! 

So, has it? Or do I write this one myself?

---

### Post by tgm4883 on 2009-09-08
> **dsbw said:**
> I've been searching for answers to this one but I think I'm hampered by "archiving" having a specific meaning to a lot of Myth folks (putting on DVD?).

I've recorded some things that I now want to save permanently. I know that I can keep them from auto-expiring in the recordings area, but I'd rather move them to my video directory.

Obviously I can copy them by hand. It'd be cool to have a menu option for a recording that allowed you to move it to the video directory, however, with an appropriate name change. (Also to do that with a whole set of titles, e.g., for a TV show.)

It's so cool, I find it hard to believe it hasn't been done! 

So, has it? Or do I write this one myself?

There have been talks about doing something like that, but AFAIK, nobody has written it yet.

---

### Post by dsbw on 2009-09-12
OK, cool. Sounds like a fun (little?) project.

---

### Post by tgm4883 on 2009-09-12
You could probably do it via a user job. Perhaps poke rhpot1991 to see if something with mythexport can be done with that

---

### Post by ahood on 2009-09-14
Another tool that could be used is [**[COLOR="Blue"]nuvexport[/COLOR]**]("http://www.mythtv.org/wiki/Nuvexport").

---

### Post by SiHa on 2009-09-14
Also, something I stumbled across last night, have a look at mythvidexport.py [[COLOR="Blue"]_here_[/COLOR]](http://www.mythtv.org/wiki/Unofficial_Plugins)

Certainly, you can tell Nuvexport to put the transcoded files somewhere else. I have a couple of user jobs, and one of them puts the videos into my 'Videos' directory. It doesn't remove the original, although I have a feeling there is an option to do that.

---

### Post by tgm4883 on 2009-09-14
This may be a moot point in 0.23, as I believe the goal is to have recorded content and videos in the same container and then searching by metadata.

---

### Post by bcg30506 on 2009-09-15
Why not just use MythArchive and choose to export a Native archive?  Then select File as the output option and pick the directory for your myth videos?  It will copy the mpg video and png thumbnail files and create an xml file for importing it back into the recordings table if you ever changed your mind.

---

### Post by dsbw on 2009-09-16
.23? I thought we were waiting for .22!

That does sound logical, though.

---

### Post by dsbw on 2009-09-16
> **bcg30506 said:**
> Why not just use MythArchive and choose to export a Native archive?  Then select File as the output option and pick the directory for your myth videos?  It will copy the mpg video and png thumbnail files and create an xml file for importing it back into the recordings table if you ever changed your mind.

I'll give it a try.

---

### Post by tgm4883 on 2009-09-16
> **dsbw said:**
> .23? I thought we were waiting for .22!

That does sound logical, though.

0.22 will be in 9.10, waiting is almost over.

---

