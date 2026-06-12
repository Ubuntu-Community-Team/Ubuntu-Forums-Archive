---
title: "Application for getting CD/DVD media info?"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by foxmulder881 on 2007-12-04
I am looking for an application that can source what recordable media is inserted to any given CD/DVD drive.

eg. Insert a blank CD/DVD and get media info: **MCC** or **CMC** or **TY** etc.

---

### Post by ron999 on 2007-12-05
Hi
When I had Windows OS I used two apps for this job.
'CDRidentifier' for CDs and 'DVD Identifier' for DVDs.

I tried to run them with Ubuntu Linux.
No luck at all with CDRidentifier, but with DVD Identifier I managed to get it running with Wine.
I don't use it now because it 'timed out', maybe it was just an evaluation version.
So if you want to try it, here's the link:-
[http://dvd.identifier.cdfreaks.com/]("http://dvd.identifier.cdfreaks.com/")

Another way to find some media info is with K3b. Use **Device > Media Info**.
For DVDs it gives 'Media ID' (eg TDK502sakuM3), then use Google.

I hope someone else comes up with a better suggestion.

:cool::cool:
Edit
Similar results if you install package dvd+rw-tools from the repos then use the command
**dvd+rw-mediainfo /dev/dvd**

---

### Post by foxmulder881 on 2007-12-06
Yeah I tried the media info tool in K3b, but it's pretty basic and doesn't really give me the information that I was after.

In Windows I used to use a combination of ImgBurn and DVDInfoPro. But neither are linux compatible.

Cheers for the suggestions anyway ron999.

If anyone else has any suggestions, fee free to sing out.

---

### Post by disturbedite on 2007-12-06
nero's infotool was very informative.  maybe it runs with wine?

---

### Post by foxmulder881 on 2007-12-06
> **disturbedite said:**
> nero's infotool was very informative.  maybe it runs with wine?

Sorry, but I should have clarified in my last post I'm after a linux natuive application. I don't use and don't wish to use WINE.

---

### Post by acoustibop on 2007-12-06
Nero have been producing a Linux version for a while now.

---

### Post by ron999 on 2007-12-06
> **acoustibop said:**
> Nero have been producing a Linux version for a while now.
Hi
The NeroLinux that I have got installed is Version 2.1.0.4. The 'Disc Info' only gives info about what's on the disc, nothing about the characteristics.
There's a NeroLinux 3 available, but it costs $24.99.:roll:

---

### Post by foxmulder881 on 2007-12-06
> **ron999 said:**
> There's a NeroLinux 3 available, but it costs $24.99.:roll:

... and from what I know, it only gives you the same information as earlier versions.

---

### Post by disturbedite on 2007-12-06
the extra nero tools (such as infotool) are not included in nerolinux.

---

### Post by jeffus_il on 2007-12-11
I downloaded a free Nero Infotool from pcworld.com, got a windows executable cdspeed.exe which I ran using wine (a 2001 cabernet savingnon), using the menu extra->discinfo, got this output:

Manufacturer        : Plasmon
Code                : 97m27s18f
Disc Type           : CD-R
Usage               : General
Recording Layer     : Dye Type 8: Short Strategy (Phthalocyanine)
Recording Speed     : n/a
Capacity            : 79:59.74
                      703 MB
Additional Capacity : n/a
Overburn Capacity   : not tested

---

### Post by ron999 on 2007-12-11
Thanks for that jeffus_il
When I right-click that exe and select Open with "Wine Windows Emulator"
it tells me that it can't find a CD drive.
Maybe I will need to check that wine is configured correctly.

---

### Post by foxmulder881 on 2007-12-11
Hmmm, interesting for anyone that uses WINE.

I've discovered that the **Media Info** option in K3b only works for DVD media and not CD media.

DVD+R Screenshot...
[IMG]http://img.techpowerup.org/071211/screenshot.png[/IMG]


CD-R Screenshot...
[IMG]http://img.techpowerup.org/071211/screenshot2.png[/IMG]

---

### Post by ron999 on 2007-12-11
> **foxmulder881 said:**
> Hmmm, 

I've discovered that the **Media Info** option in K3b only works for DVD media and not CD media.


K3b probably uses the **dvd+rw-tools** app. And it looks like there isn't a similar app for CDs.
:sad:

---

### Post by foxmulder881 on 2007-12-13
> **ron999 said:**
> K3b probably uses the **dvd+rw-tools** app. And it looks like there isn't a similar app for CDs.
:sad:

You're correct. K3b *does* use the dvd+rw-tools package to identify dvd media.

---

### Post by ron999 on 2007-12-22
Hi
I've found out how to read the info from a CD-R.
It's written in an area known as ATIP.

To read it (with a disc in the drive) use a command

**cdrecord -atip**

or 

**cdrecord dev=/dev/hdc -atip**

(where /dev/hdc or similar is your drive)

The printout gives information about your drive and at the bottom is information about the disc.
Like this:-
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -12508 (97:15/17)
  ATIP start of lead out: 359845 (79:59/70)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 22
Manufacturer: Ritek Co.


Edit: Also command
**wodim -atip**
seems to do the same job.

I've attached a printout showing some examples.
8)

---

