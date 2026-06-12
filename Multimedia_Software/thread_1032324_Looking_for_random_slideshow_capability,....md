---
title: "Looking for random slideshow capability,..."
date: 2009-01-06
forum: Multimedia Software
---

### Post by joelomar on 2009-01-06
Hello all.

I'm looking for a picture viewing app that offers a random slideshow.  F-Spot and Picasa can't do it.  The equivalent would be what I can get from FViewer or the Windows Photo Gallery app.  Set it and forget it.  Any recommendations?

---

### Post by kaibob on 2009-01-06
The utility, FEH, has a randomize option described as follows:

> -z, --randomize
When  viewing  multiple  files  in a slideshow, randomise the file list before displaying.

FEH is a light-weight but bare-bones utility, and you may want something more. But, if not, FEH is worth a look. It's in the repo's.

[http://linuxbrit.co.uk/feh/wiki/FehFeatures](http://linuxbrit.co.uk/feh/wiki/FehFeatures)

---

### Post by riebling on 2009-09-20
These settings work ideally for me as a slideshow; I made a 'Slideshow' panel button I like it so much, with this command line:

feh -zsZFD 5 /home/eric/Pictures

(your home may vary!)

---

### Post by lookslikepat on 2010-09-07
Hey there!

The FEH tip was awesome, many thanks.
I mashed up a script to make it a little more flexible and user friendly. It allows you to choose your folder and the amount of seconds between images.
[http://gist.github.com/568161]("http://gist.github.com/568161")

```
#! /bin/bash

#######################################################
##   Recursive Random Slideshow with Feh in Ubuntu   ##
#######################################################
# This uses feh
# Avaliable in the repositories (graphics universe)
# To display images "non-randomly" change line 21
# ' -zsrZFD ' to ' -srZFD '
# See ' man feh ' for all the options
# Don't forget to make this file executable:
# chmod +x ./Recursive\ Random\ Slideshow\ with\ Feh\ in\ Ubuntu

location=`zenity --file-selection --directory --title="Choose your picture folder"`
timer=`zenity --entry --title="Slideshow options" --text="Seconds between images" --entry-text "10"`

if [ $timer -eq ""]; then 
exit 1
fi

feh -zsrZFD $timer $location
```

Just save it as a file, chmod +x ./file in the terminal and you're good to go :)

---

### Post by jomacintosh on 2010-10-24
Thanks for the script.  I wonder if you could guide me through the process of making this script into an exe file that I could click on to start the slideshow.  I'm not that great on terminal these days.
Thanks

---

### Post by dealcorn on 2010-10-27
Two features of Mirage (available through Synaptic) I like are that it is lightweight and randomize slideshow can be set as a preference.  However, you do not need a terminal to copy the above script into a document you save and then set permissions property to permit execution (i.e. right click on file name...).  Then double click to run. It can also be run from the main menu if you use System/Preferences/Main Menus to add it to the graphics menu.

---

### Post by Relic4 on 2011-06-01
hi,

I have been looking for a random slide show viewer, FEH works great and thanks for the script lookslikepat. 

One little problem is my photos folder contains .nefs (nikon raw image files) producing low res pictures. Is is possible to specify the selection for only jpgs. I looked through the --help but am no good with the coding side and terminal.

Thanks
Al

---

### Post by johncrazy on 2011-06-01
> **Relic4 said:**
> hi,

I have been looking for a random slide show viewer, FEH works great and thanks for the script lookslikepat. 

One little problem is my photos folder contains .nefs (nikon raw image files) producing low res pictures. Is is possible to specify the selection for only jpgs. I looked through the --help but am no good with the coding side and terminal.

Thanks
Al

I will give you soon... I'm creating this! :KS

---

### Post by handy on 2011-06-01
Just use GQView; go to >Preferences >General >Slideshow >Random ...

It is a really full featured & light weight image viewer as well. :)

---

### Post by Relic4 on 2011-06-03
hi,

thanks john, I look forward to seeing what you create.

-handy, i tried GQView but couldnt get it to look in sub-folders. apart from that its as you say.

---

### Post by kiwited on 2011-09-29
I am also looking for random viewing abilities, but wish to not only view images, but also video clips.

I have found viewers for each, but cannot find one that does both images and video.

---

