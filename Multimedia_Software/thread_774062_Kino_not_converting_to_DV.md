---
title: "Kino not converting to DV"
date: 2008-04-29
forum: Multimedia Software
---

### Post by free10 on 2008-04-29
OK, have 7.10, and on another drive and system Kino worked fine for importing flv and other files and then exporting them to DV, but new system no go. Kino always says failed to import and convert such files to DVs. Now I just ran it off of terminal and notice this when it failed
">> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
/usr/share/kino/scripts/import/media.sh: 74: ffmpeg: not found
>> Leaving Editor
>> Left Editor"

Am I reading that right that it is missing or needs ffmpeg? Just a wild hunch on why it is failing, and if true how to I get it for it?--Dwight

---

### Post by squaregoldfish on 2008-04-29
Your hunch is correct - for some reason ffmpeg isn't installed as a dependency of Kino.

You can install it using Synaptic - just search for the ffmpeg package (it's called ffmpeg), install it and all should be well.

Steve.

---

### Post by free10 on 2008-04-29
> **squaregoldfish said:**
> Your hunch is correct - for some reason ffmpeg isn't installed as a dependency of Kino.

You can install it using Synaptic - just search for the ffmpeg package (it's called ffmpeg), install it and all should be well.

Steve.

Thanks, Kino is now working and importing and converting flv files to DV once ffmpeg was installed. There were other ffmpeg codecs ect installed by Ubuntu's system, but not the one just called ffmpeg 3.0 CVS 2007. This may be the reason why some people are having Kino not working for them when they try and import files for editing. 

I had also tried Avidemux when Kino didn't work and it wouldn't either so this may fix it as well. 

On a side note my other system where it had worked was a 1 gig celeron with 500mb of memory and this system is a Intel quad 6600 2.4 gig with 4 gigs of memory and a faster hard drive and the encoding to DV was a lot faster. Thanks for the help and have a good one--Dwight

---

