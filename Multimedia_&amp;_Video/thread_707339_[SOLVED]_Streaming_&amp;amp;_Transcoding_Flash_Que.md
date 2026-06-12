---
title: "[SOLVED] Streaming &amp;amp; Transcoding Flash Question"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by -Phoenix- on 2008-02-25
Here is my question:

I have a server (PIII 933, 512MB RAM) running standard ubuntu (7.10) as a file/print server on my network. I also have a wii, which accepts only flash video, to my understanding.  I would like to find a program to run on my server to 1)convert my video from other formats (mpeg, avi, etc) to flash on the fly and 2) host them on a web interface so that I can just go to [http://my-servers-ip-or-something](http://my-servers-ip-or-something)  and find the videos hosted, then play them on my wii with good quality.

I do know I will need a full flash server, as the wii's memory is very limited so progressive streams will not work.  

I have searched the forum, and the internet, for a good solution, but I have had no luck finding a viable solution that 1) works on ubuntu, 2) does the conversion on-the-fly, 3) has good quality and 4) hosts the files in a web interface (apache, lamp, etc).

Suggestions?

---

### Post by cozmicharlie on 2008-02-25
Do you mean something like this [http://www.yoozon.com/cms/index.php?option=com_content&task=view&id=5&Itemid=6](http://www.yoozon.com/cms/index.php?option=com_content&task=view&id=5&Itemid=6)

Not sure about the transcoding part but it seems you could set up a script to run in Apache.  I take it you are just using it as a home server and do not plan on making it public.  Someone may have an easier way but you could set up an intranet using Lamp with Joomla.  Joomla is free and open source and works very well on Linux based systems.  It has extensions for video etc [http://extensions.joomla.org/index.php?option=com_mtree&task=listcats&cat_id=1808&Itemid=35](http://extensions.joomla.org/index.php?option=com_mtree&task=listcats&cat_id=1808&Itemid=35)

This is at least one option.

---

### Post by -Phoenix- on 2008-02-25
Well, joomla certainly has a nice interface.  It will take care of 1,3, and 4.  Does anyone have any idea of a script/program that would convert the videos on demand with good quality?  It's not a huge deal, but I'd rather not have to have duplicate copies of my movies (i.e. one in original format, one in flash format), and re-encoding those movies could take a while (300+ GB).  

Thanks, though. That's at least a [very big] step in the right direction.

And yes, this will be used for my home server, nothing public/corporate.

---

### Post by fade_out on 2008-02-25
I had something like this running with mythtv before.
It was using mythweb plugin, mythflash and ffmpeg. Mythweb gave a web interface through apache of any recordings I had made, and using a set of scripts called mythflash I could click a button beside recordings that would encode them to flash format, once encoded I could click the link to stream them. 
I've since gotten rid of that pc setup though but using some combo and hacks of this should give you 1-4.
The page I found that outlined what I had to do is [http://chiefhacker.com/2007/01/22/streaming-mythtv-from-mythweb-using-flash/](http://chiefhacker.com/2007/01/22/streaming-mythtv-from-mythweb-using-flash/)

Check out ffserver too.

---

### Post by cozmicharlie on 2008-02-25
> **-Phoenix- said:**
>  Does anyone have any idea of a script/program that would convert the videos on demand with good quality?    

Thanks, though. That's at least a [very big] step in the right direction.

And yes, this will be used for my home server, nothing public/corporate.

There are a number of programs for transcoding videos.  Many are command line and should work for what you want to do.  I like PACPL ([http://ubuntuforums.org/newreply.php?do=newreply&p=4405046](http://ubuntuforums.org/newreply.php?do=newreply&p=4405046)).  It codes a number of formats and the developer is very active.  This is from the web site:

It can also convert audio from the following video formats: RM, RV, ASF, DivX, MPG, MKV, MPEG, AVI, MOV, OGM, QT, VCD, SVCD, M4V, NSV, NUV, PSP, SMK, VOB, FLV, and WMV.

---

### Post by -Phoenix- on 2008-02-26
Thanks to everyone for the help.  I think I have enough info to try this out (when I get time).  When [and if] I get everything working, I'll try to post a guide.

Thanks again.

---

