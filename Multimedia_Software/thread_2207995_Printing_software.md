---
title: "Printing software ?"
date: 2014-02-26
forum: Multimedia Software
---

### Post by Marek_Pietrulewicz on 2014-02-26
Hi,

I am looking for a printing software (does not have to be free). I have tried:

- Corel Aftershot PRo,
- Gnome Photo Printer
- Photoprint
- gThumb Image viewer
- Gwenview

the requirements are:

- printing photos 10x15 to the edge
- printing multiple photos on one page with ability to arrange them manually
- ability to force photos to fit the 10x15 page to the edges regardless of photo's aspect ratio (so that part of the photo can be cropped ) - no white strips on the sides of the prints


Any suggestions?
Marek.

---

### Post by squakie on 2014-02-26
Ooopppsss....posted before I was finished!  Removed the text here - see my next post.  Sorry about that!

---

### Post by squakie on 2014-02-26
Since this is all dealing with images, you might want to try GIMP.  I *think* it's installed by default now, but if you can't find it do:

sudo apt-get install gimp

You'll want to play with it a while to see how it works, and do a lot of searches on the net for questions you may have.  It may not seem like much at first, but it's a very powerful image editor which you can use to do what you are wanting.

You may also want to read:  [http://dingyichen.wordpress.com/2013/05/13/howto-print-multiple-photos-in-one-page-with-linux/](http://dingyichen.wordpress.com/2013/05/13/howto-print-multiple-photos-in-one-page-with-linux/)

---

### Post by IvoGuerreiro on 2014-02-26
I preferred the GIMP, but give a look to digiKam.
By the way to install (software center) or:
```

sudo add-apt-repository ppa:msylwester/digikam
sudo apt-get update
sudo apt-get install digikam
sudo add-apt-repository -r ppa:msylwester/digik

```

---

### Post by coldraven on 2014-02-26
> - ability to force photos to fit the 10x15 page to the edges regardless  of photo's aspect ratio (so that part of the photo can be cropped ) - no  white strips on the sides of the prints

For that try adjusting "Printer Properties" to "Expand (Use maximum page area)".

---

### Post by squakie on 2014-02-26
Most nwere printers support the "Expand", but not all printers do - they might still have a border around them.  ;)

---

### Post by coldraven on 2014-02-27
> **squakie said:**
> Most nwere printers support the "Expand", but not all printers do - they might still have a border around them.  ;)
If the printer cannot do "borderless" then the OP would need to buy one that does.
My Epson R300 is ten years old. (It has six re-fillable cartridges with self-resetting chips and prints lovely pictures)
[http://reviews.cnet.co.uk/printers/epson-stylus-photo-r300-review-39188594/](http://reviews.cnet.co.uk/printers/epson-stylus-photo-r300-review-39188594/)

---

