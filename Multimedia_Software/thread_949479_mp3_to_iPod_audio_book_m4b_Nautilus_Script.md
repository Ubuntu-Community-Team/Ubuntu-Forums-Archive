---
title: "mp3 to iPod audio book m4b Nautilus Script"
date: 2008-10-16
forum: Multimedia Software
---

### Post by jdforsythe on 2008-10-16
Here's a further improvement on the previous scripts. This is a Nautilus script to convert your mp3 audio books into an m4b iPod file.

All your mp3 files must be in a single directory, and must be named correctly. They will be processed in alphabetical order, so use leading zeroes.

For example, use file01.mp3 instead of file1.mp3 if there are 10 or more, file001.mp3 if there are 100 or more, etc.

To use the script, simply download the zip and unzip the file to ~/.gnome2/nautilus-scripts

Open Nautilus and navigate to the folder containing the mp3 files. Right-click in the empty space (not on the files) and choose "Scripts" then "mp3-to-m4b". Note: you must be INSIDE the folder containing the mp3 files. It will NOT work if you right-click on the folder itself, you have to right-click in the empty space from within the folder.

Dialogs will pop up asking you for the author, book title, year, and filename. Be sure when you enter the filename you leave out the .m4b as that will be automatically added later and you'd end up with file.m4b.m4b. So just enter "file" if you want "file.m4b".

If anyone has a better idea on how to display actual progress in the dialog, please let me know. I can force it to show x amount of progress after each command, but one command takes 90%+ of the processing time, and it looks like the progress bar is frozen. Right now it's one of the progress bars that bounce back and forth, just so you can see it's not frozen. Again, any ideas would be appreciated.

This script does not delete the original mp3 files. I may modify the script at a later date and add in this option, along with some others - just depends on the interest.

Enjoy!

---

### Post by aerosol666 on 2008-11-25
Hi,

thanks for the script, but when I start the script and answer the dialog nothing happens. Should there be any progress bar? After I typed in the filename nothing more comes up. Are there some software requirements?

---

### Post by blackest_knight on 2009-03-31
Heres a nice script to add to .gnome2/nautilus-scripts

#!/bin/bash collapsefolders.sh
#move all files in subfolders below this directory to the current directory
find . -type f -exec mv '{}' . \;

saver it as collapsefolders and it will get all files from a subdirectory and put them in the base folder  word of warning its not nice with duplicate file names it will lose data if two files have the same name

---

### Post by oweise on 2009-05-14
> **aerosol666 said:**
> Are there some software requirements?

Seems the script should install those requirements automatically which fails bc. of unknown reasons.

However you can fetch the depencency installation line from the script and execute it manually in console:

```
sudo apt-get install faac libid3-dev mp3wrap madplay id3v2 mplayer lame normalize-audio imagemagick
```

After that it works for me.

---

