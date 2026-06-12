---
title: "[SOLVED] Stops booting to Myth TV"
date: 2008-03-21
forum: Mythbuntu
---

### Post by niciliketo on 2008-03-21
Hi,

My Mythbuntu system has started failing to boot properly.

At startup it gets as far as the desktop background, with the Mythbuntu logo.  A series of messages are shown at the bottom of the screen, the last of which is 'Starting the Desktop Managerr' ( with two r's as I have spelt it).  There is then a long period of heavy disc activity, with no changes on screen (and no menus or anything I can click).  Eventually, the screen saver comes on!

The only change that I have made since it worked correctly was installing some automatic updates that I was offered today.  Afraid I did not pay much attention to what was in the updates, and assumed that they would not cause any problems.

I am able to ssh to the box, and using my very limited NIX skills was able to issue a few ps -aef commands, I did this because of all the disc activity.

It appears that there is a large (over 40) and growing number of mythbackend processes, not sure if this is usual, but suspect not.  I think there are lots of other processes ( update-notified, python, gnome-power-manager, etc )too, but it is hard to know if this is usual?

Please, can anyone help?  I had finally managed to get the machine setup just how I wanted it, RC, TV, VLC, etc, etc, all working, now this happens.

Also, I have noticed a number of python processes too

nic@nic-ubuntu:/etc/rc2.d$ pidof python
19269 19255 19242 19234 19053 19032 18395 18357 18214 18168 18100 18045 17943 17763 17720 17676 17565 17518 17479 17452 17419 17387 17353 17309 17252 17130 17069 17035 16947 16888 16838 16770 16702 16644 16595 16526 16449 16393 16321 16260 16212 16139 16082 16040 15980 15922 15872 15790 15740 15663 15633 15561 15497 15440 15377 15296 15245 15172 15034 14986 14946 14883 14818 14792 14742 14667 14632 14553 14481 14445 14384 14320 14258 14188 14116 14062 14012 13945 13849 13785 13728 13658 13614 13534 13471 13422 13350 13307 13228 13169 13136 13053 12998 12972 12887 12814 12768 12699 12640 12583 12487 12446 12391 12364 12269 12200 12153 12120 12059 11986 11909 11863 11822 11768 11676 11616 11532 11478 11404 11342 11269 11157 11119 11059 11021 10960 10893 10782 10735 10679 10640 10561 10528 10437 10371 10335 10260 10216 10152 10073 10024 9963 9893 9798 9720 9634 9557 9527 9492 9435 9390 9318 9272 9109 9009 8985 8944 8836 8799 8684 8624 8552 8497 8414 8364 8275 8224 8162 8086 8025 7970 7922 7873 7767 7712 7665 7553 7502 7427 7376 7299 7233 7139 7080 7000 6946 6903 6835 6798
nic@nic-ubuntu:/etc/rc2.d$ pidof mythbackend
25697 25575 25524 25425 25315 19353 19320 19227 19174 19114 19070 19016 18955 18900 18847 18788 18731 18663 18617 18548 18499 18434 18370 18318 18261 18210 18151 18091 18031 17985 17914 17856 17795 17737 17663 17604 17542 17455 17402 17347 17240 17190 17133 17078 17014 16960 16892 16841 16739 16688 16613 16573 16529 16444 16385 16328 16270 16201 16143 16094 16021 15969 15932 15848 15795 15727 15666 15611 15557 15508 15431 15366 15303 15251 15199 15148 15072 15024 14958 14901 14840 14773 14715 14656 14603 14536 14494 14431 14372 14309 14249 14169 14121 14061 14002 13950 13897 13856 13777 13720 13664 13600 13542 13444 13361 13313 13271 13229 13125 13089 13047 13011 12926 12890 12827 12729 12674 12614 12548 12502 12432 12373 12267 12194 12152 12103 12053 12004 11954 11923 11842 11752 11716 11660 11605 11548 11483 11423 11364 11304 11252 11186 11125 11070 10986 10947 10886 10826 10769 10716 10666 10606 10548 10542 10490 10476 10432 10431 10374 10365 10315 10307 10251 10240 10201 10184 10146 10121 10079 10057 10005 10003 9957 9947 9875 9812 9747 9683 9633 9626 9572 9551 9510 9509 9459 9405 9332 9312 9267 9232 9205 9136 9103 9070 9018 9000 8977 8933 8847 8783 8770 8728 8672 8657 8609 8534 8471 8464 8409 8352 8308 8266 8253 8200 8136 8130 8080 8052 8019 7971 7962 7807 7753 7711 7655 7620 7603 7560 7539 7513 7493 7459 7426 7411 7278 7234 7215 7134 7132 7084 7042 6996 6994 6930 6926 6885 6873 6808 6773 6737 6689 6594 6534 6483 6422 6358 6309 6239 6175 6042 5986 5948 5863 5799 5742 5705 5619 5557 5507 5457 5384 5352 5272 5211 5156 5116 5048 4995 4902 4860 4787 4755 4692 4642 4569 4517 4465 4397 4341 4301 4239 4161 4113 4052 3999 3945 3873 3837 3744 3709 3640 3594 3550 3489 3430 3360 3311 3263 3196 3138 3081 2997 2939 2881 2815 2754 2685 2612 2551 2503 2444 2390 2341 2265 2215 2178 2100 2046 1983 1918 1872 1787 1738 1691 1627 1575 1484 1448 1365 1320 1266 1228

Still stumped...

---

### Post by w0lfpaws on 2008-03-22
damm, im having the same problem,....only reason im using mythbuntu, is for a digital slideshow, in a 15" lcd picture frame.......everythings good, ran for weeks without issues,  now just randomly goes back to desktop,.....so start mythtv again , image gallery,....works fine again for a few days,.....back to desktop.......now after rebooting,....trying to start mythfrontend,.....its just doesnt do anything, i cant get myth to start again....wtf?    did this b4 and after updates,  is there a way to force myth to start from the command line?   this is very frustrating 
although i dont get all the weird errors ,  its just doesnt start
myth is set to start at boot

thanks

[IMG][[IMG]http://img380.imageshack.us/img380/8816/mythframeys4.th.jpg[/IMG]](http://img380.imageshack.us/my.php?image=mythframeys4.jpg)[/IMG]

---

### Post by laga on 2008-03-22
> **niciliketo said:**
> 

I am able to ssh to the box, and using my very limited NIX skills was able to issue a few ps -aef commands, I did this because of all the disc activity.


You can run 'top' to check which process is using most CPU time... 'free -m' will tell you how much memory is used (look in the '-/+ buffers/cache:' line). Also check /var/log/mythtv/* and /var/log/messages for anything suspicious.

---

### Post by niciliketo on 2008-03-23
Thanks for the info.

I tried top:
=========================================
top - 18:34:02 up 18 min,  2 users,  load average: 76.04, 58.11, 36.93
Tasks: 706 total,   7 running, 698 sleeping,   0 stopped,   1 zombie
Cpu(s): 17.1%us,  7.2%sy,  0.2%ni,  0.0%id, 74.5%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:   1026684k total,  1015080k used,    11604k free,     6824k buffers
Swap:  3004112k total,  1765528k used,  1238584k free,    89516k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6194 nic       16   0  236m  15m  11m S   13  1.5   1:19.97 mythfrontend.re
 5746 root      15   0  428m 5788 2040 S    5  0.6   0:41.74 Xorg
19182 nic       22   0 1174m  22m 9976 S    5  2.2   0:01.22 java
 6674 nic       15   0  215m  16m  11m R    3  1.6   0:38.75 mythfrontend.re
 6421 nic       15   0  217m  14m  11m R    2  1.5   0:41.71 mythfrontend.re
 6533 nic       15   0  217m  18m  11m R    2  1.8   0:31.00 mythfrontend.re
 6293 nic       15   0  216m  14m  11m S    2  1.5   0:37.47 mythfrontend.re
19122 nic       22   0 1174m  17m 9920 S    2  1.7   0:00.98 java
19239 nic       21   0 1173m  17m 9600 S    2  1.7   0:00.62 java
19570 nic       15   0  2764 1528  876 R    2  0.1   0:00.38 top
19327 nic       20   0 1173m  17m 9600 S    1  1.7   0:00.60 java
19279 nic       16   0 1173m  17m 9600 S    1  1.7   0:00.56 java
19522 nic       20   0 1172m  17m 9616 S    1  1.7   0:00.55 java
 6210 nic       18   0  206m  26m  10m S    1  2.7   0:11.53 mythbackend
19725 nic       18   0  7784 4108 2044 D    1  0.4   0:00.09 python
19729 nic       18   0  4940 3352 1580 D    1  0.3   0:00.06 restricted-mana
   31 root      10  -5     0    0    0 S    0  0.0   0:00.29 kblockd/0
=======================================
free -m
             total       used       free     shared    buffers     cached
Mem:          1002        930         71          0         22        138
-/+ buffers/cache:        770        232
Swap:         2933       1740       1193
========================================
The logs looked OK except for the mythfrontend (which was very very big)...
nic@nic-ubuntu:/var/log/mythtv$ tail -f mythfrontend.log
Starting mythfrontend.real..
2008-03-23 18:35:16.675 Current Schema Version: 1160
2008-03-23 18:35:16.734 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-03-23 18:35:16.734 Enabled verbose msgs:  important general
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
2008-03-23 18:35:40.574 Total desktop dim: 1280x768, with 1 screen[s].
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
2008-03-23 18:35:40.589 MythXOpenDisplay() failed
2008-03-23 18:35:47.399 Current Schema Version: 1160
2008-03-23 18:35:47.657 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-03-23 18:35:47.657 Enabled verbose msgs:  important general
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
2008-03-23 18:35:48.127 MythXOpenDisplay() failed
2008-03-23 18:35:48.504 Current Schema Version: 1160
2008-03-23 18:35:48.520 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-03-23 18:35:48.520 Enabled verbose msgs:  important general
Starting mythfrontend.real..
Starting mythfrontend.real..
2008-03-23 18:35:49.126 Current Schema Version: 1160
2008-03-23 18:35:49.147 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-03-23 18:35:49.148 Enabled verbose msgs:  important general
2008-03-23 18:35:50.287 Total desktop dim: 1280x768, with 1 screen[s].
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
2008-03-23 18:35:50.716 MythXOpenDisplay() failed
Starting mythfrontend.real..
===================================
So, there are lots of front ends and lots of backends, but what does it all mean?  And why has it started happening?

---

### Post by niciliketo on 2008-03-24
OK - fixed it by uninstalling myth and reinstalling.
Sorry for anyone else who has this problem, as this seems like a pretty drastic step, however all my config settings seem to have remained (except my remote control now doesn't work).

Thanks to everyone who has looked at this post, and thanks for a great product.

---

