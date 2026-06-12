---
title: "New script to convert mp3 to m4b for iTunes"
date: 2011-10-23
forum: Multimedia Software
---

### Post by HJB on 2011-10-23
Hi all.
I use my ipod solely for audiobooks.
There are many places to download ripped audio books from but they are all in mp3 format usually.
I developed this script to combine the mp3 files into audiobooks with chapters and artwork, ready to be imported into iTunes.
I have a function in there to create your own watermarked art if needed.

I hope you'll find this helpful.

You'll need the following programs installed to run this script
ffmpeg, imagemagick and mp3wrap:
Get from repositories.

mp4tags etc:
wget [http://mp4v2.googlecode.com/files/mp4v2-1.9.1.tar.bz2](http://mp4v2.googlecode.com/files/mp4v2-1.9.1.tar.bz2)
tar -xf mp4v2-1.9.1.tar.bz2
cd mp4v2-1.9.1
./configure
make
sudo checkinstall
cd

Remember to do the following with the script
chmod +x hjb_book_creation_script.sh
and run as ./hjb_book_creation_script.sh

I am no programmer.
Let me know if you can change it to make it better.
Bye

---

### Post by FakeOutdoorsman on 2011-10-24
You should list programs or packages that are required to use the script. Maybe under your version number in the head of the script would suffice.

As for your main ffmpeg command:
```
ffmpeg -i $cfg_workingDir/album_MP3WRAP.mp3 -y -vn -acodec aac -strict experimental -ab 64k -ar 44100 -threads 3 -f mp4 "$cfg_workingDir/$ffOUT" >> "$logs" 2>&1
```
The native aac encoder (sometimes called ffaacenc) in ffmpeg is usually not considered to be very good. Oneiric supports *libvo-aacenc* if the user also installs **libavcodec-extra-53**. Other Ubuntu versions can use *libfaac* if the Medibuntu version of the same package is used (libavcodec-extra-52). Unfortunately this requires additional work by the user, although it isn't much work. Instructions for that are here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

I do not believe ffaacenc supports -threads. -ab 64k might be a little low, but for audiobooks perhaps it's enough.

---

