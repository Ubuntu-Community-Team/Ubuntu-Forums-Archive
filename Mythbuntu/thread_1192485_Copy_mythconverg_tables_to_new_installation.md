---
title: "Copy mythconverg tables to new installation"
date: 2009-06-20
forum: Mythbuntu
---

### Post by roundhay on 2009-06-20
I have installed a fresh version on mythbuntu 9.04 and want to copy my dtv_multiplex & channel tables from my old mythbuntu installation to my new installation. the installations are on different hard drives.

Does anyone know the best way to do this? i would like ti use phpmyadim to do this as i am not confident with mysql commands

---

### Post by ian dobson on 2009-06-20
Hi,

Just install myth as normal after exporting the CaptureCard,CardInput,Channels and dtv_multiplex in phpadmin (option export) and just reimport the same way.

Maybe do a backup of the entire table before starting.

Regards
Ian Dobson

---

### Post by roundhay on 2009-06-20
when I try to export as an sql file phpmyadmin just displays the table in mysql format in a browser window, it doesn't dump a file I can copy to the other system to reinstall?

How can I get a file I can import?

I can export as an open office spread sheet or a text file but I'm not sure if I can reimport files in this format?

---

### Post by funkydan2 on 2009-06-21
It's all in the mythtv docs.  Really easy to follow, I did it myself the other weekend.

[http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.5](http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.5)

(or have a look at section 23.7, that might be more what you want to do)

---

### Post by roundhay on 2009-06-22
I managed to do what I wanted by choosing the field e.g. channel using phpmyadim and exporting as a csv file. This displayed the csv data in a windown inside phmyadim. I copied this data and pasted it into a text file which I save as channel.csv I did the same for the dtv_multiplex field

I then moved these 2 csv files to the HDD with my new mythtv insallation and using phpmyadmin I imported them. this worked and and I managed to import both fields to my new mythconverg database

The other methids described may work  but I am not confident enough to try them.

---

