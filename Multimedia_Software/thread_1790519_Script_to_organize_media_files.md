---
title: "Script to organize media files?"
date: 2011-06-25
forum: Multimedia Software
---

### Post by Pithikos on 2011-06-25
Anyone knows any good script/app that can organize files according to their extensions? I have a bunch of files and subfolders containing other files and what I want is to organize them all in seperate folders(movies, music, images, archives). Searched a bit but google doesn't seem that helpful..

---

### Post by furtypajohn on 2011-06-29
Here's a python script I just threw together. I leave you the exercise of testing it...
Just save it to organize.py and then run it by "python organize.py"

Make sure to edit to to add the folder names that you want to use for each extension type.


```
#!/usr/bin/python
# Traverse all of the files in the given directory and move
# them into subfolders based on their extension type.
import os
import sys


if __name__ == '__main__':
    # Define the folder names for each extension type here
    folderNames = {".jpg" : "images",
                   ".png" : "images",
                   ".avi" : "movies",
                   ".mp3" : "music"}

     
    # NOTE: Assuming files in current folder
    directory = "./"
    files = os.listdir(directory)

    # Traverse all of the files
    for filename in files:
        # Grab the extension of the file
        extension = os.path.splitext(filename)[1]
        
        if extension in folderNames:
            # Grab the folder where this file should be stored
            folder = os.path.join(directory, folderNames[extension])

            # Create the folder if it does not already exist
            if not os.path.exists(folder):
                os.mkdir(folder)
                
            # Move the file into the folder
            os.rename(os.path.join(directory, filename),
            os.path.join(folder, filename))
        else:
            print "Unable to handle file: [%s]" % filename
```

---

