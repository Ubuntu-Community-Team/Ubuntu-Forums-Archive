---
title: "IMDB script not grabbing posters"
date: 2008-04-29
forum: Mythbuntu
---

### Post by murbanci on 2008-04-29
For some reason the IMDB script for Mythvideo is not grabbing the posters from IMDB.  It gets all the other information like length, date, and synopsis.  It had been working in the past.  I think it has something to do with updating to the .22 version but not sure.  Anyone have any ideas?

Update: Submitting a picture on mythweb by clicking edit and uploading a picture, will not work either.

---

### Post by Dumdideldum on 2008-05-02
> **murbanci said:**
> For some reason the IMDB script for Mythvideo is not grabbing the posters from IMDB.  It gets all the other information like length, date, and synopsis.  It had been working in the past.  I think it has something to do with updating to the .22 version but not sure.  Anyone have any ideas?

Update: Submitting a picture on mythweb by clicking edit and uploading a picture, will not work either.

copy that

Update:
Setting /home/yourusername/.mythtv and /home/yourusername/.mythtv/MythVideo to dirty 777 solves the problem. (Tested with uploading through mythweb), depending on, where you have set the path to covers.

---

### Post by Archmage on 2008-05-02
> **murbanci said:**
> I think it has something to do with updating to the .22 version but not sure.

Since this is the new development branche, I would expect a lot of new problems/breckage till it is released.

---

### Post by Harlequin on 2008-12-07
> **Archmage said:**
> Since this is the new development branche, I would expect a lot of new problems/breckage till it is released.

The imdb.pl script is no longer supported.  Imdb have decided that the scraping of their site by mythtv constitutes a breach of their site policy.  .22 sees the abandonment of that script.  There are other options starting to float about now but I am yet to find a good replacement...

---

