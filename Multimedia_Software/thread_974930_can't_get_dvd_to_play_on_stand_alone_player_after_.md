---
title: "can't get dvd to play on stand alone player after iso burn"
date: 2008-11-08
forum: Multimedia Software
---

### Post by zeffuri on 2008-11-08
So here's the deal, I've been trying to back up my dvd collection on an external HD and to do that I've been creating iso files, throwing them in a selftitled folder and coming back to them later if I want to make a disc.

I have 2 problems at least...

1. When I first started burning the iso files to my DVD-R media, it would only get 50-70% of the way through and then fail.  (my work around was to lower the burn speed from max to the min and that seemed to work, though I'd like to burn at a faster pace)

2. The more important problem is that I have now completed a few burns by right-clicking on the iso and selecting "write to disc" (I'm guessing this is the default brasero burning software)  AND I've also created some through K3B.  Yet no matter what I use I am unable to play them on my stand alone player nor from the windows half of my machine (the linux side works just fine)

    I got to reading and found this is an issue with the released version of cdrkit 1.1.6 that comes with the fresh Ubuntu 8.04 install (or K3B and it's libraries... who knows I'm new to all this).  And I read that I need to "edit the source.list in order to update the version to 1.1.7.1 or higher (though some downgraded and had good results with that)

Will someone please give me a step by step walkthrough as how to "install" or update/downgrade the cdrkit version?  I found all the versions at cdrkit.org/releases  (but those are .tar.gz files and I have no clue as to what needs to be done.  Compile? (whatever that is - or how to do it) Install?  Extract?

Gah!  I've made a multitude of coasters already and have even tried purging K3B and re-installing it to no avail.

Please help.  And please for the love of Tux... speak slowly  :]

---

### Post by agentsmith23 on 2008-11-08
What software did you use to create the ISOs? Did you compress them to fit on a 4.7GB DVD or are you burning them onto a dual layer DVD? Have you tried uncompressing the ISOs onto the harddrive to confirm they aren't corrupt in some way?

---

### Post by alwayshere on 2008-11-08
I have burnt iso images by right clicing and write to disk in 8.04  with no problems as for brasero its no good i dont know why it even there everyones having  trouble with it.

your dvd burning drive can be a problem if it is not a good quality as i have found in the past that dvd would play on pc but would crap out at any time in in a home dvd player so i ended up searching the net and found a list of the best writers and got one it made all the difference

---

### Post by alwayshere on 2008-11-08
for the cdrkit thing type the below commands to update to latest versions 

sudo apt-get install genisoimage

push enter

sudo apt-get update

push enter

sudo apt-get install wodim

push enter

sudo apt-get update

push enter

---

### Post by zeffuri on 2008-11-12
Thanks very much for getting back to me, and I apologize for the slow response, but I was out of town until today...  Here are the results:

~$ sudo apt-get install genisoimage
[sudo] password for zeffuri: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
genisoimage is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Update - says the same thing

~$ sudo apt-get install wodim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wodim is already the newest version.

Again, the update command afterward says the same thing. (that everything is current when it's not).



Is there a way to force a cdrkit version change?
If I download one of the .tar.gz files from the cdrkit version site, how do I "install" it?

From what I've read, the main problem is version 1.1.6 of cdrkit creates bad iso files.  Usable on a linux box, but nothing else.  That is what I need to update/ change.

Thank you for your patience with me, sorry if I cause headaches...

---

### Post by alwayshere on 2008-11-12
the commands i gave you should have updated them
im using 8.10 but when i was using 8.04 i had no problems 

ill see if i can help out more later im off to work now

---

### Post by PabloBS on 2009-06-18
I'm having the same exact problem with burning of DVD iso images.

I have burned several video DVD's and I'm capable of mounting the images in Ubuntu (8.10 i386)and reproducing them like external DVD's with Mplayer.  When I try to burn the image to a backup DVD, I can't reproduce the DVD into a stand alone player connected to a TV. The iso images are not bigger than 4 GB.  

I used Brasero to get the images from the video DVD and burn them into the backups.

I have all the updates, and the hardware works fine with data CD's and DVD's.  

Do I have to use another burning software?  How can I fix Brasero to make operational video DVD's?

---

