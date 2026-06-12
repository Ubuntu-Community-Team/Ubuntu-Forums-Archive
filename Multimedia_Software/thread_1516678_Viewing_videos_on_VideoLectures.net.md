---
title: "Viewing videos on VideoLectures.net"
date: 2010-06-24
forum: Multimedia Software
---

### Post by athena_acq on 2010-06-24
I have Ubuntu 9.04 installed on my laptop. 
I cannot view the videos posted on [videolectures.net]("http://videolectures.net"). The videos never stream. 
I have tried installing the moonshine and silverlight plugins for firefox, but that did not help. 
Can someone suggest a solution? Will installing Windows Media Plater via Wine help? Or is there a plugin I am not aware of?

---

### Post by vfiz on 2010-06-24
I checked out the site and clicked on some lectures.  The ones I saw were using flash.  Do you have flash installed?  If not, you can open a terminal and do this:
```
sudo apt-get install flashplugin-installer
```
You have to have the multiverse repositories enabled, though.

---

### Post by lovinglinux on 2010-06-24
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by athena_acq on 2010-06-24
@vfiz: I already have flash-plugin installed for my Firefox. The problem is the same, the video does not stream. That is why, I thought that this might be an Ubuntu issue.
I am currently using Ubuntu 9.04 and Firefox 3.0.19

---

### Post by lovinglinux on 2010-06-24
> **athena_acq said:**
> @vfiz: I already have flash-plugin installed for my Firefox. The problem is the same, the video does not stream. That is why, I thought that this might be an Ubuntu issue.
I am currently using Ubuntu 9.04 and Firefox 3.0.19

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by ron999 on 2010-06-24
Hi
You can download those lectures onto your hard drive then view them with VLC or mPlayer if you like.
To download them use the package **get_flash_videos**.
Look for it in Ubuntu repository.

Use a command like this:-
```
get_flash_videos < URL >
```

For example:-

```
get_flash_videos http://videolectures.net/kdd07_anderson_cld/
```

:guitar:

---

### Post by athena_acq on 2010-06-24
> **lovinglinux said:**
> Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

File name:  /usr/lib/flashplugin-installer/libflashplayer.so Shockwave Flash 10.1 r53

---

### Post by athena_acq on 2010-06-24
> **ron999 said:**
> Hi
To download them use the package **get_flash_videos**.
Look for it in Ubuntu repository.
Use a command like this:-
```
get_flash_videos < URL >
```For example:-
```
get_flash_videos http://videolectures.net/kdd07_anderson_cld/
```:guitar:

I installed get_flash_videos, following the instructions [_here_]("http://www.ubuntugeek.com/get-flash-videos-a-command-line-program-to-download-flash-videos.html"). However, when I tried downloading a video, I got the follwoing error. 

[I]Make sure you have 'rtmpdump' or 'flvstreamer' installed and available on your PATH.
Download failed, no valid file downloaded
[/I] 
On trying to install *rtmpdump* using apt-get I got the following error: 

[I]Package rtmpdump is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rtmpdump has no installation candidate

[/I]Similar error was encountered when I tried installing *flvstreamer*.

---

### Post by lovinglinux on 2010-06-24
> **athena_acq said:**
> File name:  /usr/lib/flashplugin-installer/libflashplayer.so Shockwave Flash 10.1 r53

You have the latest flash.

Can you post a link to one of the videos you can't watch? Can you watch YouTube videos?

---

### Post by athena_acq on 2010-06-24
> **lovinglinux said:**
> 

Can you post a link to one of the videos you can't watch? Can you watch YouTube videos?

Yes, I can watch YouTube videos. Some of the videos I tried streaming on videolectures.net are:

[http://videolectures.net/mlss09uk_bishop_ibi/](http://videolectures.net/mlss09uk_bishop_ibi/)
[http://videolectures.net/mlss04_bishop_gmvm/](http://videolectures.net/mlss04_bishop_gmvm/)

---

### Post by lovinglinux on 2010-06-24
> **athena_acq said:**
> Yes, I can watch YouTube videos. Some of the videos I tried streaming on videolectures.net are:

[http://videolectures.net/mlss09uk_bishop_ibi/](http://videolectures.net/mlss09uk_bishop_ibi/)
[http://videolectures.net/mlss04_bishop_gmvm/](http://videolectures.net/mlss04_bishop_gmvm/)

I can watch here. It is flash. 

When you try to watch the video simply doesn't load or you get an error message?

---

### Post by vfiz on 2010-06-24
I don't know if this will help at all, but I tried to load the first video and it wouldn't load.  I scrolled down and saw the option "Switch to Flash Media Player" a couple of clicks down below where the video is supposed to play.  I've attached a screenshot.  

After clicking on that, I reloaded the page, and the lecture started playing.

---

### Post by ron999 on 2010-06-24
This is the method that I used to install rtmpdump in Ubuntu Linux:-
Download the source tarball rtmpdump-2.2e.tar.gz from

[B][http://rtmpdump.mplayerhq.hu/download/](http://rtmpdump.mplayerhq.hu/download/)
[/B]

Extract it.
Look at the README file for instructions to compile.
The command is:-

    ```
make SYS=posix
```
(Use cd to change directory to rtmpdump-2.2e first)

Then install it:-

```
sudo make install
```

Check that it's installed properly using command:-

    ```
rtmpdump -h
```

---

### Post by athena_acq on 2010-06-24
> **lovinglinux said:**
> I can watch here. It is flash. 

When you try to watch the video simply doesn't load or you get an error message?
The video does not load and I get an error after a long time (around 15-20mins) as:
Server not found: rtmp://oxy...../

---

### Post by mc4man on 2010-06-24
You may want to revisit post 12, the 'best' or certainly quickest way to view these streams is in the embedded player.
If a cookie had been set to use wmp then nothing will happen in the black video box  - a right click  on that box will show, it it comes up empty then the site is trying to open the wmp stream
(r. click should show info about jw player

It's also possible to open the wmv stream in an external player, but it takes a long time to connect - 45-80 secs here.

The link can be had by r.clicking on the "launch in a standalone WM player" -> 'copy link location' and entering that in player or from cli
Then waiting it out....

Ex. on one you tried
```
vlc mms://velblod2.ijs.si:80/2009/pascal2/mlss09uk_cambridge/bishop_ibi/mlss09uk_bishop_ibi_01.wmv

```

> vlc mms://velblod2.ijs.si:80/2009/pascal2/mlss09uk_cambridge/bishop_ibi/mlss09uk_bishop_ibi_01.wmv
VLC media player 1.0.6-git Goldeneye
[0x9c11668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: no data received
[0x9cc7a58] access_mms access error: cannot connect to server
[0x9cc7a58] access_mms access error: cannot read data 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
Each one of those access errors took about 3 secs - then the video played fine

For totem a little extra help and a little longer wait
 ```
totem mms://velblod2.ijs.si:80/2009/pascal2/mlss09uk_cambridge/bishop_ibi/mlss09uk_bishop_ibi_01.wmv[COLOR="Blue"]?MSWMExt=.wmv[/COLOR]

```
added the blue so totem 'knows' what to 'expect'

Edit: the link you r. click on can be d. clicked instead and an external player opened from pop up - vlc should work - totem (likely the default), may not because of the missing 'helper' info

---

### Post by athena_acq on 2010-06-25
> **ron999 said:**
> This is the method that I used to install rtmpdump in Ubuntu Linux:-
Download the source tarball rtmpdump-2.2e.tar.gz from

[B][http://rtmpdump.mplayerhq.hu/download/](http://rtmpdump.mplayerhq.hu/download/)
[/B]

Extract it.
Look at the README file for instructions to compile.
The command is:-

    ```
make SYS=posix
```(Use cd to change directory to rtmpdump-2.2e first)

```
rtmpdump -h
```

rtmpdump readme file mentions zlib and openssl as a prerequisite. So, I installed zlib (openssl was already installed) and tried compiling. But I got many "variable OPENSSL_nnn not" found errors. My openssl is latest version. Can you tell me your openssl, zlib versions? 

And by the way, when I rebooted my machine today morning I got many GNOME Applet errors. Most of my GNOME menus were missing. The bottom bar, time and date, top shortcut bar, etc. I had to resort to removing zlib to get my machine back to working state. Perhaps I am not using the correct version of zlib.
 ( I could only restore my GNOME menus partially, perhaps because I haven't completely removed zlib. Please see my comment [here]("http://ubuntuforums.org/showthread.php?p=9508076") regarding this. Help in restoring my GNOME will be much appreciated)

---

### Post by ron999 on 2010-06-25
These are the packages that are installed on my system:-
openssi 0.9.8.g-16ubuntu3.1
zlib1g 1:1.2.3.3.dfsg-13ubuntu3
zlib1g-dev 1:1.2.3.3.dfsg-13ubuntu3

I think that you're having dependency problems because you're running Ubuntu 9.04. I'm running 9.10.
Maybe forget this option and watch the lectures using VLC instead, as mc4man explains above.

---

### Post by mikewhatever on 2010-06-25
mc4man, thanks. Your suggestion worked in both Totem and VLC.

---

### Post by athena_acq on 2010-06-25
@mac4man: Thanks a lot. I can now view the videos in VLC.

---

