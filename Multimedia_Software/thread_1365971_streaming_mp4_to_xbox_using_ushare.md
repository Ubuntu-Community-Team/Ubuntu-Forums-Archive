---
title: "streaming mp4 to xbox using ushare"
date: 2009-12-27
forum: Multimedia Software
---

### Post by crankharder on 2009-12-27
Can't seem to find an up to date post on this subject.  I'd like to play my mp4 files on my xbox.  I set up ushare, configured the directory and started the server.  I can see the files from my xbox but when I select them it doesn't start playing.

I've seen a lot of old posts about altering mime types to allow AVI files to be played, but those don't quite apply to my situation.  Has anyone done this?  Thanx.

---

### Post by sugargenius on 2010-07-21
> **crankharder said:**
> Can't seem to find an up to date post on this subject.  I'd like to play my mp4 files on my xbox.  I set up ushare, configured the directory and started the server.  I can see the files from my xbox but when I select them it doesn't start playing.

I've seen a lot of old posts about altering mime types to allow AVI files to be played, but those don't quite apply to my situation.  Has anyone done this?  Thanx.

I'm in the same exact boat.  I tried changing the mime type in mime.c, but I get this error when I ./configure

```
root@ubuntu:/home/wlott/ushare-1.1a-NeToU# ./configure
Checking for compiler available...
Checking for locales ...
Checking for ifaddrs ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Checking for libthreadutil ...
Checking for libupnp >= 1.4.2 ...
***Error, libupnp < 1.4.2 !***

```

```
sudo pkg-config --modversion libupnp
1.6.6

```

---

### Post by keithm on 2010-08-09
I just got this to work today!

A temporary work-around is just to change the file extension from ".mp4" to ".mov". It seems that if the xbox thinks the file is a quicktime video it plays it fine.

To fix it more permanently you need to change the mime type in mime.c in the src directory of the source code.  I used the version in the repositories, gotten using ```
apt-get source ushare
```

In mime.c in the src directory delete the line for "mp4" in the list of Audio files and add the following into the list for Video files

```
{ "mp4",   UPNP_VIDEO, "http-get:*:video/quicktime:"},
```

If you don't have it you'll need to install libupnp-dev.  Then ./configure, make and checkinstall.  

If you just ./configure, make and checkinstall without any arguments (as I did) then your ushare.conf file will now need to be in /usr/local/etc/

Then to launch ushare:
```
ushare -x -D
```

---

### Post by seanzer on 2010-10-26
> **keithm said:**
> I just got this to work today!

A temporary work-around is just to change the file extension from ".mp4" to ".mov". It seems that if the xbox thinks the file is a quicktime video it plays it fine.


I tried this today.. and my xbox complained that it couldn't play the file. Are there other properties of the mp4 I should change to get it to play as a .mov?

Anybody having luck with this??

---

### Post by keithm on 2010-10-30
> **seanzer said:**
> I tried this today.. and my xbox complained that it couldn't play the file. Are there other properties of the mp4 I should change to get it to play as a .mov?

Anybody having luck with this??

What kind of mp4 is it -- what audio and video codecs are used  within it (right-click on the file, choose properties and then choose Audio and Video)?  

The xbox can only play a limited number of codecs so if your video isn't from that list it's simply not going to work.  For example when using Acidrip if you use the lavc video codec the file won't work on the xbox, but if you use xvid it will.  

If you want to test out on a file that should work straight away, download an mp4 from Youtube or Vimeo - they worked for me straight away when I changed the file name (before I 'fixed' ushare)

---

