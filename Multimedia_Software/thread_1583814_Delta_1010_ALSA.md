---
title: "Delta 1010 ALSA"
date: 2010-09-28
forum: Multimedia Software
---

### Post by Colo2 on 2010-09-28
I just assumed that OSS was required to get the Delta 1010 working. But after reading an article, It seems like OSS isn't required. Apparently, Delta support is built into ALSA. Is this true?

[http://m-audio.com](http://m-audio.com)

---

### Post by cchhrriiss121212 on 2010-09-28
Yes, I mentioned it several times on your earlier thread, the problems you get with this card come from Pulse.

---

### Post by Colo2 on 2010-09-28
Hallo :)

Yeah, I know that Pulse causes the problems, however I was wondering if ALSA actually has **driver support** for the Delta cards

---

### Post by cchhrriiss121212 on 2010-09-28
Yes it does, if you run a system with pure ALSA you will get no issues. As I posted in the other thread, this is what I have set up on my machine and it works fine. Most folks using linux for pro audio will tell you that pulse is not much use.
 
To check what cards are supported by ALSA, [see this page]("http://www.alsa-project.org/main/index.php/Matrix:Main").

If you would like, I could recommend some distros that do not come with pulse installed, and just use ALSA.

---

### Post by Colo2 on 2010-09-28
> **cchhrriiss121212 said:**
> Yes it does, if you run a system with pure ALSA you will get no issues. As I posted in the other thread, this is what I have set up on my machine and it works fine. Most folks using linux for pro audio will tell you that pulse is not much use.
 
To check what cards are supported by ALSA, [see this page]("http://www.alsa-project.org/main/index.php/Matrix:Main").

If you would like, I could recommend some distros that do not come with pulse installed, and just use ALSA.

I'd like that, thanks :)

---

### Post by Colo2 on 2010-09-28
is there a debian based one which doesn't come with Pulse? Perhaps an *buntu one?

---

### Post by Colo2 on 2010-09-28
no?

---

### Post by cchhrriiss121212 on 2010-09-28
There's no need to bump after only 10mins, people will still see your post on the first page :). According to the forum guidlines, once every 24 hours is acceptable.

Anyway, the OS I would recommend is [http://crunchbanglinux.org/]("http://crunchbanglinux.org/")CrunchBang, which is designed to be minimalist, although you can add whatever you like to it. It is Debian based as of version 10, and even though it is still an Alpha release, it is more stable than any *buntu I've ever tried.

Together with an rt kernel and jack installed it is now my main recording setup.

---

### Post by Colo2 on 2010-09-28
> **cchhrriiss121212 said:**
> There's no need to bump after only 10mins, people will still see your post on the first page :). According to the forum guidlines, once every 24 hours is acceptable.

Anyway, the OS I would recommend is [http://crunchbanglinux.org/]("http://crunchbanglinux.org/")CrunchBang, which is designed to be minimalist, although you can add whatever you like to it. It is Debian based as of version 10, and even though it is still an Alpha release, it is more stable than any *buntu I've ever tried.

Together with an rt kernel and jack installed it is now my main recording setup.


Hey, thanks for your reply!

I've actually tried Crunch before, but I didn't like it. I think I was Distro Surfing at that point, and didn't give anything a chance. I'll give it a go now. Thanks :) 

Isn't that the OS which comes with Conky?

---

### Post by cchhrriiss121212 on 2010-09-28
Yep, thats the one. I've found conky really useful for monitoring cpu usage when I'm using effects, and the keyboard shortcuts are great for launching everything. Plus it has the bonus of my delta 44 working out of the box.
Here is a screenshot of how I set mine up:
[http://i879.photobucket.com/albums/ab352/cchhrriiss121212/2010-09-28--1285687514_1920x1200_scrot.png](http://i879.photobucket.com/albums/ab352/cchhrriiss121212/2010-09-28--1285687514_1920x1200_scrot.png)

---

### Post by Colo2 on 2010-09-28
Hey
Thanks for the reply.

What desktop environment is it? xfce?

if so, is it possible to install gnome on there?

thanks

Tom

---

### Post by cchhrriiss121212 on 2010-09-28
Crunchbang has either XFCE or Openbox. Openbox is lighter, but XFCE is easier. You can install Gnome but it will bring in pulse as a dependency, and then you may as well use Ubuntu.

---

### Post by Colo2 on 2010-09-28
Hey
In the sessions list, there's no XFCE, Just:

Oenbox Session
Run Xclient script
Dwm
openbox-gnome.desktop
openbox-kde.desktop
Secure Remote connection
Failsafe GNOME
Failsafe Terminal

Any ideas?

---

### Post by cchhrriiss121212 on 2010-09-28
XFCE is only in the new version, and it comes as a separate iso image. What version are you using?

But if you want to install it to an openbox version, just install XFCE from synaptic and reboot.

---

### Post by Colo2 on 2010-09-28
Hey. 
Thanks for your reply. I'ma check this out.

---

### Post by Colo2 on 2010-09-28
BINGO. it seems to be working fine now!!!

Thank you so much for your help! :) To everyone who's helped me!

---

