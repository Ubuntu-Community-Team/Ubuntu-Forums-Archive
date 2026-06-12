---
title: "No sound on .mov files"
date: 2009-08-07
forum: Multimedia Software
---

### Post by sanjaymk on 2009-08-07
Hello All,

I'm using Ubuntu 9.04 Jaunty Jackalope on Dell Inspiron 640m.  

I'm having problems playing a .mov file.  When I play this url *[http://media.railscasts.com/videos/067_restful_authentication.mov](http://media.railscasts.com/videos/067_restful_authentication.mov)*, I get a message to *Search for suitable plugin*, and when I click on *Search* it comes back with a message that *No suitable plugins were found and that the plugin it was looking for is MPEG-4 AAC decoder*.  

Also, I tried to install VLC player by following instructions from here, [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc) but I get the below error when trying to install- 

[I]The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 1.0.1-1~ppa4) but it is not going to be installed
       Depends: libtar but it is not installable
       Depends: libx264-65 (>= 1:0.svn20081230) but it is not installable
E: Broken packages
[/I]

Any help to overcome these problems, highly appreciated.

---

### Post by HappyFeet on 2009-08-07
Video link works for me. I installed mozilla-mplayer for my browser. You will want to get the medibuntu repos to get VLC and other codecs. Do:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```
Then VLC will show up in synaptic. You might also want to install the gstreamer bad and ugly codecs, along with mozilla-mplayer.

---

### Post by andrew.46 on 2009-08-07
Hi sanjaymk,

> **sanjaymk said:**
>   I'm having problems playing a .mov file.  When I play this url *[http://media.railscasts.com/videos/067_restful_authentication.mov](http://media.railscasts.com/videos/067_restful_authentication.mov)*, I get a message to *Search for suitable plugin*, and when I click on *Search* it comes back with a message that *No suitable plugins were found and that the plugin it was looking for is MPEG-4 AAC decoder*.

Looks like the file is qtrle + aac:

```

Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '067_restful_authentication.mov':
  Duration: 00:09:30.21, start: 0.000000, bitrate: 449 kb/s
    Stream #0.0(eng): **[COLOR="Red"]Audio: aac[/COLOR]**, 44100 Hz, 1 channels, s16
    Stream #0.1(eng): **[COLOR="Red"]Video: qtrle[/COLOR]**, rgb24, 800x600

```

So if you are after a quick playback o the downloaded file the MPlayer from Medibuntu can easily playback this one:

Medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

And as Happyfeet mentions this will play in a browser well enough with the 'mozilla-mplayer'. I am not so sure though, as Happyfeet suggests, that vlc can be found in Medibuntu but I have been wrong before :-). Not so sure also how to fix the PPA errors, hopefully others can help?

Andrew

---

### Post by sanjaymk on 2009-08-08
> **HappyFeet said:**
> Video link works for me. I installed mozilla-mplayer for my browser. You will want to get the medibuntu repos to get VLC and other codecs. Do:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```
Then VLC will show up in synaptic. You might also want to install the gstreamer bad and ugly codecs, along with mozilla-mplayer.

Hi, Thank to you and andrew for taking the time to reply.  I did the command you mentioned and tried to install vlc through terminal (```
sudo apt-get install vlc mozilla-plugin-vlc
```) and through synaptic, but I get errors, saying the same thing using different verbiage.

Through Terminal
================
[I]The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 1.0.1-1~ppa4) but it is not going to be installed
  vlc: Depends: vlc-nox (= 1.0.1-1~ppa4) but it is not going to be installed
       Depends: libtar but it is not installable
       Depends: libx264-65 (>= 1:0.svn20081230) but it is not installable
E: Broken packages[/I]

Through Synaptic
=================
vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libtar  but it is not installable
 Depends: libx264-65 (>=1:0.svn20081230) but it is not installable

I also tried to install mozilla mplayer through synaptic and the error I get is 

[I]mozilla-mplayer:

Package mozilla-mplayer has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list[/I]

I do seem to have gstreamer ugly (gstreamer0.10-plugins-ugly) installed but when I typed in dirty on the search in synaptic nothing meaningful showed up.

Any help is highly appreciated.

Thanks,
Sanjay.

---

### Post by andrew.46 on 2009-08-09
Hi sanjaymk,

> **sanjaymk said:**
> 
```
The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 1.0.1-1~ppa4) but it is not going to be installed
  vlc: Depends: vlc-nox (= 1.0.1-1~ppa4) but it is not going to be installed
       Depends: libtar but it is not installable
       Depends: libx264-65 (>= 1:0.svn20081230) but it is not installable
E: Broken packages
```


Perhaps your list of sources is a bit scrambled? Could you post the results of the following:
```

cat /etc/apt/sources.list

```

and perhaps this will shed some light...

Andrew

---

### Post by sanjaymk on 2009-08-10
> **andrew.46 said:**
> 
```

cat /etc/apt/sources.list

```

and perhaps this will shed some light...

Andrew

```

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty main
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main

```

Thanks,
Sanjay.

---

### Post by andrew.46 on 2009-08-10
Hi sanjaymk,

> **sanjaymk said:**
> ```

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty main
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
**[COLOR="Red"]deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main[/COLOR]**

```
.

You have a duplicated line for the vlc PPA which probably is not the problem but I see that you have not used the 'jaunty-updates' repository and I would suggest adding these in and adding the software + updates rolled out to Jaunty after the oroginal release. This can be found under:

System -----> Administration -----> Sofware Sources ----> Updates

I attach a screenshot showing the relevant settings. Once this is in place hopefully you can successfully add the PPA vlc :-).

Andrew

---

