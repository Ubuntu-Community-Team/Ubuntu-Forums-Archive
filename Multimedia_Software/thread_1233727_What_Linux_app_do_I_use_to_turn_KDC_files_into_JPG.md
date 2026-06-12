---
title: "What Linux app do I use to turn KDC files into JPG or other nonproprietary files?"
date: 2009-08-07
forum: Multimedia Software
---

### Post by tomasrey88 on 2009-08-07
I have an old Kodak camera that has lots of KDC files. How do I turn KDC files into JPG using Linux? They are viewable using gimp and fspot but not convertible. What should I do? Thanks.

---

### Post by tomasrey88 on 2009-08-07
I guess it is impossible to turn kodak camera images (kdc) into jpg with ubuntu?

---

### Post by KinaU on 2009-08-07
Well, the only thing I can think of is opening the KDC image with an image viewing app (if you click the photo twice), and then "File" > "Save As" and change, for example IMG0001.KDC to IMG0001.JPG (the ending). Or even just right click and rename, change the last part to .JPG. 

See, it works for music...so it *might *work for your photos. I hope it works. :D

---

### Post by mc4man on 2009-08-07
This is old and it appears cli only.
Needs to be compiled, which it did  easily on hardy, whether it works not a clue, don't have any .kdc files

Converts (supposedly) to either .jpeg or .tiff

[http://linux.softpedia.com/get/Utilities/kdc2tiff-5850.shtml](http://linux.softpedia.com/get/Utilities/kdc2tiff-5850.shtml)

usage 
> doug@doug-laptop:~$ kdc2jpeg --help

USAGE
	kdc2jpeg [ global-options ] inputfile [ local-options -o outputfile1 ]
		[ local-options -o outputfile2 ] ...

OPTIONS
	-w #	output image width
	-h #	output image height
	-g #	absolute gamma correction
	+g #	relative gamma correction
	-G	no grain reduction (default)
	+G	reduce graininess
	+GG	reduce graininess (extra)
	+e	normal contrast enhancement (default)
	+E #	advanced contrast enhancement
	-e	no contrast enhancement
	-W wht	colour of light source
	+s	square pixels (default)
	-s	allow non-square pixels
	+f	fast processing
	-f	slow processing, high quality (default)
	+p	crop image if necessary to fit width and height (default)
	-p	no cropping, width and height are maximums
	-R	don't rotate image (default)
	+R	rotate image clockwise
	+B	rotate image counter-clockwise
	-C copy	note copyright in output file
	-q #	JPEG quality setting (0 to 100, default is 75)
	+P	create progressive JPEG file

Version: 0.35

or use command kdc2tiff

If you have/now a link to a sample .kdc would give it a try

edit 
project page and a caveat
[http://sourceforge.net/projects/kdc2tiff/](http://sourceforge.net/projects/kdc2tiff/)
[http://sourceforge.net/forum/forum.php?forum_id=62483](http://sourceforge.net/forum/forum.php?forum_id=62483)

---

### Post by tomasrey88 on 2009-08-09
I installed kdc2tiff using synaptic. I used command man kdc2tiff and it printed out the "manual", but it might as well be martian to me. Hey, I don't need to know any fancy commands. Just please tell me exactly what to type in to get a kdc file to become a tiff or jpeg file. Thanks.

---

### Post by tomasrey88 on 2009-08-10
This is a cut and paste of my terminal. Please tell me what I typed wrong. 

panda@pandamonium:~$ kdc2jpeg /media/disk/Pics/WashDC/P001081.KDC
Segmentation fault
panda@pandamonium:~$ 

Thanks,
:P

Same result with kdc2tiff command.

---

