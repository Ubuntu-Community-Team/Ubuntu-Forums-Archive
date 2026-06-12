---
title: "How do I get metadata for TV Show Specials from TheTVDB"
date: 2010-02-27
forum: Mythbuntu
---

### Post by kyfehr on 2010-02-27
I have been trying every naming convention to get Specials for TV Shows to download metadata. Specifically I am trying to get the metadata for Doctor Who (2005) specials. They are on the website, but doing a metadata look-up in Myth .22 either the general metadata look-up or the TV show episode/subtitle option does not find it.

The files are named Doctor Who 2005 - special name here.avi

The naming convention is the same for the episodes Doctor Who 2005 - S**E** - subtitle.avi and they are found first try.

Should I be putting S00E00 in the name for the specials???

Thanks

---

### Post by nickrout on 2010-03-01
This is how xbmc (which also uses thetvdb.com) handles it:

>  TV Show Specials

Special episodes are currently supported with TheTVDB.com scraper. In order for the XBMC scraper regular expressions to recognize them, they should be part of season 0. (Specials naming order can be observed in the Specials Season of the relevant TV show at TheTVDB.com).

Example
    Black Adder's Christmas Carol should have a file name that matches season 0 episode 2 (e.g. contain s00e02). 



See [http://wiki.xbmc.org/index.php?title=TV_Shows_%28Video_Library%29](http://wiki.xbmc.org/index.php?title=TV_Shows_%28Video_Library%29)

Dunno if that will help  on myth, but it may be worth a try.

---

### Post by kyfehr on 2010-03-03
Thanks nickrout I will give that a try.

---

### Post by canga on 2010-03-04
Thanks kyfer for raising the problem - I have been puzzling over the same thing.

Following on from nickrout's suggestion I looked at thetvdb.com wiki and found that special episodes are coded as season 0.  So, looking at the season 1 page for Dr Who (2005), you can then click on the link to previous season and up come all of the special episodes (except for Music and Monsters, which seems to be missing).

Back to the watch videos page in mythtv and select a special episode in Dr Who, such as "The Runaway Bride".  Bring up the edit metadata screen and set the series title to "Doctor Who (2005)", the subtitle to "The Runaway Bride", the season to 0 and the episode to 4.  Select done to exit the screen and save the changes.  Press w to download metadata and it works.

Now, if I could find a way of keeping the paths to banners, coverart etc after scanning for changes to the video collection then I would be a happy chap.

---

