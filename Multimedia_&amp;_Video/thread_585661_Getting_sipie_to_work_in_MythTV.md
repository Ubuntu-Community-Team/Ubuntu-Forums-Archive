---
title: "Getting sipie to work in MythTV"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Calash on 2007-10-21
Been trying to follow the following wiki to get sipie to stream Sirius radio to my MythTV box (Currently running 7.10)

[http://www.mythtv.org/wiki/index.php/Integrate_Sirius](http://www.mythtv.org/wiki/index.php/Integrate_Sirius)

sipie works fine once I found the instructions to apply the patch file.  The problem is with the two scripts that will be use by MythTV.

The sipie_myth one, if I am reading it right, creates a link link to the stream you want (ln -s), then executes the link and records the process information in a temp file.  The problem is that the command as it is listed does not work.  ps -p %1, where %1 is the process name returns an error.  I have played around and gotten a ps -C but this does not seem to record any information into the file.


At this point I am at the limit of my understanding of the scripting language.  Can anybody give me some guidance on how to get this script to work?

Thanks :)

---

