---
title: "Viewing zip FIles without unzipping"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by osiris2258 on 2007-10-30
I need to be able to view images that have been zipped inside an image viewer without unzipping the file. I get tons of these zips with hundreds of images everyday, and I simply don't have the time or the space to unzip them. I can do this in windows with ACDSee, but I haven't found a good equivalent in ubuntu. Gwenview and Showimg both look similar, but I can't get them to open zips. Comix is not good because it is too hard to get from place to place; I need the directory tree like in the other programs. At the current time I've had to fall back to rebooting to my windows partition all the time, but I can't keep doing that.

Anybody have any ideas how to either enable this or what programs can do it?

---

### Post by mdebusk on 2007-10-31
> **osiris2258 said:**
> I need to be able to view images that have been zipped inside an image viewer without unzipping the file.

I may be missing something here. Doesn't File Roller work for you? It's the default archive manager in Ubuntu and it seems to me to do what you're asking.

---

### Post by osiris2258 on 2007-10-31
In my image viewer, I need the zip to act just like a regular folder. Right now, it pops up it's own archive window, wherein I can only view one image at a time and can't scroll wheel through them.

---

### Post by mdebusk on 2007-11-01
> **osiris2258 said:**
> In my image viewer, I need the zip to act just like a regular folder. Right now, it pops up it's own archive window, wherein I can only view one image at a time and can't scroll wheel through them.

Oh, **now** I understand what you want. Something like the old "archive folder" in Object Desktop for OS/2, ages ago. I loved that feature.

It **does** involve unzipping the archive, but you don't notice it. The program unzipped it to a temporary folder, opened that temporary folder, and cleaned it all up when you closed it.

When I moved from OS/2 version 3 to version 4, I decided to not install Object Desktop. (It was a resource pig, even though it was otherwise wonderful.) I wrote a simple script in Rexx which did more-or-less the same thing. (I created the folder on my desktop and deleted it when I was done with it.)

I'm sure it's possible to poll the desktop for open windows and, if the program finds a window has been closed, take a particular action. What you're asking would be a great RFE for the Nautilus developers. Perhaps you could ask them for it.

---

### Post by osiris2258 on 2007-11-01
The thing is, I actually had this working for about a day in Gwenview right after I installed it, and then it mysteriously stopped. I was wondering if maybe it was because I was using KDE programs in GNOME. I didn't change anything so I have no idea what caused it to stop working.

---

### Post by osiris2258 on 2007-11-01
I just did a though check and according to both web pages, Gwenview and Showimg both have the inbuilt capability to browse zip and tar files. The zip functionality depends explicitly on the zlib package, which I have installed already and have tried reinstalling. So I am officially at a loss as to what to do, since I have the package that both programs need installed.

Could zlib have gotten messed up somehow? If so, how do I fix it, since 'reinstall' in synaptic did nothing and it can't be uninstalled (GNOME depends on it)?

---

### Post by mdebusk on 2007-11-02
> **osiris2258 said:**
> Could zlib have gotten messed up somehow? If so, how do I fix it, since 'reinstall' in synaptic did nothing and it can't be uninstalled (GNOME depends on it)?

I'm out of my depth here, and I wonder if this is the best forum to find an answer to this question. You might have better luck in General or Desktop Environments.

---

### Post by RomeReactor on 2007-11-02
Hi. I would suggest either [Comix]("http://comix.sourceforge.net/") for Gnome or [QComicBook]("http://www.kde-apps.org/content/show.php?content=19509") for KDE; just make sure you have **unzip** and **unrar** installed. You can find all those packages through Add/Remove or Synaptic. Or to install them from the terminal:
```
sudo apt-get install unrar unzip comix
```

EDIT: Upon more closely reading your posts, it seems this isn't what you're looking for; sorry.

---

