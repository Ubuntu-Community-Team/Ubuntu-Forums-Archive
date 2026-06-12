---
title: "Burn dvds and cds"
date: 2010-12-20
forum: Multimedia Software
---

### Post by toolmania1 on 2010-12-20
Ok.  I have tried a few methods and have not been able to burn a dvd yet.  I can create the files that would go on the dvd.  

I first created a slide show using OpenShot.  I saved it as a avi.  First off, is this the correct format?
Also, I have other files from other methods that end in .mov.  Is this the correct format?  

Can I combine the two formats of .avi and .mov on the same dvd ( have not even gotten to this point yet, but figured I might as well ask up front )?

To burn the dvd, I tried qdvdauthor.  It crashed on me after I autogrouped two files.
Also, I tried k3b and DeVeDe.  I was able to create files, but I still could not get them onto a dvd. 

I tried to take the files from k3b and DeVeDe and create a DVD in Brasero.  Brasero just closes.  No error, no success message. 

How do I get files on a dvd in Ubuntu?

I would even be happy with tutorials or links of software that was worked.

Also, I will don't know how to get an audio cd burned in Ubuntu yet.

Thanks in advance!

---

### Post by JBAlaska on 2010-12-20
Do you need to have the DVD play in a standalone DVD player or just on a computer?

If you need to use a standalone DVD player, DeVeDe can make a ISO image file that you can then burn in k3b using the "Burn Image" feature.

If you just want to play avi and mov video files on a computer, you can simply use k3b to burn these files to the DVD with the "Create Data Project" feature, likewise you can also use this feature to burn your picture or mp3 files to the DVD disk.

Let us know what device (Computer or standalone DVD player) you want to play the DVD on, and we can point you to tutorials to help.

---

### Post by toolmania1 on 2010-12-20
I will be playing this on a stand alone dvd player ( actually many different dvd players )

---

### Post by JBAlaska on 2010-12-20
In that case, DeVeDe is the way to go, choosing the "create ISO" option, then you can use k3b to burn the ISO to a blank DVD using the "Burn image" option in that program.

This seems to be a good video tutorial [Here](http://www.category5.tv/show_notes/episode_48_-_devede_3.10.php)
It takes a bit to get to what you want to do, but it's through. Also it's a older tutorial, so check your DeVeDe version, you may not need to reinstall it as mentioned in the first bit of the video.

---

### Post by toolmania1 on 2010-12-20
Thank you!

So in summary, I used PhotoFilmStrip and to take my still pics and make them into a movie.  Then, I combined those movies ( made from slide shows ) with other .mov file ( movie files from my Kodak Easy Share camera ) and put those movies into OpenShot.  I created an avi from OpenShot.

Next, I used DeVeDe and created an iso.  Then, I actually could just right click on the iso and burned it to dvd.

I did see the Burn Image in k3b though also.  I am sure that would work as well.

---

### Post by toolmania1 on 2010-12-20
Now, what about just audio cds?

My wife tried to burn one the other day and it only plays on the computer.

---

### Post by ron999 on 2010-12-20
> **toolmania1 said:**
> Now, what about just audio cds?

K3b for this job too.
K3b > File > New Project > New Audio CD Project

---

### Post by toolmania1 on 2010-12-22
Nice!

I will try this later.

I wonder if this will take the files my wife burned onto a cd that only plays onto the computer and put them into a format that can play on any cd player?

---

### Post by toolmania1 on 2010-12-24
I am marking this closed as I have another audio thread open and the above comment will more than likely work since I am already using K3b for Video.

---

