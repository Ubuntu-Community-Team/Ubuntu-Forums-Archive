---
title: "avi to dvd conversion"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by Homunculi on 2008-03-03
i am converting family videos i had saved in avi format ... 
now i have come across a problem ... 
all the files but one want to convert ... i get a core dump ... :confused:

i copied and recopies the file over and over ... just to see if it was a check sum error .. 
no deal ... 
same every time .. 
i finished my avi disks but one ... i do not know what the trouble is ,,, 
any thoughts ? 
will be greatly appreciated

:guitar:
rock on

---

### Post by kaens on 2008-03-03
What are you using to do the conversion?

---

### Post by Homunculi on 2008-03-07
this is what i use and the steps to do so .... 
mjpegtools, ffmpeg, transcode, dvdauthor, dvdrtools, dvd+rw-tools, K3b, file manager, and a terminal.

like i said all but one has converted .... i just want to know if i am doing something wrong ? 

1. Split the audio and video from the avi into an audio file and a movie file. Choose the right commands below according to where you live. For most of Europe & Australia, use PAL; for America, use NTSC. If you aren't sure what format to use, look at the chart on this site: [http://mightylegends.zapto.org/dvd/tv_standards.html](http://mightylegends.zapto.org/dvd/tv_standards.html)

For NTSC type: transcode -i bday1997.avi -y ffmpeg --export_prof dvd-ntsc --export_asr 3 -o movie -D0 -s2 -m movie.ac3 -J modfps --export_fps 29.97

For PAL type: transcode -i movie.avi -y ffmpeg --export_prof dvd-pal --export_asr 3 -o movie -D0 -s2 -m movie.ac3 -J modfps --export_fps 25

    * This first step takes the longest time to finish. 

2. Merge the audio and video into one mpg file.

In terminal type: mplex -f8 movie.ac3 movie.m2v -o movie.mpg

3. Create a file in text editor called dvdauthor.xml. Put what is shown below in the file and save the file. This is for a movie without a menu. If you want a menu or want to create more than one movie on a dvd disk, see the first link at bottom of this guide.

<dvdauthor dest="dvd"> <vmgm /> <titleset> <titles> <pgc> <vob file="movie.mpg" chapters="0,0:30,1:00,1:30,2:30,3:00,3:30,4:00"/> </pgc> </titles> </titleset> </dvdauthor>

4. Create a directory in your work folder called dvd and then run the following command in terminal: dvdauthor -x dvdauthor.xml

5. Make the dvd iso. In terminal type: mkisofs -dvd-video -udf -o dvd.iso dvd/

6. Open K3b and from the menu at top choose Tools > DVD > Burn DVD ISO Image. Click the browse button on the window that comes up and find the ISO file you have created. When it is finished checking the md5sum, click the Start button and it will start burning to your dvd disk. When it's finished you should have a dvd movie that can be played in any type of dvd player. 
:guitar:

---

### Post by kaens on 2008-03-07
It doesn't look like you're doing anything wrong - if it's just one file that's not working, it could be an encoding problem with that file (maybe?).

If it helps at all, you might want to take a look at [tovid]("http://tovid.wikia.com/wiki/Main_Page") - it's mainly a wrapper for the tools that you're using that makes dvd creation pretty easy from the command line.

---

### Post by Homunculi on 2008-03-16
well if i cannot get it i will take the vhs to the pro shop then ... 
it is the only one giving me trouble ...

---

### Post by Homunculi on 2008-04-17
ok new hard disk installed and upgraded to gutsy gibbon ... 
here is the trouble 
i go to transcode the video files and all i am getting is errors ... and in feisty fawn i did not have these errors .. 
goofy things that i am not sure about 
or i just need to find anther way that will work for me ... 
this is one of the msg i get 

vd$ transcode -i disney-vacation-2004.avi -y ffmpeg --export_prof dvd-nt
sc --export_asr 3 -o movie -D0 -s2 -m movie.ac3 -J modfps --export_fps 29.97
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg

[mpeg2video @ 0xb56a2ac8]rc buffer underflow
[mpeg4 @ 0xb56a2ac8]slice end not reached but screenspace end (-9 left 077F38, s
core= -4436)
[mpeg4 @ 0xb56a2ac8]concealing 792 DC, 792 AC, 792 MV errors
[mpeg4 @ 0xb56a2ac8]slice end not reached but screenspace end (-9 left 33766B, s
core= -16040)
[mpeg4 @ 0xb56a2ac8]concealing 792 DC, 792 AC, 792 MV errors
[mpeg4 @ 0xb56a2ac8]slice end not reached but screenspace end (-9 left 1FF703, s
core= -26019)
encoding frames [000000-181764],  59.20 fps, EMT: 1:06:21, ( 0| 0| 0)
clean up | frame threads | unload modules | cancel signal | internal threads | d                  one
[transcode] clipped 21870 audio samples
[transcode] encoded 181760 frames (0 dropped, 36352 cloned), clip length 7580.91  

or i get this trouble:
[transcode] V: video buffer     | 10 @ 720x480
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[import_ffmpeg.so] v0.1.12 (2004-05-07) (video) ffmpeg: MS MPEG4v1-3/MPEG4/MJPEG
[filter_modfps.so] v0.10 (2003-08-18) plugin to modify framerate
[filter_modfps.so] converting from 29.9700fps to 29.9700fps
[filter_modfps.so] No framerate conversion requested, exiting
[transcode] warning : filter plugin 'modfps' returned error - plugin skipped
[export_ffmpeg.so]: INFO: Set audio bit rate to 224 kbps
[export_ffmpeg.so]: INFO: Set audio codec to ac3
(aud_aux.c) Error: No Audio Module probed. Muting.
[mpeg2video @ 0xb560aac8]rc buffer underflow



if i am missing things from the upgrade .... i do not know .. when i did upgrade 
the updater told me there was no more support for packages or files on my computer 


any advice please ? ? ?

---

### Post by timcredible on 2008-04-17
i would go an easier route and try avidemux or devede or some other gui program to convert.  although last time i tried it, both avidemux and devede worked fine, but i had an issue with trying to get the 640x480 to look correct (i seem to remember it was either stretched or squished), don't remember what setting i had to change to get it to work.

if you have an avi file that's bad, avidemux should be able to fix it for you, even if you have to just delete part of the file to make it ok

---

### Post by Homunculi on 2008-04-17
i am just confused about the errors because in 7.04 i was not getting the trouble ... and the movies worked fine on the 42" wide screen ... 

and the movie clips were working fine ... 
no troubles at all in 

the nightmares of saving a few dollars ... but it is worth it at times ... 

if you got the links ... or are the packages in the apt package manager ?

the burners i have are 2 plextor and 1 pioneer

---

### Post by Homunculi on 2008-04-17
ok i got home and installed devede and avidemux ... 
ran the same video ....in both disks are great for the first 25 to 30 min ... 
then they start loosing time with audio and video ... and or the video starts blocking out ... 
is it settings in k3b ? 


i double checked the file it is fine when played in the movie player .. 
the file is in time all the way ... and i did one with the plextor and one with the poineer ... 

does any one know why i am having this trouble in gutsy ?
and it did not have this trouble in feisty ?  

:(

was really wanting to go up but if i have to restore and go back to feisty ...

---

### Post by Homunculi on 2008-05-05
after thinking it was my system i sis a little looking around and i came across an article about ffmpeg or transcode  having trouble ... 
i just restored my backup of 7.04 ff 

i will go up later when i can see that it will be stable and the troubles are resolved .... 

i had searched the errors i had gotten from the terminal window 
and that is how i found it ... i will look it up again and post the addy to the forum where i seen that ... other than that ... everything is working as it was ... 

thanks for the help :lolflag:

---

