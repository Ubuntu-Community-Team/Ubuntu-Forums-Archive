---
title: "Video Codec Pack?"
date: 2008-11-08
forum: Multimedia Software
---

### Post by ECas123 on 2008-11-08
Hello, I'm having trouble finding a video codec pack for Ubuntu 8.10 I need to play .wmv, .avi, etc. for podcasts and other videos. Can someone send me in the right direction to a good codec pack?

---

### Post by cotcot on 2008-11-08
sudo apt-get install non-free-codecs ubuntu-restricted-extras w32codecs

---

### Post by ECas123 on 2008-11-08
> **cotcot said:**
> sudo apt-get install non-free-codecs ubuntu-restricted-extras w32codecs

I get
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package non-free-codecs


---

### Post by gandaran on 2008-11-08
> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package non-free-codecs
that package doesn't exist, just install the others

---

### Post by ECas123 on 2008-11-08
> **gandaran said:**
> that package doesn't exist, just install the others

Could you tell me how?

---

### Post by gandaran on 2008-11-08
just remove the *non-free-codecs * part from the command

---

### Post by gandaran on 2008-11-08
why don't you let firefox install the codecs? every time you go to a web page that needs codecs a window will pop up asking you to install the codecs, just let it choose  and install it

edit; sorry this is for online streaming only

---

### Post by ECas123 on 2008-11-08
> **gandaran said:**
> just remove the *non-free-codecs * part from the command

Now I get 
> eddy@eddy:~$ sudo apt-get install ubuntu-restricted-extras w32codecsReading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

And as for the Firefox tip, I want codecs so VLC can play downloaded video (like on my desktop)

---

### Post by Gorgoth on 2008-11-08
```
sudo apt-get install ubuntu-restricted-extras 
``` 
in terminal oughta solve the playback in firefox... otherwise, Ive found firefox tends to bug and not properly install codecs, causing it to ask to install every time you re-open it.

```
sudo apt-get install vlc
```
Installs VLC, which in turn should also install all its dependencies for video playback...
If not try:

```
aptitude search ffmpeg
```
Should return a list of packages, one of which oughta be the overall video codec pack in addition to the restricted-extras package above...

---

### Post by steveneddy on 2008-11-08
From the links in my sig:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron)

Please feel free to look at the links in my sig for any further Ubuntu assistance.

---

### Post by ECas123 on 2008-11-08
I think somethings wrong. I installed the restricted drivers but when I try to play a .avi episode of Diggnation (a podcast) it either doesn't start or it just plays the first second of it then stops the program (in both VLC and the video player that comes with 8.10)

---

### Post by ECas123 on 2008-11-08
Anyone, please?

---

### Post by CraymelCage on 2008-11-08
thats strange that vlc isn't playing the avi. Also vlc uses internal codecs so it won't matter what other codecs you install. If you want to install all the gstreamer non free codecs just search for ubuntu-restricted-extras in synaptic package manager and install that. The gstreamer codecs work with the default player totem and they also work with other gstreamer based players as well. I personally recommend mplayer. I don't recommend using the default mplayer package in synaptic though. 

the developers behind smplayer have made a repository of there own for newer versions of mplayer. 

to use it just open up your repository list

```
 gksudo gedit /etc/apt/sources.list
```
ad this line to the list
```
deb http://ppa.launchpad.net/rvm/ubuntu intrepid main
```
then update
```
sudo apt-get update
```

Note that mplayer also uses internal codecs and does not use gstreamer. It also has non free codecs you can download from  [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) they're called binary codec packages. Mplayer should be able to play most anything in an avi with out the binary codec packages though. If you want to use them download the package, extract it, rename it to codecs and move the folder named codecs to /usr/local/lib. hope this helps.

---

