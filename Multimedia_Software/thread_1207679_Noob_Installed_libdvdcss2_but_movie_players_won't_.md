---
title: "Noob Installed libdvdcss2 but movie players won't work"
date: 2009-07-08
forum: Multimedia Software
---

### Post by unckybob on 2009-07-08
Installed libdvdcss2 but movie players won't work:

Kaffeine
Totem 
MPlayer
VLC

Installed Medibuntu Repostitories

---

### Post by az on 2009-07-08
Is this a brand-new dvd player?  Has the region been set?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes)

---

### Post by unckybob on 2009-07-09
Sorry I took so long to get back. Yes, I tried regionset. Here's what came out: 

[B]robert@DellDesktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n
robert@DellDesktop:~$ 
[/B]

I assume from this that the region is 1 and that I don't need to change it?

---

### Post by Ra-Hoor-Khuit on 2009-07-09
You've enabled the Medibuntu repo, but have you installed the ubuntu-restricted-extras metapackage?

---

### Post by unckybob on 2009-07-09
Yes. Funny thing. Now I can't burn DVDs.

---

### Post by Ra-Hoor-Khuit on 2009-07-09
More specifics then.  What type of media are you trying to play?  What happens with the different media players, do you get error messages, etc.?

---

### Post by unckybob on 2009-07-09
Kaffeine: 

   Blank Screen on the viewer

Movie Player: 

   Disapears

MPlayer: 

   Disappears

VLC: 

   Disappears

---

### Post by Ra-Hoor-Khuit on 2009-07-09
If you want help, you're going to have to provide full, detailed replies and information using things like complete sentences.  These forums move too fast for me to sit around and see if I can forcefully extract the information necessary to assist you; nor do I have the inclination to do so.

---

### Post by unckybob on 2009-07-09
Sorry I was answering your posts too cryptically. 

libdvdcss2 has been installed. I know it's working because I can rip encrypted DVDs. I couldn't before I installed it. 

I have installed the media players: Kaffeine, Totem Movie Player, MPLayer, and VLC. 

I have installed the ubuntu-restricted-extras metapackage. 

The media I am trying to play are encrypted movie DVDs. 

I mentioned above that I couldn't rip DVDs anymore. I checked it again and I was wrong. I can still rip DVDs. 

When I try to play a DVD, I get no error messages at all. The windows for Totem Movie Player, MPlayer, and VLC simply disappear. Kaffeine does nothing at all, it just sits there like it did before you asked it to play the DVD. 

I hope this is better. Thanks for looking at my posts thus far. 

Bob

---

### Post by mc4man on 2009-07-09
try this post from a few days ago,
[http://ubuntuforums.org/showthread.php?p=7565349#post7565349](http://ubuntuforums.org/showthread.php?p=7565349#post7565349)

 if still no joy then open vlc like this from a terminal, try to play dvd, (media -> open disc) and post output

```
vlc -vv
```

---

### Post by az on 2009-07-10
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing%20libdvdcss](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing%20libdvdcss)

If you are running Ubuntu 9.04, you need to do this:

Ubuntu 9.04 (i386, amd64)

    *

      Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line: 

 sudo apt-get install libdvdread4

    * Then open a terminal window and execute: 

 sudo /usr/share/doc/libdvdread4/install-css.sh

---

