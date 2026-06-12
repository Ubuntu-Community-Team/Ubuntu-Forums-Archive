---
title: "New uShare patch : Xbox 360 Music / Multiple Content Directoris"
date: 2008-05-10
forum: Multimedia Software
---

### Post by NeToU on 2008-05-10
Hey everyone,

I am now at the end of my first full week of using Ubuntu (and only Ubuntu) and to celebrate I have written a modified version of uShare with some bug fixes so that it better supports the playing of music on the Xbox 360 (particularly the Play All feature).

Please let me know what you think and whether it works for anyone else (which would be nice), I don't any other uPnP based servers to test it out on other than my 360.

Full details and the source code download are available on my website [[COLOR="Blue"]_www.NeToU.co.uk_[/COLOR]]("http://www.NeToU.co.uk") but here is a summary of the changes:

**uShare_NeToU Summary:**

    * Users can view, select and play their music files through the Xbox 360
    * The “Play All” feature should be working correctly also
    * Multiple Content directories now supported (added in ushare.conf or on the command line with the -c argument) If you have videos/music files scattered around your PC (eg, accross multiple drives) you can now access all of them from the 360.

***Notes:***

    * There is still no metadata support within uShare so music will not be sorted by album/artist etc
    * When I was testing this out I noticed a bug that restricts the user from browsing uShares media while a file was being played, I have yet to look into this however stopping the file will restore functionality.

---

### Post by NeToU on 2008-05-10
Posted this to the Geexbox forums as well since they maintain the main development.

Also, is there any way to edit my thread title? Just realised I missed the 'e' in directories :(

---

