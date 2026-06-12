---
title: "Program to edit certain EXIF metadata."
date: 2009-04-07
forum: Multimedia Software
---

### Post by studentidiot on 2009-04-07
Can anyone point me towards a program that can edit that metadata tag that defines what program the photo was created in?

 All the programs I've tried have been unable to do this.

Thanks guys!

---

### Post by lovinglinux on 2009-04-07
[http://owl.phy.queensu.ca/~phil/exiftool/](http://owl.phy.queensu.ca/~phil/exiftool/)

BTW, took 15 seconds to find that program using Google  ;)

More options at [http://www.digital-photo-software-guide.com/exif-editor.html](http://www.digital-photo-software-guide.com/exif-editor.html)

---

### Post by studentidiot on 2009-04-08
I don't use random programs from a small page on a google search.

I was hoping someone here knew what they were talking about.

---

### Post by lovinglinux on 2009-04-08
> **studentidiot said:**
> I don't use random programs from a small page on a google search.

I was hoping someone here knew what they were talking about.

It's a good practice to install programs only from repositories, but "a small page on a google search" can provide additional information and support for a program already available through official channels, which is the case with ExifTools - a popular application, that is available through the Universe repositories. Additionally, due to it's efficient algorithm, searching an application or a forum post with Google can be pretty easy. Try including *site:ubuntuforums.org* in your search string. For example the search string "*exif edit site:ubuntuforums.org*" gives you 451 posts from these forums with the words *exif* and *edit*.

To install ExifTool run the following command:

```
sudo apt-get install libimage-exiftool-perl
```

or go to Synaptic and search for *libimage-exiftool-perl* then mark the package for installation.

To know how to use the application run the following command:

```
man exiftool
```

or visit the link I have provided in the previous post.

ExifTool description from Synaptic:
> 
ExifTool is a Perl module with an included command-line application
 for reading and writing meta information in image, audio and video
files. It recognizes EXIF, GPS, IPTC, XMP, JFIF, GeoTIFF, ICC Profile,
Photoshop IRB, FlashPix, AFCP and ID3 meta information as well as the
maker notes of many digital cameras including Canon, Casio, FujiFilm,
JVC/Victor, Kodak, Leaf, Minolta/Konica-Minolta, Nikon, Olympus/Epson,
Panasonic/Leica, Pentax/Asahi, Ricoh, Sanyo and Sigma/Foveon.

Isn't it exactly what you need?

---

### Post by studentidiot on 2009-04-08
Mother of God, that's great. 

Thanks, very, very, much!

---

### Post by stani on 2009-06-27
Hi,
I'm developing a graphical program for batch editing exif metadata. It will be available as the image inspector in Phatch . In the current Phatch there is already the image inspector, but it is read only. The new version will be able to write exif tags in batch (with the write tag action) or by hand in a spreadsheet (see screenshot). 

I am looking for volunteers to test the application. You can read more about it here:
[http://ubuntuforums.org/showthread.php?t=1178224](http://ubuntuforums.org/showthread.php?t=1178224)

---

### Post by lovinglinux on 2009-06-28
> **stani said:**
> Hi,
I'm developing a graphical program for batch editing exif metadata. It will be available as the image inspector in Phatch . In the current Phatch there is already the image inspector, but it is read only. The new version will be able to write exif tags in batch (with the write tag action) or by hand in a spreadsheet (see screenshot). 

I am looking for volunteers to test the application. You can read more about it here:
[http://ubuntuforums.org/showthread.php?t=1178224](http://ubuntuforums.org/showthread.php?t=1178224)

Thanks for the tip and congratulations for your work. Phatch was already an excellent batch tool, but now with EXIF and IPTC supper is really a must-have tool.

---

