---
title: "Convert an MKV file to a DVD ?"
date: 2008-06-05
forum: Multimedia Software
---

### Post by MrGando on 2008-06-05
Hi guys , I downloaded some movies in .mkv format. I wanted to know if it's possible to convert a .mkv to a DVD,  so I can watch it on my DVD player ( and TV of course ). 

Thanks.

---

### Post by kaston on 2009-05-01
i'd like to know this as well.  i've searched the forums but haven't found an answer yet.  ideally i'd like to be able to do this with a single easy-to-use tool

---

### Post by canada72 on 2009-05-01
Yes you can. You need Convert X to DVD, which you'll have to run with Wine. It will convert avi mpeg mkv and other formats to DVD(iso).

---

### Post by kaston on 2009-05-01
do you need wine because it is a windows program?  if so i guess i can run it on my winxp virtualbox.  but i would rather not have to send data between vbox and ubuntu.  

i have also read that some people use Devede, but it apparently shrinks the size of the file when making the DVD according to this guy:  [http://forum.videohelp.com/topic349005.html](http://forum.videohelp.com/topic349005.html)

are there any other options out there?

---

### Post by Ericyzfr1 on 2009-05-01
I believe that Handbrake or Devede could do it.

---

### Post by blackgr on 2009-05-01
Devede does the job! I make dvds all the time from avis.Its great tool.

---

### Post by kwacka on 2009-05-17
Another app is avidemux - in the repos.

---

### Post by yunone on 2009-08-08
> **blackgr said:**
> Devede does the job! I make dvds all the time from avis.Its great tool.

he is talking about making a dvd from a MKV file, is that what you are doing or just going from AVI to DVD?

---

### Post by killabee44 on 2010-01-31
Devede did the job for me converting an MKV file to DVD. No problem whatsoever. Quality was good. Took a long time though.

---

### Post by in.the.darkside on 2010-02-09
Hello,
Devede works, but it doesn't allow you to choose more than one audio for your dvd. I'm looking for a program that allows you to convert a mkv file to a dvd but keeping the different audios and subtitles of the original file. If anyone knows a program to do so, please let me know. 
Thank you.

---

### Post by pariah62038 on 2010-06-20
I am also looking for a program that does that, I don't mind using wine for it, but I can't find anything.

---

### Post by mocha on 2010-10-03
tovid can do MKV to DVD with multiple audio streams.  Read the man page.  An example would be something like this:

```
tovid -dvd -ntscfilm -aspect 185:100 -vbitrate 4600 -audiotrack 1,2 -in input.mkv -out output.mpg
```

-audiotrack 1,2 is what tells tovid to encode audio tracks 1 and 2 to the resulting mpg/dvd file.  Use something like idvid or mediainfo to find out the numbers of the audio tracks you want included.

---

### Post by mrhhug on 2010-12-19
I found mkvmerge GUI (part of mkvtoolnix)the best for me, would edit the subtitles and audio then save. then create my ISO from devede

add something like this to your source
Version	APT source
Stable (aka "lenny")	
deb [http://www.bunkus.org/debian/lenny/](http://www.bunkus.org/debian/lenny/) ./
deb-src [http://www.bunkus.org/debian/lenny/](http://www.bunkus.org/debian/lenny/) ./ 
Testing 
(aka "squeeze")	deb [http://www.bunkus.org/debian/squeeze/](http://www.bunkus.org/debian/squeeze/) ./
deb-src [http://www.bunkus.org/debian/squeeze/](http://www.bunkus.org/debian/squeeze/) ./ 
Unstable (aka "sid")	
deb [http://www.bunkus.org/debian/sid/](http://www.bunkus.org/debian/sid/) ./
deb-src [http://www.bunkus.org/debian/sid/](http://www.bunkus.org/debian/sid/) ./

---

### Post by dirtrider1 on 2011-05-16
Devede will convert Avi and Mkv to DVD, you might also try Mandvd as well.

---

### Post by appalbarry on 2012-02-12
One more vote for Devede.  The madness of competing codecs and wrappers is why downloading movies will never pose a serious threat to the multinationals.

All that I wanted to do was download the last six episodes of a T V series, put them on a USB stick, and play them on my quite recent, USB ported DVD player.

YEE GODS! I tried a handful of programs in both Windows and Mint Linux, and finally used Devede to turn the MKV files into burned DVDs.

That's just insane.

---

