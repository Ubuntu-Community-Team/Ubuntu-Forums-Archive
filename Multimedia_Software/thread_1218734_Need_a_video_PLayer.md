---
title: "Need a video PLayer"
date: 2009-07-21
forum: Multimedia Software
---

### Post by sthrnpagan on 2009-07-21
I am looking for a video player that will play avi files. the player that came with Ubuntu opens the movie but the program shuts down before the movie starts. Any suggestions?

---

### Post by philcamlin on 2009-07-21
vlc works great 

sudo apt-get install vlc :popcorn:

---

### Post by sthrnpagan on 2009-07-21
thank you for the help

---

### Post by sthrnpagan on 2009-07-21
OK now im getting frustrated. I got VLC and when I try to play my movie it to is shutting down before the movie plays. what could be causing this? I want to watch my movie, please, someone help

---

### Post by lisati on 2009-07-21
have a look here: [https://help.ubuntu.com/9.04/musicvideophotos/C/video.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video.html)

---

### Post by sthrnpagan on 2009-07-21
Ok i have read the link that was posted and I downloaded MPlayer hoping that would work, I even restarted my computer to see if that would help. Nothing, the programs still shuts down before the movie even plays.

---

### Post by hazelnut on 2009-07-21
If neither vlc nor mplayer worked on your avi file, I would suspect a corrupted avi file.  

You could try to load it into avidemux and convert it to something else.

---

### Post by zetanuxi on 2009-07-21
ive tried all mplayer, vlc and a few others and i still have the same problem as the OP.

i installed XBMC. its not as light as some of the other players, but you dont have to add any codecs to it. straight after install, i could play .avi and .mkv. 

you might want to look into that.[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

### Post by sthrnpagan on 2009-07-22
I tried to get xbmc installed, i followed the directions i found on how to install. i got the repo set and the key file set but it would not show up in synaptic as a package i could download. I am trying  the conversion suggestion. hopefully this will work, if not im all out of ideas

---

### Post by sthrnpagan on 2009-07-22
I want to thank everyone that has tried to help me. I can't get anything to work, so I guess I'm destined to not watch movies on Ubuntu. Oh well. I tried. Thanks again  :(

---

### Post by sthrnpagan on 2009-07-22
Weel, apparently no on knows how to help me fix this problem im having. I want to like Ubuntu, I really do, but this video issue is really leaving a bad taste in my mouth. I have tried everything suggested. I have even read posts by others that are having a similar issue. I am starting to get really disillusioned with this OS. If any can help me, Please let me know. I am desperate to get this resolved.

---

### Post by Surkow on 2009-07-22
What happens when you run mplayer from the commandline?

For example "mplayer /home/sthrnpagan/myvideo.avi"

I'd like to see what kind of error appears.

---

### Post by sthrnpagan on 2009-07-22
> **Surkow said:**
> What happens when you run mplayer from the commandline?

For example "mplayer /home/sthrnpagan/myvideo.avi"

I'd like to see what kind of error appears.

 this is what shows up when i run the command line

MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.53GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/jason/Harry.Potter.6.Half.Blood.Prince.CAM.XviD.EngAudio-androme.mkv.
File not found: '/home/jason/Harry.Potter.6.Half.Blood.Prince.CAM.XviD.EngAudio-androme.mkv'
Failed to open /home/jason/Harry.Potter.6.Half.Blood.Prince.CAM.XviD.EngAudio-androme.mkv.


Exiting... (End of file)

---

### Post by Surkow on 2009-07-22
> **sthrnpagan said:**
> this is what shows up when i run the command line

MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.53GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/jason/Harry.Potter.6.Half.Blood.Prince.CAM.XviD.EngAudio-androme.mkv.
File not found: '/home/jason/Harry.Potter.6.Half.Blood.Prince.CAM.XviD.EngAudio-androme.mkv'
Failed to open /home/jason/Harry.Potter.6.Half.Blood.Prince.CAM.XviD.EngAudio-androme.mkv.


Exiting... (End of file)

Try

```
mplayer "/home/jason/Harry.Potter.6.Half.Blood.Prince.CAM.XviD.EngAudio-androme.mkv"
```

And are you sure you have the video file in your home directory? MPlayer is unable to find the file.

---

### Post by sthrnpagan on 2009-07-22
> **Surkow said:**
> Try

```
mplayer "/home/jason/Harry.Potter.6.Half.Blood.Prince.CAM.XviD.EngAudio-androme.mkv"
```

And are you sure you have the video file in your home directory? Since mplayer is unable to find the file.

The vid File is sitting on my desktop. When I tried the first command line with the file in my videos folder this is what is returned:

MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.53GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/jason/videos/Harry.Potter.and.the.Half.Blood.Prince.avi.
File not found: '/home/jason/videos/Harry.Potter.and.the.Half.Blood.Prince.avi'
Failed to open /home/jason/videos/Harry.Potter.and.the.Half.Blood.Prince.avi.


Exiting... (End of file)

---

### Post by dk06 on 2009-07-22
> I want to thank everyone that has tried to help me. I can't get anything to work, so I guess I'm destined to not watch movies on Ubuntu. Oh well. I tried. Thanks again :sad:


Open your Synaptic Package Manager and search for VLC & Mozilla VLC, check the boxes & Apply
______________________________________________________________________________________
If you don't see it in there, 
Search for 'Player' or 'Video' and take your pick

You are destined to get out what you put in & you don't need to put a lot in to get a lot out

Good Luck
____________________________________________________________________________________
Check out some tutorials on how to install software, I think you may be experiencing a pebkac issue.

You Can Do It, Illegitimis non Carborundum


edit:
For restricted formats,

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by pedro_orange on 2009-07-22
What sort of movie is this?
Have you installed all the necessary codecs?

I usually just do a 

```
sudo apt-get install ubuntu-restricted-extras
```

& that installs all the movie, mp3, flash stuff I need.

---

### Post by sthrnpagan on 2009-07-22
> **pedro_orange said:**
> What sort of movie is this?
Have you installed all the necessary codecs?

I usually just do a 

```
sudo apt-get install ubuntu-restricted-extras
```

& that installs all the movie, mp3, flash stuff I need.

This is what was returned when I did that command

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  winbind
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Surkow on 2009-07-22
> **sthrnpagan said:**
> The vid File is sitting on my desktop. [...]
Your desktop is not "/home/jason/" But "/home/jason/Desktop" (Or a localised name such as "Bureaublad" in Dutch).

---

### Post by sthrnpagan on 2009-07-22
The video was downloaded with transmission from a Torrent site. I can play the video in Avidemux but there is no sound. so i know the vid works. Thank you in advance for the help.

---

### Post by sthrnpagan on 2009-07-22
> **Surkow said:**
> Your desktop is not "/home/jason/" But "/home/jason/Desktop" (Or a localised name such as "Bureaublad" in Dutch).

OH thanks, i re-entered the command with the correction but still got the same return.

---

### Post by theozzlives on 2009-07-22
do you have [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") and ubuntu-restricted-extras installed?
```
sudo apt-get install ubuntu-restricted-extras
```
It's not Ubuntu, mine plays AVIs fine.

---

### Post by pedro_orange on 2009-07-22
Open a terminal and run mplayer, but instead of typing the location of the file, drag the file onto the terminal and it'll dump the location for you. 
The error msgs are saying that mplayer can't find your file.

Incidentally, you have closed down the torrent application? This may be locking the file or something.

---

### Post by Surkow on 2009-07-22
It may seem obvious, but does the same thing happen with other video files? For example you can try [this]("http://www.bigbuckbunny.org/index.php/download/") movie (Big Buck Bunny).

---

### Post by sthrnpagan on 2009-07-22
[QUOTE=theozzlives;7657324]do you have [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") and ubuntu-restricted-extras installed?
```
sudo apt-get install ubuntu-restricted-extras
```[/QUOTE

i followed the link and put in the commands to get Medibuntu. All went well no error messages. i do believe i now have Medibuntu

---

### Post by sthrnpagan on 2009-07-22
> **Surkow said:**
> It may seem obvious, but does the same thing happen with other video files? For example you can try [this]("http://www.bigbuckbunny.org/index.php/download/") movie (Big Buck Bunny).

I can run online videos (i.e youtube) just fine.

---

### Post by dk06 on 2009-07-22
> **Surkow said:**
> Your desktop is not "/home/jason/" But "/home/jason/Desktop" (Or a localised name such as "Bureaublad" in Dutch).


cd ~/Desktop

---

### Post by Surkow on 2009-07-22
> **sthrnpagan said:**
> I can run online videos (i.e youtube) just fine.

Being able to use flash in a browser does not mean you can play local video files. The only reason I want you to try to play a file with mplayer is to be able to analyze the log to see what is wrong. Currently only the location is incorrect. There are no errors playing the file because the video player does not even attempt to play the file.

---

### Post by theozzlives on 2009-07-22
After you install the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories you should install w32codecs (or w64codecs) follow the link, read the page.

---

### Post by sthrnpagan on 2009-07-22
> **pedro_orange said:**
> Open a terminal and run mplayer, but instead of typing the location of the file, drag the file onto the terminal and it'll dump the location for you. 
The error msgs are saying that mplayer can't find your file.

Incidentally, you have closed down the torrent application? This may be locking the file or something.

ok did that, dragged file to terminal and the same thing still happens. Yes transmission is shut down

---

### Post by sthrnpagan on 2009-07-22
> **theozzlives said:**
> After you install the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories you should install w32codecs (or w64codecs) follow the link, read the page.

ok got w32codecs

---

### Post by theozzlives on 2009-07-22
> **sthrnpagan said:**
> ok got w32codecs

did it work?

---

### Post by sthrnpagan on 2009-07-22
> **theozzlives said:**
> did it work?

when i typed 

mplayer /home/jason/Videos/Harry.Potter.and.the.Half.Blood.Prince.avi 

into the terminal a littel window popped up and started playing sound but no video.

all the while the terminal was running like crazy. Here are the last few lines that it put out before i stopped the video.

X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0

---

### Post by theozzlives on 2009-07-22
> **sthrnpagan said:**
> when i typed 

mplayer /home/jason/Videos/Harry.Potter.and.the.Half.Blood.Prince.avi 

into the terminal a littel window popped up and started playing sound but no video.

all the while the terminal was running like crazy. Here are the last few lines that it put out before i stopped the video.

X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0

try just double clicking on the file.

---

### Post by sthrnpagan on 2009-07-22
> **theozzlives said:**
> try just double clicking on the file.


nothing. just opens and immediately closes.

---

### Post by theozzlives on 2009-07-22
> **sthrnpagan said:**
> nothing. just opens and immediately closes.

One last thing before I move on (I'll stick around to see if it works). This is old and I used to use it to play DVDs, but it might work...
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by sthrnpagan on 2009-07-22
> **theozzlives said:**
> One last thing before I move on (I'll stick around to see if it works). This is old and I used to use it to play DVDs, but it might work...
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

ok from the first code i got this return

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread3

from the second this return:

sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found

---

### Post by theozzlives on 2009-07-22
> **sthrnpagan said:**
> ok from the first code i got this return

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread3

from the second this return:

sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found

said it was old, I'm out of ideas. I just installed 9.04 64 bit and have nothing but Medibuntu and ubuntu-restricted extras and I just played an AVI file, so I'm at a loss.

---

### Post by sthrnpagan on 2009-07-22
> **theozzlives said:**
> said it was old, I'm out of ideas. I just installed 9.04 64 bit and have nothing but Medibuntu and ubuntu-restricted extras and I just played an AVI file, so I'm at a loss.

Thanks for the help. BTW how do i edit signature permissions to allow HTML code. I have a Linux user number and ubuntu user number and would like to display them in my signature.

---

### Post by Surkow on 2009-07-22
> **sthrnpagan said:**
> when i typed 

mplayer /home/jason/Videos/Harry.Potter.and.the.Half.Blood.Prince.avi 

into the terminal a littel window popped up and started playing sound but no video.

all the while the terminal was running like crazy. Here are the last few lines that it put out before i stopped the video.

X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0 
X11 error: BadAlloc (insufficient resources for operation)  1.3% 0 0

Interesting...it's probably not a codec issue but a driver issue with xorg (graphics drivers etc).

---

### Post by sthrnpagan on 2009-07-22
> **Surkow said:**
> Interesting...it's probably not a codec issue but a driver issue with xorg (graphics drivers etc).

well, i will have to try again tomorrow night. I need sleep  gotta work today

---

### Post by sthrnpagan on 2009-07-22
Thank you to everyone that has helped me out this evening. I am truly grateful. If you come across something that might help, please post it and i will give it a shot. Goodnight all

---

### Post by Surkow on 2009-07-22
A last suggestion would be to install SMPlayer (a frontend for MPlayer) and select a different video output driver in the preferences (not xv but gl for example).

---

### Post by Conzo on 2009-07-22
> **sthrnpagan said:**
> I want to thank everyone that has tried to help me. I can't get anything to work, so I guess I'm destined to not watch movies on Ubuntu. Oh well. I tried. Thanks again  :(


Had the Same Problem ...


sudo apt-get update 
sudo apt-get install vlc libdvdcss2 


Hopes that right still learning 


Conzo one Month Off  Windows ... no more Withdraws !

---

### Post by issih on 2009-07-22
I've been having similar issues with video players recently, and in my case it seems to be linked to compiz.

to test, try hitting alt+f2 and run:

```
metacity --replace
```

then try running your video apps. If that now works it is compiz that is causing you problems by filling up your video ram.

```
compiz --replace
```

will turn your visual effects back on, but you will need to go through your settings and turn off things until you hit a workable compromise.

Hope that helps

---

### Post by sthrnpagan on 2009-07-23
> **Surkow said:**
> A last suggestion would be to install SMPlayer (a frontend for MPlayer) and select a different video output driver in the preferences (not xv but gl for example).


Thank you, Thank you, Thank you. This totally worked. MY search is over. Again thank you. You have saved me much frustration. A thousand times thank you. :KS

---

