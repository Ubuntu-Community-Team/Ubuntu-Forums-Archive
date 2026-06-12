---
title: "Help with .MTS/ACVHD software"
date: 2012-01-05
forum: Multimedia Software
---

### Post by watermelons on 2012-01-05
I've been struggling with this for a few days, so I figure I'll stop and ask in hopes of saving some headache.

This is the goal: Use an open source or freeware program to save space by trimming a .MTS video file, then converting it to a widely accessible format for further editing, such as .avi.

I can't seem to find a good program to do this. Windows Live Movie Maker works perfectly, however it will only save to .wmv, which would need to be converted again before being usable in most video editors.

I have not found any program in Windows that will allow for this, so I set up another partition for Ubuntu. 

So far I have tried kdenlive, but I can't get it working (and am uncertain if it will even do what I am asking). I get the "MLT's SDL module not found" error, and don't know what to do about it.

I have read that Cinelerra will not handle .MTS files.

I am currently trying LiVES, but it seems to only save as .OGV, and it is not handling the sound properly. This might be my mistake, but I would like to ask before spending too much more time bashing my head against my table.


Thank you very much for any help!

edit: Figured out how to get LiVES to save as other formats, but sound is still not working, and it's warning me to not load in large file sizes... So I guess my only option is to figure out how to get kdenlive working?

---

### Post by watermelons on 2012-01-05
Figured out how to get kdenlive working. I'll write it here in case anyone else finds this in a search. Seems to be a common problem.

For kdenlive, you must add their beta repository to your software sources, then reinstall. 

http:/ppa.launchpad.net/sunab/kdenlive-svn/ubuntu

Once you do this, you'll likely hit another error after starting up kdenlive. You have to update the MLT library manually:

sudo apt-get update libmlt3++


That's that, but I'm not sure how well it handles .MTS files yet. Seems awfully complex, I'll play around with it another night.

---

