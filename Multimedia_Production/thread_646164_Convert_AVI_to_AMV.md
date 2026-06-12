---
title: "Convert AVI to AMV"
date: 2007-12-20
forum: Multimedia Production
---

### Post by arashiko28 on 2007-12-20
I need help on a howto convert AVI files to AMV, which are the ones that my MP4 reads. Even though it says it can see AVI on the advertising, there's another thing when you read the manual. It says it has a program to do that on windows, but i'd like to do that without rebooting everytime i'm going to pass a video to my mp4 player. Please help!
By the way, it has linux as it's OS, I liked that:guitar:

---

### Post by Creative2 on 2007-12-21
Using patched FFmpeg
(for that try to see here [http://code.google.com/p/amv-codec-tools/](http://code.google.com/p/amv-codec-tools/))

In common case command line will look like

ffmpeg -i <input> -f amv -s <width>x<height> -r 16 -ac 1 -ar 22050 -qmin 3 -qmax 3 <output>

FFmpeg accepts any picture resolutions, but hardware players supports only:

    * 128x90
    * 128x128
    * 160x120 

Input file can be any video format supported by FFmpeg.

Note: if output file has 'amv' extention, -f amv option can be omitted.

Option -r 16 sets framerate to 16 frames/sec (other values seems to be not supported by hardware players).

Options -ac 1 and -ar 22050 sets 22050 Hz mono sound. Other formats are not supported.

Options -qmin 3 and -qmax 3 forces quantizer to be equal to 3. This will give you good quality with acceptable file size.

Example 1. Converting AVI file into AMV with 160x120 picture size:

ffmpeg -i file.avi -s 160x120 -ac 1 -ar 22050 -qmin 3 -qmax 3 file.amv

---

### Post by Creative2 on 2007-12-21
you can try without patch with 

ffmpeg -i film.avi -s 160x120 -r 16 -ac 1 -ar 22050 -qmin 3 -qmax 3 file.amv

let me know if it works.....FOR ME DOESNT WORK... i think you MUST PATCH ffmpeg

---

### Post by patslap on 2007-12-27
see [http://www.bytessence.com/bamvc.html](http://www.bytessence.com/bamvc.html)

---

### Post by arashiko28 on 2007-12-28
This is what is resulting, I fond it on a spanish forum.
Create a text file and copy inside:

amv-ffmpeg-linux-i386-20071030 -i orignal_file.mpg -f amv -s 160×128 -r 16 -qscale 2 -mbd 2 -g 1 -ac 1 -ar 22050 destiny_file.amv

Make it executable and save it where you have the videos to convert. Then, on terminal write:
sudo ./amv-ffmpeg-linux-i386-20071030 -i orignal_file.mpg -f amv -s 160×128 -r 16 -qscale 2 -mbd 2 -g 1 -ac 1 -ar 22050 destiny_file.amv

and that should be all. I'm trying to find a bigger resolution since its only like half of my mp4's screen.

---

