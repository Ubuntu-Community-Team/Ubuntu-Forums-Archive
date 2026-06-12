---
title: "DvdStyler"
date: 2009-01-04
forum: Multimedia Software
---

### Post by firstc624 on 2009-01-04
I am trying to create a dvd menu using dvd styler.

can someone help me out.  I have created it and layed out the menus the way i would like it, but when i go to burn the didk the program crashed every single time.

I read somewhere that it could be a menu creation that causes the crash i can repeat the crash for as long as i want so i can help to diagnose this if someone can help me out.  I ran this command

gdb dvdstyler

when i try to burn it i get the following error 

Output #0, mpeg2video, to '/home/firstc624/dvd2/dvd/menu1-0.mpg_bg.m2v':
    Stream #0.0: Video: 0x0000, yuv420p, 720x480 [PAR 0:1 DAR 0:1], q=2-31, 6144 kb/s, 29.97 tb(c)

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7fdf3e41f780 (LWP 21162)]
0x00007fdf3b920d07 in sws_scale () from /usr/lib/libswscale.so.0
(gdb) 
(gdb) 
(gdb) Quit
(gdb) quit
The program is running.  Exit anyway? (y or n) y



Please help in anyway you can.

---

### Post by zeronothing on 2009-01-04
I'm not sure what version your using but on the getdeb [[COLOR="Blue"]website[/COLOR]]("www.getdeb.net") they have version 1.7.0. you might want to give it a shot to see if it fixed any of the issues you might be having. also on the get deb website they have the .deb package only available for ubuntu 8.10.

---

### Post by firstc624 on 2009-01-04
I am currently running version 1.7.0  

i am also currently running 64 bit verion of ubuntu.

If any more information is needed i will post it.



i just noticed i downloaded the i386 version from getdeb, i guess they don't have a an amd64 version.


UPDATE:  Went and downloaded from main website, they have a 1.7.1 for intrepid 64 bit.   will let you know if it helps

---

### Post by firstc624 on 2009-01-04
Ok new help.  I have the program running now, but am getting errors when tring to work w/ file
[HTML]DVDStyler v1.7.1
FFmpeg: libavformat 52.7.0, libavcodec 51.50.0, libavutil 49.6.0
Prepare
Cleaning temporary directory
Generating menus
Generating menu 1 of 2
Prepare
Create menu mpeg
Multiplexing subtitles (buttons) into mpeg
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>
INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
STAT: 0:00:00.000
INFO: Picture /home/firstc624/dvd3/dvd/menu1-0.mpg_buttons.png had 2 colors
INFO: Picture /home/firstc624/dvd3/dvd/menu1-0.mpg_highlight.png had 2 colors
INFO: Picture /home/firstc624/dvd3/dvd/menu1-0.mpg_select.png had 2 colors
INFO: Pickbuttongroups, success with 1 groups, useimg=1
INFO: Skipped 35280 bytes of garbage
INFO: Found EOF in .sub file.
INFO: Max_sub_size=580
WARN: Button y coordinates are odd for button button01: 304x328-386x355; they may not display properly.
WARN: Button y coordinates are odd for button button02: 360x376-456x403; they may not display properly.
INFO: 1 subtitles added, 0 subtitles skipped, stream: 32, offset: 0.00
Statistics:
- Processed 0 subtitles.
- The longest display line had -1 characters.
- The maximum number of displayed lines was 0.
- The normal display height of the font arial.ttf was 0.
- The bottom display height of the font arial.ttf was 0.
- The biggest subtitle box had 580 bytes.
Generating menu 2 of 2
Prepare
Create menu mpeg
Multiplexing subtitles (buttons) into mpeg
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>
INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
STAT: 0:00:00.000
INFO: Picture /home/firstc624/dvd3/dvd/menu1-1.mpg_buttons.png had 2 colors
INFO: Picture /home/firstc624/dvd3/dvd/menu1-1.mpg_highlight.png had 3 colors
INFO: Picture /home/firstc624/dvd3/dvd/menu1-1.mpg_select.png had 3 colors
INFO: Pickbuttongroups, success with 1 groups, useimg=1
INFO: Skipped 29177 bytes of garbage
INFO: Found EOF in .sub file.
INFO: Max_sub_size=1402
WARN: Button y coordinates are odd for button button01: 304x312-424x335; they may not display properly.
WARN: Button y coordinates are odd for button button02: 360x368-514x395; they may not display properly.
WARN: Button y coordinates are odd for button button03: 424x424-554x447; they may not display properly.
INFO: 1 subtitles added, 0 subtitles skipped, stream: 32, offset: 0.00
Statistics:
- Processed 0 subtitles.
- The longest display line had -1 characters.
- The maximum number of displayed lines was 0.
- The normal display height of the font arial.ttf was 0.
- The bottom display height of the font arial.ttf was 0.
- The biggest subtitle box had 1402 bytes.
Create VOB files
Transcode video file: /home/firstc624/Tape 1.vob
Input #0, mpeg, from '/home/firstc624/Tape 1.vob':
  Duration: 00:24:00.60, start: 0.500000, bitrate: 6310 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 9000 kb/s, 29.97 tb(r)
    Stream #0.1[0x80]: Audio: 0x0000
Output #0, dvd, to '/home/firstc624/dvd3/dvd/title0-0-0.vob':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 0:1 DAR 0:1], q=2-31, 9000 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: 0x0000
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
sample rate not set
Could not write header for output file #0 (incorrect codec parameters ?)
Error by transcoding of /home/firstc624/Tape 1.vob[/HTML]

---

### Post by zeronothing on 2009-01-04
do you have the ubuntu-restricted-extas package installed? that has all or most of the codecs required to encode videos and watch video files.

---

### Post by zeronothing on 2009-01-04
You might want to try out QDVDAuthor as another way to create your own dvd's. I'm just throwing out another option at you if you keep having problems.

---

### Post by firstc624 on 2009-01-04
Ok i did not have the restriced stuff enabled and i thought i did, but that did nolve my problem.  here is what the program says upon tring to create the dvd.

[HTML]DVDStyler v1.7.1
FFmpeg: libavformat 52.7.0, libavcodec 51.50.0, libavutil 49.6.0
Prepare
Cleaning temporary directory
Generating menus
Generating menu 1 of 2
Prepare
Create menu mpeg
Multiplexing subtitles (buttons) into mpeg
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>
INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
STAT: 0:00:00.000
INFO: Picture /home/firstc624/dvd3/dvd/menu1-0.mpg_buttons.png had 2 colors
INFO: Picture /home/firstc624/dvd3/dvd/menu1-0.mpg_highlight.png had 2 colors
INFO: Picture /home/firstc624/dvd3/dvd/menu1-0.mpg_select.png had 2 colors
INFO: Pickbuttongroups, success with 1 groups, useimg=1
INFO: Skipped 35280 bytes of garbage
INFO: Found EOF in .sub file.
INFO: Max_sub_size=580
WARN: Button y coordinates are odd for button button01: 304x328-386x355; they may not display properly.
WARN: Button y coordinates are odd for button button02: 360x376-456x403; they may not display properly.
INFO: 1 subtitles added, 0 subtitles skipped, stream: 32, offset: 0.00
Statistics:
- Processed 0 subtitles.
- The longest display line had -1 characters.
- The maximum number of displayed lines was 0.
- The normal display height of the font arial.ttf was 0.
- The bottom display height of the font arial.ttf was 0.
- The biggest subtitle box had 580 bytes.
Generating menu 2 of 2
Prepare
Create menu mpeg
Multiplexing subtitles (buttons) into mpeg
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>
INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
STAT: 0:00:00.000
INFO: Picture /home/firstc624/dvd3/dvd/menu1-1.mpg_buttons.png had 2 colors
INFO: Picture /home/firstc624/dvd3/dvd/menu1-1.mpg_highlight.png had 3 colors
INFO: Picture /home/firstc624/dvd3/dvd/menu1-1.mpg_select.png had 3 colors
INFO: Pickbuttongroups, success with 1 groups, useimg=1
INFO: Skipped 29177 bytes of garbage
INFO: Found EOF in .sub file.
INFO: Max_sub_size=1402
WARN: Button y coordinates are odd for button button01: 304x312-424x335; they may not display properly.
WARN: Button y coordinates are odd for button button02: 360x368-514x395; they may not display properly.
WARN: Button y coordinates are odd for button button03: 424x424-554x447; they may not display properly.
INFO: 1 subtitles added, 0 subtitles skipped, stream: 32, offset: 0.00
Statistics:
- Processed 0 subtitles.
- The longest display line had -1 characters.
- The maximum number of displayed lines was 0.
- The normal display height of the font arial.ttf was 0.
- The bottom display height of the font arial.ttf was 0.
- The biggest subtitle box had 1402 bytes.
Generating DVD
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>
INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
WARN: First cell is not marked as a chapter in PGC 0, setting chapter flag
STAT: Picking VTS 01
STAT: Processing /home/firstc624/dvd3/dvd/menu1-0.mpg...
WARN: unknown mpeg2 aspect ratio 1
WARN: Partial sector read (1220 bytes); discarding data.
INFO: Video pts = 0.000 .. 0.033
STAT: Processing /home/firstc624/dvd3/dvd/menu1-1.mpg...
WARN: unknown mpeg2 aspect ratio 1
Error executing of command: dvdauthor -o "/home/firstc624/dvd3/dvd" -x "/home/firstc624/dvd3/dvd/dvdauthor.xml"
[/HTML]

---

### Post by OrangeVixen on 2010-03-27
Just to let you know, I'm getting the same crash on DVDStyler version 1.7.2, it happens when I try to burn to either an ISO image or DVD it always crashes during the "Create menu mpeg" line on the "Generate DVD" dialog.

---

