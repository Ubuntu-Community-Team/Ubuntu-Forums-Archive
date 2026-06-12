---
title: "Enjoy Ibulk: bulk video converter for viewing on the Ipod."
date: 2010-06-17
forum: Multimedia Software
---

### Post by d3v1150m471c on 2010-06-17
I've been working on a small program to perform a very specific and useful task of quickly and efficiently converting videos to go on any Apple Ipod or Iphone. This includes both classic and 5th generation Ipods as well. Ibulk is a command-line only program but incredibly easy to use and runs off FFmpeg with AAC functionality. The program comes with a Read Me file which will explain its options and instructions in concise detail. Ibulk converts several videos in its input folder to the desired H.264 or XviD video encoding to its output folder. All videos are created in mp4 format with 160Kbps 48000Hz audio sound quality (highest setting an Ipod can handle) and both video encoders at the highest bitrate an Ipod can handle with the exception of some videos which will be auto-adjusted to meet the Ipod's requirements. Ibulk is written in the native unix/linux language and so it should work on any linux distro.
[[COLOR=Red][/COLOR]]("http://www.mediafire.com/?zmlmymnjgch")

---

### Post by d3v1150m471c on 2010-06-18
The download and source code is also available at **[sourceforge]("https://sourceforge.net/projects/ibulk/")** for those of you who are interested.
[**Source Code**]("https://sourceforge.net/projects/ibulk/files/")

---

### Post by d3v1150m471c on 2010-06-19
bravo uniform mike papa

---

### Post by d3v1150m471c on 2010-07-04
I've just finished ibulk_1_7_0 and the coding the project coming out rather nicely. here's its current synopsis:

```

Ibulk 1.7.0: Converts all videos in /home/d3v11/Ibulk/input to
/home/d3v11/Ibulk/output for use on an Apple Ipod or Iphone. All
videos will be encoded inside an .mp4 container.

usage: ibulk [ -L or -H ] [ -I, -T, or -P ]
                     OR
       ibulk [ -v, -c, or -h ]

-L Converts videos with H.264 encoding. This option may
   create large videos and take significantly longer
   to encode but with higher quality.

-H Converts videos with XviD encoding. This option sacrifices
   some quality but makes smaller videos and takes less time
   to encode.

-T Converts videos with a 640x480 ratio. Best if viewing
   video on a television via adaptor.

-I Converts videos with a 320x240 ratio. Best if viewing
   video on an ipod.

-P Converts videos with a 480x320 ratio. Best if viewing
   video on an iphone.

-r Repairs Ibulk directories and files if not found. Set this
   flag initially when installing Ibulk as directed in the
   included Read Me file.

-v Displays Ibulk's version number.

-c Display contact information.

-h Gives a brief summary of the program, its usage, and its
   options. 

```

---

### Post by d3v1150m471c on 2010-07-07
added more functionality to the code with a single video conversion option:

```

Ibulk 1.8.0: Converts all videos in /home/d3v11/Ibulk/input to
/home/d3v11/Ibulk/output for use on an Apple Ipod or Iphone. All
videos will be encoded inside an .mp4 container.

usage: ibulk [ -L or -H ] [ -I, -T, or -P ]
                     OR
ibulk -S /home/d3v11/folder/video [ -L or -H ] [ -I, -T, or -P ]
                     OR
           ibulk [ -v, -c, or -h ]

-L Converts videos with H.264 encoding. This option may
   create large videos and take significantly longer
   to encode but with higher quality.

-H Converts videos with XviD encoding. This option sacrifices
   some quality but makes smaller videos and takes less time
   to encode.

-S Converts a single video. If using this option you must use
   the full path to the video. Aliases or variables in the
   path cannot be used. See usage note above for details.

-T Converts videos with a 640x480 ratio. Best if viewing
   video on a television via adaptor.

-I Converts videos with a 320x240 ratio. Best if viewing
   video on an ipod.

-P Converts videos with a 480x320 ratio. Best if viewing
   video on an iphone.

-r Repairs Ibulk directories and files if not found. Set this
   flag initially when installing Ibulk as directed in the
   included Read Me file.

-v Displays Ibulk's version number.

-c Display contact information.

-h Gives a brief summary of the program, its usage, and its
   options.


```

---

### Post by docsmooth on 2011-07-29
Bump - any work for Natty? gtkdialog and libavcodec-unstripped-52 don't appear post-maverick versions that I can find, including multiverse and mediabuntu.

---

