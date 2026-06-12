---
title: "EXIF and IPTC"
date: 2008-03-22
forum: Multimedia Production
---

### Post by tyto_alba on 2008-03-22
Hi there,

I have a large collection of photographs, all tagged nicely with EXIF and IPTC meta data.  Most of them in raw but some jpeg as well. 

What I want to do now is to create a database that contains all the IPTC and EXIF data + a small thumbnail and the location of each image. So that, when I search the DB for  keywords, date, location, or whatever I get a small preview of all pics matching that description as well as a path to the image (this should also work with images stored on external drives or CDs). After the initial setup some new images need to be added to the DB every now and than.

Is there a ready made solution that would do this for me? 

Thanks
tyto

---

### Post by Martin-Herrmann on 2008-04-01
> **tyto_alba said:**
> 
I have a large collection of photographs, all tagged nicely with EXIF and IPTC meta data.  Most of them in raw but some jpeg as well. 

What I want to do now is to create a database that contains all the IPTC and EXIF data + a small thumbnail and the location of each image. So that, when I search the DB for  keywords, date, location, or whatever I get a small preview of all pics matching that description as well as a path to the image (this should also work with images stored on external drives or CDs). After the initial setup some new images need to be added to the DB every now and than.

Is there a ready made solution that would do this for me? 


Hi,

Mapivi ([http://mapivi.de.vu]("http://mapivi.de.vu")) provides everything you are looking for: searchable database, full EXIF and IPTC support, thumbnails, offline picture support. The only restriction is, that it does not support RAW pictures. :(
As most of your pictures are in RAW format this won't help much unless you generate a JPEG for each RAW picture with the same file name as workaround.
Another possibility could be Digikam, but AFAIK it does not support offline pictures.

Regards
         Martin

---

### Post by tyto_alba on 2008-04-08
> **Martin-Herrmann said:**
> 
Mapivi ([http://mapivi.de.vu]("http://mapivi.de.vu")) provides everything you are looking for: searchable database, full EXIF and IPTC support, thumbnails, offline picture support. The only restriction is, that it does not support RAW pictures. :(


I tried Mapivi some time (half a year?) ago, couldn't get it to work properly on my setup :-(

> **Martin-Herrmann said:**
> 
As most of your pictures are in RAW format this won't help much unless you generate a JPEG for each RAW picture with the same file name as workaround.


I'm seriously thinking of archiving all my pics in jpeg. - Smaller files, easier to handle, and a good chance that I will still be able to read them in 30 years time ... Maybe now would be a good time to start the conversion?

> **Martin-Herrmann said:**
> 
Another possibility could be Digikam, but AFAIK it does not support offline pictures.


No it doesn't (and it's not the only one with this problem). Any program that forces me to store all the pics in the same folder just won't work for me.

cheers

tyto

---

### Post by Martin-Herrmann on 2008-04-21
> **tyto_alba said:**
> I tried Mapivi some time (half a year?) ago, couldn't get it to work properly on my setup :-(

Did you try the Perl variant or the Linux executable of Mapivi?
Any error messages that could help? What exactly didn't work? Maybe I can help you.

You will find Ubuntu installation information here: [http://ubuntuforums.org/mapivi-install]("http://ubuntuforums.org/showthread.php?t=130912&highlight=mapivi")

> **tyto_alba said:**
> I'm seriously thinking of archiving all my pics in jpeg. - Smaller files, easier to handle, and a good chance that I will still be able to read them in 30 years time ... Maybe now would be a good time to start the conversion?

I would say it is a good idea to archive an additional JPEG for the reasons you mentioned. Anyhow I would not delete the originals (e.g. RAW files).

> **tyto_alba said:**
> No it doesn't (and it's not the only one with this problem). Any program that forces me to store all the pics in the same folder just won't work for me.

Same for me, but as far as I know both Digicam and F-Spot support managing pictures in place in their recent versions, don't they?

Regards
         Martin

---

### Post by MetalMusicAddict on 2008-04-21
[jhead]("http://http://www.sentex.net/~mwandel/jhead"), [ExifTool]("http://owl.phy.queensu.ca/~phil/exiftool"), [ExiFlow]("http://exiflow.sourceforge.net/wiki/Main_Page") and [ExifTagger]("http://dague.org/ExifTagger") are the few I can think of right now. I'll look for others.

---

