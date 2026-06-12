---
title: "a script of mine: right click, look up on IMDB"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by aeiah on 2008-03-30
**[COLOR="Red"]so i made a more complicated one. you may find it more useful if you have oddly named movie files. scoot over to page two[/COLOR]**


[img]http://img241.imageshack.us/img241/4066/screenshotwv4.png[/img]


this is a simple python script i wrote that will allow you to right click on a film and view its IMDB page. ive used google's 'im feeling lucky' feature because imdb doesnt always display the film's page straight away when you search (this feature was updated 6.26BST 31/04/08)

open a terminal and type:

sudo gedit /usr/bin/imdb

and paste in the code below and save

```


#! /usr/bin/python

import sys, os, optparse, os.path

from optparse import OptionParser
parser = OptionParser()
parser.add_option("-i", "--input", action="store", type="string", dest="video")
(options, args) = parser.parse_args()

myPath = options.video
(dirName, fileName) = os.path.split(myPath)
(fileBaseName, fileExtension)=os.path.splitext(fileName)
t = fileBaseName.strip().replace('cd1', '')
s = t.strip().replace('cd2', '')
u = s.strip().replace('CD1', '')
v = u.strip().replace('CD2', '')
os.system("firefox 'google.com/search?btnI=1&q="+ v + " imdb'" )

```

then make it executible by typing this into the terminal once you've saved it:

sudo chmod 755 /usr/bin/imdb

you can run it from the terminal by typing imdb -i <filename>, although to make it appear in the right click menu for video files, you'll have to use nautilus actions

once installed, go to system > preferences > nautilus actions configuration

click the Add button and fill it in as shown here. 

[img]http://img262.imageshack.us/img262/7567/screenshot2oj3.png[/img]

download the imdb icon i use [(link)](http://img241.imageshack.us/img241/3716/iconimdbsmop6.jpg) or use something else.

on the conditions tab, select the filetypes you want this to apply to. mine are:

*.avi ; *.mkv ; *.mov ; *.mpg ; *.mp4


that should be it! the script should make it far easier to decide which legal backup copy or open source movie you feel like watching :)

---

### Post by nilarimogard on 2008-03-30
Any way to remove dvdrip and other things that are written in a movie title downloaded from a torrent tracker? Like right clicking on: The.Wall.Man.2006.DVDRip.XviD-WRD to only enter in the search query: "The Wall Man" and maybe the year and that's it.

---

### Post by aeiah on 2008-03-31
the problem with that is that it tends to be random, so you cant remove specific words. the best thing to do would be to ignore everything beyond a set of numbers (the year), and to replace . with a space. this can be done in python and i may have a look into it tonight.

currently, the script just removes the extention and  "cd1" or "cd2" from the filename. i always rename my files y'see, because they can look rather ugly. plus most scene releases dont even have the title in the filename, just the initials followed by the release group name. The.Wall.Man.2006.DVDRip.XviD-WRD is likely to be WM-WRD.avi :(

---

### Post by nilarimogard on 2008-03-31
yeah but i made it look up the name when right clicking on the folder, so it sees the name, the only problem is that it has DVDRip.XviD-WRD at the end, so it doesn't search right

---

### Post by aeiah on 2008-03-31
yea i know. thats what i was saying... me or someone else would have to implement a way of ignoring everything in the filename / folder name beyond the year.

---

### Post by adamprawitz on 2008-04-02
This is a really cool script!  Thanks for putting it out there!

---

### Post by dannofoo on 2008-04-25
Nice script, were about to code the "remove all after the year tag", but realized, you would want the year tag in some cases.   

Hollywood really loves those remakes.

Anyway, here's the upgraded script from above, just add the lines u want removed from the search, i missed some strings i guess.

```
#! /usr/bin/python

import sys, os, optparse, os.path

from optparse import OptionParser
parser = OptionParser()
parser.add_option("-i", "--input", action="store", type="string", dest="video")
(options, args) = parser.parse_args()

myPath = options.video
(dirName, fileName) = os.path.split(myPath)
(fileBaseName, fileExtension)=os.path.splitext(fileName)
t = fileBaseName.strip().lower()
t = t.strip().replace('readinfo', '')
t = t.strip().replace('readnfo', '')
t = t.strip().replace('xvid', '')
t = t.strip().replace('dvd', '')
t = t.strip().replace('limited', '')
t = t.strip().replace('ac3', '')
t = t.strip().replace('fs', '')
t = t.strip().replace('ws', '')
t = t.strip().replace('subbed', '')
t = t.strip().replace('read', '')
t = t.strip().replace('nfo', '')
t = t.strip().replace('internal', '')
t = t.strip().replace('line', '')
t = t.strip().replace('-', ' -')
t = t.strip().replace('_', ' ')
t = t.strip().replace('.', ' ')

os.system("firefox 'google.com/search?btnI=1&q="+ t + " imdb'" )
```


Thanks again for the idea, aeiah :)

---

### Post by yousillygoose on 2008-06-16
This is a pretty sweet idea.  I am now using it and changed one thing.

os.system("firefox 'google.com/search?btnI=1&q="+ v + " site:www.imdb.com'" )

I use that so that google searches only imdb.  You had it set to search imdb with its search but that can be occasionally flawed (very rarely though).  I felt that this would fix the potential faulty search  :)

---

### Post by yousillygoose on 2008-06-16
you also should add:
t = t.strip().replace("'", '') 

to the script.  If the file name has a possessive or any reason for a ' in it the script will fail without this

---

### Post by yousillygoose on 2008-06-17
I just wrote this  [https://addons.mozilla.org/en-US/firefox/addon/7622](https://addons.mozilla.org/en-US/firefox/addon/7622)  . 
If you like the option in nautilus than you will love it in Firefox.  You can highlight, right click, and lookup your selection directly to IMDB using this  :)

---

### Post by aeiah on 2008-07-01
wow, i hadnt checked back on this in a while. im writing a kind-of mediacenter type app right now so i can learn more python and learn about mysql for work. i havent done a great deal but the first thing im doing is a script that will take almost any relevant filename and convert it into an imdb link. right now it works with almost anything but its rough around the edges. i hope to finish it soon and ill post it here when i do ^_^

---

### Post by mbarvian on 2008-07-01
This sounds promising, good work!

---

### Post by aeiah on 2008-07-15
as i mentioned the other week, ive been working on a more complex version of this that will solve the problem of having scene release and p2p named movie files not showing up. its pretty obvious why they didnt. the last script suited me fine because i rename all my backed up movies to proper names but other people dont, and since im planning on encorporating this script into a future movie cataloging program i ought to address that problem.

[img]http://img530.imageshack.us/img530/4441/screenshotet9.png[/img]

please be aware that this script isnt really quick like the last one, and if you have a normally named file i suggest using my first one instead of this.



to install:

1. download my attatched script

2. untar it and make it executable

3. install nautilus-actions if you havent already (you could create a launcher of your own or use the terminal if you want instead)

4. install w3m if you havent got it

5. click the add button and fill it in as shown (or however you want to really)

```
python /path/to/movieponderer -i
```
dont forget the %M part.

6. on the conditions tab, select the filetypes you want. your best bet is to use this in the mimetype field:
```
video/* ; application/x-rar ; application/x-cd-image
```

7. ooooh, nearly forgot: near the top of the script, you can specify the foldernames you want to be blacklisted from the search. this is useful if you keep all your movies in a folder called 'film' but sometimes want to search for a foldername you dont expect, such as one that'll contain the film name.


let me know what files it gets stuck on, and any suggestions for making my code better because i know its a mess.

---

### Post by dannofoo on 2008-07-19
hah, nice yousillygoose.  i wrote something simlair for firefox, but it didnt parse and remove the jibberish from textstrings properly. 


will check yours out :)

---

