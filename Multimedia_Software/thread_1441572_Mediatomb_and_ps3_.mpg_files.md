---
title: "Mediatomb and ps3 .mpg files"
date: 2010-03-28
forum: Multimedia Software
---

### Post by Sirsteveo on 2010-03-28
So I have mediatomb running and I have a bunch of videos I watch on my ps3 but there all .avi files but I have other videos that are .mpg files the only files that show up on my ps3 are the .avi files the .mpg files dont show up. Does mediatomb not work with .mpg or what do I need to do to make it work?

---

### Post by JoKeR123 on 2010-03-29
I'm pretty sure that the PS3 itself isn't compatible with the .mpg files.

Try putting it on a flash drive then play on a PS3 to see if its MediaTomb or what..

---

### Post by 21jeremy21 on 2010-05-13
Malarkey!

It does support .mpg files. I used to use mkv2vob through virtualbox under win xp to convert my .mkv files and stream them using mediatomb, and it outputs .mpg files

Since doing a format and upgrading to 10.04, I can't get it to show my .mpg files on the ps3 xmb thru mediatomb.

I noticed on the mediatomb web gui that my .mpg files had a weird mimetype (application/octlet or something similar). Upon checking mediatomb's config.xml i noticed in the "<extensions-mimetype..." section, there is no entry for .mpg files.

How I wish I had backed up my old config.xml file !! :mad: lol

I'll be back when I figure this out, hopefully soon.

---

### Post by 21jeremy21 on 2010-05-13
Add the following line to the 

<mappings>
      <extension-mimetype ignore-unknown="no">

section of ~/.mediatomb/config.xml:

```
<map from="mpg" to="video/mpeg"/>
```



After restarting mediatomb, any new mpg files added to the database should now get the right class and mimetype automagically. 



To fix the class and mimetype of the existing mpg files in your database, either delete your database (~/.mediatomb/mediatomb.db) and add your files again, or change the class/mimetype of each existing mpg file individually.


To change an individual file, go into the mediatomb web gui (address can be found by running mediatomb from terminal)


Browse your database (tab on upper left) to find the mpg file in question. Then click the "edit" logo for that file. Change the "class" field to ```
object.item.videoItem
``` and the "mimetype" field to ```
video/mpeg
``` . Restart mediatomb and away you go!


:guitar:

---

### Post by thomasv2 on 2010-09-21
Thanks for reporting back!

This just solved the exact problem i had!

ThomasV2

---

