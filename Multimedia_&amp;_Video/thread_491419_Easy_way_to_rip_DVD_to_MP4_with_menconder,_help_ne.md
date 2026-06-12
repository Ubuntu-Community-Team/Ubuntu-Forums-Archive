---
title: "Easy way to rip DVD to MP4 with menconder?, help needed"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by kirbyboy on 2007-07-03
Hi, i would like to see my DVD's in PSP and i would need to encode them to MP4, after searching the web, it looks like the best way is using mencoder, but the problem i have is that mencoder has a LOOOOOT of options, and i don't understand them very well, can somebody tell me the code to make a MP4 with good quality for my PSP?, thanks.

---

### Post by lintoon on 2007-07-03
Try VLC media player.  Go to File-Wizard and follow the instructions.  Dvd is an input option and MP4 is an output option.  I've never tried it but it seems easy enough.  

Or maybe try Avidemux.

---

### Post by kirbyboy on 2007-07-04
Avidemux looks like very hard to install, is it in the repositories?, there are not instructions in web page about install it in Feisty Fawn.

I'll try later about VLC, can you change bitrates and fps with VLC?

---

### Post by lintoon on 2007-07-04
I'm almost certain it is.  I installed it a long time ago and can't remember.  When I installed Ubuntu originally I enabled the universe repositories so maybe it is in there.  Just use synaptec package manager to install it.

I'm at work at the minute so I will check vlc when I get home.

---

### Post by kirbyboy on 2007-07-04
I'm using Avidemux but it crashes, i have this message in terminal(if i run from terminal, is the only way of getting error messages that i know):

(avidemux:7341): Gtk-CRITICAL **: gtk_box_pack_end: assertion `child->parent == NULL' failed (Lots of times)

No accelerated IMDCT transform found
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 
Output #0, mp4, to '/media/hdb1/job1':
  Stream #0.0, 29,97 fps(c): Video: 0x0000, 320x240, q=2-31, 2000 kb/s
  Stream #0.1: Audio: 0x0000, 24000 Hz, 5:1, 64 kb/s
pedro@pedro-desktop:~$ avidemux>>log.txt
No accelerated IMDCT transform found

avidemux: ADM_JSAvidemux.cpp:579: const char* getCurrentContainerAsString(): Afirmación `0' fallida.
Cancelado (core dumped)


Can somebody help?

Other problem i have is that i have to insert the dvd in /media/cdrom1 (is a rw dvd unit) because my normal dvd is called burn:///, not /media/cdrom0, so i can't see the files inside the dvd from this unit.

---

### Post by lintoon on 2007-07-04
I don't know what your fault could be.  Maybe someone else can help with that.

I've checked vlc and you can change the bitrate.  I can't find a setting for fps but that doesn't mean you can't change it.  I've googled and found some posts talking about setting fps at the command line so would imagine you can do it in the program gui.

Also, check out kmencoder as a graphical front end for mencoder.

---

### Post by kirbyboy on 2007-07-04
I have searched in repositories and kmencoder is not there, isn't it?
Will it work ok with gnome?

---

### Post by HuwSy on 2007-07-04
I use iriverter, its built on gtk so works fine under gnome and uses mencoder. Very few settings to fiddle with which is both a good and bad thing but not having complete control over the output isnt important when youl only watch the converted video once or twice. And it converts direct from a single file, batch from a directory or convert a whole dvd. ;)

---

### Post by lintoon on 2007-07-04
My mistake.  Kmencoder is the front end under KDE.

Gmencoder is for gnome.  It doesn't seem to be in the repositories.  It may not be what you are looking for but it could be worth checking out.

Here is the home page.  There is a debian apt source you can add to your repositories on the left hand side.

[http://gmencoder.sourceforge.net/](http://gmencoder.sourceforge.net/)

---

### Post by kirbyboy on 2007-07-04
Somebody knows the options i have to put to mencoder to get a mp4 that works with a PSP?, i could make a mp4 but it didn't work in PSP, i'll try again, i hope i have more luck tomorrow.

---

### Post by lintoon on 2007-07-04
Here's a couple of gui psp converters:

[http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)

[http://sourceforge.net/projects/vive/](http://sourceforge.net/projects/vive/)

---

### Post by lintoon on 2007-07-04
HuwSy recommended iriverter. It is in the repositories.

[http://iriverter.thestaticvoid.org/](http://iriverter.thestaticvoid.org/)

---

### Post by kirbyboy on 2007-07-05
I just have bad luck, iriverter doesn't detect my dvd drive, i suposse is for the problem i said before about my dvd drive, and i think it would not convert a video to a psp format too for the options i have seen.
I can't compile vive because i need gtk+ 2.0(i think ubuntu now comes with a superior or the same version, not sure)
I can't compile pspvc because it has an error configuring ffmpeg(i installed it trought sinaptyc too but i don't have luck today)

---

### Post by HuwSy on 2007-07-06
have you installed libdvdread and libdvdcss? might help with some apps.

---

### Post by lintoon on 2007-07-06
Check this post for ffmpeg.

[http://ubuntuforums.org/showthread.php?t=77286](http://ubuntuforums.org/showthread.php?t=77286)

---

### Post by stmiller on 2007-07-06
Just use handbrake. No GUI in Linux, but does an excellent job.

[http://handbrake.m0k.org/](http://handbrake.m0k.org/)

And ffmpeg is in Medibuntu. No need to compile it, etc. Just add Medibuntu as a repo:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by kirbyboy on 2007-07-06
Hi, i'll try later about handrake, but the ffmpeg i must install is the version that comes with pspvc to make it work, in config.err i have the next message:

gcc -I/usr/local//share/pspvc/include -fomit-frame-pointer -c -o /tmp/ffmpeg-conf--10042-.o /tmp/ffmpeg-conf--10042-.c
gcc -Wl,--warn-common -L/usr/local//share/pspvc/lib -lX11 -o /tmp/ffmpeg-conf--10042- /tmp/ffmpeg-conf--10042-.o -lm
/usr/bin/ld: cannot find -lX11
collect2: ld devolvió el estado de salida 1

I think my computer is not working right too, is there a command to make ubuntu works like the first day?, it may happened something to my ubuntu.

---

### Post by sainfoin on 2007-09-28
Just three step then you can enjoy your DVD on psp at once
1. download a convertion software, let's make aimersoft DVD to PSP converter  as an example(i have been using it)
Download and install Aimersoft DVD to PSP Converter, you can free download the latest version from here:
[http://www.aimersoft.com/dvd-to-psp-converter.html](http://www.aimersoft.com/dvd-to-psp-converter.html)
2. Run Aimersoft DVD to PSP Converter , click “Add” button to import your DVD, then click “Start” to start the conversion, the default setting works perfect.
3.After conversion finished, then  connect your psp to pc, you can follow this step to add the DVD to psp
1)create a folder named "MP_ROOT" in PSP memory stick
2) inside that folder create a "Video" folder
3) then copy your MP4 file to this folder
or just turn to this software, it contains a tool called psp video manager, which can help you  to save video to PSP or export PSP MPEG4 located in your PSP to your computer directly and you don't need to manually rename PSP MPEG4 files

---

### Post by easyease on 2007-09-28
"DeVeDe" is a front end for mencoder and is way easier to use than avidemux. it can convert movies to mp4 or  divx........
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

