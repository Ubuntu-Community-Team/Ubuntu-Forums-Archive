---
title: "m4a tag edit in amarok"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by janx_spirit on 2007-10-18
i just upgraded to 7.10 and for some reason i can no longer edit the tags for my m4a files in amarok.  please help this is driving me insane.

---

### Post by meindian523 on 2008-01-09
meaning you could do it earlier in Feisty?How could you do that?

---

### Post by narehart on 2008-01-09
Try installing libmp4v2-0 and libmp4v2-dev from the repositories and see if that will give you the M4A tag editing function back.  

If not you might have to uninstall Amarok and reinstall it from source with the  --with-mp4v2   option for M4A/AAC tag support.

---

### Post by craigyjack on 2008-01-10
Why doesn't Amarok come compiled with m4a/aac tagging in the repos? Given the rising popularity of the aac format, it seems many users would want that option. Isn't whoever compiles the program and packages it for the Ubuntu repos just creating more user problems and troubles by not including it. Why not just compile with it, even if some won't use it, some users will so it is of benefit. I just don't see the reasoning its not in there by default in the repos :)

Most of my collection is in m4a from my old iTunes days, and now I am stuck with them because I dont want to convert lossy to lossy :)  So I hope and want media programs to gain some better support for aac. Its not like its a brand new format :) mp3 is outdated anyway (even if it does have the best compatability) - and if I started all over I'm not sure I would want to go with ogg, i like the format and its great that its open source, but its support by other programs outside is limited - but that is the fault of other programs, not ogg. Man, codecs and media players can be annoying sometimes eh :)

---

### Post by narehart on 2008-01-10
Well, I completely agree with you.  I think the version of Amarok in the repositories should come with M4A/AAC support.  Especially considering, Amarok has the ability to play them and adding that funtionality would only require the downlaod of two additional packages and one additional command.

I personally compiled Amarok myself to add newer MTP capabilities to it but while I was doing that I also added M4A/AAC support because sometimes friends give me music in that format and I want the ability to change the tags in case they don't care about keeping their music organized as much as I do.

As for OGG.  Yeah, it would be a great format if I only played music on my PC and never had the need to transfer to a portable media player or burn CDs.

---

