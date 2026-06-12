---
title: "Next problem: how do I install my Canon MP640?"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by Bernie Gallagher on 2010-07-03
Hi!  It's me again...   Now that I got my wireless card working, I want to install my printer.  
 
I went to Canon.com and, of course, they support every flavor of Windoze and even MAC/OS, but not Linux.  
 
I didn't really expect this to work, but I tried anyay loading the driver CD for the printer and running the SETUP.EXE program.   I got a cryptic error message.  Poo!
 
The printer is a Canon PIXMA MP640.  It's hard-wired to my router and accessing it through the network.  Anyone know where I can get a network driver for this printer?

---

### Post by pdc on 2010-07-03
Bernie:

you need a printer driver for your MP640?

if you go here

[http://support-sg.canon-asia.com/?personal](http://support-sg.canon-asia.com/?personal)

and search on ....... eg MP610 

you will find linux drivers: rpm, deb, source

[http://support-sg.canon-asia.com/P/search?model=PIXMA+MP610&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-sg.canon-asia.com/P/search?model=PIXMA+MP610&menu=download&filter=0&tagname=g_os&g_os=Linux)

and if you search on MP630 (or MP638 ..........) you get a choice of linux drivers: rpm, deb, source

[http://support-sg.canon-asia.com/P/search?model=PIXMA+MP638&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-sg.canon-asia.com/P/search?model=PIXMA+MP638&menu=download&filter=0&tagname=g_os&g_os=Linux)

so I wonder if this is really true

> 
I went to Canon.com and, of course, they support every flavor of Windoze and even MAC/OS, *but not Linux*. 

You can also look on the Canon Europe site, 

.... and for the MP640, Canon Europe list you rpm or deb or source files .......

(*instead Canon Asia offer linux drivers for the MP648* ................)

[B][U]SO GO HERE 
[/U][/B]
[http://software.canon-europe.com/products/0010757.asp](http://software.canon-europe.com/products/0010757.asp)

can I suggest you try this? from the European site?

As Ubuntu is a debian derivative, you should download the debian packages as most easy to install:

Each of the Canon printer drivers usually come as packages of two:

a common package and a specific package for a defined printer

so download the COMMON PACKAGE first (and install it)

and then the MP648 package;

I assume this is the way the latest packages listed on the Europe site work

YOu will see Canon also offer drivers for the scanner function;

hopefully you have the 32 bit Ubuntu installed; these drivers are for 32 bit systems; for a 64 bit system, they do not know to look in lib64 so we can advise on a symbolic link if you have 64 bit

(Another option is to buy turboprint: it is a very good programme, as befits the very good printer you have treated yourself to: 

[http://www.turboprint.info/](http://www.turboprint.info/)

you can see they offer you a 30 day trial: it again is easy to install .............)

good luck; let us know how you get along

---

### Post by DJYoshaBYD on 2010-07-03
do everything ^^^^^^that guy said, except buy software.. lol.. there is almost always an open source alternative.. :)

at least, that is my experiment..

---

### Post by Bernie Gallagher on 2010-07-03
Well, that's interesting that the Canon Asia site had a Linux driver for the MP 640, but the USA site didn't list a driver for Linux.  I'm downloading it now...

---

### Post by pdc on 2010-07-04
I guess Canon is an Asian company originally ........... ?

from Japan ? so they have the MP648 model offered there ... it is the European Canon site that offers the MP640 driver;

all best wishes with the installation; 

do you have 32bit or 64 bit ubuntu ........ ??????

---

### Post by Bernie Gallagher on 2010-07-04
Well, I requested two versions of Ubuntu from Canonical: Ubuntu 9.10 Desktop Edition, and Ubuntu 9.10 Server Edition. I installed the Desktop Edition on my laptop. The packaging doesn't actually come out and say x-bit version, but the blurb says, "This desktop edition will run on most PCs, including those with Intel or AMD processors." So I think it's safe to conclude it is the 32-bit version. 
 
And so far, I like all the Linux equivalent software like Firefox and OpenOffice. But, I have a few games like M$ Train Simulator that there's no Open Source version for, nor even a Linux version. That's why I want WINE. And I just want the warm fuzzy feeling that I can still run all my old M$ software before I take the plunge and Linufy ALL my PCs...

---

### Post by Bernie Gallagher on 2010-07-05
I downloaded that driver from the Canon Asia site.  I have a ...tar.gz file in my downloads folder.  What do I do with it?

---

### Post by pdc on 2010-07-06
strange;

when I click on the site it offers me the debian driver as the MP640_debian_driver_pack.tar  

If you open your downloads directory, and RIGHT-CLICK on the .tar file, select the top option: Open with Archive Manager

Once that opens, 

then click on the top line, the package; (that says .tar.gz) and highlight and click;

it should open down to the point you see the cjncommon.deb file and the cjnMP640.deb file

if you RIGHT-CLICK on the COMMON one first, and select install with gdebi installer and then do the same for the cjnMP640; you will then have the drivers installed; your system may then come to life;

if not, paste this into a spare browser window:

> [http://localhost:631/](http://localhost:631/)

and select Manage printers and you should be able to configure from there

I was also curious about this

> do you have 32bit or 64 bit ubuntu ........ ?????? 

If you don't know, open a terminal and copy and paste this command in

> uname -aand look for i686 or some other clue

---

### Post by Bernie Gallagher on 2010-07-08
Linux Klavierstein 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by pdc on 2010-07-09
so that is good:

you are using 32 bit Ubuntu, so ...... all should go well ........

---

### Post by Bernie Gallagher on 2010-07-09
Good to know.  It's an old laptop, so I doubt it would run 64 bit anything...

---

### Post by Bernie Gallagher on 2010-07-09
> **pdc said:**
> ...If you open your downloads directory, and RIGHT-CLICK on the .tar file, select the top option: Open with Archive Manager...

Thanks!  I followed all that and installed both drivers.  I rebooted.  But when I tried to print something from OO, it gave me a one choice of GENERIC PRINTER.  I tried to print to the generic printer anyway, but nothing happened.  Is there one more step I need to do?

---

### Post by pdc on 2010-07-10
open a page on Firefox (or whatever your browser is); 

into the browser space at the top: paste this

> [http://localhost:631/](http://localhost:631/)

that opens CUPS and in the middle column, click on 

"adding printers and classes"

then click on 

Printers .. I suggest manage printers ... any listing for your Canon?

If not fossik around in add new printer 

if so, select ..... if not, the install did not go as planned ..

---

### Post by Bernie Gallagher on 2010-07-10
Yes!  That worked!  Thank you!  

And yes, I use Firefox.  It's what came pre-installed on Ubuntu, and is what I use on my Windoze machine too.  Do you recommend a different browser?  Chrome maybe?

---

### Post by pdc on 2010-07-10
Great! Enjoy!

If your system works, just go on using it and enjoy!

If you had the energy to make a new post on the hardware section called something like

> **SOLVED: install Canon MP640 Ubuntu**

and just make a link to this thread:

Google can find it and help others; 

Well done to get your printer working; enjoy

Now that I know it works, I might get one myself!!

---

### Post by Bernie Gallagher on 2010-07-10
> **pdc said:**
> Now that I know it works, I might get one myself!!

Right.  It's a good little printer.

---

### Post by charliko1 on 2011-08-11
> **Bernie Gallagher said:**
> Right.  It's a good little printer.

Dohar@ubuntu:~$ uname -a 
Linux ubuntu 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
char@ubuntu:~$ 
Does this mean 64 bit sys?

If so how do i get drivers for my pixma mp640?

Thanks in advance,

charlie

---

### Post by pdc on 2011-08-11
you go here

[https://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP640.aspx?type=download&page=1](https://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP640.aspx?type=download&page=1)

as this page has the debian driver for ubuntu; and the scangear software for the scanning part

if you click on the debian printer driver, your system should offer to open with archive manager; or save;

I suggest save; and save in your Downloads directory;

open a terminal

type

> cd Downloads hit Enter

type 

> ls .........this command lists what is there......

you should see cnij.......whatever.tar.gz

type

> tar -xvzf cnij  and then hit the TAB key; the computer should identify the file and spell the rest of the file's name for you

when you have the full name, hit ENTER key

now type

> chmod +x cnijfilter-mp640series-3.20-1-i386-deb/install.sh

hopefully hitting enter will now run this install file ............

this should install the files

for your 64bit you need to create a symbolic link

again copy and paste this into a terminal

> ln -s /usr/lib/cups/filter/pstocanonij /usr/lib64/cups/filter

how is it all coming along ...........

---

