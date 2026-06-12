---
title: "MD5 Checksummer or like?"
date: 2009-01-12
forum: Multimedia Software
---

### Post by metalguy639 on 2009-01-12
I need a program that will make checksums as well as check them. I cannot seem to find any documentation on MAKING the checksum files. Tons on checking files but none on how to make them in linux. Can I use MD5sum to make files? If so how do I do that?

---

### Post by binbash on 2009-01-12
i guess you can do it with : 
md5sum linux.iso > linux.iso.md5

or just read this :

[http://blogs.koolwal.net/2008/07/22/how-to-generate-a-md5sum-checksum-file-for-linux-iso-images/](http://blogs.koolwal.net/2008/07/22/how-to-generate-a-md5sum-checksum-file-for-linux-iso-images/)

---

### Post by wolfen69 on 2009-01-12
after you get an .iso, (we'll assume it's on the desktop) do:
```
md5sum /home/user/Desktop/name_of_file.iso
``` it will spit out the md5 for you.
then i just compare the numbers real quick. maybe not the official way, but it works.

---

### Post by metalguy639 on 2009-01-12
Ok I do not want an iso of the files that I'm doing the sum for. I'm doing the sum for mp3 files and its only so that if someone downloads them from me they can run the check and see that all the files are there. No iso needed.

---

### Post by ajcham on 2009-01-12
No, the iso mentioned above was just an example of a file you might take a checksum *of*.
Just replace that with the mp3 file you want to sum.

---

### Post by lipidicman on 2009-05-23
I wanted a GUI, then realised I could use **Thunar's Custom Actions** to avoid the command line and have a one click **'generate MD5'** and **'verify MD5'** options.  I'm not clear whether this could be achieved in Nautilus as I have replaced it with Thunar on my systems.


**Generating recursive md5 files with relative paths for a directory**
```
md5deep -rl ./* >verify_newtmp.md5
```
Make it appear as an option for directories.  You will need md5deep installed.  You could write a more complex line with a find function and use md5sum as below.  I use md5deep sometimes for its ability to do negative matching and missing files, so it is easier here
```
find . -type f -print0 | xargs -0 md5sum > verify_newtmp.md5
```


**Verifying files**
```
Xdialog --title "results" --msgbox "$(sed -e 's:\ \*:\ \ \.\/:' -e 's:\\:\/:g' -e 's/^M$//' <%n | md5sum -c 2>&1 | egrep 'FAILED$|md5sum:' )" 0 0
```
This needs Xdialog to pop up the output.  It uses SED to convert a file if it is windows sourced (' *' to '  ./', backslashes and finally DOS to UNIX line ends) as I made a lot of files with MD5summer and mkwACT tools in windows.  You need to add the action for all *.md5 files.  The 2>&1 and egrep ensures md5sum messages and any hash failed lines are reported to the Xdialog box.  File OK lines are not necessary, but this can be adjusted as needed. the %n is replaced by Thunar with the selected filename.

Perhaps Zenity is better as it is part of Ubuntu and you can copy and paste:
```
sed -e 's:\ \*:\ \ \.\/:' -e 's:\\:\/:g' -e 's/^M$//' <%n | md5sum -c 2>&1 | egrep 'FAILED$|md5sum:' | sed '1i\%f' | zenity --text-info
```
The second sed command adds the path and name of the md5 file to the output (provided by %f by Thunar)


Thought this might be of use.  I worked this out by putting together a lot of posts by other people, so thanks to all.  Please let me know of any errors.  Also if anyone knows how to add these commands to Nautilus, that would be welcomed as it is the default file manager

---

