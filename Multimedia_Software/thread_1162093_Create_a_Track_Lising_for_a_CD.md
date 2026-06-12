---
title: "Create a Track Lising for a CD"
date: 2009-05-17
forum: Multimedia Software
---

### Post by stevena0 on 2009-05-17
Hello,

I DJ, and I spend a lot of time creating CDs with loads of MP3s on them. Trouble is, I struggle to remember the track names, and it's a hassle to type them all out.

I wrote this simple script that gets all the mp3 files in a folder, and outputs a basic track listing based on the ID3 tags. Thought I'd share just in case anyone has the same problem...

```
#!/usr/bin/env python

from ID3 import *
import os, glob, sys

do_debug = False

def debug(msg):
    if do_debug:
        print msg
       
def run():
    songs = []
    if len(sys.argv) < 3:
        usage()

    debug("Looking for files...")

    string = sys.argv[2]+'\n'
    track = 1

    files = os.listdir(sys.argv[1])
    files.sort()
    for file in files:
        if file.split(".")[-1].lower() == "mp3":
            id3info = ID3("%s/%s" %(sys.argv[1],file))
            artist = id3info.artist or "Unknown"
            song = id3info.title or "Unknown"

            string = string + str(track) + ". " + artist + ' - ' + song + '\n'
            track = track +1
                               

    print string
        
    

def usage():
    print "python track_lister.py music_folder cd_name"
    exit()

if __name__ == "__main__":
    run()
```

You'll need the ID3 tagging module [http://id3-py.sourceforge.net/](http://id3-py.sourceforge.net/) in the same directory as that script, then run python track_lister.py DIRECTORY, CD_NAME.

Hope it's useful,

Steve

---

### Post by SuperSonic4 on 2009-05-17
What kind of output would this give?

Normally I would just open Kate and copy and paste the names and slip it in the cd case

---

### Post by stevena0 on 2009-05-17
It just gives the output

CD_TITLE

TRACK_NO. ARTIST - SONG_TITLE
TRACK_NO. ARTIST - SONG_TITLE
...

I was doing the same thing, but when I'm doing a few hundred mp3s at a time, it can get a bit boring! I tend to have a folder per CD and then just run this over it to get my track listing.

---

