---
title: "Applet for having &quot;Facebook photo uploader&quot; functionality in your website?"
date: 2008-11-09
forum: Multimedia Software
---

### Post by greenpython on 2008-11-09
hi all, not sure if this is the best category so feel free to move if necessary...

a friend of mine needed a website double quick for a party he organised in october, had to be **bi-lingual**, some **music playing** from one of the djs, an **embedded google maps** and a spinning logo.  so first thing i managed to talk him out of the spinning logo ;) 

well i had a few spare evenings, was a little out of practice, but built a simple html site using an old copy of dreamweaver (couldnt get quantaplus to work, i tried!) so we made this  [www.leclub.cc]("http://www.leclub.cc")

so the party is a big success, over 1000 people, he's happy... then gives me 300+ photos after to upload to the site... oh bugger... i can make the thumbnails of all the pics using a script, but then i gotta create 300 separate .htm pages and a mess around with the links here there and everywhere...

so here's my question, i think i need to re-build the site using something much more maintainable code (maybe **joomla?**), with a **photo uploading function** much the same as facebook. (oh yeah the **menu** is real pain now, i gotta edit each piece of code for each page if there are any changes :( )

well actually, no-one else needs to upload the pictures, so it doesnt have to be within the site itself, but then i think from a technical point of view it does... maybe i need a single login just for me?

anyone solved a similar issue?

oh and he's got another party coming up in a month, so could do with these pics uploaded this week, then ready for the next batch after... aggggh!

any advice / simple solutions / examples would be much appreciated!

(then if it works i'll switch the thread around to be a step by step guide for anyone interested)

cheers!

greenpython

---

### Post by greenpython on 2008-11-21
Hi All, ok, well I found some solutions to the issues I had... they may be known, but I'd like to share ;)

 - I used photoshop (sorry, didn't have the time to learn gimp) to create a basic script to take all photos in one folder, reduce the size and dpi, and dump them in a little "thumbnail" folder.

 - For the site, I was faced with having to create single pages for every picture (cos im more of a design guy than a coder), now I only have 27 good ones to upload first, but there are hundreds more coming!  So I used an excellent free script by Lokesh Dhakar, called Lightbox2:

[http://www.huddletogether.com/projects/lightbox2/](http://www.huddletogether.com/projects/lightbox2/)

This meant I don't need separate pages, can add pictures much easier (cos it's just the thumbnails i need to add on one page), and it looks pretty cool!

It's also quite easy to configure once it has been installed, for example I change the behaviour of the script slightly so that my "previous" and "next" buttons are always displayed (in the original script they hide).

Of course I haven't gone for the "real" solution, which was to re-build the site in joomla (or flex... any opinions on this?)... but once again the site is "good enough".

If you are interested, you can check the updates made here 

[http://www.leclub.cc/](http://www.leclub.cc/)

Cheers

greenpython

---

### Post by hyper_ch on 2008-11-21
you could also have a look at coppermine:  [http://coppermine-gallery.net/](http://coppermine-gallery.net/)

---

