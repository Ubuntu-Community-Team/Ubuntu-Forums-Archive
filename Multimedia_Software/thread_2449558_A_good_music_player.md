---
title: "A good music player?"
date: 2020-08-29
forum: Multimedia Software
---

### Post by mmcmonster2 on 2020-08-29
I don't want to start a flamewar, but just want to comment here that the state of music players on Linux is somewhat grim.

* Banshee hasn't been updated since 2014 and doesn't appear to be available to download for Ubuntu or derivatives.

* Clementine (successor to Amarok) has both odd defaults as well as a different way to manage playlists compared to how everyone else does it. I often clobber a playlist by just double clicking on something.

* Rhythmbox has lost it's top menu and can't sort music within a playlist by selecting the column you want to sort by. You also can't move those columns around via the UI.

* Audacious ... I don't know.  I can't figure out how to point the program to my music library.  File->Settings doesn't include a Music Folder option.

* Songbird is not available for Linux anymore, and was always a resource hog and unstable.

* Sayonara I can't seem to install without installing snapd.  The repo doesn't support current Ubuntu versions.


At this point the only option which is at least a little useful is Rhythmbox.  I'll just have to get used to the lack of menus (who thought that was a good idea???) and the lack of sorting playlists (seems like an odd omission).

I thought someone had forked Banshee and kept the code base going, but can't seem to find it.  It really was my favorite option.

---

### Post by TheFu on 2020-08-29
For sorting or filtering , I use normal file system methods and pass that list into a normal player, like mpv.  The OS is extremely capable in doing this stuff, why not use it.  Playlists are just lists of music files, put into a file.  Doing that is trivial thanks to all the file and text processing commands built into every Unix system.

Linux isn't Windows. Think differently.

cmus is another option. I liked xmms when I was new to Linux desktops. Happy I finally embraced the Unix-way.

---

### Post by monkeybrain20122 on 2020-08-29
You can checkout [strawberry ]("https://www.strawberrymusicplayer.org/")(a fork of clementine) or [guayadeque ]("https://launchpad.net/~anonbeat/+archive/ubuntu/guayadeque")(not very impressive interface but featureful and capable of handling large collections)

---

### Post by Yellow Pasque on 2020-08-29
> **mmcmonster2 said:**
> * Audacious ... I don't know.  I can't figure out how to point the program to my music library.  File->Settings doesn't include a Music Folder option.

It's just "Add Folder". Audacious is not a "library" player, and is playlist-driven.

A new media player takes getting used to. I used foobar2000 in WINE for the first year or two I used Linux.

---

### Post by mmcmonster2 on 2020-08-29
Maybe I'm just an old dog that doesn't want to learn new tricks.

I personally like the iTunes interface that was copied by Banshee, Rhythmbox, and Songbird.  It worked well and was easy to navigate.

I'm surprised that none of the modern open source music players copied that interface. :(

(And I'm sorry, but playlist management should be considered an important part of a music player.  Using a text editor and file manager to manage the playlist is a failure of the music player.)

I've never tried Strawberry or Guayandeque.  No real statement on the Strawberry site on how they differentiate themselves from Clementine or any pictures on the Guayadeque site.

---

### Post by Yellow Pasque on 2020-08-29
It sounds like you may like Strawberry.

---

### Post by malspa on 2020-08-29
> **mmcmonster2 said:**
> Maybe I'm just an old dog that doesn't want to learn new tricks.

Ha-ha, I'm an 'old dawg' -- good luck with that! But anyway I've been using Audacious for the past few years. I've spent time with lots of other Linux music/media players over the years; I was (happily) using VLC to play my music prior to switching to Audacious (media player vs. simple music player). I figure you'll get used to whatever you settle in with. Usually just takes a little time to get comfortable with the UI.

---

### Post by monkeybrain20122 on 2020-08-30
> **mmcmonster2 said:**
> 

I've never tried Strawberry or Guayandeque.  No real statement on the Strawberry site on how they differentiate themselves from Clementine or any pictures on the Guayadeque site.

Strawberry's website has a lot of screenshots, it offers an appimage you can just download (make executable) and run, no need for installation. If you don't like it just delete it.
Guayadeque has no appimage, but it is easy to install with the ppa. Again if you don't like it just uninstall it. Here is a (a bit old) [review ]("https://www.omgubuntu.co.uk/2011/03/review-guayadeque-0-2-9-the-lightweight-music-app")of guayadeque, you can take a look

 > Sayonara I can't seem to install without installing snapd.  The repo doesn't support current Ubuntu versions

If you don't mind beta, it offers an [appimage]("https://sayonara-player.com/files/beta/appimage/"). Just like strawberry, you can download the appimage, make it executable and then click and play, don't like it then just delete.

There is also a lesser know itune lookalike player called [musique]("https://flavio.tordini.org/musique"). It offers a deb works on Ubuntu >=20.04.

If you don't want to learn new stuffs it will be tough, Apple has killed itune too.

---

### Post by TheFu on 2020-08-30
> **monkeybrain20122 said:**
>  If you don't want to learn new stuffs it will be tough, Apple has killed itune too.

Next to be killed - MS-Outlook!  2 of the largest bloated programs ever made ... besides Java development tools. ;)

---

### Post by andrew.46 on 2020-08-31
I confess to a dislike of those all encompassing music players that scan hard drives for music, download album art and lyrics, rip audio cds etc etc. My own needs have been met for some time with SMplayer and a back end of an up to date mpv...

---

### Post by shantiq on 2020-09-07
> **Yellow Pasque said:**
> It sounds like you may like Strawberry.


+1 for what you seem to wish for OR Foobar under Wine works PERFECTLY

---

### Post by SeijiSensei on 2020-09-07
> **andrew.46 said:**
> I confess to a dislike of those all encompassing music players that scan hard drives for music, download album art and lyrics, rip audio cds etc etc. My own needs have been met for some time with SMplayer and a back end of an up to date mpv...
I'm with andrew on this. I use SMPlayer and mpv for everything.

---

### Post by Yellow Pasque on 2020-09-07
> **shantiq said:**
> Foobar under Wine works PERFECTLY

[https://hydrogenaud.io/index.php?topic=119786.0](https://hydrogenaud.io/index.php?topic=119786.0)

---

### Post by alias2 on 2020-10-06
> **mmcmonster2 said:**
> I 

* Banshee hasn't been updated since 2014 and doesn't appear to be available to download for Ubuntu or derivatives.



Miss banshee that is the only one I found that is complete and well designed...
Do you know if there is a possibility to install it on ubuntu 20.04 ?
I try to compile it, from version 6.2
[http://banshee.fm/download/](http://banshee.fm/download/)
```

apt install intltool
apt install libgtk2.0-dev
apt install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
./autogen.sh

checking for GST... no
configure: error: Package requirements (gstreamer-0.10 >= 0.10.26
        gstreamer-base-0.10 >= 0.10.26
        gstreamer-plugins-base-0.10 >= 0.10.26
        gstreamer-controller-0.10 >= 0.10.26
        gstreamer-dataprotocol-0.10 >= 0.10.26
        gstreamer-fft-0.10 >= 0.10.26) were not met:

No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-controller-0.10' found
No package 'gstreamer-dataprotocol-0.10' found
No package 'gstreamer-fft-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.


```
then try to modify in the file
build/m4/banshee/gstreamer.m4
 0.10 by 1.0 mais but it doesn't work

```
 checking for GST... no
configure: error: Package requirements (gstreamer-1.0 >= 1.0
        gstreamer-base-0.10 >= 1.0
        gstreamer-plugins-base-0.10 >= 1.0
        gstreamer-controller-0.10 >= 1.0
        gstreamer-dataprotocol-0.10 >= 1.0
        gstreamer-fft-0.10 >= 1.0) were not met:

No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-controller-0.10' found
No package 'gstreamer-dataprotocol-0.10' found
No package 'gstreamer-fft-0.10' found
```
Seems that it really need 0.10 version, any idea ?

---

