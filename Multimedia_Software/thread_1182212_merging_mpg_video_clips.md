---
title: "merging mpg video clips"
date: 2009-06-08
forum: Multimedia Software
---

### Post by furoido on 2009-06-08
Hi guys!
Want to merge three short .mpg video clips into one. Can anyone give a complete newbie at this  step-by-step instructions on how to do it, similar to the below step-by-step? I tried following the below, which appeared to merge the 3 clips, but when I tried playing the new clip back, it froze at was was the end of the original first clip (although, funnily enough, the sound carried on....)



Try the program Pitivi.

Code:

sudo apt-get install pitivi

Then, type in your root password and install the program.
After it is done go to "Applications" >> "Sound & Video" >> "Pitivi Video Editor".
Then, drag the movies that you need into the program. Then, drag them from the program's "clips" section to the bottom in a timeline. After you are done you can click "Render Project".

---

### Post by benerivo on 2009-06-08
If you have mencoder installed, then you could initially try...```
mencoder -oac copy -ovc copy -o '/home/ben/newvideo.avi' '/home/ben/test1.avi' '/home/ben/test/2.avi'
```
where newvideo is the output and test 1 and 2 are the input files, and the commands before the file names are telling it to make a direct copy of the video and audio.

---

### Post by furoido on 2009-06-08
Bene, thanks...just one thing....do I type those commands in terminal?

---

### Post by andrew.46 on 2009-06-09
Hi furoido,

> **furoido said:**
> Want to merge three short .mpg video clips into one. 

This format is one of the few that should be suitable to use with the *cat *command. So to merge 3 of these into 1 new file:

```
cat vid1.mpg vid2.mpg vid3.mpg > merged_vid.mpg
```

Reference here:

3.18 How can I join video files?
[http://ffmpeg.org/faq.html#SEC30](http://ffmpeg.org/faq.html#SEC30)

All the best,

Andrew

---

### Post by furoido on 2009-06-09
What am I doing wrong here, someone??


andrew@andrew-desktop:~$ cat vid1.mpg vid2.mpg vid3.mpg > merged_vid.mpg
cat: vid1.mpg: No such file or directory
cat: vid2.mpg: No such file or directory
cat: vid3.mpg: No such file or directory

---

### Post by binbash on 2009-06-10
does vid1 vid2 etc locate at Desktop?Because you are giving this command at desktop folder.Navigate to the folder where vid1.mpg vid2.mpg is located.

---

### Post by andrew.46 on 2009-06-10
Hi furoido,

> **furoido said:**
> What am I doing wrong here, someone??

```
andrew@andrew-desktop:~$ cat vid1.mpg vid2.mpg vid3.mpg > merged_vid.mpg
cat: vid1.mpg: No such file or directory
cat: vid2.mpg: No such file or directory
cat: vid3.mpg: No such file or directory
```


I have been less than clear :-). The names I gave (vid1.mpg) were *examples* only, you will need to substitute the actual names of your own files. Plus, as binbash has mentioned, you will need to navigate to the actual folder containing these files.

All the best,

Andrew

---

### Post by zero777zero on 2009-06-10
to navigate to the folder where your files are type in the termainal "cd" followed by the path of the folder where ur files are

---

