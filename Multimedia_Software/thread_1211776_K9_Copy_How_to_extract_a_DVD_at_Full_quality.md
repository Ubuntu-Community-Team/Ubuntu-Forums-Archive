---
title: "K9 Copy How to extract a DVD at Full quality"
date: 2009-07-13
forum: Multimedia Software
---

### Post by tomreid on 2009-07-13
Hi

I was just looking for a simple programme for Ubuntu that will extract the contents of a DVD (vob files, etc) without any compression.

K9 Copy seems to be the closest, but it always seems to want to compress the DVD output to around 4.3 Gb max, obviously to have the output of dual layer commercial disc fit on a domestic single layer DVD.

I was more interested in just buying a large drive, getting rid of my DVDs and keeping their contents there, not re-burning the DVD onto another disc. Can I get K9 copy not to do any compression? There seems to be some control (the second last screen you see before you finalize the rip) but I couldn't figure out how that worked. 

Other programmes, like Acid Rip, always seem to want to change the output into Avi containers or similar.

I'm really just looking for a simple extraction of the DVDs contents, somthing similar to how Mac the Ripper which I've used on macs.

cheers

---

### Post by mc4man on 2009-07-13
don't have k9 nor have used it in quite some time but somewhere in the settings is a place to set the target size, the default is 4.3 Gb.
 Just raise it above your dvd's size (7.6 Gb should do for most dvd's

Edit 
for non structured protected titles vobcopy with the -m parameter works quite well
(mirrors the complete disk into a folder in file format (VIDEO_TS

---

### Post by Bigtime_Scrub on 2009-07-13
The DVD's are huge because it is part of the encryption process to prevent 'pirating.' k9copy by default does compress but you can control how much. 

Insert a DVD and open k9copy. The left window of k9copy shows the DVD structure. Select what parts you want copied. (You may select them all if you wish.) 

Now got to Settings -> Configure k9copy

The output directory here is only a temporary storage area so k9copy can work. Under the settings window on the left you will see several icon options, the one you want is "DVD" which is the second one from the top just below "Devices." 

Select that and you get a new window with some other options. Under DVD size the default selection is 4400 MB which is 4.4 Gigs. Adjust it to whatever you like by highlighting the number and either typing in a new amount or using the arrow keys next to it to increase or decrease the value in megabytes. 

Keep in mind you can also select what kind of output you desire which can be either TS_folders, a .iso, or anything else you like. FYI i save mine as iso files that I mount with AcetoneISO or you can just store them on your hard drive and extract from them later if you wish.

---

### Post by tomreid on 2009-07-13
Thanks guys, just so I understand, the DVD size in the default section which I sill set will not be an absolute value that the programme will aim for?

i.e. if  put it to 10Gb, and the DVD is only 7GB in size, it will only create a copy that's 10GB or 7GB?

It was the term "default" that confused me.

cheers

---

