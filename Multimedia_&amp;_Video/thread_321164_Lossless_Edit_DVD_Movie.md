---
title: "Lossless Edit DVD Movie"
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by SteveF on 2006-12-18
This is not really an Ubuntu question but more of a generic DVD authoring question.  I'm hoping to get some info/pointers on where to look for the information.  My forum and google searches are not returning what I'm looking for.

I'm going to be converting some home video to DVD.  From what I read, it appears my best option would be to buy a standalone DVD burner and copy the VHS tapes to DVD.  This would quickly and easily get the movies to DVD format.

Long term though, I would like to modify the movies by trimming content (not looking to enhance or make fancy video, just remove unwanted content - dead space or staying too long on one subject, etc). I may also want to add menus and if possible set my own chapters.

From what I read, I should be able to do this without loss of quality and without needing to convert to/from mpeg since I'm not really editing the content (other than deleting scens).  Please let me know if that is incorrect.

Is there software for Linux/Ubuntu that can do this?  I'm looking for software (and it can be multiple apps) that will read from DVD, make mpg file, modify files as specified and then resave the new/modified file(s) out to DVD.  I saw something about DVDStyler, but I could not tell if I could delete scenes and if re-encoding is needed.

Thanks for any information that can be provided.

Steve

---

### Post by budgie9 on 2006-12-18
Hi Steve,
A nice set of questions of which I am also interested in knowing the answers to. However, I don't really think we are going to get the answers here. 
I used to use Adobe Premiere, which if I recall correctly did all you asked, and all that I wanted. But it will not run under Wine, I have tried it. ( Unless someone knows better.) 

I am currently looking at two programs Kino is one which will permit one to edit the content as well as another called MainActor, which at this time seems better, though I still have not had time to go through all the options available. You will have to pay for a copy, though  there is a free trial version on their website.
There are some other programs mentioned in this forum. None I have looked at but I am sure some kind person will add them here for us.
I have dumped a fair amount of VHS video to DVD disk using some of the Windows programs but so far, not used  the programs in Linux. I suspect KB3 is the program for this, unless someone knows of something better still. 
Here is an interesting site to look at. I found it when I was using Suse for a short spell. It has some interesting stuff related to this subject.
[http://www.acaciaclose.co.uk/4436/index.html](http://www.acaciaclose.co.uk/4436/index.html)
I will watch this post with much interest.
 David

---

### Post by pg99 on 2006-12-18
I think there's really no better place to go than the doom9 forums.  You'll get far more info than you ever need there ;)   Try this linux faq for a big starter - not sure there's much about actual editing, it tends to be more about transcoding (coverting), but there are definitley some useful tools like vobcopy, mplayer/mencoder, dvdauthor mentioned there (BTW DVDStyler is a frontend to dvdauthor, so it will just create a DVD file structure and maybe menus from compatible mpegs, it wont do editing)
[http://forum.doom9.org/showthread.php?s=&threadid=91894](http://forum.doom9.org/showthread.php?s=&threadid=91894)

another useful linux specific place is the tovid forums - they are more concentrated on making dvds from avi (mpeg-4 to mpeg-2 conversions) but they have 'todisc' which creates some very nice dvd menus from compatible mpegs.
[http://www.createphpbb.com/phpbb/?mforum=tovid](http://www.createphpbb.com/phpbb/?mforum=tovid)
[http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)

hth for starters

---

### Post by SteveF on 2006-12-18
> **budgie9 said:**
> Hi Steve,
A nice set of questions of which I am also interested in knowing the answers to. However, I don't really think we are going to get the answers here. 
I used to use Adobe Premiere, which if I recall correctly did all you asked, and all that I wanted. But it will not run under Wine, I have tried it. ( Unless someone knows better.) 

I am currently looking at two programs Kino is one which will permit one to edit the content as well as another called MainActor, which at this time seems better, though I still have not had time to go through all the options available. You will have to pay for a copy, though  there is a free trial version on their website.
There are some other programs mentioned in this forum. None I have looked at but I am sure some kind person will add them here for us.
I have dumped a fair amount of VHS video to DVD disk using some of the Windows programs but so far, not used  the programs in Linux. I suspect KB3 is the program for this, unless someone knows of something better still. 
Here is an interesting site to look at. I found it when I was using Suse for a short spell. It has some interesting stuff related to this subject.
[http://www.acaciaclose.co.uk/4436/index.html](http://www.acaciaclose.co.uk/4436/index.html)
I will watch this post with much interest.
 David

David,

Thanks for the link, I'll take a look at it.  Though I'll use wine when needed (I use Picture Window Pro and Qimage for my photographs), I prefer to find native apps first.  A Windows app which I may test under Wine if I can't find a solution is TMPGEnc MPEG Editor.  It is located here:
[http://tmpgenc.pegasys-inc.com/en/product/tme20.html](http://tmpgenc.pegasys-inc.com/en/product/tme20.html)

Seems to do what I'm looking for (along with their companion DVD Author).  But not free and Windows.

Steve

---

### Post by SteveF on 2006-12-18
> **pg99 said:**
> I think there's really no better place to go than the doom9 forums.  You'll get far more info than you ever need there ;)   Try this linux faq for a big starter - not sure there's much about actual editing, it tends to be more about transcoding (coverting), but there are definitley some useful tools like vobcopy, mplayer/mencoder, dvdauthor mentioned there (BTW DVDStyler is a frontend to dvdauthor, so it will just create a DVD file structure and maybe menus from compatible mpegs, it wont do editing)
[http://forum.doom9.org/showthread.php?s=&threadid=91894](http://forum.doom9.org/showthread.php?s=&threadid=91894)

another useful linux specific place is the tovid forums - they are more concentrated on making dvds from avi (mpeg-4 to mpeg-2 conversions) but they have 'todisc' which creates some very nice dvd menus from compatible mpegs.
[http://www.createphpbb.com/phpbb/?mforum=tovid](http://www.createphpbb.com/phpbb/?mforum=tovid)
[http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)

hth for starters

Thanks.  Some reading for me to get started with.  I'll take a look.  My overall goal is to limit encoding/decoding to cutdown on quality loss, but I'll see what they say.

Steve

---

### Post by pg99 on 2006-12-19
agreed, you shouldn't need to do any encoding/decoding at all. sounds like you just want to do some cutting.  maybe give avidemux a go [http://www.avidemux.org/wki/index.php?title=Cutting](http://www.avidemux.org/wki/index.php?title=Cutting)

---

### Post by SteveF on 2006-12-19
> **pg99 said:**
> agreed, you shouldn't need to do any encoding/decoding at all. sounds like you just want to do some cutting.  maybe give avidemux a go [http://www.avidemux.org/wki/index.php?title=Cutting](http://www.avidemux.org/wki/index.php?title=Cutting)

That looks like what I might want.  Thanks.

---

