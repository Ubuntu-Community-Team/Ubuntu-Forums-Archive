---
title: "Converting DVD's to PS3 compatable format?"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by sirskeleton on 2007-09-06
I was just wondering what the best tool or method of turning DVDs to PS3 compatible formats.

# MPEG-4 SP (AAC LC)
# H.264/MPEG-4 AVC Main Profile (AAC LC)
# MPEG-1 (MPEG Audio Layer 2)
# MPEG-2 PS (MPEG2 Audio Layer 2, AAC LC, AC3(Dolby Digital), LPCM)
# MPEG-2 TS (MPEG2 Audio Layer 2)

I'm not sure which one is best for the PS3 so any help would be .... helpful.

---

### Post by lisati on 2007-09-06
I haven't tried it with "Wine" (on Ubuntu) yet but I use a Windows program called "Pinnacle Studio" which can output files in a variety of formats.

The publisher's website can be found at [www.pinnaclesys.com](www.pinnaclesys.com)

---

### Post by sirskeleton on 2007-09-06
I was looking more for a linux based solution...im too broke to buy stuff.

---

### Post by sirskeleton on 2007-09-07
bumpity bump bump

---

### Post by Npl on 2007-09-08
H.264/MPEG-4 AVC would be the best choice (concerning quality per filesize).

x264 is a free encoder, and I believe mplayer/mencoder uses it (but I dont have experience with those, Im using megui+x264 on windows). [Doom9]("http://www.doom9.org/") has some profiles, so the created file is compatible with PS3.

---

### Post by JOWIROMA on 2007-09-10
Well, This is what I have been doing to get movies that I rent to be ripped.

1st: I downloaded a program called Vobcopy you can get it from the repositories...
then I insert the dvd into the drive and put in a terminal: 
```
 vobcopy -m 
```

and this will rip the full dvd content into my home folder.

2nd: I downloaded a program called HandBrakeCLI from:
[http://handbrake.m0k.org/?article=download](http://handbrake.m0k.org/?article=download)
and then put the shell of the downloaded file into /usr/bin.
now in a terminal: 
```
 HandBrakeCLI -i /home/monark/themovie -o /home/monark/desktop/ps3movie.mp4 
```

where "-i" would be your input file or media and "-o" would be your output file and I know that I have more options in the command line that I used for subtitles and quality but right now I am at work and I do not remember them but I will post them for you as soon as I get home if you want...

and another thing you can use Handbrake to rip your dvd and encode them directly without putting them in your hard drive because this takes a lot of space, it would be:
```
 HandBrakeCLI -i /media/themovie -o /home/monark/desktop/ps3movie.mp4 
```

now I copy the dvds into my hard drive because I rent the movies so some times I do not have the time to covert them (for me it takes almost 6 hours to convert because I use 2 passes to get a better quality and my computer is a little bit old) so I copy them and then  when I have the time I just put my computer to rip the movies and then when handbrake is done with the process I just erase the vob file of the movie letting free almost 9gb of mu hdd.

I hope this help some of you... I will post my full script so you can see what I used to convert my movies to play in the PS3...

now FYI I use a program called mediatomb, this is a mediaserver software I use to stream the movies from my PC to my PS3 on my network like an AppleTV or like
a WindowsMediaPlayer style without using your PS3 hard drive space so I play them from my PC through my PS3 and even you can use it to copy the files into your PS3 over the network so you wont have to used a cd or memory stick to move your movies or music to your PS3; neat ah???

---

### Post by sirskeleton on 2007-09-10
Tried what you said JOWIRAMA. It works nice but, takes forever. Could I save time by just using my dvd drive as the -i ?

---

### Post by JOWIROMA on 2007-09-10
> **sirskeleton said:**
> Tried what you said JOWIRAMA. It works nice but, takes forever. Could I save time by just using my dvd drive as the -i ?

YEAH SURE: 
```
 HandBrakeCLI -i /media/themovie -o /home/yourhome/Desktop/ps3movie.mp4
```

let me know if you want to see my option for the encoding

oh! I told you that it takes a lot of time. if you do it one pass it could take 2:30 hours and double if you do it 2 pass.
I just do this on the weekends, I just put it to run in the morning and I just go do my things and when I am back it is done..
PATIENCE!!!!!

---

### Post by seb3000 on 2007-09-27
JOWIROMA,

How've you configured Mediatomb so that you're able to view the Handbrake-created H264 mp4 files on your PS3? My PS3 sees Mediatomb, but playback ends with an error right after briefly displaying a black screen. (Images and music work fine.)

Thanks!

---

### Post by JOWIROMA on 2007-10-01
> **seb3000 said:**
> JOWIROMA,

How've you configured Mediatomb so that you're able to view the Handbrake-created H264 mp4 files on your PS3? My PS3 sees Mediatomb, but playback ends with an error right after briefly displaying a black screen. (Images and music work fine.)

Thanks!

I am sorry man it took me so long to answer but your problem might be the encoding through HandBrake,
could you post your HandBrake script and I will post mine tonight so you can see the differences, what it is happening to you happened to me and my problem was that I was using a wrong codec for the audio so when I ran Mediatomb you could see the files on the ps3 but when I tried to play them I had the same error as you.
So show me your script and I will help you find a solution.

---

### Post by JOWIROMA on 2007-10-01
These are my HandBrake scripts:

These are my settings for a movie:
```

HandBrakeCLI -i /home/path-to-movie/dvdmovie -o /home/target-path/Desktop/YOUR-PS3MOVIE.mp4 -e x264b30 -E faac -2 -b 800 -B 128 -t 1 -s 1 

```

These are my settings for a movie or show that is natively for tv, like a tv show or something
like that (ex: family guy, venture brothers, the office...)
```

HandBrakeCLI -i /home/path-to-tvshow/tvshow -o /home/target-path/Desktop/YOUR-PS3TVSHOW.mp4 -e x264b30 -E faac -2 -b 800 -B 128 -t 4 -s 1 -d

```

where:

-e x264b30   is your video encoder

-E faac           is your audio encoder

-b 800            is your video bitrate

-B 128            is your audio bitrate

-t 4                  is your title (for movies is usually 1 but just to be sure run the script with number   0 and the HandBrake will scan the movie and on the result look for the biggest title and that would be the title that contains the movie that it is the one you want to put on option "-t".

-s 1  is for subtitles, I like my movies with subtitles but if you do not want them just do not put the option.

-d this is to use deinterlace option and I used only for tv shows and tv movies.


Now "seb3000" the same error that you have now, I got it because I was using another encoder for the audio and now with the settings shown above my PS3 play the files directly in the PS3 HDD or through Mediatomb media server without any problems...

let me know if you have any questions and I hope that all this can help you.

---

### Post by dthiery on 2007-11-12
The PS3 will play VOB files perfectly fine on their own (from a media server or copied to the PS3) and you can skip the handbrake step entirely.  I just use:

vobcopy -l -i /path/to/dvd

and then just use the resulting vob file.  So far I've only noticed one problem with this; on some movies (only one I've tried so far) I get spanish audio.  I'm not sure why that happened and have yet to find a way around it, but since it's only one of my movies so far, I can live with using handbrake on that one.

Dave

---

### Post by JOWIROMA on 2007-11-26
> **dthiery said:**
> The PS3 will play VOB files perfectly fine on their own (from a media server or copied to the PS3) and you can skip the handbrake step entirely.  I just use:

vobcopy -l -i /path/to/dvd

and then just use the resulting vob file.  So far I've only noticed one problem with this; on some movies (only one I've tried so far) I get spanish audio.  I'm not sure why that happened and have yet to find a way around it, but since it's only one of my movies so far, I can live with using handbrake on that one.

Dave

Hey, what would be the quality of the video and size of file using that method???

---

### Post by dthiery on 2007-12-20
Sorry for taking so long to reply!

The quality is the exact same as the DVD itself.

---

### Post by davidme on 2007-12-22
Found this:

#
#
3) PS3
#
./HandBrakeCLI -i DVD -o ~/Movies/movie.mp4 -B 160 -R 48 -E AAC -e x264 -f MP4 -m -p -b 2500 -x level=41

From here: [http://snipplr.com/view/3056/handbrake-cli-presets/](http://snipplr.com/view/3056/handbrake-cli-presets/)

---

### Post by atypicalwinter on 2008-01-10
im very much a newbie when it come sto linux but i was wondering how i can change the output file of vobcopy to an external hdd as the 10gb space availible on ps3 is not enough lol thanks for anyone help in advance :)

---

