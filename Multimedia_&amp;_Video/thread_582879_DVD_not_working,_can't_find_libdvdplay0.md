---
title: "DVD not working, can't find libdvdplay0"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by El Zoido on 2007-10-20
Hello!

I did a fresh install of Gutsy 2 days ago (upgrade from Feisty locked up :/ ) and therefore had to reinstall all the codecs and stuff.
However, I can't find the libdvdplay-package in Synaptics. Downloading it via console didn't work either, although I enabled all sources. It just isn't there.
Because of this I can't play DVDs right now.

As an alternative I tried to install VLC, as I thought it would come with its own codecs, but even with VLC, DVD playback isn't working.

Has anyone got an idea how to get the libdvdplay?

Greetings,
El Zoido

*** UPDATE ***

I found a link that provided the missing libdvdplay0 and libdvdcss2 packages, so I could install them manually. Totem is automaticaly playing DVD-movies now, but refuses to play the menus. It keeps stating that some packages are missing (I installed the other libdvd packages).
VLC is working fine now, however, so at least I can watch DVDs again.

Still I wonder why I couldn't find the packages in the repositorys...

---

### Post by Grimgoil on 2007-10-20
> **El Zoido said:**
> 
I found a link that provided the missing libdvdplay0 and libdvdcss2 packages, so I could install them manually..
Just a pointer, your not the only person with problems, if you find a way to fix something, share. 
Thank you

(A guy trying to play DVD's too)

---

### Post by Grimgoil on 2007-10-20
mistake

---

### Post by El Zoido on 2007-10-20
Well, just in case:

[libdvdplay0]("http://security.ubuntu.com/ubuntu/pool/universe/libd/libdvdplay/libdvdplay0_1.0.1-7_i386.deb")

[libdvdcss2]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb")

---

### Post by mc4man on 2007-10-20
libdvdplay is somewhat outdated  libdvdnav is what's being used now
but if it works who's to argue

---

### Post by rapsball4 on 2007-10-22
Trying to set this up myself on my 64-bit version - those links say wrong architecture for me.  I didn't actually bother setting it up on Feisty (just used Windows when I wanted to watch movies) before, so I don't have any kind of a head start in knowing how to do this.  I installed libdvdnav as well as mplayer and other things I found online through various places that it said would make it work.

---

### Post by Quadcore on 2007-10-22
I had DVd problems too, reinstalled Mplayer from source and problem is fixed hehe..

---

### Post by rapsball4 on 2007-10-22
I tried to do that, and failed because it couldn't find a couple header files.

---

### Post by nasov on 2007-10-22
howdy i just installed gutsy on my moms pc and I promised her that everything will be working before o'll go back to mine. yesterday we watched a dvd but today the same DVD doesn't work in totem, kaffeine, gxine ... I installed all of the packages mentioned above but still DVDs are a no go zone...

can anyone help?

kind regards

tom
**[COLOR="Red"]***SOLVED - just tried Mplayer and it working....[/COLOR]**

---

### Post by sjd on 2007-12-03
SOLVED:

Instead of downloading/installing libdvdplay0, I uninstalled everything else - gxine, totem, etc. and installed vlc through synaptic.  Took a little futsing - Opened VLC, clicked on File, Open Disc, clicked Disc tab, changed from DVD (menus) to DVD and OK - idisc started playing immediately).


I am also trying to play a dvd and found libdvdnav4 and libdvdread3 were not installed, which I've since installed.  But, neither synaptic or terminal searches found the libdvdplay0 on my system.  I saw the link to download it but, am so green I don't know whether I should "Open" or "Save", where to "Save" to, or how to install once it is saved.

From what I've read I'm thinking Gdebi is run if you click 'Open' or that I can download it to ?anywhere? and run apt-get install - but, I want to make sure it is installed in a way that 'links' it to the update manager (like apt-get).

Thanks for any assistance you can provide.

sjd

---

