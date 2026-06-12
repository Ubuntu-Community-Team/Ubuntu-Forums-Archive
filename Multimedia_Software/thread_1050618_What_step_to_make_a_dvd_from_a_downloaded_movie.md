---
title: "What step to make a dvd from a downloaded movie"
date: 2009-01-25
forum: Multimedia Software
---

### Post by sofasurfer on 2009-01-25
I have read many dvd autoring sites. Can't connect the dots. So let me just ask some questions.

1) I can convert a movie file to many differant formats with 'winff', such as avi, mpeg, quicktime, wmv, etc. This allows a movie to be played on movie players that support differant formats. Correct?

2) But when I want a movie to be placed onto a dvd, don't I have to convert it to a particular format specifically to be played on a dvd player?

3) I converted a movie file to a DVD format using Winff. But the file that was created is a mpeg. Now when I try to burn it to DVD using K3B or Brasero I see no option for mpeg. I only see option for data dvd and 
dvd iso. How do I burn a mpeg file to dvd?

4) I the past, using Windows, I have converted dvds to those ts files or whatever they were and could save them to dvd. But converting my present movie files do not create the ts files. Am I supposed to be seeing ts files?

I hope I am making this understandable. I don't know all the terminology yet.

---

### Post by sofasurfer on 2009-01-26
bump

---

### Post by wolfen69 on 2009-01-26
> **sofasurfer said:**
> 

3) I converted a movie file to a DVD format using Winff. But the file that was created is a mpeg. Now when I try to burn it to DVD using K3B or Brasero I see no option for mpeg. I only see option for data dvd and 
dvd iso. How do I burn a mpeg file to dvd?



after creating the mpeg file, use devede to create the .iso

devede is kind of weird in the respect that when it is done, it will say "done burning to disc" or something to that effect, when you havn't burned anything. but just go to your home folder to find the .iso, then burn the image with whatever.

---

### Post by sofasurfer on 2009-01-26
Thanks for your reply. I will go try it now.

---

### Post by Twitch6000 on 2009-01-26
If you do not mind paying for software Nero for Linux will do all of this you are requesting within a click =].

It only cost about 30 dollars(I think...) and works great :D.

---

### Post by sofasurfer on 2009-01-27
I used Winff to convert a .avi movie to .mpeg. Then I used Devede to convert the .mpeg to a iso. Before running Devede I ran the preview and the movie did play properly. After running Devede I was left with a .iso file. 

After the .iso file was created I ran K3B and got this error...
"Attempt to re-run with DVD compatible to engage DAO or apply full blanking proceedure. Write error".

So I ran Brasero to create the disk and when I run it the only thing that plays is the text menu that I created. And yes, I did choose a movie .iso to burn to the disk.

Any ideas what is wrong?

---

### Post by FakeOutdoorsman on 2009-01-28
What WinFF preset did you use?  Try just using ffmpeg to encode to mpg.  It has the easy to use "target" option and will automatically choose the correct parameters:
```
ffmpeg -i input.avi -target ntsc-dvd output.mpg
```
or if your country uses PAL instead of NTSC:
```
ffmpeg -i input.avi -target pal-dvd output.mpg
```

---

