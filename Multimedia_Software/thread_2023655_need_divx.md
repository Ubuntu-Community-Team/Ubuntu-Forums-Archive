---
title: "need divx"
date: 2012-07-12
forum: Multimedia Software
---

### Post by nhyrum on 2012-07-12
trying to watch some videos on the internet and it says i need divx plugins. i have the firefox flash player plugins and installed the ubuntu specific package thing. how do i install divx? do i just do some sudo get- install divx thing like i dig for the others?

---

### Post by Whovian on 2012-07-12
Did you install the restricted extras? It has all the necessary plugins to view videos.

---

### Post by nhyrum on 2012-07-13
> **Whovian said:**
> Did you install the restricted extras? It has all the necessary plugins to view videos.

i already installed the ubuntu restricted extras.

what about vlc? how do i install that?

---

### Post by ubudog on 2012-07-13
> **nhyrum said:**
> 
what about vlc? how do i install that?

This should do it:
```
sudo apt-get install vlc
```

---

### Post by mastablasta on 2012-07-13
> **nhyrum said:**
>  
what about vlc? how do i install that?
 
 
like any other porgramme it can be found in Ubuntu software center
 
you can also use command like if you prefer...

---

### Post by bobsan on 2012-07-15
To watch divx in FF you need to install the gecko-mediaplayer. The totem divx plugin also works but not very good. vlc is awesome as a standalone player but its mozilla plugin just sucks, never works on anything. You can get the latest gecko-mediaplayer from [https://launchpad.net/~ed10vi86/+archive/video](https://launchpad.net/~ed10vi86/+archive/video)

To install the proper codecs add medibuntu to your sources list and install w32/64 codecs. Here is the detailed instruction. [http://www.unixmen.com/how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui/](http://www.unixmen.com/how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui/)

---

