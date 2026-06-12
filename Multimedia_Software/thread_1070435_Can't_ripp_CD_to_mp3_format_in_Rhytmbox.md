---
title: "Can't ripp CD to mp3 format in Rhytmbox"
date: 2009-02-15
forum: Multimedia Software
---

### Post by mravljica on 2009-02-15
I use Ubuntu 8.10 amd64. I want to copy some audio CD's to my computer with Rhytmbox and in Preferences I wanted to select to "CD quality, MP3" but I don't have that option listed in dropdown menu. However it is listed and set to Active in Edit option (next to dropdown menu).

What is wrong here?

---

### Post by amauk on 2009-02-15
this all depends on which libavcodec you have installed

Encoding to MP3 is protected under a license
technically, you need to purchase a license from the Fraunhofer Institute

Because of this restriction, by default, Ubuntu does not ship with the ability to encode MP3's

Ubuntu ships with the libavcodec51 package
this allows encoding in all un-protected formats

Install the libavcodec-unstripped-51 package to enable encoding in all formats (including ones which you need a license)

It's now your problem if you are encoding to formats without the proper authorization

---

