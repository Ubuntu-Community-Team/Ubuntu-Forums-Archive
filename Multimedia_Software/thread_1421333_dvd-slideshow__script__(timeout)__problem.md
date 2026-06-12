---
title: "dvd-slideshow  script  (timeout)  problem"
date: 2010-03-04
forum: Multimedia Software
---

### Post by ashishvalsad on 2010-03-04
we are using dvd-slideshow 0.8.2.

i have successfully created video using this tool.

i have successfully use the kenburns effect for zoom and pan.

i am facing one problem that time taken to create video is too long.

for  two images with crossfad takes 3 minuts and the length of this video is 6 sec.

following is the input text file data.

[COLOR=Blue]my_pictures/img1.jpg:10:sub:kenburns:75%;right;75%;left;
crossfade:2
my_pictures/img2.jpg:10:sub:kenburns:75%;left;75%;right; [/COLOR] 



for two to three images everything goes right and video is created.

but when i have taken 12 images at input text file (try to make video with 12 images)
the script goes time out and i am not able to create video.


following is the input text file data (in which i am failing to create video).


[COLOR=Blue]my_pictures/img1.jpg:10:sub:kenburns:75%;right;75%;left;
crossfade:2
my_pictures/img2.jpg:10:sub:kenburns:75%;left;75%;right;
crossfade:2
my_pictures/img3.jpg:10:sub:kenburns:75%;bottom;75%;top;
crossfade:2
my_pictures/img4.jpg:10:sub:kenburns:75%;top;75%;bottom;
crossfade:2
my_pictures/img5.jpg:10:sub:kenburns:85%;middle;45%;middle;
crossfade:2
my_pictures/img6.jpg:10:sub:kenburns:45%;middle;85%;middle;
crossfade:2
my_pictures/img7.jpg:10:sub:kenburns:75%;right;75%;left;
crossfade:2
my_pictures/img8.jpg:10:sub:kenburns:75%;left;75%;right;
crossfade:2
my_pictures/img9.jpg:10:sub:kenburns:75%;bottom;75%;top;
crossfade:2
my_pictures/img10.jpg:10:sub:kenburns:75%;top;75%;bottom;
crossfade:2
my_pictures/img11.jpg:10:sub:kenburns:85%;middle;45%;middle;
crossfade:2
my_pictures/img12.jpg:10:sub:kenburns:45%;middle;85%;middle;
 [/COLOR]

i am calling following script in php file.

[COLOR=Blue]dvd-slideshow -n 'test_complete' -o output -f  output/Complete_example.txt [/COLOR]



i am really stuck at this point , we want to make this feature on our site.

can anyone suggest how to solve this issue?


Thanks,
Ashish.

---

### Post by irwand on 2010-05-17
dvd-slideshow has a debug level that spits out a lot of info during processing.
See here:
[http://dvd-slideshow.sourceforge.net/wiki/Config_File_0.8.0](http://dvd-slideshow.sourceforge.net/wiki/Config_File_0.8.0)
look at the debug setting..
increase the debug setting and try again, see what it tells you in the log file. Hopefully you'll be able to figure out what's going on.

dvd-slideshow will quit when it's parsing the file, if it can't find the file specified. Double check your file names.

---

