---
title: "XMLTv guide inserts colons"
date: 2009-09-24
forum: Mythbuntu
---

### Post by theirishfozz on 2009-09-24
Hi guys, I'm SURE I saw something about this somewhere but I can't find it now.. 

Basically my problem is that XMLTv downloads my latest guide in the form "<show name>:<episode title>". As a result all episodes of the same show are listed separately and record-all functions will record all instances of that one episode..grrr. 

I have a manual script populating the guide in the DB so I'm tempted to go into the XML file pre-commit and remove any parts of titles after a colon however this would remove the episode title which doesn't seem to be stored in the description. A solution to this is to place the title at the start of the description.

In summary I'd just run a pattern match across the entire XML file (tempted to use java or python for this as my shell isn't as good plus they have xml parsers),
-if <title lang="en">*</title> contains a :
-remove and save the section after the colon
-find the next instance of <desc lang="en"> (should be next line)
-add saved episode title to the start of the text followed by a colon.

My question is if people have done this already or perhaps if there is a way to handle this built into xmltv/mythtv.

thanks
Fozz

---

