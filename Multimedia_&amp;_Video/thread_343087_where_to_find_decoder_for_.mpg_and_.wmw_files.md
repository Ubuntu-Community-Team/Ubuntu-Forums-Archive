---
title: "where to find decoder for .mpg and .wmw files"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by sshahir on 2007-01-20
I cannot play .mpg and .wmv files using Totem. When I try to play those files, an  error message pops up and says that I need to install the right decoder. 

I have found the [&#8220;Can't play MPG or WMV&#8221;]("http://ubuntuforums.org/showthread.php?t=243988&referrerid=163608")  thread.

Unfortunately, the instruction within the thread is outdated.

I am wondering if anyone has any sugestion?


Thanks,
sshahir

---

### Post by RomeReactor on 2007-01-20
Hi. Install totem-xine and w32codecs. Make sure you have universe and multiverse  repositories enabled.

```
sudo apt-get install totem-xine w32codecs
```

---

### Post by sshahir on 2007-01-21
I don't know why I cannot run the command successfully. I have received the "totem-xine is not available" error message.

How can I make universe and multiverse repositories enabled?

---

### Post by moshuptrail on 2007-01-21
I think those used to be in 
[http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/)

but that repo seems to be gone (returns 404)

Anyone know where w32codecs went?  I'd like to know too!

---

### Post by sshahir on 2007-01-21
I found W32codecs on the link below.
[http://www.debian-multimedia.org/pool/main/w/w32codecs/]("http://www.debian-multimedia.org/pool/main/w/w32codecs/")

but I don't know how to install it. any sugestion?

---

### Post by moshuptrail on 2007-01-21
sudo dpkg --install w32codecs_20061022-0.0_i386.deb

looks like it installed on my pc, but it didn't solve my mplayer radio problems

---

### Post by NewWithoutClue on 2007-01-21
VLC will play just about anything, or so it seems.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by sshahir on 2007-01-21
Even though I've installed w32codecs, but I still cannot run the files. I have tried to load multimedia (univers), 

> **RomeReactor said:**
> Hi. Install totem-xine and w32codecs. Make sure you have universe and multiverse  repositories enabled.

```
sudo apt-get install totem-xine w32codecs
```

but I couldn't find multimedia (multiverse) within package manager.

Any sugestion why I cannot play .mpg or wmv files?

---

### Post by NewWithoutClue on 2007-01-21
> **sshahir said:**
> 
but I couldn't find multimedia (multiverse) within package manager.

Any sugestion why I cannot play .mpg or wmv files?

>.<

System > Synpatic Package Manager > Settings > Repositories

Put a check in all the check boxes on the first tab.

---

### Post by sshahir on 2007-01-21
As you said, I have checked all the boxes on the Repositories/first tab,

> **NewWithoutClue said:**
> >.<

System > Synpatic Package Manager > Settings > Repositories

Put a check in all the check boxes on the first tab.
but I still cannot play .mpg or wmv files. Any sugestion how I can fix the problem.

---

### Post by RomeReactor on 2007-01-22
Take a look at my post in [this]("http://www.ubuntuforums.org/showthread.php?p=2048056") thread. Did you install totem-xine?

---

### Post by vaximily on 2007-02-13
I'm running Ubuntu 6.06.1 LTS Server w/ Gnome installed.
Here's what I did (from CLI)

> $sudo get-apt install totem-xine
yadda yadda, hit Y for yes if it asks for it........

> $wget [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)

once that downloads:
> $sudo dpkg --install w32codecs_20061022-0.0_i386.deb

This should work fine for you.


[B]I however, still don't have working .wmv codecs because that package only works for i386 not x64.
[/B]
Any ideas here?

---

### Post by RomeReactor on 2007-02-13
Hi. Try searching the [64-bit users]("http://www.ubuntuforums.org/forumdisplay.php?f=134") forum; i'm almost certain i've seen some posts there regarding this issue.

---

### Post by vaximily on 2007-02-13
[http://ubuntuforums.org/showthread.php?t=188974&highlight=mplayer+32bit+libraries](http://ubuntuforums.org/showthread.php?t=188974&highlight=mplayer+32bit+libraries)

That How-To showed me everything I needed, works perfect now :).

---

### Post by jacobraj on 2007-04-10
I just followed the same procedure listed above, totem movie player worked fine on a 32 bit 

Jacob

---

