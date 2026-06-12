---
title: "Totem Movie Player"
date: 2009-01-19
forum: Multimedia Software
---

### Post by ShawnMichael on 2009-01-19
Once again I am new to Linux.  So when I try to play my dvd movie here, it wont load and I keep getting errors.  What should I do?  Or from what I have read Totem Dvd player sucks, so is there any other dvd prog that anyone could suggest to me?  I am also deaf, so keep in mind that I need closed captioning as well.  

Thanks!

---

### Post by gettinoriginal on 2009-01-19
Have you tried VLC player, it seems to get good reviews from others on here. :P

---

### Post by steeleyuk on 2009-01-19
Totem doesn't suck, its quite a powerful player, its just the lack of visible options masks how good it is.

Heres a link to the community docs explaining how to [setup DVD playback]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").

---

### Post by ShawnMichael on 2009-01-19
still dont work.  both of them dont

---

### Post by Melcar on 2009-01-19
VLC should have no problems playing DVDs.  What errors do you get?  You could try Mplayer as well.

---

### Post by mc4man on 2009-01-19
@ShawnMichael
what may work well for you is to install the latest smplayer and a recent mplayer. I believe it has support for closed captions and certainly works well.
Plus the developer answers any questions posed here very quickly.

The page is here
[http://smplayer.sourceforge.net/downloads.php](http://smplayer.sourceforge.net/downloads.php)
description, info
[http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

Your best option is to add his launchpad repo to your sources and then install from either synaptic or the terminal (this will install everything needed, and update mplayer if you've already installed.

```
sudo apt-get install smplayer mplayer
```

To add the repo go System -> Admin... -> Software sources -> Third-Party Software and click add.
Copy and paste 1 of these 2 lines in the Apt line box, use the one for your version of ubuntu. Then click 'add source', 'close' and 'reload'

8.10 (intrepid): ```
deb http://ppa.launchpad.net/rvm/ubuntu intrepid main
```

8.04 (hardy): ```
deb http://ppa.launchpad.net/rvm/ubuntu hardy main

```


After that run the  apt-get line above. Any problems using just start a new post with smplayer in the title.

You'll also need libdvdcss2, if you haven't installed yet just go here, click on and follow the prompts to install (good for both hardy and intrepid. (click on the i386, if you get a wrong architecture message then go back and choose amd64

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

Or if your using Intrepid (8.10) just run this in a terminal
```

sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by kleptik on 2009-01-19
Anyone know if it'll play unencrypted DVDs from a network location? Does it have a purdy DVD library interface?

---

