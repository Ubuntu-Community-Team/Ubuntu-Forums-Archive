---
title: "mythexport qut working"
date: 2009-01-24
forum: Mythbuntu
---

### Post by ctucker10 on 2009-01-24
I installed and configured mythexport a couple of weeks ago. I was using it to transcode my recordings to .mp4 format for transfer to my iPhone. It was working great until a couple of days ago. Now it's giving me a headache.

I am running Mythbuntu 8.10 with all updates. To install mythexport I added a respository:

```
deb http://ppa.launchpad.net/mythbuntu-testing/ubuntu intrepid main
```

To troubleshoot I removed and reinstalled the packages: mythexport atomicparsley

Then I reconfigured using:

```
sudo dpkg-reconfigure mythexport
```

I used all of the defaults except for the MySQL root password because I assigned a different password to the MySQL root account (when configuring it to include Netflix data a few months ago).

Then I made sure that I had symbolic links pointing to config.xml in my automatic login account. I added links in the 'root' and 'mythtv' accounts.

Next, for convenience, I created a directory in my automatic login account called 'mythexport'. Then I created a symbolic link in /var/lib/mythtv pointing at the new directory so that my exported recordings will appear in a more convenvient location. Basically I deleted the original /var/lib/mythtv/mythexport directory and replaced it with the symbolic link.

mythbackend.log is reporting
```
JobQueue: Started "Export to iPhone (4:3)" for ...
ERROR: Directory is not writable
JobQueue:Finished "Export to iPhone (4:3)" for ...

```

I have checked the owner, group and permissions on the the directory I created and don't see any problems. Any suggestions will help. Thanks.

---

### Post by ctucker10 on 2009-01-25
Since my original post I've performed the following: I uninstalled mythexport and atomicparsley again, but this time with the following CLI input:

```
sudo apt-get autoremove mythexport atomicparsley
```

Then I reinstalled them as before:

```
sudo apt-get install mythexport atomicparsley
```

I expected the configuration script to run during the install. It didn't so I ran it manually:

```
sudo dpkg-reconfigure mythexport
```

I used most of the defaults except this time I changed the 'exportdir' to '/home/curtis/mythexport' ('curtis' is the account that mythfrontend launches from after automatic login). I also added the password for the MySQL root account. (I verified the password just to be sure.)

Next, I checked the OWNER, GROUP and PERMISSIONS on 'exportdir'. Just to be safe I changed the OWNER to 'mythtv'.

I also made sure that symbolic links pointing to '/home/curtis/.mythtv/config.xml' were in the the 'root' and 'mythtv' accounts.

Finally, I restarted the machine and attempted an export. I have attached the output of mythbackend.log. I don't know how to interpret these results. Your help is appreciated. Thanks.

```
curtis@mythtv-desktop:~$ tail -50 /var/log/mythtv/mythbackend.log
2009-01-25 08:26:28.583 MainServer::HandleAnnounce Monitor
2009-01-25 08:26:28.588 adding: mythtv-desktop as a client (events: 0)
2009-01-25 08:26:32.785 MainServer::HandleAnnounce Monitor
2009-01-25 08:26:32.788 adding: mythtv-desktop as a client (events: 0)
2009-01-25 08:26:33.104 Reschedule requested for id -1.
2009-01-25 08:26:33.365 Scheduled 64 items in 0.3 = 0.03 match + 0.23 place
2009-01-25 08:26:34.294 MainServer::HandleAnnounce Monitor
2009-01-25 08:26:34.301 adding: mythtv-desktop as a client (events: 0)
2009-01-25 08:27:04.505 JobQueue: Started "Export to iPhone (4:3)" for "The Boondocks" recorded from channel 1060 at Wed Aug 20 04:00:00 2008
2009-01-25 08:27:04.979 MainServer::HandleAnnounce Monitor
2009-01-25 08:27:04.984 adding: mythtv-desktop as a client (events: 0)
Use of uninitialized value $syndicatedepisodenumber in pattern match (m//) at /usr/bin/mythexport line 197.
Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport line 317.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport line 317.
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, nuv, from '/var/lib/mythtv/recordings/1060_20080820040000.nuv':
  Duration: 10:15:09.8, start: 0.400000, bitrate: 127 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480 [PAR 4:3 DAR 2:1], 29.97 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Unknown encoder 'h264'
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, nuv, from '/var/lib/mythtv/recordings/1060_20080820040000.nuv':
  Duration: 10:15:09.8, start: 0.400000, bitrate: 127 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480 [PAR 4:3 DAR 2:1], 29.97 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Unknown encoder 'h264'
AtomicParsley error: can't open /home/curtis/mythexport/TOON-The_Boondocks-Guess_Hoe_s_Coming_to_Dinner-20080820040.mp4 for reading: No such file or directory
AP error trying to fopen: No such file or directory
rm: cannot remove `/home/curtis/mythexport/TOON-The_Boondocks-Guess_Hoe_s_Coming_to_Dinner-20080820040.mp4': No such file or directory
mv: cannot stat `/home/curtis/mythexport/*temp*': No such file or directory
ERROR: File is not available, please check your backend logs. at /usr/bin/mythexport line 342.
2009-01-25 08:27:06.150 JobQueue: Finished "Export to iPhone (4:3)" for "The Boondocks" recorded from channel 1060 at Wed Aug 20 04:00:00 2008.
2009-01-25 08:30:03.045 MainServer::HandleAnnounce Monitor
2009-01-25 08:30:03.048 adding: mythtv-desktop as a client (events: 0)
curtis@mythtv-desktop:~$ 

 
```

---

### Post by ctucker10 on 2009-01-25
Hmmm...fixed it. I changed the 'export_codec' from 'h264' to 'mpeg4' and now mythexport is working again.

What I don't understand is why. When I originally configured mythexport (2 weeks ago) I used 'export_codec=h264' and it worked fine. Anyway, this problem is solved.

---

