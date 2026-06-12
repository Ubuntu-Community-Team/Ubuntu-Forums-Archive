---
title: "mplayer Invalid NAVI packet!"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by Ethos on 2006-12-15
Hello all im trying to rip a vob file from a dvd so that I can encode it to mp4, but when im ripping the vob im getting ```
Invalid NAVI packet! lba=0x2401  navi=0x23D7  
Invalid NAVI packet! lba=0x2402  navi=0x23D7  
Invalid NAVI packet! lba=0x2403  navi=0x23D7  
Invalid NAVI packet! lba=0x2404  navi=0x23D7  
Invalid NAVI packet! lba=0x2405  navi=0x23D7  
Invalid NAVI packet! lba=0x2406  navi=0x23D7  
Invalid NAVI packet! lba=0x2407  navi=0x23D7  
Invalid NAVI packet! lba=0x2408  navi=0x23D7  
Invalid NAVI packet! lba=0x2409  navi=0x23D7  
Invalid NAVI packet! lba=0x240A  navi=0x23D7  
Invalid NAVI packet! lba=0x240B  navi=0x23D7  
Invalid NAVI packet! lba=0x240C  navi=0x23D7  
Invalid NAVI packet! lba=0x240D  navi=0x23D7  
Invalid NAVI packet! lba=0x240E  navi=0x23D7  
Invalid NAVI packet! lba=0x240F  navi=0x23D7  
Invalid NAVI packet! lba=0x2410  navi=0x23D7  
Invalid NAVI packet! lba=0x2411  navi=0x23D7  
Invalid NAVI packet! lba=0x2412  navi=0x23D7  
Invalid NAVI packet! lba=0x2413  navi=0x23D7  

``` Any ideas?

---

### Post by megs on 2007-01-10
Hi,
Not sure if this will be related - there's lots of other information about this can be caused by not having libdvdcss installed, but I found it can also be caused if you've not set the region on your dvd drive.  I booted into OSX (Mac Mini) and played a dvd, that did it, but you can also use regionset I think.
Cheers,
Megs

---

### Post by jaddle on 2007-09-29
I'm seeing a similar problem, but the disc does play properly for a while. It's disc 3 of Firefly, and it gets about halfway through an episode before dying with these errors:

Invalid NAVI packet! lba=0xC45EE  navi=0xC45DE  
...

There are hundreds of those lines. The dvd plays just fine in xine, though I prefer mplayer these days.

the problem occurs whether I'm playing the disc itself, or a mirror made with vobcopy.

---

### Post by chris_nava on 2008-06-19
In my case, cleaning the DVD appears to have fixed the problem.

---

