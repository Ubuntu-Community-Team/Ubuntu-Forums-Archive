---
title: "Video Capture - Scratching My Head..."
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by jmchaffie on 2007-09-04
I've downloaded and installed about every vid capture program out there and am still befuddled as to why I am coming up with such ragged and slow frame rates on my computer.

I'll start with Xvidcap as it seems the most popular and just give you specs and you tell me if I'm just setting things up wrong or if I need something different...

My specs first off are:
AMD64 - 2xCore (running 32-bit Ubuntu Studio (Feisty))
2GB memory
Nvidia 512 MB 6600 PCI express
Brand new ASUS board

I have great system performance all around, gaming is sweet, Second Life is smooth as butter (well aside from laggy days in SL) I can run Beryl like it's yesterday's GL scrap, BUT... if I try to run ANY video captue software.. no matter what settings I use (DivX defaults, low framerates, Shockwave, flash, mpeg, you name it) I get dropped frames down to 6 fps or worse, and I ca't figure it out.

I see videos all the time on YouTube and such where people are doing full screen captures that look great. I need to do some scrren captures for a contest, and Istabul gets the closest in ogg format, but still only if I select a small window and it still jerks a bit.

Any help is much appreciated...
 -John

---

### Post by loell on 2007-09-04
perhaps you can try the latest version of recordmydesktop for fiesty, it had some little speed improvements

[http://ubuntuforums.org/showthread.php?t=294605]("http://ubuntuforums.org/showthread.php?t=294605")

---

### Post by jmchaffie on 2007-09-04
I appreciate it.

I'm getting a file read error though when I try to use your application. I have tried changing the temporary file location to my own home directory, I have tons of drive space ,etc... however here is the message I get...

Recording is Finished.
RecordMyDesktop has exited with status: 3328
Description: Cannot open file for writing.

It does this 1 second or so after clicking the record button. I've tried renaming the file, changing directory loactions (the working directory anyway), etc.

Not sure what's involved.

Thanks again!
John

---

### Post by loell on 2007-09-04
could you reboot, and see if the problem persist. by default the recorded video will be on your home  directory is (/home/your_username) with an ogg format.

---

### Post by jmchaffie on 2007-09-04
Thank you again btw...

Unfortunately the same error persists. Just to be sure I did things properly...
I made sure I didn't have any previous version by running remove first (I never seem to realize I might or might not already have a version of a multimedia app in Studio ;)

Then I ran:  sudo apt-get install recordmydesktop gtk-recordmydesktop

Everything installed without any errors or problems.

When I start the program, it of course starts at a good framerate with sound disabled, I went ahead and turned the frame rate down a bit, chose 'Save As' - entered in 'Test01.ogg' and left it in /hom/jmchaffie - my regular home directory it had chosen.

It stopped immediately reporting the error in my previoius post, and no matter what I try, changing temporary file location, my saved file location, settings, what not. It's the same result.

Hope that helps some...

---

### Post by jmchaffie on 2007-09-05
HEY! Got the software working, but still have frame rate issues. 

Upon reccomendation from a friend - On a windows XP partition that I hadn't used in almost a year, I booted it up and installed a video capture program called FRAPS.

I was able to get perfect, smooth video capture at full screen even.

So there has to be a program for linux, whether it be one of the ones I have, or another one that will do the same. Like I said, with all the linux vids online out there... there has to be something.

I have consistently had better fps on gaming and video in linux compared to windows, so I must have some donked settings or am not doing something right, any help would be much appreciated. 

THANK YOU!
- John McHaffie

(Also: don't forget, although I'm getting awesome gaming and video response - doesn't mean I don't have something else setup wrong - I am NOT trying to insinuate a performance issue with any of the software packages themselves, as it's obvious they work for many other people!!! )

---

### Post by loell on 2007-09-05
```
HEY! Got the software working, but still have frame rate issues.
```

is this recordmydesktop, if so, is it from the repository? or is from the link i gave above?


would you like to record games or just a desktop demo?
if it is opengl based games that you'd like to record, i think

you need [yukon capture program]("http://www.neopsis.com/projects/yukon/")

---

