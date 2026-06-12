---
title: "how to converter video for ipod in command line(CLI)"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by philidox on 2007-11-06
I wanna be we'll adaptered to the command line interface.  Can anyone tell me how to set the video settings in the command line for a video conversion ipod read. thx

---

### Post by Lostincyberspace on 2007-11-06
Try using mencoder it works well for me.

---

### Post by philidox on 2007-11-06
ok cool but what do i type in the cli in order to set it up for ipod format?

---

### Post by Lostincyberspace on 2007-11-06
I would use mpeg look up the correct iuse it for encoding to avi but ipods dont support avi.

I use the following code that i found online

 ```
mencoder "in"."ext" -oac mp3lame -lameopts preset=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200 -ofps 25 -of avi -o "out".avi
```

it looks like you could just replace .avi with .mpg to use with your ipod.

if not just google it

---

### Post by Creative2 on 2007-11-07
read this 
[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

or if you hhave ffmpeg (from medibuntu repo ) use this
ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 OUTPUT

---

### Post by philidox on 2007-11-07
GOD i love you creative2 that was awesome man we gotta talk more teach me more man!!!  do you have more howto's and tutorials cause that was straight to the point.  Can help me out with another dilemma how do I get those video uploaded on my ipod thinliquidfilm is messing up.  I finally started using gpooder for podcasting and I need a keyboard shortcut for my volume control under kubuntu.  Thanx again your the man!

The only thing is how do i use convertit to convert to ipod format.  I thought i was going to be straight forward but I got a lil lost in the gui.  Please reply quick!

---

### Post by Creative2 on 2007-11-07
mmm i am sorry man but i have not ipod,  many people have asked to add command line for ipod so i have tried but i can't do more of this

---

### Post by Creative2 on 2007-11-07
maybe you can see this 

[http://www.youtube.com/watch?v=VtIa3xw2s3w](http://www.youtube.com/watch?v=VtIa3xw2s3w)

---

### Post by philidox on 2007-11-07
Just show me how to use the converter and i'll take care of the rest.  I'm really lost on how it works.  I'll make a youtube vidoe once i get it working for ipod, let me take care of the ipod user:)

---

### Post by Creative2 on 2007-11-30
well,  but.... mm.. what haven't understood about converIT...??

Salut

---

