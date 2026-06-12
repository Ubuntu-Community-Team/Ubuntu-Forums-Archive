---
title: "Thumbnail generator for videos?"
date: 2008-05-30
forum: Multimedia Software
---

### Post by Aahz on 2008-05-30
Hello !

Here is the following question for the ubuntu gurus: I need a program/plugin that would scan a movie, make screenshots at small intervals and then compile them into one big(or small) jpeg picture, preferably also by adding the name of the video, duration, and quality.

Is there such a program? This is also important in a linux/windows fight with my friend, as he says ubuntu can't do this :popcorn:

P.S. I need the proggie to do a comprehensive backup/preview of my major movie collection.

---

### Post by abhiroopb on 2008-05-30
Could you clarify please: you want to make screenshots at regular intervals, yet you want them "compiled" into ONE jpeg picture? If you just want to take ONE screenshot of ONE movie thats a different issue altogether.

---

### Post by shusai on 2008-06-28
There is exactly such a program but I forgot it's name after making a fresh installation. ](*,)

It worked great with all movies I tried, you can configure almost everything, like how many images you want, the size, time, frames, distance between pictures, you can delete single images and of course it will add various informations to the final single picture like name, duration, size, codecs, ...

It would be great if someone knew this program!

---

### Post by Gunman1982 on 2008-06-28
Short use of google an e voila: [http://tobyinkster.co.uk/blog/2007/08/19/dhyana/]("http://tobyinkster.co.uk/blog/2007/08/19/dhyana/")

---

### Post by shusai on 2008-06-28
No, I found many similar scripts like that, most of them using mplayer or ffmpeg, but the program I am looking for had a nice GUI and was really easy to use...

---

### Post by forger on 2008-06-28
post back if you remember ;)

edit: it shouldn't be that hard to create a "gui" using zenity

I found ffmpegvideothumbnailer in the repositories:
> 
Package: ffmpegthumbnailer
Description: fast and lightweight video thumbnailer
 FFmpegthumbnailer is a lightweight video thumbnailer that can be used by file
 managers to create thumbnails for your video files. The thumbnailer uses ffmpeg
 to decode frames from the video files, so supported videoformats depend on the
 configuration flags of ffmpeg.

> 
$ ffmpegthumbnailer
invalid arguments
Usage: ffmpegvideothumbnailer [options]

Options:
  -i<s>  : input file
  -o<s>  : output file
  -s<n>  : thumbnail size (default: 128 )
  -t<n>  : time to seek to (percentage) (default: 10)
  -f     : create a movie strip overlay
  -w     : workaround issues in old versions of ffmpeg
  -h     : display this help


---

### Post by forger on 2008-06-28
ok, the answer for a gui is qframecatcher:
[http://developer.berlios.de/projects/qframecatcher/](http://developer.berlios.de/projects/qframecatcher/)

```

sudo apt-get install libqt4-dev libxine-dev build-essential
wget http://download.berlios.de/qframecatcher/qframecatcher-0.4.1.tar.gz
tar xzf qframecatcher-0.4.1.tar.gz; cd qframecatcher/src
qmake; make; ./qframecatcher

```

(the image that contains all the frame images is referred below as "the BIG image")

1) menu File > Options
Frames to capture = set how many frames you want to capture
Image width / height = the frame image width and height (not the BIG image)
Margin = margin between frame images
Columns = columns for the frame images, say you set "frames to capture" as 24 and 6 columns will create a 6 column x 4 in each column BIG image
Press Ok
2) Load your movie / video file
3) Click the "Save file" button to save them all in ONE BIG image, or "Save folder" to output each frame separately.

---

### Post by xc3RnbFO8P on 2008-06-28
delete

---

### Post by shusai on 2008-06-28
I finally found it! :D
As I didn't find it with Google anymore, I searched my 10 MB big history.dat in my /home backup and there it was:

[SIZE="4"][VideoCut]("http://www.kde-apps.org/content/show.php/show.php?content=60826&")[/SIZE]

---

### Post by lovinglinux on 2008-09-05
> **shusai said:**
> I finally found it! :D
As I didn't find it with Google anymore, I searched my 10 MB big history.dat in my /home backup and there it was:

[SIZE="4"][VideoCut]("http://www.kde-apps.org/content/show.php/show.php?content=60826&")[/SIZE]

Thank you very much. I was also looking for something like this. VideoCut is perfect, even better than Media Player Classic, which I used for the same task on Windows.

---

### Post by lproe on 2008-12-12
qframecatcher is a great program and I like it a lot.  It was working good with debian etch and then it stopped working when I upgraded to lenny.  As a matter of fact,  qframecatcher does not work with debian lenny.  ubuntu 8.10 or kubuntu 8.10.  When I use it to catch frames for the vide, all I get is the specification for the video and no pictures.  

If someone and tell me how to fix this, I will really be happy.

  










thank you and 

thank you for using linux


lee

---

### Post by johnhammonds on 2009-04-07
I hate to dig up an old thread and ask such an off the wall question, but I've about came to my ropes end with this.

I'm trying to find a program like this for OS X Leopard. I know this is the Ubuntu forum, but I've gotten pretty desperate. The mac forums I've tried have gone unanswered and figured by chance someone here just might know.

Freeware, shareware, payware, Idon'tcareware!

Something!

I need a program just like described in the first post of this thread. VideoCut, qframecatcher, Media Player Classic.

Something to take a video file and output a certain amount of thumbnails into one picture file so I can show a preview of some of my movie files.

Example:


Any help would be GREATLY appreciated! ;-)

---

### Post by johnhammonds on 2009-04-09
I know this was an odd place to ask about a Mac app, but since I did and now that I found a solution, I wanted to at least post up about it.

The good news is it is a Freeware app and you can download the source code from the authors site as well.

The program is called Screen Grabber v2.0.2

Link:

```
http://www.peylow.se/screengrabber.html
```

I have to give credit to angel1g7 on another forum as he passed the link to me.

I'm so glad he did. I was really beating my head against the wall over it. ](*,)

---

### Post by Scifer on 2010-10-28
> **shusai said:**
> I finally found it! :D
As I didn't find it with Google anymore, I searched my 10 MB big history.dat in my /home backup and there it was:

[SIZE=4][VideoCut]("http://www.kde-apps.org/content/show.php/show.php?content=60826&")[/SIZE]
Thank You so much! I was looking for a tool like this for months.

---

### Post by X_Splinter on 2012-04-13
I was a looking for one that you could manually select each thumb like Image Grabber II for Windows.

---

