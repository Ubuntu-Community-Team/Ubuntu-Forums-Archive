---
title: "KDENLIVE  slideshow filename bug"
date: 2019-12-08
forum: Multimedia Software
---

### Post by iamtheeggman2 on 2019-12-08
Hi,

I wanted to do a slideshow made of a lot of picture files, the problem is though how the file are being sorted/organised in terms of sequential numbering. 

The problem lies in the numbering of the files, they go like this in filemanager:

1.jpg
2.jpg
3.jpg
4.jpg
5.jpg
6.jpg
7.jpg
8.jpg
9.jpg
10.jpg
11.jpg
12.jpg
13.jpg
14.jpg
15.jpg
16.jpg
17.jpg
18.jpg
19.jpg
20.jpg

etc 

The problem starts when you get to 120 in kedenlive because it is labeling the second character  of 2 as higher than equal to the one before where 1 is for 119. This results in the playlist looking like this:

119.jpg
12.jpg <<<<<<
120.jpg
121.jpg


This means its not doing the photos in order and this problematic pattern goes on, can I do anything like use any mass filename rearrange to change the filenames to make it easier for kdenlive to make a slideshow properly? Or perhaps this would be an unavoidable bug?

Maybe i'll try find a timelapse slideshow creator.

Thanks in advance

Edit:solution
I found an option that reads "filename pattern" it turns out that fixes it!

---

### Post by uRock on 2019-12-08
I had mentioned in your other thread using Motion for the time lapse. It doesn't have the file name issues as the default file names start with the time stamps, then add photo numbers to the end of the filename. It will be a great tool if you're doing this kind of project on a regular basis.

---

### Post by iamtheeggman2 on 2019-12-14
Thanks for the Motion suggestions, this week, i tried to use kdenlive again for a slideshow however using the filename pattern option didn't made the list of files I was using disappear, so it wouldn't let me proceed, how weird?

---

