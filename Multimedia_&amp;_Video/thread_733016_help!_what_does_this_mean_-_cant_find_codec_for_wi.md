---
title: "help! what does this mean - cant find codec for windows audio speech format ax0"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by bigfoot1979 on 2008-03-23
no sure what to do about this. Using ubuntu 7.10, playing an avi file on mplayer... 

Any help out there?

---

### Post by pytheas22 on 2008-03-23
It means that you're missing the proprietary codec to play the kind of file you want ("avi" is just a wrapper for multimedia files that could contain lots of different kinds of formats, so just because you can play one multimedia file with an .avi extension doesn't mean you can play others).  Do this to make sure that all of the non-free codecs are installed:
```

sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg streamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly
```

---

### Post by bigfoot1979 on 2008-03-23
Cheers, 

I tried it and got this - but I'm not sure what to do next. am I missing the streamer0.10-fluendo-mp3? 

I'm pretty amazed at how all you guys know these codes, where do you learn this stuff from? I just find Ubuntu so difficult and frustrating. 

haydn@ubuntu:~$ sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg streamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly
[sudo] password for haydn:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
E: Couldn't find package streamer0.10-fluendo-mp3
haydn@ubuntu:~$

---

### Post by pytheas22 on 2008-03-23
> I'm pretty amazed at how all you guys know these codes, where do you learn this stuff from? I just find Ubuntu so difficult and frustrating.

I don't know these codes, I just find them on websites by searching for stuff like "ubuntu install proprietary codecs" on Google or within these forums :)  You'll get more comfortable with these things as you learn more about Ubuntu and how to get support.

Anyway, the reason this didn't work at first is because there was a typo in the code that I copied and pasted from this website [http://linuxhelp.blogspot.com/2007/10/install-multimedia-codecs-in-ubuntu-710.html](http://linuxhelp.blogspot.com/2007/10/install-multimedia-codecs-in-ubuntu-710.html); try this instead:
```

sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3
```

and post your results.

---

### Post by bigfoot1979 on 2008-03-23
hi, 

cheers for the code again. the new one you sent worked a treat and now can watch avi on Mplayer.

Won post the terminal output because it was rather long. 

Solution FOUND!

thanks

---

### Post by pytheas22 on 2008-03-23
Glad it worked; good luck with Ubuntu!

---

