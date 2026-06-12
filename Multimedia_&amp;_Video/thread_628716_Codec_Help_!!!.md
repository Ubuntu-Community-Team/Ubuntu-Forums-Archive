---
title: "Codec Help !!!"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by Giampy on 2007-12-01
I have installed Ubuntu 7.10

I can see a DVD.....

I cannot lissen any mp3 .............. !!!!!

I cannot see any .avi or dvix ................!!!!

I have installed a lot of variuos codec without success. 
Codec installed : EasyUbutnu, Medibuntu codec, Java package (100 Mb ), ecc
No Amarok, Caffeine, Mplayer, Totem Xine, can solve my problem.
[B]
Help me ![/B]   please.....

Giampy

---

### Post by elliotjreed on 2007-12-01
Run...

sudo apt-get install ubuntu-restricted-extras
sudo apt-get install kubuntu-restricted-extras
sudo apt-get instal xubuntu-restricted-extras
sudo apt-get install w32codecs
sudo apt-get install libdvdcss2

or on a 64-bit Ubuntu:

sudo apt-get install ubuntu-restricted-extras
sudo apt-get install kubuntu-restricted-extras
sudo apt-get instal xubuntu-restricted-extras
sudo apt-get install w64codecs
sudo apt-get install libdvdcss2

If these fail, VLC media player has it's codecs built-in, so will probaly work!

---

### Post by Giampy on 2007-12-01
ok, i will try .
But i have already VLC installed but doesn't work.

by

---

### Post by A + on 2007-12-01
I've got the same problem as the original poster.  Totem and VLC not working.  I issued the commands to install the restricted areas.  Ubuntu can see my stargate disc and the Audio Video folders in it when I open but just doesn't play the disc.

I'll root through the forum for an answer though.  Could be a long night...

---

### Post by Ehtetur on 2007-12-01
> **Giampy said:**
> I can see a DVD.....
ummm... you did mean can not, yes?

To see if Ubuntu sees the DVD, run this from terminal:
> lshw | grep DVD

---

### Post by A + on 2007-12-01
lshw | grep DVD ...

"WARNING: You should run this program as super-user." 

and that was that.  The tutorial told me there was no root account in ubuntu but there must be...do you happen to know my password?

---

### Post by fenian on 2007-12-01
Do this...
from the Applications menu choose Add/Remove.
In the pulldown menu show choose all available applications.
Check the following....
Ubuntu Restricred extras
Gstreamer extra plugins
Gstreamer ffmpeg video plugins
GStreamer plugins for mms, wavpack, quicktime, musepack
GStreamer plugins for aac, xvid, mpeg2, faad

Click the apply changes box.
Next open a terminal window and type the following...

> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

(if you are using an older ubuntu like feisty or dapper replace gutsy with the proper name)

next type
> 
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


next type...

> sudo apt-get install libdvdcss2

and

> sudo apt-get install w32codecs

That should give you the required packages to play DVD,MP3,DIVX and a wide variety of media files.

---

### Post by A + on 2007-12-01
DVD player now working...

I'm after installing a bunch of things - restricted packages and half of xine and gstream and none of them worked until I did this from another thread:

> **fraia said:**
> Hi
 Just got my dvd playback working with VLC - I did  the following:
first i uninstalled automatix2 and all of my other attempts at video playback, including totem-xine, gxine etc. It could just be superstitious but i think it helps to start cleanly sometimes...
 
 sudo apt-get install libdvdread3 fakeroot debhelper
 
then run:
 sudo /usr/share/doc/libdvdread3/install-css.sh

then install vlc:
sudo apt-get install vlc

and now it works on all the dvd's i've thrown at it.
 Hope it helps

I uninstalled nothing.  I did the above, rebooted and it got my DVD player working perfectly (so far, that is -  not holding my breath)  No more sh1te Vista interference hopefully - thanks fraia

---

### Post by Giampy on 2007-12-02
I have already installed the :

sudo apt-get install libdvdcss2 

sudo apt-get install w32codecs

but is still NOT working !!!

I don't understand..........  I will install fedora ........maybe...

bye

---

### Post by Giampy on 2007-12-02
Mplayer give this error :
[B]
LAVF_header: av_find_stream_info() failed[/B]

thank for help

---

### Post by riverstore on 2007-12-03
Hi fenian!
     My computer can't connect to Internet,  What should I do.

---

### Post by ferdostar on 2007-12-03
Hi,
How do you want connect to the internet?

---

### Post by riverstore on 2007-12-04
My computer doesn't connect to Internet, I want to manually download those codec and install offline

---

### Post by ferdostar on 2007-12-04
> **riverstore said:**
> My computer doesn't connect to Internet, I want to manually download those codec and install offline
 You can't download them if you have no internet connection, you can try with the livecd

---

### Post by riverstore on 2007-12-05
> **ferdostar said:**
> You can't download them if you have no internet connection, you can try with the livecd
     May I manually download required files from a Windows computer and install them to a Linux computer?

---

### Post by ferdostar on 2007-12-05
> **riverstore said:**
> May I manually download required files from a Windows computer and install them to a Linux computer?
In this cas you can :)

---

### Post by kazuya on 2007-12-05
simplest solution would be to install a distro such as Linux Mint which is essentially Ubuntu but with codecs already installed and a few other aesthetic effects, artwork or apps on the run from default install. This may be easiest.

Else, follow this if no internet on that machine:

[http://ubuntuforums.org/showthread.php?t=575729&page=5](http://ubuntuforums.org/showthread.php?t=575729&page=5)

Yes, Step #3 does give errors messages. But, ignore them and continue down the yellow brick road.
There are 2 versions of the libdvdcss2.deb file available.
They are:
libdvdcss2_1.2.9-1_i386.deb [http://files.filefront.com/libdvdcss.../fileinfo.html](http://files.filefront.com/libdvdcss.../fileinfo.html)
and 
libdvdcss2-dev_1.2.9-1_i386.deb [http://download.videolan.org/pub/lib...2.9-1_i386.deb](http://download.videolan.org/pub/lib...2.9-1_i386.deb)

I used the first one. 

Both of the last two links I posted are still active.
Just click "Open" the file with the default program, do not "Save" it. Then click "Install Software". Let it finish. Then it should work.

I compiled the "How-To" instructions from 3 other posters comments from various sites, then did research on my own, and then found the libdvdcss2 files using Google. After 2 hours around midnight, I could play DVDs.

I have both Totem MPlayer and VLC Media Player working perfectly. Except Totem freezes after about 30-45 minutes of playing.
So, I use VLC. It works flawlessly.
Hope this helps.
Good luck.
DeadToad

save file or debs on flash drive or CD rewriteables or whatever to use on the machine with no internet.

---

### Post by riverstore on 2007-12-05
Does this package independence?

---

