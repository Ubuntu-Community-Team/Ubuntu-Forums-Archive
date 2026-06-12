---
title: "Trouble finding multimedia converter"
date: 2009-03-20
forum: Multimedia Software
---

### Post by firewarrior on 2009-03-20
Hey all. I have been searching all over the internet for a good multimedia converter for my audio books. The file extensions that the books are in are .m4b. I want to be able to transfer them to my Garmin nuvi 750. It is capable of having an SD card and will read .mp3. I am looking to see if there are any converters that will take these audio books from m4b to mp3. If anyone can point me in the right direction that would be of great help.

---

### Post by hichamroudi on 2009-03-20
> **firewarrior said:**
> Hey all. I have been searching all over the internet for a good multimedia converter for my audio books. The file extensions that the books are in are .m4b. I want to be able to transfer them to my Garmin nuvi 750. It is capable of having an SD card and will read .mp3. I am looking to see if there are any converters that will take these audio books from m4b to mp3. If anyone can point me in the right direction that would be of great help.


I think this link will help you:

[http://intuitivenipple.net/10/converting-mp3s-to-m4b-audiobooks-and-m4b-to-mp3](http://intuitivenipple.net/10/converting-mp3s-to-m4b-audiobooks-and-m4b-to-mp3)

---

### Post by firewarrior on 2009-03-20
I have tried this line of code in the terminal but not sure if that is where it is needed to be input. The website is not clear on how to run this line of code. If there is someone who can explain how to get this to work that would be awesome. I'm still kind of new to linux. Only been using it for about 4 months.

---

### Post by Neo_The_User on 2009-03-20
just copy and paste them in. like so...

```

ffmpeg -i <infile.m4b> -acodec libmp3lame -ar 22050 <outfile.mp3>

```

So it would be like...

```

ffmpeg -i black-hole-sun.m4b -acodec libmp3lame -ar 22050 black-hole-sun.mp3

```

I think.. 

first run this command though..

```

sudo apt-get install ffmpeg libmp3lame

```

---

### Post by firewarrior on 2009-03-20
Still no go on the line of code. It installed ok but it says no such file or directory.

---

### Post by Neo_The_User on 2009-03-20
cd to the directory the files are in.

for example if my files are in /home/firewarrior/media then I would do:

```

cd
cd media

```

or you can do it this way

```

cd /home/firewarrior/media

```

Or you can just drag the files into the terminal (not a good idea)

---

### Post by hichamroudi on 2009-03-20
where are your .m4b files located?

---

### Post by Neo_The_User on 2009-03-21
> **hichamroudi said:**
> where are your .m4b files located?

as long as the OP knows... lol

---

### Post by firewarrior on 2009-03-22
Thanks for all the help. Got SoundConverter downloaded and that got the job done.

---

### Post by FakeOutdoorsman on 2009-03-22
> **Neo_The_User said:**
> 

first run this command though..

```

sudo apt-get install ffmpeg libmp3lame

```
There is no libmp3lame package.  Intrepid users can enable restricted encoders in FFmpeg such as mpeg4, mpeg2video, libmp3lame, libxvid, libfaac, and libx264, by installing the **libavcodec-unstripped-51** package (Jaunty users can install **libavcodec-unstripped-52**).
```
sudo apt-get install ffmpeg libavcodec-unstripped-51
```

---

### Post by andrew.46 on 2009-03-24
Hi,

I hope I am not the only one here who had not heard of m4b before :-). The sample I found:

[http://samples.mplayerhq.hu/ipod/MAKE_2005-08-01.m4b](http://samples.mplayerhq.hu/ipod/MAKE_2005-08-01.m4b)

was one of the few files I have ever found that MPlayer barfed on while I noted that FFplay and FFmpeg had no such troubles:

```

  Duration: 00:02:57.54, start: 0.000000, bitrate: 162 kb/s
    Stream #0.0(eng): Audio: aac, 22050 Hz, mono, s16
    Stream #0.1(eng): Subtitle: text / 0x74786574
    Stream #0.2(eng): Video: tiff, rgb24, 167x166, 50 tbr, 50 tbn, 50 tbc
    Stream #0.3(eng): Subtitle: tx3g / 0x67337874
```

Very interesting!

Andrew

---

