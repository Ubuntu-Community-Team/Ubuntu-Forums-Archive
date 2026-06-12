---
title: "trying to download a youtube video"
date: 2010-09-23
forum: Multimedia Software
---

### Post by Ka Fish on 2010-09-23
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]**I found "HOWTO: Download a youtube song into MP3" by**[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=Verdana][ ForksHolder]("http://ubuntuforums.org/member.php?u=461318"). I got stuck on the third step.                                                                                                                                                                                                                     ka@ka-desktop:~$ sudo apt-get install ffmpeg youtube-dl
[sudo] password for ka: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4
  libqimageblitz4 libkscreensaver5 libsolidcontrolifaces4
  plasma-widgets-workspace libplasma-geolocation-interface4 libksgrd4
  kdebase-workspace-bin libkworkspace4 libplasmagenericshell4 libkfontinst4
  libkephal4 kdebase-workspace-data ksysguardd libplasmaclock4 libweather-ion4
  kdebase-workspace-kgreet-plugins libsolidcontrol4 akonadi-server
  libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libavdevice52 libavfilter0
Suggested packages:
  rtmpdump
The following NEW packages will be installed:
  ffmpeg libavdevice52 libavfilter0 youtube-dl
0 upgraded, 4 newly installed, 0 to remove and 23 not upgraded.
Need to get 385kB of archives.
After this operation, 1,257kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libavdevice52 4:0.5.1-1ubuntu1 [74.3kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libavfilter0 4:0.5.1-1ubuntu1 [49.5kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main ffmpeg 4:0.5.1-1ubuntu1 [237kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe youtube-dl 2010.04.04-1 [25.0kB]
Fetched 385kB in 1s (224kB/s)      
Selecting previously deselected package libavdevice52.
(Reading database ... 202898 files and directories currently installed.)
Unpacking libavdevice52 (from .../libavdevice52_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libavfilter0.
Unpacking libavfilter0 (from .../libavfilter0_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package ffmpeg.
Unpacking ffmpeg (from .../ffmpeg_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package youtube-dl.
Unpacking youtube-dl (from .../youtube-dl_2010.04.04-1_all.deb) ...
Processing triggers for man-db ...
Setting up libavdevice52 (4:0.5.1-1ubuntu1) ...

Setting up libavfilter0 (4:0.5.1-1ubuntu1) ...

Setting up ffmpeg (4:0.5.1-1ubuntu1) ...
Setting up youtube-dl (2010.04.04-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ka@ka-desktop:~$ youtube-dl
Usage: youtube-dl [options] url...

youtube-dl: error: you must provide at least one URL
ka@ka-desktop:~$ youtube-dl [http://www.youtube.com/watch?v=5PF-yJcM8ck](http://www.youtube.com/watch?v=5PF-yJcM8ck)
[youtube] Setting language
[youtube] 5PF-yJcM8ck: Downloading video info webpage
[youtube] 5PF-yJcM8ck: Extracting video information
ERROR: format not available for video
ka@ka-desktop:~$ youtube-dlhttp://www.youtube.com/watch?v=5PF-yJcM8ck
bash: youtube-dlhttp://www.youtube.com/watch?v=5PF-yJcM8ck: No such file or directory
ka@ka-desktop:~$ 
 What an I doing wrong?
[/FONT][/FONT][/COLOR]

---

### Post by ron999 on 2010-09-23
Hi
I don't know what went wrong the first time.
But the second time you didn't leave a space between words:-
> ka@ka-desktop:~$ youtube-dlhttp://www.youtube.com/watch?v=5PF-yJcM8ck

Try it again with a gap, also use **-t** to get the correct title.
```
youtube-dl -t http://www.youtube.com/watch?v=5PF-yJcM8ck
```

---

### Post by Ka Fish on 2010-09-23
ka@ka-desktop:~$ youtube-dl -t [http://www.youtube.com/watch?v=5PF-yJcM8ck](http://www.youtube.com/watch?v=5PF-yJcM8ck)
[youtube] Setting language
[youtube] 5PF-yJcM8ck: Downloading video info webpage
[youtube] 5PF-yJcM8ck: Extracting video information
ERROR: format not available for video
ka@ka-desktop:~$

---

### Post by ron999 on 2010-09-23
Try update.
Like this:-
```
sudo youtube-dl --update
```

Result is this:-
> Updating to latest stable version...
Updated to version [COLOR="Red"]2010.08.04[/COLOR]

Then try again:-
```
youtube-dl -t http://www.youtube.com/watch?v=5PF-yJcM8ck
```

Result is this:-
> [youtube] Setting language
[youtube] 5PF-yJcM8ck: Downloading video webpage
[youtube] 5PF-yJcM8ck: Downloading video info webpage
[youtube] 5PF-yJcM8ck: Extracting video information
[download] Destination: You_Will_Carry_My_Load-5PF-yJcM8ck.flv
[download] 100.0% of 14.17M at   52.64k/s ETA 00:00 


---

### Post by lisati on 2010-09-23
Thread closed: see link in my sig.

---

