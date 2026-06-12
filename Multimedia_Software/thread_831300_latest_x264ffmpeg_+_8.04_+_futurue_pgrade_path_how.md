---
title: "latest x264/ffmpeg + 8.04 + futurue pgrade path howto?"
date: 2008-06-16
forum: Multimedia Software
---

### Post by mem on 2008-06-16
why cant there be 1 standard way of installing support for the latest x264/ffmpeg in Ubuntu 8.04. I just want to be able to playback 1080p movies with dual core/quad core support.

i've done the search on the forums and come up with 1000 different ways of doing it and have no idea which one to trust. Nor does installing from source really provide a good upgrade path.

am i missing something or is this truly just the kind of support we've got at this point. :(

some examples (i have no idea which one to follow):
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

---

### Post by nstgc379 on 2008-06-16
[edit] I didn't see the links. Sorry. I'm sure my answer is in one of those[/edit]


I don't have a real answer, as I was planning on asking the same question in a different way. I was looking through the man pages for MPlayer and it seems you can set individual codecs (meaning for "H.264" and mpeg) to produce multiple threads. If this thread dies without an answer, I'll ask again.

---

### Post by andrew.46 on 2008-06-16
Hi,

I read your post with great interest, in part because I wrote the MPlayer walkthrough that you refer to :-).

> **mem said:**
> why cant there be 1 standard way of installing support for the latest x264/ffmpeg in Ubuntu 8.04. I just want to be able to playback 1080p movies with dual core/quad core support.

Ubuntu does a great job supplying packages of things like MPlayer and ffmpeg but if you want the *latest* version of these there is no other way than to produce your own. Thus the compiling guides that you have mentioned.

> i've done the search on the forums and come up with 1000 different ways of doing it and have no idea which one to trust. Nor does installing from source really provide a good upgrade path.

If you are not happy installing from source [Nathan's amazing guide]("http://ubuntuforums.org/showthread.php?t=766683") will be the best that Ubuntu has to offer IMHO. But I believe for the very latest, which offers greater benefits but also potentially greater problems, you will need to compile from the upstream source.

You are mistaken that there is no upgrade path. The software from subversion and git repositories is designed for easy upgrade with either 'svn update' or 'git pull'. To place your packages within the Ubuntu package management system simply use the checkinstall utility.

> am i missing something or is this truly just the kind of support we've got at this point. :(

Well actually you are missing one important thing :-). The three authors of these guides (including myself) are not on the forum staff and in fact are just regular Ubuntu users like yourself who have taken it upon themselves to write these guides. Takes a fair bit of research and a willingness to support the users of these guides. 

If there is something lacking in the guides themselves you can usually send a message to the author and the problem will be fixed. If there is an area of instruction completely missing from the forums you can write it up yourself as a new guide.

As for playback of your movies you may find that Nathan's guide will be enough and I would encourage this as a first stop, although this will not give you the 'latest' that you have spoken of. If the quality is not enough you may need to consider MPlayer from svn. To convert your own movies you can either use MPlayer compiled against the git x264 or install your own ffmpeg as suggested by FakeOutdoorsman. A few great choices :-).

All the best,

   Andrew

---

### Post by cozmicharlie on 2008-06-16
Good question - usually because their is more than one way to do something is the best answer I can provide.  I successfully used this method and it worked fine for me [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095).  I did not rename my ffmpeg and I do get the update method but I just ignore it.

---

### Post by mem on 2008-06-17
i'm still confused as to what i need to get actual playback (decoding) working properly on x264 videos.. 

i really have no need to encode, i just want to make sure that decoding will utilize both cores (very high resolution videos for work, 1080p and higher).

---

### Post by cozmicharlie on 2008-06-17
It does not matter if you want to encode or just play, you still need to install them.  If you want the most recent version than install using the method in this post [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095).  

You could first try and use the ffmpeg from the Medibuntu repository and see if that works for you.  It is a lot easier to install (just add the Medibuntu repository to your source list and install it through Synaptic).  

To add the Medibuntu repository, open the terminal (Applications > Accessories > Terminal) and paste these wget commands into it:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Then go into Synaptic and install ffmpeg.  You will want to install other codecs also (Ubuntu Restricted Extras, gstreamer, faad, faac, etc).  This post shows you how 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by nstgc379 on 2008-06-17
In my case I just wish force smp decoding.

I tried two things at least. One was "-libx264 thread=2" and "-lavdopts thread=2". While the video does seem to use both cores, I can't player 1080p encodes. Is x264 really this much worse then CoreAVC?

---

### Post by cozmicharlie on 2008-06-18
> **nstgc379 said:**
> In my case I just wish force smp decoding.

I tried two things at least. One was "-libx264 thread=2" and "-lavdopts thread=2". While the video does seem to use both cores, I can't player 1080p encodes. Is x264 really this much worse then CoreAVC?

That is beyond my knowledge but for advanced 1080p, I would want to go with the latest ffmpeg and x264 build which means you should compile it using source [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) - you may want to use one of the nightly builds.

---

