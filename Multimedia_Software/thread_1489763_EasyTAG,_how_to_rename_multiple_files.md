---
title: "EasyTAG, how to rename multiple files ?"
date: 2010-05-21
forum: Multimedia Software
---

### Post by le1 on 2010-05-21
I'm trying to figure out how can I fill up multiple files with easytag. It looks like one can do it by selecting all files and using one of the schemes like " %a - %b/%n - %t " but to be absolutely honest I have no clue how it works. I'd like to fill up all selected files' tags with Artist, Title, Album, Year, Track# and Genre. How can one do it ?

---

### Post by dartmusic on 2010-05-21
Select all files you want to edit, enter (for instance) the Artist info you want in the Artist field, then click the little square to the right of the field and whatever info you have entered will be copied to that field in ALL files that you have selected.  Repeat for the remaining fields.

---

### Post by ron999 on 2010-05-21
........

---

### Post by joshedmonds on 2010-05-22
Use the 'Scanner' functions in the menu (or the green scanning icon) with the correct syntax. 

For example to rename multiple files as 'Track Number - Artist - Song Title' and put them in a directory as with the name of the Album you would select 'Rename File and Directory' and use syntax:
```
%b/%n - %a - %t
```

To rename files with additional free text, simply use it between expressions, e.g.
```
%a - %b (Bonus Disc) - %n - %t
```

Filling tags uses the same codes, so the files must have the correct name and be in a directory structure such that all the information you want is available from the file name and path.

More information is available at [http://easytag.sourceforge.net/EasyTAG_Documentation.html]("http://easytag.sourceforge.net/EasyTAG_Documentation.html")

You could try using the CDDB function to find the album, however I have never had any success with this process after the files have been created (i.e. when no longer a 'disc')

---

### Post by le1 on 2010-05-22
Thanks "**dartmusic**" the answer was so right in front of my face, hah

"**joshedmonds**" as for your help, it looks like this is crucial:

*"Filling tags ... the files must have the correct name and be in a directory structure such that all the information you want is available from the file name and path."*

The question would be:

If I want to fill up 60 files, only the "title" space, as following: 
"Track 1" for the "1st file", "Track 2" for the "2nd file" and so on...

How can I do it using these schemes ?

---

### Post by joshedmonds on 2010-05-22
Unless the files are named appropriately, i.e. named in a consistent manner containing the number you wish to use e.g. '1' or 'Track 1' or 'ABC 1 XYZ' then you won't be able to use the autofill function. You may have been a bit specific with your question, as another program may be the best tool for this type of batch tagging (but I don't know what program).

---

### Post by ario on 2010-07-20
> **dartmusic said:**
> Select all files you want to edit, enter (for instance) the Artist info you want in the Artist field, then click the little square to the right of the field and whatever info you have entered will be copied to that field in ALL files that you have selected.  Repeat for the remaining fields.

Thanks man! God Bless You!
It solved my problem:).

---

### Post by ayip_eiger on 2010-09-08
> **dartmusic said:**
> Select all files you want to edit, enter (for instance) the Artist info you want in the Artist field, then click the little square to the right of the field and whatever info you have entered will be copied to that field in ALL files that you have selected.  Repeat for the remaining fields.

I'm really stuck with this problem, but your asnwer makes me happy again, thx a lot..):P

---

### Post by chipster123 on 2011-04-09
Just wanted to let anyone who cares know that this thread helped me a lot! EasyTag is great.

I used it to recover songs from a friends an iPod (they are all F00/BHUJ.m4a type naming) and rename them to their original Album, artist, tract etc. file names. Using a pattern '/home/converted/%b/%n - %a - %t' it reorganized everything into proper directories.

The only thing that fooled me was it didn't seem to actually write the renamed files. It just went through all the motions of telling me the new names. Then, when I was giving up and exiting, it asked me "do you want to save the changes?" or something like that, and I say "yes" of course, then the action started. 500+ renamed files later, the program exited and the iPod arranged directory/files were renamed and rearranged to normal naming scheme.

---

### Post by julio prada on 2011-08-08
Very strange interfase, you have to click on a little gray circle to the right of the field to apply, not clear either if files are selected or not.
I was looking for something better than Nautilus and Banshee to remane and put tags.

---

### Post by arito on 2011-08-21
The interface for file renaming is indeed frustrating. I just spent 45 minutes trying to figure out how to actually execute the naming scheeme I selected. I was looking for an OK button, or something. When you know how it works there's no problem, but until that many will scratch their heads...

---

