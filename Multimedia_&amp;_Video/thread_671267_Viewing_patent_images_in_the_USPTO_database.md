---
title: "Viewing patent images in the USPTO database"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by PapaNerd on 2008-01-18
According to the USPTO website ([http://www.uspto.gov/patft/help/images.htm](http://www.uspto.gov/patft/help/images.htm)), a special plug-in is needed to view patent images stored in "TIFF files using ITU T.6 or CCITT Group 4 (G4) compression" format.  That website refers to a Linux plug-in available at [http://fredrik.hubbe.net/plugger.html](http://fredrik.hubbe.net/plugger.html).  A keyword search within the Synaptic Package Manager under 7.10 refers to the [http://mozplugger.mozdev.org](http://mozplugger.mozdev.org) website.

Has anyone tried either of these tools, or found something else, that will view patent images?

---

### Post by jeffus_il on 2008-01-18
The plugger program enables your browser to call a program called "display" which belongs to the imagemagick linux package. This package can be installed on all linux distributions. 
You can use this combination to view the patents in your internet browser or you can download the documents and view them on your local hard drive using "display".

---

### Post by PapaNerd on 2008-01-22
Thanks for the info.  Unfortunately, I am unable to get past the configure step using plugger 5.1.3.  I presume this is a missing library, but the log file messages are not specific as to where the failure is, so I cannot determine what is missing.  Output is as follows:

./configure
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.

Any suggestions will be appreciated.

---

### Post by jetpeach on 2008-02-21
i had managed to compile plugger 5.1.3 and even created a deb file i was going to post on getdeb, but plugger didn't seem to fix the problem for me - firefox still wouldn't display the patent images.
but now i installed " mozplugger " and the images display nicely. so it seems compilation is not necessary, just install mozplugger and make sure imagemagick is installed as well (i think it is in the base ubuntu packages, so should be already)

---

### Post by kiddo on 2008-04-24
no no no, don't compile "plugger", it's an old, dead project from 2001 (if I remember correctly). **Mozplugger is its replacement**. 

Just install mozplugger and images now show up in the browser. At least that's my case. The problem is that you can't zoom and save the images or anything. Back in dapper, I think I used gqview and mozplugger which allowed me to do that, but installing them in hardy does not make any difference to if I install only mozplugger. I hope this can help someone get started...

But the thing is, what is the point of using the crappy website of the USPTO when Google has the same contents, much more accessible and better organized? ([http://www.google.com/patents](http://www.google.com/patents))

---

### Post by intotechs on 2008-05-15
i have a similar problem viewing USPTO figures except i am running on XP.  when i click on images, it comes back and ask me to install Quicktime plugin.  i already have the latest version of Quicktime so what am i missing?  tia for any hints or help.

here is the patent example.  google patents doesn't find it.
[http://appft1.uspto.gov/netacgi/nph-Parser?TERM1=20070100332+&Sect1=PTO1&Sect2=HITOFF&d=PG01&p=1&u=%2Fnetahtml%2FPTO%2Fsrchnum.html&r=0&f=S&l=50](http://appft1.uspto.gov/netacgi/nph-Parser?TERM1=20070100332+&Sect1=PTO1&Sect2=HITOFF&d=PG01&p=1&u=%2Fnetahtml%2FPTO%2Fsrchnum.html&r=0&f=S&l=50)

---

