---
title: "Problem creating a Video DVD using dvdauthor with multiple videos"
date: 2008-09-01
forum: Multimedia Software
---

### Post by thychamp on 2008-09-01
This is my first time trying to take my home movies that are in avi format and create a video DVD with them.  I am using tovid to convert the avi files to mpg.  That worked perfect.  I then created the xml file that dvdauthor needs by using 'makexml' script.  This created the following xml:

```
<dvdauthor dest="FamilyTripDisc">
<!-- makexml 0.31 -->
<vmgm>
</vmgm>
<titleset>
  <titles>
    <video  />
    <pgc>
      <vob file="VID00025.tovid_encoded.mpg" chapters="00:00:00" />
    </pgc>
    <pgc>
      <vob file="VID00026.tovid_encoded.mpg" chapters="00:00:00" />
    </pgc>
    <pgc>
      <vob file="VID00027.tovid_encoded.mpg" chapters="00:00:00" />
    </pgc>
    <pgc>
      <vob file="VID00028.tovid_encoded.mpg" chapters="00:00:00" />
    </pgc>
    <pgc>
      <vob file="VID00029.tovid_encoded.mpg" chapters="00:00:00" />
    </pgc>
  </titles>
</titleset>
</dvdauthor>
```

I then run the following command:

```
dvdauthor -x FamilyTripDisc.xml
```

It successfully creates the dvd structured folders and files.  The audio_ts and video_ts.  The problem is when I watch the newly created dvd on the computer (using VLC) or burned to a disc on a dvd player, the video stops after the first mpg and freezes.

What am I doing wrong?

---

### Post by thychamp on 2008-09-02
I figured out what was wrong.  The makexml script does not generate the correct xml file for dvdauthor.  After doing some research on the different ways to configure the xml, I found the following xml will make it that the video will proceed after the first mpg:

```
<dvdauthor dest="FamilyTripDisc">
<vmgm>
</vmgm>
<titleset>
  <titles>
    <video  />
    <pgc>
      <vob file="VID00025.tovid_encoded.mpg"  />
      <vob file="VID00026.tovid_encoded.mpg"  />
      <vob file="VID00027.tovid_encoded.mpg"  />
      <vob file="VID00028.tovid_encoded.mpg"  />
      <vob file="VID00029.tovid_encoded.mpg"  />
  </pgc>
  </titles>
</titleset>
</dvdauthor>
```

:KS

---

