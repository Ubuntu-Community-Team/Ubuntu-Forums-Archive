---
title: "merge mkv files from command line"
date: 2009-09-13
forum: Multimedia Software
---

### Post by pythonscript on 2009-09-13
I have several mkv files that are all part of one movie, named pl.mkv.001, pl.mkv.002, etc, and I'm trying to merge one. However... only the first one plays in vlc/totem, etc, so how do I merge these? I tried installing mkvtoolnix and its gui, but when I add movies to the gui interface, they all come back corrupted, even the first one, which plays just fine. How do I merge these? Thanks!

---

### Post by andrew.46 on 2009-09-13
Hi pythonscript,

> **pythonscript said:**
> I have several mkv files that are all part of one movie, named pl.mkv.001, pl.mkv.002, etc, and I'm trying to merge one.

I wonder if what you are actually after is the *append* command? This will be true if you are trying to join your files end to end rather than *merge* them into a single file. It can be done from the commandline but I attach a screenshot to demonstrate the gui option. mkvtoolnix will be a little fussy about which files it can append though...

The only alarm bell that rings a little is the naming convention of your files, these do not represent sections of a multi-part archive such as is seen with rar?

Andrew

---

### Post by pythonscript on 2009-09-13
Sorry I wasn't clear. I am talking about the append command, but when I click that, mkvtoolnix can't find the files. I can only add them to the list by dragging them into the window. Also, I thought that the files might be part of a split archive, but I can't extract them, and none of them say anything about rar/7z, zip, tar, etc. The first file (pl.mkv.001) plays fine; it's the rest that won't, so I'm at a loss.

---

### Post by pedja_portugalac on 2009-09-13
Did you download that files from somewhere like rapidshare etc? Maybe they are splited by uploader using some program like HJ-Split? I have seen that a lot in the past. If it's the case here is link for free spliter and joiner (you must have java installed): [http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)

---

### Post by andrew.46 on 2009-09-13
Hi pythonscript,

> **pythonscript said:**
> Sorry I wasn't clear. I am talking about the append command, but when I click that, mkvtoolnix can't find the files.

Then the problem is clear: mkvtoolnix only allows the addition of 'Supported Media Files' and based on the suffix of .001 etc this will not happen. The commandline usage will probably fail as well unfortunately:

```
mkvmerge -o newfile.mkv part1.mkv +part2.mkv
```

which I have lifted from the man pages. I suspect you will need to have a look at joining these files another way, is this from a torrent?

Andrew

---

### Post by pythonscript on 2009-09-13
No, these files are not from a torrent, but they're from a set of file sharing links (megaupload, I believe). I tried renaming them (dropping the .002, etc, suffix) too, but to no avail. Command line arguments yield this error message:

```
pythonscript@pythonlaptop:~/Desktop/pl$ mkvmerge -o pans.mkv PL-uSk.mkv.001 +PL-uSk.mkv.002
mkvmerge v2.4.1 ('Use Me') built on Dec 13 2008 21:03:46
'PL-uSk.mkv.001': Using the Matroska demultiplexer.
'PL-uSk.mkv.002': Using the AVC/h.264 ES demultiplexer.
'PL-uSk.mkv.001' track 1: Using the MPEG-4 part 10 (AVC) video output module.
'PL-uSk.mkv.001' track 2: Using the AAC output module.
'PL-uSk.mkv.001' track 3: Using the text subtitle output module.
'PL-uSk.mkv.002' track 0: Using the MPEG-4 part 10 ES video output module.
No append mapping was given for the file no. 1 ('PL-uSk.mkv.002'). A default mapping of 1:0:0:0 will be used instead. Please keep that in mind if mkvmerge aborts complaining about invalid '--append-to' options.
Error: The file no. 0 ('PL-uSk.mkv.001') does not contain a track with the ID 0, or that track is not to be copied. Therefore no track can be appended to it. The argument for '--append-to' was invalid.
pythonscript@pythonlaptop:~/Desktop/pl$ 

```

---

### Post by andrew.46 on 2009-09-13
Hi pythonscript,

> **pythonscript said:**
> No, these files are not from a torrent, but they're from a set of file sharing links (megaupload, I believe).

It would be nice to see the original files, can you post a link? Feel free to send me the link by PM if that is better.

All the best,

Andrew

---

### Post by armitage1337 on 2009-09-20
> **pythonscript said:**
> I have several mkv files that are all part of one movie, named pl.mkv.001, pl.mkv.002, etc, and I'm trying to merge one. However... only the first one plays in vlc/totem, etc, so how do I merge these? I tried installing mkvtoolnix and its gui, but when I add movies to the gui interface, they all come back corrupted, even the first one, which plays just fine. How do I merge these? Thanks!

You don't need mkvtoolnix or anything. The files were just split at the binary level if they follow the *.001, *.002, *.003 pattern. You can use the following command for any filetype (just change the name as needed):```
cat pl.mkv.* > pl.mkv
```

---

### Post by ruchita.sen on 2010-07-16
Thankyou very much it worked.... I installed mkvtoolkit and what not... it was of great help...

---

### Post by Jose Catre-Vandis on 2010-07-24
For info, it looks like the files you downloaded were split up by a program called **hjsplit** (or **lxsplit**). There is a nice java applet to do the gui work for you of joining all the files back together

---

### Post by hasanujjaman on 2011-02-04
Just download "HJ-Split" from the following link..........
  [http://www.hjsplit.org/linux/](http://www.hjsplit.org/linux/)

---

### Post by cyberspeeyush on 2011-03-31
thanks a lot.. it worked perfectly..

---

### Post by cyberspeeyush on 2011-03-31
thanks a lot.. it worked perfectly..

---

### Post by emilywind on 2011-08-17
I recently ran into this issue, and would like to highlight armitage1337's method of joining the files. It does not require you to download anything as it uses a standard linux command; cat.

```
cat filename.mkv.* > filename.mkv
```

For a bit of a background for those wanting to learn the terminal a bit: cat reads the contents of a file, * means anything so it will read all files starting with filename.mkv., and > directs the output into a file (think pacman eating the file(s) and pooping it/them back out :) ).

Worked just fine for my recent encounter with a file of this sort.

---

### Post by scottro on 2012-09-23
Even though this thread is several years old now, I too want to say thank you--I hadn't realized that the 001, 002 and so on meant it was split at binary level. In on of those fairly meaningless coincidences, Sept. 20th was my birthday, so the answer was posted on my birthday.  So, let me add my thanks to Armitage.

---

