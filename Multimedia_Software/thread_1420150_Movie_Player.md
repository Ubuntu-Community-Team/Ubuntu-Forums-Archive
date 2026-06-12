---
title: "Movie Player"
date: 2010-03-02
forum: Multimedia Software
---

### Post by Jonny87 on 2010-03-02
I have recently had problems a with Movie player. It seems to having trouble playing DVD's and video files. it has a tendency to stop/freeze and sometimes if I try move the progress bar or scroll back or forward it wil just instantly close the Movie Player. I'm wondering is there a way to check it for bugs or is there a more reliable/better quality player that I could get instead. I would like to know how to fix it though if possible.

---

### Post by Idefix82 on 2010-03-02
I recommend VLC. It's by far the most reliable and versatile movie player I know.

---

### Post by bluelamp999 on 2010-03-02
I recommend VLC as a replacement - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

Can't really help when it comes to trouble-shooting Movie Player...

---

### Post by Jonny87 on 2010-03-02
Ok thanks, will look into VLC. Does it play all formats?

---

### Post by andrew.46 on 2010-03-03
Hi Jonny,

> **Jonny87 said:**
> Ok thanks, will look into VLC. Does it play all formats?

Much of vlc's versatility stems from its reliability on FFmpeg's libavcodec so it depends on how this has been built....

Andrew

---

### Post by handy on 2010-03-03
> **andrew.46 said:**
> Hi Jonny,



Much of vlc's versatility stems from its reliability on FFmpeg's libavcodec so it depends on how this has been built....

Andrew

It doesn't look that way when you read down this page, but of course I could be missing something, as it has happened once or perhaps twice before: :)

[http://www.videolan.org/videolan/](http://www.videolan.org/videolan/)

---

### Post by Baljamin on 2010-03-03
I recommended use Goom Player.

---

### Post by marc480 on 2010-03-03
Hello,

I had recently tried Movie player. Actually I just threw in a dvd to see what would happen. The dvd drive made some noises then MoviePlayer showed up for about two seconds and disappeared. I looked in the repository for something similar to MoviePlayer, but couldn't find anything that time that seemed adequate. After reading this thread I will try this VLC and see what happens and get back here to post the results.

By the way I'm running Ubuntu 9.10 on a T41 IBM ThinkPad.

---

### Post by Yellow Pasque on 2010-03-03
I fixed some of my Movie Player/Totem issues by using the latest gstreamer: [https://launchpad.net/~gstreamer-developers/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~gstreamer-developers/+archive/ppa?field.series_filter=karmic)

---

### Post by marc480 on 2010-03-03
Ok, I'm back. And with my results. 

I went to the VLC website and was confused by the process. Realising that there was a multistep process to go through to install this player rather put me off, even though they said it was easy. I'm not at that level of Ubuntu competency yet. Anyway I went to the Ubuntu help menu and in the section labeled 'music, CDs and DVDs, there was a section about playing DVDs. It gave a quick check of already installed software and some easy instructions for installing one last piece of software via the terminal. It worked and I was able to view my sample dvd, a star trek dvd, because it was handy. 

So my results are, the Movie Player in Ubuntu does and can be made to work. So far, so good.

---

### Post by handy on 2010-03-03
> **marc480 said:**
> Ok, I'm back. And with my results. 

I went to the VLC website and was confused by the process. Realising that there was a multistep process to go through to install this player rather put me off, even though they said it was easy. I'm not at that level of Ubuntu competency yet. Anyway I went to the Ubuntu help menu and in the section labeled 'music, CDs and DVDs, there was a section about playing DVDs. It gave a quick check of already installed software and some easy instructions for installing one last piece of software via the terminal. It worked and I was able to view my sample dvd, a star trek dvd, because it was handy. 

So my results are, the Movie Player in Ubuntu does and can be made to work. So far, so good.

The easy way to install VLC, is via synaptic, as I'm sure that VLC is in the Ubuntu repo's.  

Synaptic is always the first place to look for a package, as if the package is there, it will install reliably & simply, & it is also a guaranteed safe (does not incorporate mal-ware of any kind) source of packages.

I'm glad you got to play movies anyway. :)

---

### Post by andrew.46 on 2010-03-03
Hi handy,

> **handy said:**
> It doesn't look that way when you read down this page, but of course I could be missing something, as it has happened once or perhaps twice before: :)

I have been mistaken many more times than this :). However perhaps the best test is to run vlc against a few of your favourite media files in this fashion:

```
cvlc -vvv ***[COLOR="Red"]my_file[/COLOR]***
```

and examine the admittedly voluminous output, I suspect you will be a little surprised to see how often libavcodec is at work.

All the best,

Andrew

---

### Post by handy on 2010-03-03
It showed up twice on an .mp4 vid.

I had a quick look for the libavcodec file but couldn't find it. I want to rename it & see what happens? :)

---

### Post by handy on 2010-03-03
I just got around to doing a search with Worker & found the following path in Arch:

/usr/include/libavcodec/

I renamed the directory & tried to view the same .mp4 vid; it works fine.

Surprisingly. 

I had to give it a try. :confused:

[Edit:] I wonder if I needed to reboot the system?

I'll give that a go later.

---

### Post by Dr Droid on 2010-03-04
I hope that someone can help me or at least point me in the right direction. Recent I have experienced problems with media players like vlc and mplayer. I noticed that if I have the files of a dvd video on my filesystem that I can right click on the containing folder; like so (right click on joe_dirt):
<joe_dirt>
     <video_ts>
     <audio_ts>
</joe_dirt>

It will bring up the dvd menu, then i can click play and the movie starts.... The weird part is that I can hear the backround sounds, like voices of the extras and the music, but I cannot hear the voices of the actors. It is very confusing. Please help.

---

### Post by Jonny87 on 2010-03-04
Ok so since my last post I've taken the advice that was given (thanks) and downloaded VLC. Yes, it played the files better than what Movie Player. I also downloaded a few other for insurance, I installed GNOME Mplayer, Xine, and i think there was one more but can't remember but i'll have a look when I get home.
 
Yea the Repos is the best place to get the VLC and anyother software in response to the messages above. Quick and easy too.
 
Thanks for your help guys.

---

