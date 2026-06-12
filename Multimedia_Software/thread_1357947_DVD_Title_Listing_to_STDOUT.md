---
title: "DVD Title Listing to STDOUT?"
date: 2009-12-17
forum: Multimedia Software
---

### Post by jephthah on 2009-12-17
I'm writing a terminal script that will, given a media source (Video in a bad format, personal dvd, etc) simply spit out the correctly formatted h264 video.  I've got mplayer and mencoder accomplishing most of this now - dumping if necessary, cropping if necessary, encoding, etc - but for DVDs (personal backups) I'm hung up on the task of isolating for the script...

A)The DVD Label
B)The Title (track) listing.

Obviously, the DVD label provides a good automated name for the output file, and the title listing is used to isolate which title to rip and encode.

There are numerous tools that will give this to me in an interactive way, ie, k9copy, dvdrip, etc.  Using these, however, I have to pull up another program, load the disc, view the titles, and give arguments to my script informing it of the correct title and the output filename.  This defeats almost the entire purpose of the tool, which is start-to-finish automation given only the media source - filename or "dvd".  Therefore, I need a tool that will spit out the DVD Label and the titles with length (and potentially more information like aspect ratio, but not necessarily) to STDOUT so that my script can take this information and use it. 

Does anyone know of a package that will do this for me?  If not, can anyone direct me to APIs for the libs that I could use to write (In C or otherwise) a tool that will do this?  Thanks!

---

### Post by diesch on 2009-12-17
Have a look at *lsdvd*

---

### Post by jephthah on 2009-12-17
Exactly what I need.  Fantastic!  Thank you.

---

