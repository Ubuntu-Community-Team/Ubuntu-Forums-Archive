---
title: "xmms2 help (debian)"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by abierstedt on 2008-02-24
hey all,


I did some looking around but it doesn't seem like others are having this problem. For the past week or two xmms2 has not worked the way I normally use it. xmms2 constantly restarts and seems to have errors from time to time. Often times i will add music from mlib and try to play it and nothing starts. It seems as if whenever i use "xmms2 list" the player will self destruct. Here is an example of the way I use it and what has been going on -  


```

anthony@Bongzilla:~$ xmms2 list
ERROR: Disconnected
Log output will be stored in /home/anthony/.cache/xmms2/xmms2d.log

anthony@Bongzilla:~$ xmms2 list
Log output will be stored in /home/anthony/.cache/xmms2/xmms2d.log
xmms2 started

Total playtime: 0:00:00
anthony@Bongzilla:~$ xmms2 config output.plugin alsa
Config value output.plugin set to alsa

anthony@Bongzilla:~$ xmms2 mlib searchadd artist="gwar"
anthony@Bongzilla:~$ xmms2 play
anthony@Bongzilla:~$ xmms2 list

Total playtime: 0:00:00
anthony@Bongzilla:~$ xmms2 mlib searchadd artist="gwar"
anthony@Bongzilla:~$ xmms2 list

Total playtime: 0:00:00
anthony@Bongzilla:~$ xmms2 mlib searchadd artist:"gwar"
anthony@Bongzilla:~$ xmms2 list
->[0/4018] Gwar - The Reaganator (03:02)
  [1/4019] Gwar - The Bonus Plan (01:13)
  [2/4020] Gwar - You Can't Kill Terror (03:14)
  [3/4021] Gwar - Fistful Of Teeth (03:57)
  [4/4011] Gwar - Bring Back The Bomb (04:20)
  [5/4012] Gwar - Krosstika (03:33)
  [6/4013] Gwar - Womb With A View (02:23)
  [7/4014] Gwar - Decay Of Granduer (04:02)
  [8/4015] Gwar - War Party (03:14)
  [9/4016] Gwar - Bonesnapper (The Faces Of The Slain) (04:40)
  [10/4017] Gwar - Lost God (03:56)

Total playtime: 0:37:35
anthony@Bongzilla:~$ xmms2 play
anthony@Bongzilla:~$ xmms2 stop
anthony@Bongzilla:~$ xmms2 list
ERROR: Disconnected
anthony@Bongzilla:~$ xmms2
xmms2           xmms2d          xmms2-launcher 
anthony@Bongzilla:~$ xmms2-launcher
Log output will be stored in /home/anthony/.cache/xmms2/xmms2d.log
xmms2 started
anthony@Bongzilla:~$ xmms2 mlib searchadd artist:"gwar"
anthony@Bongzilla:~$ xmms2 list
->[0/4018] Gwar - The Reaganator (03:02)
  [1/4019] Gwar - The Bonus Plan (01:13)
  [2/4020] Gwar - You Can't Kill Terror (03:14)
  [3/4021] Gwar - Fistful Of Teeth (03:57)
  [4/4011] Gwar - Bring Back The Bomb (04:20)
  [5/4012] Gwar - Krosstika (03:33)
  [6/4013] Gwar - Womb With A View (02:23)
  [7/4014] Gwar - Decay Of Granduer (04:02)
  [8/4015] Gwar - War Party (03:14)
  [9/4016] Gwar - Bonesnapper (The Faces Of The Slain) (04:40)
  [10/4017] Gwar - Lost God (03:56)

Total playtime: 0:37:35

anthony@Bongzilla:~$ xmms2 play
Log output will be stored in /home/anthony/.cache/xmms2/xmms2d.log
xmms2 started
anthony@Bongzilla:~$ xmms2 stop
ERROR: Couldn't stop playback: Disconnected
anthony@Bongzilla:~$ sudo apt-get --purge remove xmms2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxmmsclient3 xmms2-plugin-alsa xmms2-plugin-id3v2 xmms2-plugin-mad xmms2-core xmms2-client-cli xmms2-plugin-vorbis libnss3-0d libxmmsclient-glib1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xmms2*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
After this operation, 32.8kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 94179 files and directories currently installed.)
Removing xmms2 ...
anthony@Bongzilla:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxmmsclient3 xmms2-plugin-alsa xmms2-plugin-id3v2 xmms2-plugin-mad xmms2-core xmms2-client-cli xmms2-plugin-vorbis libnss3-0d libxmmsclient-glib1
The following packages will be REMOVED:
  libnss3-0d libxmmsclient-glib1 libxmmsclient3 xmms2-client-cli xmms2-core xmms2-plugin-alsa xmms2-plugin-id3v2 xmms2-plugin-mad xmms2-plugin-vorbis
0 upgraded, 0 newly installed, 9 to remove and 3 not upgraded.
After this operation, 2019kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 94171 files and directories currently installed.)
Removing libnss3-0d ...
Removing xmms2-client-cli ...
Removing libxmmsclient-glib1 ...
Removing libxmmsclient3 ...
Removing xmms2-plugin-vorbis ...
Removing xmms2-plugin-mad ...
Removing xmms2-plugin-id3v2 ...
Removing xmms2-plugin-alsa ...
Removing xmms2-core ...
anthony@Bongzilla:~$ sudo apt-get -t stable  install xmms2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libxmmsclient-glib0 libxmmsclient0 xmms2-client-cli xmms2-core xmms2-plugin-alsa xmms2-plugin-id3v2 xmms2-plugin-mad xmms2-plugin-vorbis
The following NEW packages will be installed:
  libxmmsclient-glib0 libxmmsclient0 xmms2 xmms2-client-cli xmms2-core xmms2-plugin-alsa xmms2-plugin-id3v2 xmms2-plugin-mad xmms2-plugin-vorbis
0 upgraded, 9 newly installed, 0 to remove and 3 not upgraded.
Need to get 927kB of archives.
After this operation, 1700kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://ftp.us.debian.org](http://ftp.us.debian.org) stable/main libxmmsclient-glib0 0.2DrGonzo-4.1 [7044B]
Get:2 [http://ftp.us.debian.org](http://ftp.us.debian.org) stable/main libxmmsclient0 0.2DrGonzo-4.1 [33.7kB]
Get:3 [http://ftp.us.debian.org](http://ftp.us.debian.org) stable/main xmms2-core 0.2DrGonzo-4.1 [803kB]
Get:4 [http://ftp.us.debian.org](http://ftp.us.debian.org) stable/main xmms2-client-cli 0.2DrGonzo-4.1 [26.0kB]
Get:5 [http://ftp.us.debian.org](http://ftp.us.debian.org) stable/main xmms2-plugin-vorbis 0.2DrGonzo-4.1 [9396B]
Get:6 [http://ftp.us.debian.org](http://ftp.us.debian.org) stable/main xmms2-plugin-mad 0.2DrGonzo-4.1 [13.1kB]
Get:7 [http://ftp.us.debian.org](http://ftp.us.debian.org) stable/main xmms2-plugin-id3v2 0.2DrGonzo-4.1 [12.2kB]
Get:8 [http://ftp.us.debian.org](http://ftp.us.debian.org) stable/main xmms2-plugin-alsa 0.2DrGonzo-4.1 [11.8kB]
Get:9 [http://ftp.us.debian.org](http://ftp.us.debian.org) stable/main xmms2 0.2DrGonzo-4.1 [10.9kB]
Fetched 927kB in 0s (1402kB/s)           
Selecting previously deselected package libxmmsclient-glib0.
(Reading database ... 94095 files and directories currently installed.)
Unpacking libxmmsclient-glib0 (from .../libxmmsclient-glib0_0.2DrGonzo-4.1_i386.deb) ...
Selecting previously deselected package libxmmsclient0.
Unpacking libxmmsclient0 (from .../libxmmsclient0_0.2DrGonzo-4.1_i386.deb) ...
Selecting previously deselected package xmms2-core.
Unpacking xmms2-core (from .../xmms2-core_0.2DrGonzo-4.1_i386.deb) ...
Selecting previously deselected package xmms2-client-cli.
Unpacking xmms2-client-cli (from .../xmms2-client-cli_0.2DrGonzo-4.1_i386.deb) ...
Selecting previously deselected package xmms2-plugin-vorbis.
Unpacking xmms2-plugin-vorbis (from .../xmms2-plugin-vorbis_0.2DrGonzo-4.1_i386.deb) ...
Selecting previously deselected package xmms2-plugin-mad.
Unpacking xmms2-plugin-mad (from .../xmms2-plugin-mad_0.2DrGonzo-4.1_i386.deb) ...
Selecting previously deselected package xmms2-plugin-id3v2.
Unpacking xmms2-plugin-id3v2 (from .../xmms2-plugin-id3v2_0.2DrGonzo-4.1_i386.deb) ...
Selecting previously deselected package xmms2-plugin-alsa.
Unpacking xmms2-plugin-alsa (from .../xmms2-plugin-alsa_0.2DrGonzo-4.1_i386.deb) ...
Selecting previously deselected package xmms2.
Unpacking xmms2 (from .../xmms2_0.2DrGonzo-4.1_all.deb) ...
Setting up libxmmsclient-glib0 (0.2DrGonzo-4.1) ...
Setting up libxmmsclient0 (0.2DrGonzo-4.1) ...
Setting up xmms2-core (0.2DrGonzo-4.1) ...
Setting up xmms2-client-cli (0.2DrGonzo-4.1) ...
Setting up xmms2-plugin-vorbis (0.2DrGonzo-4.1) ...
Setting up xmms2-plugin-mad (0.2DrGonzo-4.1) ...
Setting up xmms2-plugin-id3v2 (0.2DrGonzo-4.1) ...
Setting up xmms2-plugin-alsa (0.2DrGonzo-4.1) ...
Setting up xmms2 (0.2DrGonzo-4.1) ...
anthony@Bongzilla:~$ xmms2 mlib addpath /media/shared/audio/music/
anthony@Bongzilla:~$ xmms2 mlib searchadd artist:"afi"
xmms2 started
ERROR: Unable to generate query
anthony@Bongzilla:~$ xmms2 mlib searchadd artist="afi"
xmms2 started
anthony@Bongzilla:~$ xmms2 list
xmms2 started

Total playtime: 0:00:00
anthony@Bongzilla:~$ xmms2-launcher
xmms2 started
anthony@Bongzilla:~$ xmms2 mlib searchadd artist:"afi"
ERROR: Unable to generate query
anthony@Bongzilla:~$ xmms2 mlib addpath /media/shared/audio/music
xmms2 started
anthony@Bongzilla:~$ xmms2 mlib searchadd artist:"afi"
ERROR: Unable to generate query
anthony@Bongzilla:~$ xmms2 mlib searchadd artist:"gwar"
ERROR: Unable to generate query
anthony@Bongzilla:~$

anthony@Bongzilla:~$ xmms2 mlib loadall
anthony@Bongzilla:~$ xmms2 list
->[0/8407] 00+-+4hero+-+Play+With+The+Changes.m3u (00:00)
  [1/3] 4hero - Morning Child - 4 Hero & Carina Andersson (04:36)
  [2/4] 4hero - Take My Time - 4 Hero & Jack Davey (04:07)
  [3/5] 4hero - Look Inside - 4 Hero & Face (04:07)
  [4/6] 4hero - Sink Or Swim - 4 Hero & Lady Alma (03:51)
  [5/7] 4hero - Give In - 4 Hero & Darien Brockington/Phonte (04:53)
  [6/8] 4hero - Play With The Changes - 4 Hero & Talita Long/Harry Mizell (05:57)
  [7/9] 4hero - Something In The Way - 4 Hero & Bembe Segue/Kaidi Tatham (04:59)
  [8/10] 4hero - Stoke Up The Fire - 4 Hero & Face (05:05)
  [9/11] 4hero - Awakening - 4 Hero & Ursula Rucker (04:45)
  [10/12] 4hero - Sophia - 4 Hero (03:54)
  [11/13] 4hero - Superwoman (Where Were You When I Needed You) - 4 Hero & Terry Devos (0
  [12/14] 4hero - Why Don't You Talk - 4 Hero (04:35)
  [13/15] 4hero - Bed Of Roses - 4 Hero & Jody Watley (04:06)
  [14/16] 4hero - Gonna Give It Up - 4 Hero & Lady Alma (02:46)
  [15/17] 4hero - Our Own Place - 4 Hero (04:09)
  [16/18] 4hero - Dedication To The Horse (01:52)
  [17/8408] AlbumArtSmall.jpg (00:00)
  [18/8409] folder.jpg (00:00)
  [19/8410] AlbumArtSmall.jpg (00:00)
  [20/8411] AlbumArt_%7b2C62403D-D5E9-4FD6-82A6-30D15C57CAA0%7d_Large.jpg (00:00)
  [21/8412] AlbumArt_%7b2C62403D-D5E9-4FD6-82A6-30D15C57CAA0%7d_Small.jpg (00:00)
  [22/8413] Folder.jpg (00:00)
  [23/25] 7 Seconds - Satyagraha (03:09)
  [24/26] 7 Seconds - Busy Little People (03:27)
ERROR: Disconnected

```


I have tried from stable testing and unstable (using lenny)
Does anyone have a guess to why I am having these issues? I have been using this player for months and have not experienced these problems. My roomate has the same problem to. Also sometimes it works and sometimes it doesnt. The problem happens most when i try to jump in the playlist or list the current playlist.

I may try mpd would anyone recommend it over xmms2?

thanks

---

### Post by chocolatetoothpaste on 2008-02-24
Look here at this guide, see if it helps:
[http://ubuntuforums.org/showthread.php?t=706736](http://ubuntuforums.org/showthread.php?t=706736)

---

