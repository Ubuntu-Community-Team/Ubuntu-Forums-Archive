---
title: "how do I add chapters in dvdauthor cli"
date: 2008-05-05
forum: Multimedia Software
---

### Post by hurtstotalktoyou on 2008-05-05
Hi, all.

When I author a DVD from an mpeg file, I've always used dvdauthor in terminal.  The commands I use are as follows:

> dvdauthor -o /path/to/dvd/folder/ -t movie.mpg
> dvdauthor -o /path/to/dvd/folder/ -T

This creates a basic DVD, but without chapters--which is fine, since I usually don't want chapters.  This time, though, I'd like to have chapters at every 15 minutes of the movie.  Does anyone know what parameters I add to do this?

Any help would be much appreciated.  Thanks in advance!

---

### Post by yabbies on 2008-05-05
<dvdauthor dest="your_file">
<!-- makexml 0.31 -->
<vmgm>
</vmgm>
&#8722;
<titleset>
&#8722;
<titles>
<video/>
&#8722;
<pgc>
<vob file="your_file.mpg"
chapters="00:00:00,00:05:00,00:10:00,00:15:00"/>
</pgc>
</titles>
</titleset>
</dvdauthor>

this is the xml file format that will create chapters
open a text editor and save with an extension of .xml

an easier way is to use Tovid
it's not in the repos but you can install it from here
[http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu]("http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu")

then simply use the command 

```
makexml YOUR_FILE.mpg -out YOUR_FILE
```

it will spit out an xml file with 5 minute interval chapters
and then you can simply create a dvd directory and burn to disc

pop in dvd

```
makedvd -burn YOUR_FILE.xml
```

---

### Post by kitrule on 2010-04-13
man dvdauthor

-c chapterpts

--chapters=chapterpts

Specifies a comma (,) separated list of chapter markers. Each marker is of the form [[h:]mm:]ss[.frac] and is relative to the SCR of the next file listed  (independent of any timestamp transposing that occurs within dvdauthor). The chapter markers ONLY apply to the next file listed. Defaults to 0.


e.g. "dvdauthor -o /path/to/dvd/folder/ -t -c 0,5:0 movie.mpg"
p.s. 0 should be first in the list.

---

### Post by mukund_linux on 2010-06-21
hii,,,

i am trying to author a dvd using dvdauthor.my subtitle file is:

[B][SIZE=3]<subpictures>
  <stream>
    <spu
     force="yes"
     start="00:00:00.00"
     image="menu1.png"
     select="menu2.png"
     highlight="menu2.png"
     autooutline="infer"
     outlinewidth="6"
     autoorder="rows"
    />
  </stream>
</subpictures>[/SIZE][/B]

I then used the spumux command

spumux menu.xml < out1.mpg > out_final2.mpg


my dvd authoring file is:

[SIZE=4][B]<dvdauthor dest = "DVD7">
  <vmgm> 
    <menus> 
      <pgc> 
        <vob file="out_final2.mpg" pause="inf"/> 
         <button>jump title 1;</button>                
         <button>jump title 2;</button>                      
    </pgc> 
    </menus> 
  </vmgm> 
<titleset>
 <titles>
   <pgc>
     <vob file = "out.mpg" /> 
     <post> call vmgm menu 1; </post>
 </pgc> 
   <pgc>
     <vob file = "out.mpg" /> 
     <post> call vmgm menu 1; </post>
 </pgc>
 </titles>
</titleset>
</dvdauthor>
[/B][/SIZE]
 when i am sing the command 

dvdauthor -x main1.xml

but i am getting the error:
[B]
[SIZE=2]DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_IN
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing out.mpg...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
ERR:  SCR moves backwards, remultiplex input.[/SIZE]
[/B]

please guide me as what to do???

---

### Post by dvdbrtrnd on 2011-08-04
Hi,

First post here (and one year later), so please, take this reply as a reminder :

dvdauthor is a nice software but you have to give to it a fully compliant mpeg with VOBUS inside (a VOB file in fact).

You can do this when you mux your mpeg with :

mplex -f8 input.ac3 input.m2v -o output.mpg

NOTES :
A)"-f8" is the most important argument here
B)input.m2v must have clean headers 
try the command "file input.m2v". It have to return a complet string like this : "input.m2v: MPEG sequence, v2, MP@ML interlaced Y'CbCr 4:2:0 video, CCIR/ITU PAL 625, 16:9, 25 fps"

David

---

