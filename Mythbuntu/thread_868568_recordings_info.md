---
title: "recordings info"
date: 2008-07-24
forum: Mythbuntu
---

### Post by misterspider on 2008-07-24
I created a folder /mythtv for my recordings, and have folders like
/mythtv/recordings/Movies
/mythtv/recordings/Documentaries
within here. The files are just long sequences of numbers specifying recording date and time etc, but in Myth, when i select "watch recordings" it has detailed information about the file like Name of movie etc.

Where does it store this information? I would like to change the directory of one file and dont want to lose the program info.

---

### Post by tgm4883 on 2008-07-24
This information is stored in the database.  Look in the recorded table

---

### Post by misterspider on 2008-07-26
Thanks. 
So can i just edit this table and move a recording, even to a new machine running myth?

---

### Post by nickrout on 2008-07-26
no because there are other relevant tables too like the markup table.

---

### Post by jlagrone on 2008-07-26
There's a script that you can add recordings to a new box (or if you downloaded them or whatever).  It is included in the install.  You want

```
/usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz
```

Copy it to your home folder, extract it, and make it executable

```
cp /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz ~/
gzip -d ~/myth.rebuilddatabase.pl.gz
chmod a+x ~/myth.rebuilddatabase.pl.gz

```

Then copy the video files to where ever you want them and then run the script.  You'll have to pass it your database password and tell it where you put the files.  When it finds a file it'll ask you a couple of questions about it and you'll be set.  You can get more info here [http://www.mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl]("http://www.mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl").

For reference, this works with the default mythbuntu settings, if you have a different database name or something else out of the ordinary you may have to pass it more options
```
~/myth.rebuilddatabase.pl --pass <database password> --dir <video location>
```

---

### Post by tgm4883 on 2008-07-26
An easier way to move recordings to a new machine is to use mytharchive and export them in native mythtv format.  You should retain all show info this way

---

