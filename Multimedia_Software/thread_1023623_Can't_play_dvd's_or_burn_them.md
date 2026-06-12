---
title: "Can't play dvd's or burn them"
date: 2008-12-28
forum: Multimedia Software
---

### Post by Robert John Kelly on 2008-12-28
i don't know why but i managed to set up every player i could possibly find that will play on ubuntu. xine or any other variation of it won't play a dvd. the dvd is ironman by the way incase there is just a problem with this movie. the most common error is that i don't have the rights to watch this movie. also i can't find a burning program that will work as good as nero 8 but on linux. the linux version of nero sucks... please help

---

### Post by labinnsw on 2008-12-28
Have you tried the following?

Go to: System>>Administration>>software sources
Under Ubuntu Software tab: check " Software restricted by copyright or legal issues (multiverse)"
Select: Close then Reload

---

### Post by Robert John Kelly on 2008-12-28
will that do it? just curious, i'm upgrading from 8.04 to 8.10 right now so i have to wait for a good hour before i can try. i haven't even come accross that yet so i could very well see it working. if is thanks for your time, much appreciated.

---

### Post by labinnsw on 2008-12-28
I think that in addition to this, you will need to install the required codecs. In any event before too long, you should be able to play any video.

---

### Post by Robert John Kelly on 2008-12-28
where in the world do i find codecs for ubuntu? i got vlc media player on here doesn't that usually install most of them?

---

### Post by balaknair on 2008-12-28
Issue 1: DVD playback- You need some additional packages to play encrypted DVDs, which cannot be distributed with the Ubuntu CD due to legal and technical restrictions(because DVD decryption software may be prohibited in some countries).
To install these packages, enable the multiverse repositories as described by labinnsw in the previous post. Then open the Applications menu> Add/Remove Applications--> search for ubuntu restricted extras, and install the package. It'll be a fairly large download, and includes non-open-source stuff like Adobe Flash, Sun Java, MP3 codecs etc.

Issue 2: CD/DVD Burning program: There are a large number of CD burning apps available on Linux. If you want something similar to Nero, the default app in Ubuntu(Brasero) is similar to Nero Express, and aims to keep it simple. K3B is a feature-packed CD/DVD burning app, though not as simple as Brasero.
If you want to create DVD movies(a video DVD), you can opt for something like DeVeDe, which can create DVDs and SVCDs with menus and title/chapter formatting. 
Ripping DVD movies- try DVD::rip or Acidrip--> rip DVDs and encode as AVI or MPEG.

All these are available via the Add/Remove Applications tool, once you have enabled the 'Universe' and 'Multiverse' repositories.

---

### Post by labinnsw on 2008-12-28
Usually selecting the media prompts the installation of the necessary codecs if they are not already installed. The repositories need to be enable first.

---

### Post by Robert John Kelly on 2008-12-28
you guys are awesome thank a million

---

