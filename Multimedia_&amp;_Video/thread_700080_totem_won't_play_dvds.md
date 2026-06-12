---
title: "totem won't play dvds"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by z987k on 2008-02-18
well kind of.... It won't play the dvd's if I hit the movie -> play disc "".  It says "Please install the necessary plugins and restart Totem to be able to play this media."  If I navigate to the .vob file and play that using totem it plays fine.  Mplayer also plays fine, but I'd like to get totem to work as I prefer it for dvd's.

---

### Post by amohanty on 2008-02-18
Use the xine backend:
sudo apt-get install totem-xine

and then follow:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

HTH
AM

---

### Post by corevette on 2008-02-18
> **z987k said:**
> ...but I'd like to get totem to work as I prefer it for dvd's.
i know it is another workaround, but you could always do a:
```
sudo apt-get install vlc
```
just because i <3 vlc player
but try installing *totem-xine* first and see if that solves your problem

---

### Post by andrewjoy on 2008-02-18
i second that sir
```

sudo apt-get install vlc
```

will solve all your problems

but if you want to use totem use the xine back end

---

### Post by julian67 on 2008-02-18
I love totem for everything except DVD's where it's a real pita whichever backend you have. afaik the only way to make it play a DVD with a menu is for the DVD to be autostarted on insertion. Mplayer is similarly unsatisfactory for DVDs with menus and VLC is definitely the best free palyer out there for this, it will even play DVDs with menu from .iso disk images. The original xine is ok but has a tendency to crash (in my experience).

---

### Post by geo909 on 2008-02-18
Not sure, but if you install ubuntu-restricted-extras,
I think there are also libraries for encrypted DVDs.

---

### Post by chavanak on 2008-02-18
i second geo909.... /try that it might just work!!!! This is always a problem due to copyrights :(

---

### Post by ubuntu-freak on 2008-02-18
I agree with the pro VLC comments. In my opinion VLC should be the default DVD player in Ubuntu. Why? Cos it's simply superior to everything else. Even those pain in the **** new DVDs can be made to work in VLC. You can make it default by following part 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833), and if the standard encryption beating solution doesn't work for some new DVDs, check out the link in paragraph 9 of the troubleshooting section at the bottom.
 
I've never had any need to use Xine. I'm surprised how many people recommend others to install it. It's benefited me using MPlayer for most vids and streaming, and Totem Gstreamer for any that MPlayer has trouble with. 
 
Nathan

---

