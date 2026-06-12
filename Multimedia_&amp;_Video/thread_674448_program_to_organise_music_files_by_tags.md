---
title: "program to organise music files by tags"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by markp1989 on 2008-01-21
in my music folder, i have alot of files that were recovered from an ipod, so there is no organization to any of the files the  folders are named f0,f1,f3 etc and the flies are just random letters, all files have tags set 

example of current structure 
/music/ipodbackup/f0/abcd.mp3

i was wondering if there are any programs that will scan the music folder, and create folders, move and rename files accordingly so that i will have my music organized like this 
/home/mark/music/artist/album/tracknumber-songname.mp3

does any one know of file that will do this?  
thanks in advance

---

### Post by AndyCooll on 2008-01-21
You want something like Easytag (my personal recommendation) or Tagtool. Either of these can mass rename files based on the contents of the tags.

:cool:

---

### Post by markp1989 on 2008-01-21
> **AndyCooll said:**
> You want something like Easytag (my personal recommendation) or Tagtool. Either of these can mass rename files based on the contents of the tags.

:cool:

thanks for the fast response, i have installed easytag, but cannot work out how to use it to reorganise my files, would you be able to give me a bit of help?

---

### Post by tgalati4 on 2008-01-21
If you kept the original file structure intact and simply copied the entire iPod to your harddisk, you could use gtkpod, rythmbox, banshee, amarok, etc to read the database and it will import all the music and then you can organize it the way you want.

Once you pull the 123Iamarandomfilenamebecauseappleisretarded.mp3 out of the file tree, it's difficult to do anything with it without editing each filename and tag separately.

You want to avoid that.

If the database became corrupted, then you will have problems.  You can still force the import and a new database will be created by what tags the music program was able to read successfully.

Try all the players and report back which one you had the most success with.

---

### Post by kko1 on 2008-01-22
Hello.

> **markp1989 said:**
> i have installed easytag, but cannot work out how to use it to reorganise my files, would you be able to give me a bit of help?

*Easytag* will do **all** of the renaming and organising for you, based on the tags.

In *Easytag*, you do this:
- select a folder*
- shift-select all the files from top to bottom or vice versa, that is any of the files you want to rename and organise
- press the symbol that looks (to me) like a green door; it starts what is (oddly) called a "*file scanner*" in *easytag*. (I'm using easytag v. 1.99.11, so it could be different in your version.)
- there, you can (among other things) auto-rename files and auto-create new folders
- *easytag* actually shows a pretty useful tooltip at this point, you should be able to follow that to get the auto-processing set up like you want to
- for help on what the symbols mean, select the "Show Legend" -option behind the lifesaver help symbol.

*) Actually, you should also be able to put all the files (if none of them have the same names) in a single folder, and process them all at once. **But please test this first on a single folder, to see if it works like you want it to, just in case. It's always a good idea to use some caution, and it's not a big job to process one (or ten) folder(s) at a time instead of treating them all at once.**

To create a complete structure, say, under a path that starts with */music/* (or */home/markp/music/*), and with the substructure like */music/Artist - Album/Artist - Song Number - Title.extension* you could use this:

/music/%a - %b/%a - %n - %t

(You don't specify the extension, *easytag* will automatically use the right one.)

Then you again press the "green door" in the scanner window to "scan" (process) the files. Follow the tooltips and explore the "*file scanner*", you should be able to organise your files as you like.

**NB: After "scanning" the files and closing the scanner window you have to keep your files selected and select "save changes".** (I'm not sure if Easytag in all its versions suggests some automatic changes to the *tags* themselves, so be careful in what you confirm when the program asks you. You can deny changing the tags, and only allow it to change the filenames and paths.)

Hope this helps.

kko1

---

### Post by AndyCooll on 2008-01-24
> **kko1 said:**
> Hello.



*Easytag* will do **all** of the renaming and organising for you, based on the tags.

In *Easytag*, you do this:
- select a folder*
- shift-select all the files from top to bottom or vice versa, that is any of the files you want to rename and organise
- press the symbol that looks (to me) like a green door; it starts what is (oddly) called a "*file scanner*" in *easytag*. (I'm using easytag v. 1.99.11, so it could be different in your version.)
- there, you can (among other things) auto-rename files and auto-create new folders
- *easytag* actually shows a pretty useful tooltip at this point, you should be able to follow that to get the auto-processing set up like you want to
- for help on what the symbols mean, select the "Show Legend" -option behind the lifesaver help symbol.

*) Actually, you should also be able to put all the files (if none of them have the same names) in a single folder, and process them all at once. **But please test this first on a single folder, to see if it works like you want it to, just in case. It's always a good idea to use some caution, and it's not a big job to process one (or ten) folder(s) at a time instead of treating them all at once.**

To create a complete structure, say, under a path that starts with */music/* (or */home/markp/music/*), and with the substructure like */music/Artist - Album/Artist - Song Number - Title.extension* you could use this:

/music/%a - %b/%a - %n - %t

(You don't specify the extension, *easytag* will automatically use the right one.)

Then you again press the "green door" in the scanner window to "scan" (process) the files. Follow the tooltips and explore the "*file scanner*", you should be able to organise your files as you like.

**NB: After "scanning" the files and closing the scanner window you have to keep your files selected and select "save changes".** (I'm not sure if Easytag in all its versions suggests some automatic changes to the *tags* themselves, so be careful in what you confirm when the program asks you. You can deny changing the tags, and only allow it to change the filenames and paths.)

Hope this helps.

kko1

This is a fairly complete starter on how to use Easytag. Just a few additional thoughts.
1. You can select all the files in a folder simply by clicking on the "Select All Files" button.
2. Easytag by default automatically keeps the same file extension.
3. Clicking on the "Green Door" opens up a small window. Besides "Scanner" is the default option to "Process Fields", you can change this to "Rename File and Directory". There are then a number of pre-created masks to choose from (though you can make one of your own if you prefer). Once you've chosen your mask you then have to click on the "Green Door" in this small window to add it to the list of actions for Easytag to undertake. It is possible to get Easytag to run a whole sequence of actions in one go. As you can gather, Easytag can be an extremely powerful tagging tool.
4.When you are happy, click on the floppy disk icon and Easytag will begin making the changes.

:cool:

---

