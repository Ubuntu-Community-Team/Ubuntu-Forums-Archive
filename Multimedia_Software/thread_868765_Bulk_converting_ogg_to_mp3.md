---
title: "Bulk converting ogg to mp3"
date: 2008-07-24
forum: Multimedia Software
---

### Post by alephnaught on 2008-07-24
Hi there.

My music collection is a horrible, hideous mess, thrown together over many years by amalgamating the music of my friends as well as my own acquisitions. Now that I'm DJing, I'm starting to regret not having organized things more sensibly from the get go.

Anyway, I have a great mass of oggs tucked among various folders, and I need to convert them all to MP3 for my DJing software to cope with them (and so that various other devices will cooperate). What I need is a program or a script that will search through my music folder and subfolders, find all ogg files, and convert them to an mp3 of an appropriate quality based on the quality of the ogg file. It would ideally then check that the conversion had been successful and delete the original file.

Bonus points if you can figure out a way to scan through and delete all non-music or non-playlist files.

Anyone got any ideas here?

---

### Post by unutbu on 2008-07-24
First install the ffmpeg package:
```

sudo apt-get install ffmpeg
```

Next, save this to a file called ogg2mp3.py
```

#!/usr/bin/env python
import sys
import os
import subprocess

from optparse import OptionParser
parser = OptionParser()
parser.add_option("-s", "--simulate",
                  action="store_true", dest="simulate", default=False,
                  help="simulate")

try:
    (opt, args) = parser.parse_args()
except:
    parser.print_help()
    exit()

argpath=args[0]
for root, dirs, files in os.walk(argpath,False):
    for name in files:
        filename=os.path.join(root, name)
        (shortname, extension) = os.path.splitext(filename)
        newname=shortname+".mp3"
                
        if extension == '.ogg':
            cmd=['ffmpeg', '-sameq', '-i', filename, newname]
            if opt.simulate:
                print " ".join(cmd)
            else:
                try:
                    retcode = subprocess.call(cmd)
                except OSError, e:
                    print >>sys.stderr, "Execution failed:", e
```

Save this to a file called purge.py:

```
#!/usr/bin/env python
"""
purge.py DIR
simulates the removal process so you can see what will be removed.

purge.py --really DIR
removes everything in DIR except files that have extension .mp3 or .m3u
empty subdirectories are also removed
subdirectories which contain mp3 or m3u files are preserved.


This program is dangerous! Be afraid.
"""

import os
from optparse import OptionParser
parser = OptionParser()
parser.add_option("--really",
                  action="store_true", dest="really", default=False,
                  help="really remove files")

soundext = ['.m3u','.mp3']

try:
    (opt, args) = parser.parse_args()
except:
    parser.print_help()
    exit()

argpath=args[0]
for root, dirs, files in os.walk(argpath,False):
    """ Remove files whose extension is not in soundext """
    for name in files:
        filename=os.path.join(root, name)
        (shortname, extension) = os.path.splitext(filename)        
        if extension not in soundext:
            if opt.really:
                os.remove(filename)
            else:
                print "remove %s"%filename
    """ Remove empty directories """
    for dirname in dirs:
        path=os.path.join(root, dirname)
        if opt.really:
            try:
                os.removedirs(path)
            except OSError, e:
                pass
        else:
            print "remove dir %s"%path

```
Make both executable:
```

chmod 755 ogg2mp3.py purge.py
```

I suggest you backup your music before using these scripts. At the very least copy some files with crazy names (spaces, apostrophes, parentheses, unicode characters) into a test directory, and run the follow commands there first. I have tested these scripts myself, but you can never be too careful. Backup!

To convert all .ogg files into .mp3 files:
```

./ogg2mp3.py -s DIR         # This prints the ffmpeg command that will be run
./ogg2mp3.py DIR            # This does the actual conversion
```

where DIR is the path to the directory containing the ogg files. ogg2mp3.py is pretty harmless. No files are every removed. At worst, ffmpeg will fail to convert the ogg into an mp3.

To purge a directory of all files that don't end in .mp3 or .m3u:

```
./purge.py DIR              # This SIMULATES the removal of files, printing names only
./purge.py --really DIR     # This actually removes the files
```

---

### Post by Ducksgoquak on 2008-07-29
Sweet thanks for the ogg2mp3.py :) Worked amazing!

---

### Post by ibutho on 2008-07-29
There is script called ogg2mp3 thats included in some distros (If you google ogg2mp3 you will find it). I am pretty sure it does a similar job to the script above, but I couldn't find it in the Ubuntu package list.

---

### Post by alephnaught on 2008-08-01
Oh wow, that is a totally amazing response! I hadn't expected anything so comprehensive - thanks so much for taking the time to do that. I'll try it out tomorrow. :D

---

### Post by alephnaught on 2008-08-01
Also, I suck at reading code but I assume I can add .flac, .wav, .aac etc to the 'soundext =' line to preserve folders with them also?

---

### Post by unutbu on 2008-08-01
Yes, if you edit it to
```

soundext = ['.m3u','.mp3', '.flac', '.wav', '.aac']

```
then files with any of these extensions will be left untouched.

---

