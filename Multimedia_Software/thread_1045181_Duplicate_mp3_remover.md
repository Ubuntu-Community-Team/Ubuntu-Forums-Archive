---
title: "Duplicate mp3 remover"
date: 2009-01-20
forum: Multimedia Software
---

### Post by stevena0 on 2009-01-20
Hi,

I've been using Ubuntu for a few years, but I've only just signed up to the forums. So hi, and thanks for the forums - they've been a godsend.

I was wondering if anybody knew if someone has written a script to remove duplicate mp3 files from a music library. I copied my music from a few friends and now I have lots of duplicates which is kind of annoying if I want to play an album.

I was thinking of writing a little script to do this for me, but I thought I'd check to see if anyone else has written one first. If not, I'll get cracking and post it back here.

On a similar note, does anyone know if I can make Rhythmbox ignore duplicate songs?

Thanks.

---

### Post by stevena0 on 2009-01-20
In case anybody is interested - I wrote a very crude script myself. Here it is:

```
#!/usr/bin/env python

from ID3 import *
import os, glob, sys

def debug(msg):
    if len(sys.argv) == 2:
        print msg
        
def rm_print(msg):
    try:
        if sys.argv[2] == "-rm":
            print msg
    except IndexError:
        pass

def run():
    songalbums = []
    songalbumspaths = []
    songartists = []
    songartistspaths = []
    if len(sys.argv) < 2:
        usage()

    debug("Looking for duplicates...")

    for (dirpath,dirnames,filenames) in os.walk(sys.argv[1]):
        for file in filenames:
            if file.split(".")[-1].lower() == "mp3":
                id3info = ID3("%s/%s" %(dirpath,file))
                if id3info.artist.strip() == "" or id3info.album.strip() == "" or id3info.title.strip() == "":
                    debug("Ignoring %s | %s - %s - %s" % ("%s/%s" %(dirpath,file),id3info.artist,id3info.title,id3info.album))
                    continue
                if id3info.artist.lower().strip() == "unknown" or id3info.album.lower().strip() == "unkown" or id3info.title.lower().strip() == "unkown":
                    debug("Ignoring %s | %s - %s - %s" % ("%s/%s" %(dirpath,file),id3info.artist,id3info.title,id3info.album))
                if (id3info.title,id3info.album) in songalbums:
                    debug("Duplicate song/album")
                    debug("\tOLD: %s\n\tNEW: %s" % (songalbumspaths[songalbums.index((id3info.title,id3info.album))],"%s/%s" %(dirpath,file)))
                    debug("\t%s - %s\n" % (id3info.title,id3info.album))
                    rm_print("#Title/ablum %s - %s - %s" % (id3info.title, id3info.artist, id3info.album))
                    rm_print("#OLD: %s\n#NEW: %s" % (songalbumspaths[songalbums.index((id3info.title,id3info.album))].replace("(","").replace(")",""),("%s/%s" %(dirpath,file)).replace("(","").replace(")","")))
                    rm_print("\trm -f \"%s\"\n" % ("%s/%s" %(dirpath,file)))
                else:
                    songalbums.append((id3info.title,id3info.album))
                    songalbumspaths.append("%s/%s" %(dirpath,file))
    

def usage():
    print "python duplicate_remover.py music_folder [options]"
    print "options:\n\t-rm Prints the rm command to remove dupicates. This won't remove any files, it just gives you the command."

if __name__ == "__main__":
    run()
```

You'll need this python ID3 tag module - [http://id3-py.sourceforge.net/](http://id3-py.sourceforge.net/)

The way it works is to remove any song where there exists another song with the same title and album name. It's not perfect because of slight differences in spelling of titles/albums etc. but it worked ok for me.

To run:

Save that code as duplicate_remover.py
Run chmod +x duplicate_remover.py
./duplicate_remover.py your_music_directory prints out information about the duplicates it has found
./duplicate_remover -rm your_music_directory prints out the command to delete the duplicates.

Note that the -rm flag only prints out the command, it doesn't do any deleting. To do the deleting, you'll need to run the output of ./duplicate_remover.py your_music_directory -rm. You should check this script first to make sure it's not going to delete anything that's precious to you!!!

Hope it helps someone.

Steve

---

### Post by Lgbouchet on 2009-01-20
Thanks Steve, very useful.  Can I suggest that the size of the file should also be equal?  I have run it through my db (some 50K files), and I got a lot of false positive because of wrong information in some of my mp3 files.  Unfortunately, I am not a python writer, otherwise I would have made the modifications to your code.

Thanks

Lionel

---

### Post by sedawk on 2009-01-20
There are some free tools available to remove duplicate files according
to name, size, modification time, checksum, etc.
Some might be for windows so you might give them a try inside of "wine".


Normally I use the checksum to identify duplicate backups of my
digital camera. So the first step is to create a file where column 1
is the checksum and column 2 is the location of the file
(tools "find"+"md5sum"). Then I sort that list (tool "sort").
Then I identify duplicates in the list (tool "uniq").
Then comes some manual work, e.g. you have to decide if you
delete the duplicate from "backup_xmas" or from "xmas_and_newyear".
This is where I find unix and using a tool like "grep" more useful
then fighting with some GUI tool (for windows).

---

### Post by stevena0 on 2009-01-21
```
#!/usr/bin/env python

from ID3 import *
import os, glob, sys

def debug(msg):
    if len(sys.argv) == 2:
        print msg
        
def rm_print(msg):
    try:
        if sys.argv[2] == "-rm":
            print msg
    except IndexError:
        pass

def run():
    BYTES_DIFFERENT_OK = 0
    songalbums = []
    songalbumspaths = []
    songartists = []
    songartistspaths = []
    if len(sys.argv) < 2:
        usage()

    debug("Looking for duplicates...")

    for (dirpath,dirnames,filenames) in os.walk(sys.argv[1]):
        for file in filenames:
            if file.split(".")[-1].lower() == "mp3":
                id3info = ID3("%s/%s" %(dirpath,file))
                if id3info.artist.strip() == "" or id3info.album.strip() == "" or id3info.title.strip() == "":
                    debug("Ignoring %s | %s - %s - %s" % ("%s/%s" %(dirpath,file),id3info.artist,id3info.title,id3info.album))
                    continue
                if id3info.artist.lower().strip() == "unknown" or id3info.album.lower().strip() == "unkown" or id3info.title.lower().strip() == "unkown":
                    debug("Ignoring %s | %s - %s - %s" % ("%s/%s" %(dirpath,file),id3info.artist,id3info.title,id3info.album))
                if (id3info.title,id3info.album) in songalbums:
	            diff = os.path.getsize(songalbumspaths[songalbums.index((id3info.title,id3info.album))]) - os.path.getsize("%s/%s" %(dirpath,file))		    
		    if abs(diff) <= BYTES_DIFFERENT_OK:
                        debug("Duplicate song/album")
                        debug("\tOLD: %s\n\tNEW: %s" % (songalbumspaths[songalbums.index((id3info.title,id3info.album))],"%s/%s" %(dirpath,file)))
                        debug("\tOLD SIZE: %s\n\tNEW SIZE: %s" % (os.path.getsize(songalbumspaths[songalbums.index((id3info.title,id3info.album))]),os.path.getsize("%s/%s" %(dirpath,file))))
                        debug("\t%s - %s\n" % (id3info.title,id3info.album))
                        rm_print("#Title/ablum %s - %s - %s" % (id3info.title, id3info.artist, id3info.album))
                        rm_print("#OLD: %s\n#NEW: %s" % (songalbumspaths[songalbums.index((id3info.title,id3info.album))].replace("(","").replace(")",""),("%s/%s" %(dirpath,file)).replace("(","").replace(")","")))
                        rm_print("#OLD SIZE: %s\n#NEW SIZE: %s" % (os.path.getsize(songalbumspaths[songalbums.index((id3info.title,id3info.album))]),os.path.getsize("%s/%s" %(dirpath,file))))
                        rm_print("\trm -f \"%s\"\n" % ("%s/%s" %(dirpath,file)))
                else:
                    songalbums.append((id3info.title,id3info.album))
                    songalbumspaths.append("%s/%s" %(dirpath,file))
    

def usage():
    print "python duplicate_remover.py music_folder [options]"
    print "options:\n\t-rm Prints the rm command to remove dupicates. This won't remove any files, it just gives you the command."

if __name__ == "__main__":
    run()
```

Glad it was of use to someone - that should check for file size aswell now. If you change the value of BYTES_DIFFERENT_OK, it will allow the file size to be different by the given number of bytes (just in case your files are sourced from different places and slightly different).

Doing a checksum on them sounds like a good idea actually. I might look into adding that if I get some time.

I had problems similar to yours when, for example, I have a lot of songs by one artist whose titles are all "Unkown" or "Track x". I just had to look through and remove these manually, but hopefully the file size check will help a bit.

Thanks.

---

### Post by Lgbouchet on 2009-01-21
Thanks, it works well. My plan is to first run it with a 0 file size difference, and remove duplicate files first like that.  Then, I will run it again without checking for the size, and verify the false positive.  

I tried to use fdupes to remove duplicate based on the checksum, but it did not find all the duplicate files. If you have a large music db, that you are trying to clean, you need multiple tools.  fdupes is a good start, then your script work great to also compare the id3 tags with the file size.

Thanks

Lionel

---

