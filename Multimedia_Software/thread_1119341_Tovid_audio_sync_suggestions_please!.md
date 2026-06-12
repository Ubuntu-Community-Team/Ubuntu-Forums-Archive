---
title: "Tovid audio sync suggestions please!"
date: 2009-04-07
forum: Multimedia Software
---

### Post by mrtomservo on 2009-04-07
Hi everyone!

I have been trying to encode AVI's to DVD format using Todiscgui, taking the output and running it from the command line.  The problem has been with the audio slowly and steadily becoming separated from the video.  By the end of the video the audio is approximately 2 seconds off.  The original AVI's are not damaged, and the audio is fine. Non-gui options are preferable as the encoding is done on a headless Ubuntu 8.10 server.  I have tried many command line options, the most recent being:

```
/usr/bin/todisc -menu-title 'Movies' -files 'Movie1.avi' 'Movie2.avi' -titles 'Movie1' 'Movie2' -dvd -ntsc -background /home/user/pictures/a1menu.jpg -out /home/user/processing/101102 -no-ask -no-warn -tovidopts '-ffmpeg' -align center -menu-title-geo north -chain-videos -playall
```

I've Googled and searched these forums, but i've yet to find something that will fix this problem.  Some "tovid options" i've tried are -async 1 (and numbers other than 1), -ffmpeg, removing -chain videos, and -playall.  None of the tweaks made a difference. Seeing it takes 3 hours to convert 2 movies, any time saving suggestions would be welcomed! ;)

It should be noted the Ubuntu 8.10 Server is running 2.6.27-11-server, 1 gb ram, 3.2 ghz celeron, Tovid Version 0.31. I have tried the same conversion on my main pc in the signature that is running 8.04, and it does the same thing.  

Thanks for the time!

---

### Post by inobe on 2009-04-07
not much experience with tovid, probably used it once last year, i currently devede, i use to use mandvd but that gave me a bunch of stupid errors......

devede seems to be working very well for me, the encoding process seems to take a bit longer but as long as it works.

---

### Post by mrtomservo on 2009-04-08
Excellent, thanks for the suggestion!  I'll check it out and post back if devede works properly for me.

---

### Post by kpkeerthi on 2009-04-08
Try by removing -ffmpeg option.

---

### Post by mrtomservo on 2009-04-10
Thank you very much for the replies.  I have indeed tried the tovid command without the "-ffmpeg" option, and tried a various assortment of others.  

I tried devede and it encoded perfectly!  Problem is it's got a gui, which I was trying to avoid.  Though maybe there's a way to to run that via cli too.  I'll figure that out on my own. :)

Thanks again!

---

### Post by Motorhead Kaze on 2009-08-22
Say kpkeerthi, you have any idea how to remove that ffmpeg option within the GUI? I used Tovid GUI all last year without any issue -- wish I could say that about DeVeDe -- but after reinstalling Hardy on a new computer, I reinstalled Tovid too and now the video/sound is all messed.

So if I don't use ffmpeg, how do I tell Tovid to pick something else instead?

Thanks!

---

