---
title: "converted wmv to mpg how do i put to dvd?"
date: 2009-08-31
forum: Multimedia Software
---

### Post by stinger30au on 2009-08-31
i have a wmv file that i want to convert and stick on to a dvd so i can play it as a standard dvd in any dvd player

i have use 9.04 and i installed winff

i pointed it to the wmv file and in the presets i told it dvd 4:3 aspect and hit go

it has produced a file with an extension of mpg

no other files, just this one on its own

now usually in a dvd format there is vob file and the likes and the vob files are usually 1 gig in size or there abouts.

the wmv file i have is a few hundred meg and it made a 2.4 gig mpg file.
the file plays fine with vlc or whatever, but how the heck do it put it on to a dvd for it to be read?

do i fire up k3b and create new video dvd and just shove the file in to the "video_ts" directory and hit burn or what?

---

### Post by howefield on 2009-08-31
Devede will convert the mpg file to dvd format. It'll create an iso file that you can then burn to dvd.

---

### Post by stinger30au on 2009-08-31
> **howefield said:**
> Devede will convert the mpg file to dvd format. It'll create an iso file that you can then burn to dvd.

correct

i tried this

but the convert that devede does all the colours are all wrong

the convert done with winff, all the colours are correct

---

### Post by ApEkV2 on 2009-08-31
try tovid

---

### Post by stinger30au on 2009-08-31
> **ApEkV2 said:**
> try tovid

i will try this and see how i go

thanks

---

### Post by stinger30au on 2009-08-31
tovid is running in the background and says it is creating a .mpg file so i may end up at square one again.
if i do, the info below looks like it will help

after more googling i have just come across this

[http://ubuntuforums.org/archive/index.php/t-53486.html](http://ubuntuforums.org/archive/index.php/t-53486.html)

this is the part im most insterested in

If the file is in mpeg2 format already, you don't need to convert it to a dvd format with Transcode or Mencoder - you need to create the dvd image instead. (Also barring any other funkiness like low-compressed bitrates, etc.)

Here is how you create a dvd-player-readable dvd: (you'll need dvdauthor & mkisofs installed):

1. Create the dvd file structure:dvdauthor -o dvd -t movie.mpg 


   2. Finalize the structure:dvdauthor -o dvd -T 


 3. Create the ISO:mkisofs -dvd-video -o dvd.iso dvd/ 
 
4. Burn the iso image. (You can use your iso burning tool of choice here - I use Gnomebaker - but if you're in KDE you'll probably want to use K3B.)

As I said before, barring any funkiness, and if your mpg is a compliant mpeg2 - you'll have a dvd-player-readable dvd.  :)

---

### Post by mc4man on 2009-09-01
The post you found is correct, you don't want to encode twice. If winff created a dvd compliant mpeg (mpeg2) then all you need to do is author it, make an iso and burn.

If you have mediainfo this is similar to what you'd want to see (highlights.
This is for NTSC, PAL would show some different values, same idea though

> Complete name : /home/doug/Desktop/live/3.mpeg 
[COLOR="Blue"]Format : MPEG-PS [/COLOR]
File size : 213 MiB 
Duration : 5mn 46s 
Overall bit rate : 5163 Kbps 
Video ID : 224 (0xE0) 
[COLOR="Blue"]Format : MPEG Video 
Format version : Version 2 [/COLOR]
Format profile : Main@Main Standard : NTSC 
Format settings, Matrix : Default 
Duration : 5mn 46s 
Bit rate mode : Variable 
Bit rate : 4 510 Kbps 
Nominal bit rate : 9 000 Kbps 
Width : 720 pixels 
Height : 480 pixels 
Display aspect ratio : 16/9 
Frame rate : 29.970 fps 
[COLOR="Blue"]Standard : NTSC [/COLOR]
Colorimetry : 4:2:0 
Scan type : Progressive 
Bits/(Pixel*Frame) : 0.435 
Stream size : 186 MiB (87%) 
[COLOR="Blue"]Audio ID : 128 (0x80) 
Format : AC-3 [/COLOR]
Format/Info : Audio Coding 3 
Duration : 5mn 46s 
Bit rate mode : Constant 
Bit rate : 448 Kbps 
Channel(s) : 2 channels 
Channel positions : L R 
Sampling rate : 48.0 KHz 
Stream size : 18.5 MiB (9%) 
[COLOR="Blue"]Format : DVD-Video[/COLOR] 

I usually just use ffmpeg, a starting point, good for most conversions is

```
ffmpeg -i whatever.wmv -target ntsc-dvd whatever.mpeg
```
or
```
ffmpeg -i whatever.wmv -target pal-dvd whatever.mpeg
```

(the only .wmv's I had a problem with are 1080p, i've trial and errored to better results, someone who knows ffmpeg better than me could advise if you have or in the future have some

I use this little java script to author, works great once you get the idea how to use, for 1 video nothing to 'get', piece of cake.

Thread on something a bit different with link to Varsha (authoring app) and some Varsha screens if dvdauthor doesn't work out (it should be fine

[http://ubuntuforums.org/showthread.php?t=1231648](http://ubuntuforums.org/showthread.php?t=1231648)

---

### Post by stinger30au on 2009-09-01
thanks for the feedback

---

### Post by andrew.46 on 2009-09-17
Hi stinger30au,

Some may interested in the PAL angle rather than the NTSC syntax normally given. The following would then be useful:

First create the mpg:

```
ffmpeg -i input.wmv -target pal-dvd -sameq -aspect 16:9 output.mpg
```

which is pretty much what mc4man specified but I have added -sameq (useful for the smaller videos I have been transcoding) and manually specified the aspect ratio (dvdauthor sometimes chokes without this). Next to create the dvd structure:

```
dvdauthor -t -o dvd --video=pal -f output.mpg
dvdauthor -T -o dvd 
```

I believe ntsc is the default and although dvdauthor should pick this up automagically it does not always seem to. This is similar to the syntax you have discovered yourself. Next to create the iso:

```
mkisofs -dvd-video -o my_dvd.iso dvd/
```

and finally to burn to dvd:

```
growisofs -dvd-compat -Z /dev/dvd=my_dvd.iso
```

Can I say that the commandline rules :)

Andrew

---

