---
title: "Extracting the information of a movie file"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by protenniser on 2008-01-21
Hi all,

I am using ubuntu gutsy gibbon. Is there a program/package to extract the movie information (the resolution, the movie type, sound bit rate, sound type, etc.) of a movie file (avi, mpg, vob, etc.)?

Thanks for all help...

---

### Post by tophcito on 2008-01-21
Hello!

For me the Totem Movie Player (Applications -> Sound & Video -> Movie Player) works just fine.

Open the movie file in said player, and on the the top of the Sidebar you can select either playlist or properties to be displayed. The latter gives Video: Resolution, Codec, Frame-, and Bitrate and Audio: Codec, Channels, Sample-, and Bitrate.

If u were looking for a command line program, some basic information can be retrieved with the command ```
file moviefile
```, where moviefile is the name of the file you want to analyze.

cheers.

---

### Post by protenniser on 2008-01-21
Hi tophcito,

I really never thought about movie player could do that. Also thanks for the command line information. However I still wonder is there a program that directly extracts these info and writes to a file (maybe .nfo) in an such a way that the process is automated.

Thanks...

---

### Post by philc on 2008-01-22
I think FFmpeg might do something like what you want.

Use is:

ffmpeg -i input_file.extension

FFmpeg will just open your input file without doing anything to it. Something like this will be returned in the terminal window:
> 
phillc@phillc-laptop:~/kapitalkonvert$ ffmpeg -i 848_Termi.mov
FFmpeg version SVN-r11213, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-libvorbis --enable-libtheora --enable-liba52 --enable-libdc1394 --enable-libgsm --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-pthreads --enable-libx264
  libavutil version: 49.6.0
  libavcodec version: 51.49.0
  libavformat version: 52.2.0
  built on Dec 13 2007 20:20:36, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '848_Termi.mov':
  Duration: 00:00:51.7, start: 0.000000, bitrate: 862 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 480x360 [PAR 0:1 DAR 0:1], 25.00 tb(r)
    Stream #0.1(eng): Audio: mpeg4aac, 44100 Hz, stereo
Must supply at least one output file

If you wanted to write these details to a file you could do something like this in Perl, where the script is launched with "perl input_file.extension" :
```

$input_file = shift;
$ffmpeg_input_details="ffmpeg -i ${input_file} 2>input_file.txt";
system($ffmpeg_input_details);
```

If you specifically just wanted to read back the duration, video and audio details then:

```
open(INPUTFILE,"input_file.txt");
@inputfile = <INPUTFILE>;
@input_file_video = grep (/Video:/i, @inputfile);
@input_file_audio = grep (/Audio:/i, @inputfile);
@input_file_duration = grep (/Duration:/i, @inputfile);

print "File contains the following video data:\n"; 
print "@input_file_video\n";
print "File contains the following audio data:\n"; 
print "@input_file_audio\n";
print "File is of the following length:\n"; 
print "@input_file_duration\n";

```

This is one way, perhaps not the best, but there are lots of options.

---

### Post by protenniser on 2008-01-22
Hi philc,

Thank you very much for your help and perl knowledge ;)
Your approach is the kind of approach I want to use.
I will try to modify the code and make it work for my purposes, thanks again...

---

### Post by protenniser on 2008-01-22
Hi all,

Thanks to all, I have managed to create the exact code that will produce me an automated .nfo files of only video files (though only tested for .avi). The program uses the "file" command from ubuntu (linux) to generate those files. It can traverse the directory recursively. It only traverses video files (for now only .avi, .mpeg, .mpg, .vob, .wmv) (however file command didn't create any results for wmv files). It doesn't process files that already has .nfo files. It is purely written in java (only with the dependency of file command) .

This is the general information about the program I write (I wish I could write simpler scripts but the best programming language I know (for now) is java.). It is for sure to work with jre 1.5 (not tested with 1.4). I will both put the source files and the generated jar file as an attachment in a zip, so that the people want to create automated generated files could use them. (Also who want to develop them).

If you want to run the program directly from .jar open a console and go to the directory that you have downloaded the jar file then
```

java -jar nfo_generator.jar

```
It will ask you the top directory you want to process (enter one) i.e.
/home/kmuslu/MyDownloads
And it will process all the video files recursively in that directory.

I am also open to all suggestions btw.

Again thanks for all help.

---

