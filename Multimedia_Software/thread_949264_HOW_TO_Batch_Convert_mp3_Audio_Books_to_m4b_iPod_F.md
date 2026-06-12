---
title: "HOW TO Batch Convert mp3 Audio Books to m4b iPod Format"
date: 2008-10-16
forum: Multimedia Software
---

### Post by jdforsythe on 2008-10-16
First of all, special thanks goes out to member Sir_Yaro who wrote the original "to m4b" conversion script that I modified to create this. That thread (and script) are available at: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=180073](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=180073)

Okay, I modified that script to be able to batch convert a bunch of mp3 audio books in my collection to iPod m4b format and I figured it might be useful to someone else. This currently only supports mp3 to m4b conversion. The original script converted other audio files to wav then to m4b which takes a lot of space, and I don't have anything other than mp3 books so I removed that functionality, but if enough people want that added back in, I would be willing to make a second version. I'm just not sure how popular flac or ogg audio books are :)

The zip file includes two scripts:
mp3-to-m4b
mp3-to-m4b-batch

Download the zip and open a terminal in the directory you downloaded to, then do the following:
```

unzip mp3-to-m4b-batch.zip
chmod a+x mp3-to-m4b
chmod a+x mp3-to-m4b-batch

```

Move the mp3-to-m4b script to a permanent spot, for instance:
```

mv mp3-to-m4b ~/bin

```

The mp3-to-m4b-batch file needs to be edited. Instructions are included in the file. This is where you specify the locations of the various audio books and the tags (title, author, year) and filename for the final m4b file. Script has the ability to split the book into multiple m4b files.

A sample mp3-to-m4b-batch file might look like this:
```

#!/bin/bash
##
## cd /PATHTOBOOK
## mp3-to-m4b OUTFILE "TITLE" "AUTHOR" YEAR y/n [#]
##   leave off the .m4b extension from OUTFILE
##     i.e. AAIW would yield AAIW.m4b, AAIW.m4b would yield AAIW.m4b.m4b
##   y,n - whether to split into multiple m4b files (appends " #" to filename)
##   [#] optional, filesize in bytes of original mp3 files for each file
##       so this isn't final size of m4b but a measure of original mp3s
##       default is 150000000 (150MB)

cd /data/audiobooks/"Alices Adventures in Wonderland"
mp3-to-m4b AAIW "Alice's Adventures in Wonderland" "Lewis Carroll" 1865 y 120000000

cd /data/audiobooks/"Book 2"
mp3-to-m4b BOOK2 "Book 2" "Author Name" 2008 y

cd /data/audiobooks/"Book Three"
mp3-to-m4b BOOKTHREE "Book Three" "Author Three" 2003 n

```

Just include another set of cd & mp3-to-m4b lines for each book and fill in the information. Then navigate to where the mp3-to-m4b-batch script is in a terminal and execute:
```

./mp3-to-m4b-batch

```

Then wait awhile! I hope you find it useful.

Edit: Forgot to mention, the first time it is run, it will check for the needed packages and ask if you want to install them, if they aren't all present. After the packages are installed, it is completely automated.

---

### Post by l33tpolicywonk on 2010-03-26
It's worth noting: If you don't care about uniting the files and just want your MP3 files to display in order in the Audiobooks section, you can right click on mp3 files with gtkpod and designate them "Podcast" or "Audiobook". Works for me.

---

