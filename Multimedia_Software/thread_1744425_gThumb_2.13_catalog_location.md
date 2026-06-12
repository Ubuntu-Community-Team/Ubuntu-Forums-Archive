---
title: "gThumb 2.13 catalog location?"
date: 2011-04-30
forum: Multimedia Software
---

### Post by Cerapter on 2011-04-30
I've been used to the catalogs being stored in ~/.gnome2/gthumb/collections. Using feh and a self-made script, this allowed me to view slideshows by simply clicking an icon on the panel and selecting a list. I was very happy with this.

Now, I cannot seem to find the catalogs files in gThumb 2.13. Are they all in one file somewhere?

---

### Post by mjc1 on 2011-04-30
~/.local/share/gthumb/catalogs/

---

### Post by Cerapter on 2011-05-01
Thanks a lot. Now I can get to work converting all the old catalogs and updating my script.:D

---

### Post by Cerapter on 2011-05-01
For anyone interested, here's a python script I made for converting old gThumb catalogs to the new format (and the new location):

I honestly don't even know if this was necessary, but I didn't find any other way since I did a fresh install of Ubuntu and wanted the old catalogs.

The script just needs you username, and then it should do the trick! However, I would make sure that there's no catalogs in the new system that could risk becoming overwritten. I don't take responsibility for any damage done.

```
# loop through all .gqv files in the folder ~/.gnome2/gthumb/catalogs
# and create the library folders and .catalog files in ~/.local/share/gthumb/catalogs

import os, glob

username="YOUR USERNAME"
OLD = "/home/"+username+"/.gnome2/gthumb/collections/"
NEW = "/home/"+username"/.local/share/gthumb/catalogs/"

def ensure_dir(f):
    d = os.path.dirname(f)
    if not os.path.exists(d):
        os.makedirs(d)


dirnam = ""

def scandirs(path):
    global dirnam
    for currentFile in glob.glob( os.path.join(path, '*') ):
    fname = os.path.basename(currentFile)
        if os.path.isdir(currentFile):
        dirnam = os.path.basename(currentFile)
        NEWfolder = NEW + dirnam + "/"
        ensure_dir(NEWfolder)
    
            scandirs(currentFile)
    elif fname[-4:] == ".gqv":
        fin = open(currentFile, 'r')
        fout = open(NEW + dirnam + "/" + fname[0:-4] + ".catalog", 'w')

            fout.write('<?xml version="1.0" encoding="UTF-8"?>\n')
            fout.write('<catalog version="1.0">\n')
            fout.write('  <files>\n')
            for line in fin:
            lnum+=1
            if lnum>1:
                fout.write('    <file uri=')
                fout.write(line.strip("\n"))
            fout.write('/>\n')
        fout.write('  </files>\n')
        fout.write('</catalog>')

        fin.close()
        fout.close()
scandirs(OLD)

```

---

