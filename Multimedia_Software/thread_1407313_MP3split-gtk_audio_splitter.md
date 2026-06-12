---
title: "MP3split-gtk audio splitter"
date: 2010-02-15
forum: Multimedia Software
---

### Post by ubiubi on 2010-02-15
Hi all

I've roughly 8 hours of lecture notes which I want to break down into manageable chuncks (eg. 30 min or so).

I tried using mp3split-gtk and on the screen graphics managed to indicate the breaks. I could not see how I could save them. Can anybody help me. Is it simpler using the command line with instructions to divide the file. If so what do I type. I'm embarrassed to say that I find the instructions for that a little daunting. It's not important for the files to be all the same size. Would it be possible to break the file down to say 16 smaller files?

Cheers for any advice.:D

---

### Post by ajgreeny on 2010-02-15
I've never really used the gtk gui for this program; I looked at it but quickly found it more troublesome than the command line.  However, I use the command line version a great deal, and find it very simple to use.  I have made a folder in home called mp3edit to which I copy any files I want to edit, and then I navigate to that folder and use the commands from there.  It makes finding the files produced much easier, and tab completion of file names speeds things up as well.

To split the 8 hrs into 30 min chunks it simply needs the command ```
mp3splt -t 30.00 8hourfile.mp3
```  You can add the -a option, as well as the -t, and if there are silences below the standard threshold of 40db it will adjust the split point to a silence within 30 seconds of the chosen 30.00 minutes set in the command.

The manual is very helpful, and to get the manual in txt form, which you can save to disk and use as a aide-memoire, open the gnome-help in your menus and in the search box type **man:mp3splt**.  Copy all that to a txt file, save it, and you may find it easier than using **man** in terminal; it is certainly easier to search.

---

### Post by ubiubi on 2010-02-15
Hello Ajgreeny

Thanks very much for your frply and suggestion. I tried it and it worked perfectly. I also on a second file tried the same operation with the gui and finally got it to work. It was of course very simple but not very intuitive. Anyway, I now can use the command line and the graphical technique.

Mark

:popcorn:

---

