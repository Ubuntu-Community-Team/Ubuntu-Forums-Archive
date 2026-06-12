---
title: "GStreamer in Ubuntu 13.04. What's happening?"
date: 2013-05-04
forum: Multimedia Software
---

### Post by Edu Camargo on 2013-05-04
[FONT=-moz-fixed]

Hello,

I posted the message bellow in Banshee's Mailing list, but I  also decided to pass it on to the forum so we can help each other on  this matter.



Hi guys, some help on this issue. 

I've noticed two strange behaviors with Banshee but I decided to make  some tests to check if is there anything wrong with Banshee actually. As  you noticed, I decided to dive into Ubuntu 13.04 this time and it was a  great choice to me due to some performance enhancements with the Orca  screen reader. And the official repositories already bring Banshee  2.6.1. The issues are occurring with FLAC, my format of choice. 

I've tried ripping "The ArchAndroid" by "Janelle Monáe. Everything  seemed ok while checking the files with Banshee, but I got these  unexpected results: 

1. Checking with EasyTag, I noticed that the year tag was not added. 

2. I went to test the files on my Windows machine using Foobar2000,  which refused to play with an error "unsupported format or corrupted  file". Since I'm aware about Banshee using GStreamer framework for all  multimedia purposes, I thought it was something with GStreamer adding  some incorrect frame (s) or something. 

All other applications play the files nicely. And Foobar plays other  FLAC files without problems. 

To confirm, I installed Grip since it uses commandline apps to handle  extraction and encoding of files. Reripped the CD to FLAC using Grip and  checked the results on my Windows machine. Foobar2000 played them  without complaints. 

As a final test, I decided to rerip the tracks using Rhythmbox. The  results were the same produced by Banshee, which made me think what I've  presumed and manifested on the subject field. So, congratulations,  Bansheeers!  

What might be occurring? 

Maybe I could post this in the Ubuntu Forums? 

Well, thanks in advance for any solution. This really anoys me. 

Peace, 

Edu. 

[/FONT]

---

