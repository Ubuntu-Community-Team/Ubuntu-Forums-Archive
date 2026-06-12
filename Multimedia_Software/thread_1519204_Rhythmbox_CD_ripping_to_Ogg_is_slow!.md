---
title: "Rhythmbox CD ripping to Ogg is slow!"
date: 2010-06-27
forum: Multimedia Software
---

### Post by Anton32828 on 2010-06-27
I have been using Ubuntu for business apps (OpenOffice and mail) with great results. I just started to play around with some of the multi-media stuff this weekend when I got a new computer. Having heard a great deal about the advantages of Ogg, I decided to rip some music CDs to that format using Rhythmbox, and was surprised to see very slow performance.

For comparison I also ripped the same CD to MP3. The performance was significantly faster.

My computer is a quad-core Intel i5 with 4GB of RAM. System monitor shows low CPU and memory usage during the ripping process, which is kind of annoying. My machine could load the whole CD to memory and rip 4 tracks in parallel (one per CPU) if the code supported such processing.

Is Ogg just naturally slow or is this a Rhythmbox issue? Are there better / faster CD-import front-ends that I could use to generate the files? I couldn't find much guidance on the wiki and FAQ site. 

Thanks,

---

### Post by Giwex on 2010-06-28
Not a solution but try to install Soundconverter (directly from Ubuntu Software Center) and see if it faster.

---

### Post by hansdown on 2010-06-28
Hi Anton32828.

I was ripping music with rythmbox also.

It's been a while since I've used it, but I don't recall it being so painfully slow.

---

### Post by nothingspecial on 2010-06-28
If the output file is larger then the time taken will be longer.

How do the output file sizes compare.

---

### Post by Stavro on 2010-06-28
This is not necessarily a bad thing. Slow encoding time could mean higher quality files. Both mp3 and ogg have one thing in common; that is they both use 'dumb-decoders' so consequently all the work is done at encoding stage. A lot of mp3 encoders sacrifice quality over encoding time and certainly many improvements have been made in recent years for achieving fast rip times with minimal loss to overall sound in this format. It depends what mp3 encoder you are comparing ogg with?

If quality is really what you are looking for though; nothing beats letting it work slowly. For the mp3 format using LAME with the appropriate settings is best. Historically as far as I can gather ogg has always been primarily concerned with quality over speed of encoding. How do they compare up in sound?

---

### Post by Anton32828 on 2010-06-28
Thanks to all who replied. I will install soundconvertor to see if there is a difference.
 
The sound quality is the same between the MP3 conversion and the ogg conversion to the extent I can hear via my cheap SanDisk headphones. The ogg file size is smaller (as expected). 
 
There may be a glitch in my DVD drive (or generic driver) performance. Some CDs audibly spin up within the drive and then rip faster after an initial rip of half a track or so. Other CDs stay at a slow initial spin.

---

### Post by Giwex on 2010-06-29
I realized that I didn't mean to install soundconverter but Asunder, sorry for bad advice :(

---

