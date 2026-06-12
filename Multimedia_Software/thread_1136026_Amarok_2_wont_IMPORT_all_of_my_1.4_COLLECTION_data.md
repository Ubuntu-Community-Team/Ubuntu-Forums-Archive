---
title: "Amarok 2 wont IMPORT all of my 1.4 COLLECTION database."
date: 2009-04-24
forum: Multimedia Software
---

### Post by BrowneR on 2009-04-24
I have just fresh installed 9.04 Jaunty and am now using Amarok 2 instead of Amarok 1.4.

I have tried to import my old Amarok 1.4 collection database but it only adds 4 files out of my 20,000+ collection!

First I installed the libqt4-sql-sqlite package and then copied my old collection.db to the amarok settings directory.

I can then select "import collection" from within Amaroks settings dialogue and follow the wizard to import the data. It then says "Migrating" and displays a couple of tracks it finds. Within a few seconds it reports it has finished despite the collection.db being over 32Mb!?

Anyone having similar issues? Suggestions would be appreciated.

Cheers

---

### Post by dmatej on 2009-05-01
Yes, I have the same problem. And any following attempt to repeat the import results in error:

Importing downloaded album art
Failed: No tracks were imported

---

### Post by BrowneR on 2009-05-01
dmatej:

I have found what seems to be a work around for this issue.

Start off by removing any exisiting amarok 2 collection database (or just delete ~/.kde/share/apps/amarok/).

Then setup a new collection in amarok 2 selecting the folders which contain your music files and let it scan through your music collection. When it is done scanning then try to import your old amarok 1.4 collection using the wizard.

For me amarok then scanned through and imported my ratings etc. for songs where they existed. This meant it only reported importing ~10,000 songs out of my 20,000+ collection but I think thats because they were the only files which I have got around to adding ratings too. The others were essentially unchanged in the new collection if that makes sense.

Hope that works for you too.

---

