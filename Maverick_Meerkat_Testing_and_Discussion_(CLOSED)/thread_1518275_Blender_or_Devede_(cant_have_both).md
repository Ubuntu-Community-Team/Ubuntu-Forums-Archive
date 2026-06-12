---
title: "Blender or Devede (cant have both)"
date: 2010-06-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2010-06-26
Blender or Devede is it possible to have both > ?

libavutil49 .......... gets removed if devede is added ..... 

and Blender needs it to run .......... so  stops working .....

keith@keith-laptop:~$ blender
blender-bin: error while loading shared libraries: libavutil.so.49: cannot open shared object file: No such file or directory
keith@keith-laptop:~$ 

_________________________________________________________________

Once you install .......... **libavutil49 ............... Blender** will work ok .........

But then you cannot have **Devede ........... which uses ...... libavutil-extra-49** .......
and if you try installing it ......... it automatically removes libavutil49 ...........

__________________________________________________________________

---

### Post by lavinog on 2010-06-26
It looks like a dependency issue.
You should file a bug for this issue.

You could install devede with the package manager, and download blender from blender.org

---

### Post by mc4man on 2010-06-26
> Blender or Devede is it possible to have both
You can have both installed - blender does allow libavutil-extra-49 

The issue then is libavutil-extra-49 is basically empty - there are no .so's  installed.

Ideally both should be re-built for libavutil-50 | libavutil-extra-50 or devede should allow libavutil-49 which does contain .so files

---

### Post by 23dornot23d on 2010-06-26
> **lavinog said:**
> It looks like a dependency issue.
You should file a bug for this issue.

You could install devede with the package manager, and download blender from blender.org


Tried this .... Blender 2.5 in its own directory would not work otherwise thats the way I would have run them ....... cheers for the reply ....

---

### Post by 23dornot23d on 2010-06-26
> **mc4man said:**
> You can have both installed - blender does allow libavutil-extra-49 

The issue then is libavutil-extra-49 is basically empty - there are no .so's  installed.

Ideally both should be re-built for libavutil-50 | libavutil-extra-50 or devede should allow libavutil-49 which does contain .so files

Try it out ..... let me know how it goes .....  thanks for the reply ..........

I tried it ..... unless I am missing something ..... is there a way of forcing both to stay , seems each one removes the other by default .

I have Blender 2.49b installed ...... and run 2.5 from a separate download ....... if I need derede - Iwill install it when needed then remove it

again after I have done my task .....

..... think the problem lies with Derede ...... as Blender has been around longer .......

---

### Post by mc4man on 2010-06-26
> Try it out...

Atm it's a bit of a moot point - as noted the issue is not that they both can't currently be installed - it's that libavutil-extra-49 is an 'empty' package.
I believe both blender and devede will be re-built at some point this summer (off of ffmpeg 0.6
(or do yourself in meantime


> 
commit Log for Sat Jun 26 15:08:27 2010

Installed the following packages:
autopoint (0.17-11ubuntu1)
[COLOR="Blue"]blender[/COLOR] (2.49.2~dfsg-2ubuntu1)
cvs (1:1.12.13-12ubuntu1)
[COLOR="Blue"]devede[/COLOR] (3.16.8-0ubuntu1)
gettext (0.17-11ubuntu1)
libalut0 (1.1.0-2)
libavcodec-extra-52 (4:0.6-1ubuntu1)
libavdevice-extra-52 (4:0.6-1ubuntu1)
libavformat-extra-52 (4:0.6-1ubuntu1)
[COLOR="Red"]libavutil-extra-49 [/COLOR](4:0.6~svn20100505-1ubuntu3)
libavutil-extra-50 (4:0.6-1ubuntu1)
libdc1394-22 (2.1.2-3)
libftgl2 (2.1.3~rc5-3)
libpostproc-extra-51 (4:0.6-1ubuntu1)
libswscale-extra-0 (4:0.6-1ubuntu1)
ttf-dejavu (2.31-1)
ttf-dejavu-extra (2.31-1)


(Ot - Tried the live dvd you've been using for 10.10 - kinda interesting - like the icon and theme choices, not so keen on some of the default packages they've chosen.

---

### Post by 23dornot23d on 2010-06-26
> **mc4man said:**
> Atm it's a bit of a moot point - as noted the issue is not that they both can't currently be installed - it's that libavutil-extra-49 is an 'empty' package.
I believe both blender and devede will be re-built at some point this summer (off of ffmpeg 0.6
(or do yourself in meantime




(Ot - Tried the live dvd you've been using for 10.10 - kinda interesting - like the icon and theme choices, not so keen on some of the default packages they've chosen.

_________________________________________________________________

Cheers ,,,, I noticed that too ..... it all installs without a glitch ..... when you try opening blender though nothing happens ........ 

Yep the Ultimate Edition is quite nice ..... as you say the package choice may not
suit everybody ..... but it is a slightly bigger install at just over 1 gig .....

I always add the 3D programs and up to now most things look ok .....

Wings 3d and k3dsurf and Blender....... I must try OFX out too ....

The mouse keeps playing up ..... gives a double click all the time - when releasing ..... 
quite frustrating doing 3D work as I like the mouse to work properly - may be my worn out old mouse though ......
have been thinking of getting a better one .......

Ok thanks again ..... the realtime kernel is good too ..... but the graphics card will not pick up when running it ...... 

but thats another story for another thread ...... 
(as both kernels use the same file system I expected the Nvidia 195.36.24 driver to work too .... alas ... but it does not )

Not sure if that is part of this Maverick testing here or not !!! ..... 
( as it seems a totally different kernel ,,,, so will keep that one to one side ....... )

---

### Post by mc4man on 2010-06-26
If you're inclined to fool around a bit

I somewhat doubt that devede actually needs the extra version of libavutil.

So, without rebuilding you can do this - takes about 1 min.or so

Go here and copy the script in post 4 to a file in home dir. named editdeb, save and make executable (or put in a bin in path, for Ex.is just in home dir.

[http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

Then place the devede .deb in home dir. (grab from /var/cache/apt/archives

In a terminal run (adjust blue if different
./editdeb /home/<your user name>/[COLOR="Blue"]devede_3.16.8-0ubuntu1_all.deb[/COLOR]

Then edit the control file that opens like this (added blue

> Package: devede
Version: 3.16.8-0ubuntu[COLOR="Red"]1[/COLOR]
Architecture: all
Maintainer: Alessio Treglia <quadrispro@ubuntu.com>
Installed-Size: 4024
Depends: python, python-support (>= 0.90.0), python-gtk2, python-gobject, python-cairo, mencoder, dvdauthor, genisoimage, vcdimager, imagemagick, mplayer, libavcodec-extra-52, libavformat-extra-52, [COLOR="Blue"]libavutil49 |[/COLOR] libavutil-extra-49, libpostproc-extra-51, libswscale-extra-0
Section: video
Priority: optional
Homepage: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)
Description: simple application to create Video DVDs
 DeVeDe is a program to create video DVDs, suitables for home players, from
 any number of video files, in any of the formats supported by Mplayer.
 .
 It allows user to create subtitles and even menus.

Click save in gedit and close terminal - new .deb will be created - install it, then install libavutil49 and see



Ex. (from livecd
> ubuntu@ubuntu:~$ ./editdeb '/home/ubuntu/devede_3.16.8-0ubuntu1_all.deb' 
Building new deb...
dpkg-deb: building package `devede' in `devede_3.16.8-0ubuntu1_all.modfied.deb'.
ubuntu@ubuntu:~$ sudo apt-get install libavutil49
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ubuntu-sso-client
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libavutil-extra-49
The following NEW packages will be installed:
  libavutil49
0 upgraded, 1 newly installed, 1 to remove and 80 not upgraded.
Need to get 93.3kB of archives.
After this operation, 143kB of additional disk space will be used.
Do you want to continue [Y/n]? y
ect...



Now both devede and blender are installed and 'working' (can't test how well on live cd

Note - the modified .deb could be updated back to orig.  - if you wanted to prevent then adjust red version # - make a 2
(I'm on the ubuntu live cd, not ult.

---

### Post by 23dornot23d on 2010-06-26
Looks good will give it a go .... thank you ...

---

### Post by mc4man on 2010-06-26
At the end of the day a rebuild is really the proper solution for both, in regards to libavutil and also the other ffmpeg shared libs.

 - this is just a bit of a fool around to see -

---

### Post by 23dornot23d on 2010-06-26
Did as you said above and it worked fine ,,,, thank you ... 

I realize its not the full solution but it appears to work ..... 

it still needs a test DVD doing before I can say its 100% I will add to this later
if I manage to do one successfully ......

Both Programs run together now and ,,,
Blender works well ..... ok ... cheers ...... :p

---

