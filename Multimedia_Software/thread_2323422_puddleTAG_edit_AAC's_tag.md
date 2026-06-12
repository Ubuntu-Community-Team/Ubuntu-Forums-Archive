---
title: "puddleTAG edit AAC's tag"
date: 2016-05-05
forum: Multimedia Software
---

### Post by czgirb on 2016-05-05
**Ubuntu 14.04LTS in Compaq CQ40-328TU**

currently, i use  **puddleTAG 1.1.1 with Qt 4.8.6**
lately i found there are some **AAC** (**not all AAC**) is unable to be processed and i don't know why ... process will stuck and ended with high CPU usage.
so i was forced to give ubuntu's default, **easyTAG** a try ... and it's OK.

is there an error with my **puddleTAG**? how can i fix it?
i love the way **puddleTAG** process my file and i much prefer it to **easyTAG**
cos i don't know how to **add field** in **easyTAG** ... :D :D :D ... i wish to add "**performer**" field ... [FONT=times new roman][I]googling already ... but found nothing
[/I][/FONT][B]
[SIZE=5]Thank you[/SIZE][/B]

---

### Post by czgirb on 2016-06-09
today, i found there is several **AAC file** within my computer which **unable** to do an edit ... both via **PuddleTAG** and **EasyTAG** ... why?

is there an error with my **puddleTAG** or **EasyTAG**? how can i fix it?  [FONT=times new roman]*googling already ... but found nothing*[/FONT]

---

### Post by X-RED_Tech on 2016-06-09
Have you tried to edit it in a different computer/OS? You can do that with an app in Android or iOS... Then, if the symptom is the same, you know the problem is in the files, not the software.

---

### Post by shantiq on 2016-06-10
hi cz   some files in aac/m4a   can be difficult

maybe try command line AtomicParsley  all these options >>>>


install   ```
sudo apt-get install atomicparsley
```


**EDIT**:  then i realized it does not have "performer"    will leave info here anyway as reference




```
AtomicParsley -h

AtomicParlsey sets metadata into MPEG-4 files & derivatives supporting 3 tag
 schemes: iTunes-style, 3GPP assets & ISO defined copyright notifications.

AtomicParlsey quick help for setting iTunes-style metadata into MPEG-4 files.

General usage examples:
  AtomicParsley /path/to.mp4 -T 1
  AtomicParsley /path/to.mp4 -t +
  AtomicParsley /path/to.mp4 --artist "Me" --artwork /path/to/art.jpg
  Atomicparsley /path/to.mp4 --albumArtist "You" --podcastFlag true
  Atomicparsley /path/to.mp4 --stik "TV Show" --advisory explicit

Getting information about the file & tags:
  -T  --test        Test file for mpeg4-ishness & print atom tree
  -t  --textdata    Prints tags embedded within the file
  -E  --extractPix  Extracts pix to the same folder as the mpeg-4 file

Setting iTunes-style metadata tags
  --artist       (string)     Set the artist tag
  --title        (string)     Set the title tag
  --album        (string)     Set the album tag
  --genre        (string)     Genre tag (see --longhelp for more info)
  --tracknum     (num)[/tot]  Track number (or track number/total tracks)
  --disk         (num)[/tot]  Disk number (or disk number/total disks)
  --comment      (string)     Set the comment tag
  --year         (num|UTC)    Year tag (see --longhelp for "Release Date")
  --lyrics       (string)     Set lyrics (not subject to 256 byte limit)
  --lyricsFile   (/path)      Set lyrics to the content of a file
  --composer     (string)     Set the composer tag
  --copyright    (string)     Set the copyright tag
  --grouping     (string)     Set the grouping tag
  --artwork      (/path)      Set a piece of artwork (jpeg or png only)
  --bpm          (number)     Set the tempo/bpm
  --albumArtist  (string)     Set the album artist tag
  --compilation  (boolean)    Set the compilation flag (true or false)
  --hdvideo      (boolean)    Set the hdvideo flag (true or false)
  --advisory     (string*)    Content advisory (*values: 'clean', 'explicit')
  --stik         (string*)    Sets the iTunes "stik" atom (see --longhelp)
  --description  (string)     Set the description tag
  --longdesc     (string)     Set the long description tag
  --storedesc    (string)     Set the store description tag
  --TVNetwork    (string)     Set the TV Network name
  --TVShowName   (string)     Set the TV Show name
  --TVEpisode    (string)     Set the TV episode/production code
  --TVSeasonNum  (number)     Set the TV Season number
  --TVEpisodeNum (number)     Set the TV Episode number
  --podcastFlag  (boolean)    Set the podcast flag (true or false)
  --category     (string)     Sets the podcast category
  --keyword      (string)     Sets the podcast keyword
  --podcastURL   (URL)        Set the podcast feed URL
  --podcastGUID  (URL)        Set the episode's URL tag
  --purchaseDate (UTC)        Set time of purchase
  --encodingTool (string)     Set the name of the encoder
  --encodedBy    (string)     Set the name of the Person/company who encoded the file
  --apID         (string)     Set the Account Name
  --cnID         (number)     Set the iTunes Catalog ID (see --longhelp)
  --geID         (number)     Set the iTunes Genre ID (see --longhelp)
  --xID          (string)     Set the vendor-supplied iTunes xID (see --longhelp)
  --gapless      (boolean)    Set the gapless playback flag
  --contentRating (string*)   Set tv/mpaa rating (see -rDNS-help)


```

if in bulk use this syntax once in the folder EX:

```
for f in *.aac; do AtomicParsley  "$f"  --albumArtist "Franky Boi"    "${f%.aac}.aac"; done 

```

---

### Post by czgirb on 2016-06-10
> **X-RED_Tech said:**
> Have you tried to edit it in a different computer/OS? You can do that with an app in Android or iOS... Then, if the symptom is the same, you know the problem is in the files, not the software.

Today, I've tried to edit the TAG via Foobar ... and re-scan it by PuddleTAG
... and hoopla ... the TAG was edited.
why??? is puddleTAG and easyTAG is not fully compatible with AAC?


**@shantiq**
SORRY ... i don't understand with what you mean
Would you mind to describe it more details?

---

### Post by shantiq on 2016-06-10
ha czgirb I was trying to show another route but it is not a good one for what you want  ....    and now you have done it anyway  so no need to bore you :]

---

### Post by czgirb on 2016-06-10
> **shantiq said:**
> ha czgirb I was trying to show another route but it is not a good one for what you want  ....    and now you have done it anyway  so no need to bore you :]

OMG ... i really really do not understand with what you mean.
please don't misunderstand.
even I already successfully edit the tag, but i still wish that such file was able to be done by my **puddleTAG**.
so i think there must be an error with my puddleTAG.
i still wish there is someone who can tell me how can i fix the problem?

---

