---
title: "Blender VSE Audio Video Out of Sync"
date: 2013-11-30
forum: Multimedia Software
---

### Post by singhasubhajit.ind on 2013-11-30
I have two TIFF sequencess. One of them is 48 frames long and another contains 00000001.tiff to 00188691.tiff frames. The details of frame dimention and other information related to the tiff files are given below.

$ identify -verbose 00188691.tiff
Image: 00188691.tiff
Format: TIFF (Tagged Image File Format)
Class: DirectClass
Geometry: 1280x528+0+0
Resolution: 72x72
Print size: 17.7778x7.33333
Units: PixelsPerInch
Type: TrueColor
Base type: TrueColor
Endianess: MSB
Colorspace: sRGB 
Depth: 8-bit
Channel depth:
red: 8-bit
green: 8-bit
blue: 8-bit
I have also two corresponding wave files with the same length of tiff files exported from the same editing software. The information of those files are stated below.

[IMG]https://lh5.googleusercontent.com/5eV5n-4YSlnwhUrDtbVDTDD7QkmBhpVKVHq0C0I6UA=w651-h186-p-no[/IMG]

[IMG]https://lh6.googleusercontent.com/tndp-iEgml1ns1tw_cnYIwKyiVV23qSbd-50u0-P0w=w651-h186-p-no[/IMG]

Now I have to join this two image sequences with their corresponding sound track, resize the image strip, adding some effects and export the as mp4. For this reasone i have decided to use Blender VSE. My Blender virson is 2.66a running on Ubuntu Studio 13 and i have all the codec library installed such as ffmpeg, libx264, libopenjpeg etc.

I am using Jack with ALSA driver as an audio plaback system.

[IMG]https://lh6.googleusercontent.com/H_G1fBt9Jzu2Ys3SaYPAAf29ukcRbcePtOwHLU8Cgg=w147-h179-p-no[/IMG]

My Render property settings is:

[IMG]https://lh6.googleusercontent.com/UIfXi5JQcaO5lroTMqPjUKbm8cth_qQhzk-_L5uxaA=w417-h179-p-no[/IMG]

Now the problem is that when I imprort Image sequence and Audio clips separetly, thouge the number of video frames are imported perfectly, audio is getting out of sync gradually and becoming bigger in length as compared to video.

[IMG]https://lh4.googleusercontent.com/6Qqhh5HpBkQ7TVTWqSZb1OSjIvtkqDOfaRUXHJctAA=w154-h179-p-no[/IMG]

The imported sound property is

[IMG]https://lh4.googleusercontent.com/Ks-WmnVt8a2St8K9dHJIzdDSltz376Bjp2W56x_6j8k=w156-h179-p-no[/IMG]

I have checked the AV-sync option, which is already turn on

[IMG]https://lh5.googleusercontent.com/vTKgKfmKPH0HStab7b96-02HS399qDgFfOE8yVvq__A=w422-h179-p-no[/IMG]

Still when I import audio files both of them become out of sync and increase in length. The first audio file is of 2 seconds and 41 miliseconds long (49 frames), but when gets imported it becomes 50 frames long. On the other hand the second audio file is stretched almost 2 minuets.
Can anyone help me to overcome from this situation?


I need a beep to beep audio of the final render also. Is it possable to render out correct length audio from blender? Waiting for your reply. Please help me.

---

