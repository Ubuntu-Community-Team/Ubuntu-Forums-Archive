---
title: "combine grabbers dk and swe. error code 256"
date: 2007-12-04
forum: Mythbuntu
---

### Post by weiser on 2007-12-04
Hey,

I'm running Mythbuntu with great happynes. 

but I have a big problem with combine grabber.

I combine tv_grab_dk and tv_grab_db_swe.

When I set the grabbers up, it all work fine, but after that it stop to get information from dk. And give an error: FAILED: xmltv returned error code 256.

Hope somebody kan help me....


-- 
Weiser

---

### Post by axelsvag on 2007-12-07
I got about the same problem with one exception. I just get danish info two days ahead instead of 5 days is supposed to work. Have you looked in the xmltv file and found the danish channels?

---

### Post by Nikas on 2007-12-07
I do this in a cronjob every night:

rm -f /tmp/dk.xml

/usr/bin/tv_grab_dk --days 6 --output /tmp/dk.xml

/usr/bin/mythfilldatabase --no-delete --update --quiet --file 1 0 /tmp/dk.xml

mythfilldatabase --max-days 14 --quiet

This gives me 6 days from the danish source and 14 from the swedish.
I only want listings for TCM from danmark because that channel is missing in the swedish source.

---

