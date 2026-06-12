---
title: "Need help turning AVI into DVD"
date: 2008-12-16
forum: Multimedia Software
---

### Post by BellinXFelon on 2008-12-16
I am trying to take AVI files and burn them to DVD so that they will play in a dvd player. What do I need to do, like what programs should i use and how should i do this?

---

### Post by taurus on 2008-12-16
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install devede
```
You can now find it in Applications -> Sound & Video.

---

### Post by Jose Catre-Vandis on 2008-12-16
I have used this tutorial with success in the past, simple and straight forward. Seems to have disappeared from the forum so here is a link to a pdf of the post:
```
http://rapidshare.com/files/174030499/HOWTO_Make_Dvd_Videos_From_An_Avi_File.pdf
```

---

### Post by parajuito on 2008-12-16
Devede :) ive never had problem with devede :P

---

### Post by Jose Catre-Vandis on 2008-12-16
I lied, this is the process I used:
> Convert AVI to DVD using transcode, mencoder and dvdauthor

here's 6 basic steps to convert a .AVI to DVD so you can watch your movies on your home player, not just your computer. . .But first we need to figure out if it's a fullscreen movie or letterbox movie. . .Movies normally come in two sizes: 4:3 (fullscreen) or 16:9 (letterbox) which they call aspect ratio. . .They also come in two formats PAL (Non-US) and NTSC (US). . .The following examples are for NTSC Only!

what you need first:
transcode
mplayer
Mjpegtools
ffmpeg
dvd+rw-tools
Dvdauthor
some hardrive space

in this example I will be using a 16:9 movie.avi for our conversion. . .

1.) Split the .avi file into 2 separate files, one for video and one for audio:

##############################################################################################################################################

transcode -i movie.avi -y ffmpeg --export_prof dvd-ntsc --export_asr 3 -o movie -D0 -s2 -m movie.ac3 -J modfps=clonetype=3 --export_fps 29.97

##############################################################################################################################################

this will make:
movie.m2v (video)
movie.ac3 (audio)

note: if you're doing a fullscreen (4:3) movie then simply change --export_asr 3 to --export_asr 2

2.) (optional) Extract 5.1 Audio:

Code:

tcextract -d2 -i movie.avi -a0 -x ac3 | tcextract -d2 -x ac3 -t raw > movie.ac3

This is an extra step if you know your .avi file actually has 5.1 surround sound. (Step one only produces a stereo .ac3 file !)
How can you tell? Do this first:

Code:

mplayer -vo dummy -identify movie.avi 2> /dev/null | grep "5.1 ("

if you get this output then you have 5.1:

Code:

AC3: 5.1 (3f+2r+lfe) 48000 Hz 384.0 kbit/s

if you don't, just ignore this step!

3.) Put the video & audio file back together:


##############################################################################################################################################

mplex -f 8 -o dvd_movie.mpg movie.m2v movie.ac3

##############################################################################################################################################

this will make dvd_movie.mpg ready for DVD authoring. . .

4.) open your favorite text editor and paste the following:

##############################################################################################################################################

<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="dvd_movie.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
      </titles>
   </titleset>
 </dvdauthor>

##############################################################################################################################################

save the file as: dvdauthor.xml
in the same directory as your movie files
(you can also change the chapters to fit the times of your movie)

5.) Create a DVD directory where your movie files are and do this:

##############################################################################################################################################

dvdauthor -x dvdauthor.xml

##############################################################################################################################################

this will create two AUDIO_TS and VIDEO_TS directories in your DVD directory. . .

6.) Test it & Burn it:

to test it:

##############################################################################################################################################

xine dvd:/full/path/to/DVD/VIDEO_TS/

##############################################################################################################################################

to burn it:

##############################################################################################################################################

growisofs -Z /dev/dvd -dvd-video DVD/

##############################################################################################################################################

note: I like to use DVD-RW discs for a test before I use a real disc. . .
If all goes well, the above will produce movie with no menus, just the movie that should play when you put in your disc. . .and if there's more than one .avi then simply do this in your dvdauthor.xml file:

##############################################################################################################################################

<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="dvd_movie_part1.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
       <pgc>
         <vob file="dvd_movie_part2.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
     </titles>
   </titleset>
 </dvdauthor>

##############################################################################################################################################


---

### Post by BellinXFelon on 2008-12-17
I have used devede but i am not sure whether to transcode into an .iso or disc structure or convert to mpeg only, what works best?

---

