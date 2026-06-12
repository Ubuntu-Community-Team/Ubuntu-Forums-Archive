---
title: "Kubuntu: tovid fails in last stage-WHY!"
date: 2006-10-20
forum: Multimedia &amp; Video
---

### Post by mibadt on 2006-10-20
Hi,
I have 1 GB RAM Kunutu Dapper PC which I try to use to convert an AVI file to a DVD compliant MPEG file using tovid.

As can be seen from the following logs:
a. No space problems on any involved partition.
b. tovid **successfully does 99.9% of its "magic"**, yet fails at the very last stage of merging the separate video and audio (temp) files into a combined mpeg file.

More info:
1. The output file does not exist prior to running tovid. (Is this the problem??). UNfortunately it ca't be found after unning tovid either...
2. The destination partion is a FAT32 partition (shared between Linux and MS).Although the resultant mpeg file shouls be smaller than 2 GB, can this be the problem (FAT 32 limitation).


PLease advise !

Thanks a lot upfront.  :p 

Michael Badt
---------relevant outputs---------------------

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb7             6.0G  4.9G  742M  88% /
varrun                507M  112K  507M   1% /var/run
varlock               507M     0  507M   0% /var/lock
udev                  507M  128K  507M   1% /dev
devshm                507M     0  507M   0% /dev/shm
/dev/sdb2             7.1G  3.4G  3.4G  51% /home
/dev/sda1             8.6G  6.2G  2.4G  73% /media/sda1
/dev/sda3              58G   51G  6.9G  89% /media/sda3
/dev/sda4             9.2G  3.0G  6.3G  33% /media/sda4
/dev/sdb1             8.4G  2.6G  5.8G  32% /media/sdb1
/dev/sdb5             148G  116G   32G  79% /media/sdb5
/dev/sdb6             400M  197M  204M  50% /media/sdb6
/dev/sdb8              10G  2.2G  7.9G  22% /media/sdb8
/dev/sdb9             7.0G  220K  7.0G   1% /media/sdb9
miki@Atlantis:~$ tovid -pal -dvd -in /media/sda3/DV_Material/Lipicia_01.avi  -out /media/sda3/DV_Material/Lipicia_01
--------------------------------
tovid
DVD and (S)VCD video conversion script
Version 0.28
with: core magick dvd vcd transcode
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
tovid command-line used:
-pal -dvd -in /media/sda3/DV_Material/Lipicia_01.avi -out /media/sda3/DV_Material/Lipicia_01
Using config file /home/miki/.tovid/tovid.config, containing the following options:
(none)
Changing to working directory: /home/miki

=========================================================

Converting /media/sda3/DV_Material/Lipicia_01.avi to compliant PAL DVD format
Saving to /media/sda3/DV_Material/Lipicia_01.mpg
Storing log and temporary files in /home/miki/Lipicia_01.Chc7pu

=========================================================

Probing video for information. This may take several minutes...
The encoding process is estimated to require 800 MB of disk space.
You currently have 3431 MB available in this directory.
Analysis of file /media/sda3/DV_Material/Lipicia_01.avi:
  720 x 576 pixels, 25.000 fps
  Duration (best guess): 00:19:03 (HH:MM:SS)
  dvsd video with pcm audio
Target format:
  720 x 576 pixels, 25.000 fps
  m2v video with ac3 audio
  7840 kbits/sec video, 224 kbits/sec audio
Using auto-detected aspect ratio of 125:100 (override with -aspect)
Letterboxing horizontally
Input is already 25.000 fps. Framerate will not be altered.
Scaling picture to 672 x 576
Centering picture against a 720 x 576 black background

=========================================================

Encoding audio stream to ac3 with the following command:
nice -n 0 ffmpeg -i "/media/sda3/DV_Material/Lipicia_01.avi" -vn -ab 224 -ar 48000 -ac 2 -acodec ac3 -y "/home/miki/Lipicia_01.Chc7pu/audio.ac3"

Processing started. Please wait...
    ---  Encoding audio to ac3: 31 MB written to audio.ac3

Audio encoding finished successfully.

=========================================================

Encoding video stream with the following commands:
nice -n 0 mplayer -benchmark -nosound -noframedrop -noautosub -vo yuv4mpeg:file="/home/miki/Lipicia_01.Chc7pu/video.yuv" -vf-add scale=672:576 -vf-add expand=720:576 "/media/sda3/DV_Material/Lipicia_01.avi"
cat "/home/miki/Lipicia_01.Chc7pu/video.yuv" | nice -n 0 mpeg2enc --sequence-length 4300 --nonvideo-bitrate 304 --aspect 2 -f 8 -b 7840 -g 4 -G 9 -D 10 -K hi-res --frame-rate 3 -v 0 --video-norm p --reduction-4x4 2 --reduction-2x2 1 -q 5 -o "/home/miki/Lipicia_01.Chc7pu/video.m2v"

Processing started. Please wait...



Processing started. Please wait...
    ---  Encoding video stream: 1064 MB written to video.m2v


=========================================================

Multiplexing audio and video together with the following command:
mplex -V -f 8 -o "/media/sda3/DV_Material/Lipicia_01.mpg" "/home/miki/Lipicia_01.Chc7pu/video.m2v" "/home/miki/Lipicia_01.Chc7pu/audio.ac3"
Multiplexing finished successfully
du: cannot access `/media/sda3/DV_Material/Lipicia_01*.mpg': No such file or directory
Output files:
expr: syntax error
expr: syntax error

=========================================================

    ----------------------------------------
    Final statistics
    ----------------
    tovid 0.28
    File: /media/sda3/DV_Material/Lipicia_01.mpg, 1143 secs DVD PAL
    Final size:      0 kilobytes
    Target bitrate:  7840 kbits/sec
    Average bitrate:  kbits/sec
    Peak bitrate:     kbits/sec
    Took 00:31:25 to encode on  AMD Athlon(tm) 64 Processor 3200+ 1000.000 mhz
    -----------------------------------------
    EOF
Statistics written to /home/miki/.tovid/stats.tovid
Cleaning up...
removed `/home/miki/Lipicia_01.Chc7pu/video.yuv'
Removing temporary files...
removed `/home/miki/Lipicia_01.Chc7pu/video.m2v'
removed `/home/miki/Lipicia_01.Chc7pu/audio.ac3'
removed `/home/miki/Lipicia_01.Chc7pu/tovid.log'
removed `/home/miki/Lipicia_01.Chc7pu/tovid.scratch'
removed directory: `/home/miki/Lipicia_01.Chc7pu'

=========================================================

Done!

=========================================================

Your encoded video should be in the file(s) /media/sda3/DV_Material/Lipicia_01.mpg.
Thanks for using tovid!

=========================================================

miki@Atlantis:~$ cd /media/sda3/DV_Material/
miki@Atlantis:/media/sda3/DV_Material$ ls Lip*
Lipicia_01.avi
miki@Atlantis:/media/sda3/DV_Material$

---

### Post by mibadt on 2006-10-20
Sorry,
I solved the problem-originally I hadn't write permission to the destination partition.

:D :D

---

