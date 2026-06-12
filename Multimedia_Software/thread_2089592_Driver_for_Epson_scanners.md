---
title: "Driver for Epson scanners?"
date: 2012-11-29
forum: Multimedia Software
---

### Post by felkar on 2012-11-29
Has anyone got an "Epson scanner - model 4490" to work in an Ubuntu 12.10 environment?

"Avasys" offers a driver that may(?) work with Ubuntu 11.10 - see:

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do).

It also posts the following warning:

*Download for Perfection 4490 PHOTO ((IMPORTANT NOTICE!! Check the following))Installing Image Scan! for Linux causes boot problems*

In spite of these flagged issues, I attempted to install the offered Avasys package:

iscan-data_1.13.0-1_all.deb 	27,514 bytes

The install worked and did not cause any "boot problems".

But my scanner claimed that it could not find the Epson driver.

What have I missed?

felkar

---

### Post by pdc on 2012-11-30
hi felkar

if I start at the newer Epson site, 

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

and enter [COLOR="Magenta"]4490[/COLOR] it takes me to here

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

and if I click on the top option it takes me to here 

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20233&DSCCHK=e8c8d6c7f9da68399277d5eddbf8121aecda09d5](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20233&DSCCHK=e8c8d6c7f9da68399277d5eddbf8121aecda09d5)

as you are ubuntu you need debian packages and there are two bits to the iscan ..........

1) install the [COLOR="SeaGreen"]**iscan-data_1.19.0-1_all.deb**[/COLOR] from the bottom of the page [COLOR="Blue"]FIRST[/COLOR]

.......[COLOR="Blue"]**then**[/COLOR] ...........

2) [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.[COLOR="Magenta"]ltdl7[/COLOR]_i386.deb[/COLOR] for [COLOR="Magenta"]32bit[/COLOR] or 

   [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.[COLOR="Magenta"]ltdl7[/COLOR]_amd64.deb[/COLOR] for [COLOR="Magenta"]64bit[/COLOR] 

(the [COLOR="Plum"]**ltdl7**[/COLOR] is for newer kernels......[COLOR="Plum"]**ltdl3**[/COLOR].......is for old kernels)

....that is the core install........ there is also a plug in I see ..

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15834&DSCCHK=4a0291307149a2e6969a35146d4d162dc76575cf](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15834&DSCCHK=4a0291307149a2e6969a35146d4d162dc76575cf)

If you follow my advice, I would suggest to DELETE all from your prior install, and do as above.....

...let us know how it goes..............

---

### Post by felkar on 2012-12-02
> **pdc said:**
> hi felkar


[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20233&DSCCHK=e8c8d6c7f9da68399277d5eddbf8121aecda09d5](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20233&DSCCHK=e8c8d6c7f9da68399277d5eddbf8121aecda09d5)

as you are ubuntu you need debian packages and there are two bits to the iscan ..........

1) install the [COLOR="SeaGreen"]**iscan-data_1.19.0-1_all.deb**[/COLOR] from the bottom of the page [COLOR="Blue"]FIRST[/COLOR]

.......[COLOR="Blue"]**then**[/COLOR] ...........

2) [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.[COLOR="Magenta"]ltdl7[/COLOR]_i386.deb[/COLOR] for [COLOR="Magenta"]32bit[/COLOR] or 

 
....that is the core install........ there is also a plug in I 
...let us know how it goes..............

The first reference and the plug-in were easy.  The second (core) reference was not.  I found it - ultimately - with the following caveat:

[COLOR="red"]Index of [ftp://djam.spb.ru/other/soft/Drivers/Scanner_Epson_Perfection_V330_Photo/2.29](ftp://djam.spb.ru/other/soft/Drivers/Scanner_Epson_Perfection_V330_Photo/2.29)

This type of file can harm your computer. 

/home/felixk/Downloads/iscan_2.29.1-5~usb0.1.ltdl7_i386.deb
[/COLOR]

I have downloaded the package and will install it  - when I get the courage.

Thank you for the advice

felkar

---

### Post by pdc on 2012-12-02
[ftp://djam.spb.ru/other/soft/Drivers/Scanner_Epson_Perfection_V330_Photo/2.29/](ftp://djam.spb.ru/other/soft/Drivers/Scanner_Epson_Perfection_V330_Photo/2.29/)

I can't understand what that has to do with the Epson links I suggested.............

......help me understand..............

things should work with what you have installed ........

.......this.........

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15834&DSCCHK=4a0291307149a2e6969a35146d4d162dc76575cf](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15834&DSCCHK=4a0291307149a2e6969a35146d4d162dc76575cf)

.......from the Epson site is some sort of plug-in ...............you can check it out.............

........and install it .............if you want...........

---

### Post by felkar on 2012-12-03
> **pdc said:**
> [ftp://djam.spb.ru/other/soft/Drivers/Scanner_Epson_Perfection_V330_Photo/2.29/](ftp://djam.spb.ru/other/soft/Drivers/Scanner_Epson_Perfection_V330_Photo/2.29/)

I can't understand what that has to do with the Epson links I suggested.............

......help me understand..............

things should work with what you have installed ........



I fear that I was too brief.

[ftp://djam.spb.ru/other/soft/Drivers/Scanner_Epson_Perfection_V330_Photo/2.29/](ftp://djam.spb.ru/other/soft/Drivers/Scanner_Epson_Perfection_V330_Photo/2.29/)

has **one** entry that lists the recommended driver - "iscan_2.29.1-5~usb0.1.ltdl7_i386.deb".  This driver was not present on the Avasys list.

I downloaded it and parked it in my "Download" directory; hence the full address (on my computer) was:

/home/felixk/Downloads/iscan_2.29.1-5~usb0.1.ltdl7_i386.deb

====================================

Follow-up
=========

I have unpacked and installed the 3 ".deb" packages.

My "Epson 4490 Photo Scanner now works and 
Ubuntu 12.10 reboots without problems.

Once again, many thanks for the (badly-needed) advice.

felkar

---

### Post by pdc on 2012-12-03
delighted to hear your scanner is working well now; that's great; enjoy :)

---

### Post by Czechrite on 2012-12-28
I had some mixed success with this. I actually did get it to run and detect the scanner with iscan but I had to run iscan under "sudo".

The other scanner apps worked as well and I'd really like to have tried xscan but the backlight on the scanner didn't light while using xscan...so it was mostly black. I was scanning 120x120 type large format negatives.

All this has taken almost 19 hours and a lot of determination not to go back to Windows and to learn everything I can about LINUX systems.

I guess I'll be tinkering my holiday time-off for days!

---

### Post by maclenin on 2012-12-29
Perhaps, this will help focus the search: [http://ubuntuforums.org/showthread.php?t=1447789](http://ubuntuforums.org/showthread.php?t=1447789) 

It's a how-to I put together for an Epson Perfection V30 scanner, but the methodology could provide clues (for others)....

---

### Post by felkar on 2012-12-30
> **Czechrite said:**
> I had some mixed success with this. I actually did get it to run and detect the scanner with iscan but I had to run iscan under "sudo".

SNIP

All this has taken almost 19 hours and a lot of determination not to go back to Windows and to learn everything I can about LINUX systems.

I guess I'll be tinkering my holiday time-off for days!

I have found it to be a challenge to persuade an Epson Scanner to work in *any* Linux environment (I have used RedHat, Debian and now Ubuntu).

But it is not a topic that belongs to "Ubuntu Forums".  

I started this thread to follow up a "flagged possible boot problem with the recommended iscan package";  this turned out to be a red herring (my observed "boot problem" has become very infrequent since updating my kernel).

 My only advice to any Linux user, who is struggling with an (Epson) scanner is:

"Have a look at "VueScan"

That is a commercial package; in my book, if you can get it to work, it is greatly superior to iscan (it uses an iscan driver).

felkar

---

