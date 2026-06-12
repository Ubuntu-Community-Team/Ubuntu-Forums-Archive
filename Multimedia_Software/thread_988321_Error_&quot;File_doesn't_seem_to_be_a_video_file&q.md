---
title: "Error &quot;File doesn't seem to be a video file&quot; with DeVeDe"
date: 2008-11-20
forum: Multimedia Software
---

### Post by sjeffs on 2008-11-20
I have been experiencing a problem recently with DeVeDe and other programs that convert Video to DVD's. I am using 64bit Ubuntu Hardy.

When I try and add an AVI file to DeVeDe it comes up with an error  "File doesn't seem to be a video file" .

I am running version 3.6. I uninstalled it using Synaptic Package Manager (complete install) and then re-installed but got the same error.
I then unistalled through the terminal and reinstalled again, but still the same error.

When I ran the progam through the Terminal the full message is as follows

Traceback (most recent call last):

  File "/usr/lib/devede/devede_newfiles.py", line 672, in on_moviefile_file_set

    devede_dialogs.show_error(_("File doesn't seem to be a video file."))

TypeError: __init__() takes exactly 3 arguments (2 given)


I have also tried with Tovid and although I don't get the same error it gives me the following:

MP3 DVD-Rip.avi.tovid_encoded.0/video.m2v"

/usr/bin/tovid: line 304: 10201 Segmentation fault      nice -n 0 mplayer -benchmark -nosound -noframedrop -noautosub -vo yuv4mpeg:file="/home/shay/Team America - World Police XviD MP3 DVD-Rip.avi.tovid_encoded.0/video.yuv" -vf scale=720:576 "/home/shay/Videos/Team America - World Police XviD MP3 DVD-Rip/Team America - World Police XviD MP3 DVD-Rip.avi"

[tovid]: Encode stopped, killing all sub processes

[tovid]: Keeping temporary files used during encoding in /home/shay/Team America - World Police XviD MP3 DVD-Rip.avi.tovid_encoded.0

[tovid]: tovid encountered an error during encoding:

[tovid]:     Couldn't create file: "/home/shay/Team America - World Police XviD MP3 DVD-Rip.avi.tovid_encoded.0/video.m2v"

I have tried this with AVI files that I had already converted and burned to Disc using DeVeDe so it was working with these AVI files before. Also they all work fine when you use and of the Movie Players and they play all the way through as I have been streaming them through to my TV.

Would anyone know what the problem is?

---

### Post by binbash on 2008-11-20
Can you please paste the codec output of your video file with mediainfo or some software like that? ([http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612](http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612) )

---

### Post by sjeffs on 2008-11-21
Thanx for coming back
This is the new one that I have down loaded and have actually burnt to CD on a Windows platform (sorry for swearing)

mmpython media info

filename : The.Kingdom.Of.The-Crystal.avi
Attributes:
        type: AVI 
        length: 7352
 Stream list:  
   Video Stream:
        length: 7352
        bitrate: 2997
        codec: DivX v5
        width: 664
        height: 268
        fps: 23.98  
   Audio Stream:
        channels: 2
        samplerate: 48000
        codec: MPEG Layer 3

This is an older one that I have burnt successfully in the past using DeVeDe but will not now as I get the Error "File doesn't seem to be a video file"

mmpython media info

filename : 300[2006]DvDrip[Eng]-aXXo.avi
Attributes:
        type: AVI 
        length: 6995
 Stream list:  
   Video Stream:
        length: 6995
        bitrate: 2997
        codec: DivX v5
        width: 620
        height: 256
        fps: 23.98  
   Audio Stream:
        channels: 2
        samplerate: 48000
        codec: MPEG Layer 3

Thanx

---

### Post by binbash on 2008-11-21
Did you install w32codecs?I have no problems converting divx5 files with devede, please be sure you installed w32codecs.

---

