---
title: "Confused about ATI drivers, XGL, Beryl"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by hypersire on 2007-05-03
Hi all - I just installed linux on my HP DV8000z laptop with an ATI Radeon 200M integrated video card. I enabled the ATI drivers via that applet for 3rd party drivers. In the Synaptics pkg manager, it shows that I have xorg-driver-fglrx 7.1.0-8.34+2.6.20.5-15.20 installed.

I've been reading all sorts of posts about people upgrading to the latest ATI drivers and enabling XGL and Beryl. The procedure sounds very error-prone. It seems that half the time even experienced users don't get it working.

My questions are:

What exactly are XGL and Beryl? I know they are some sort of 3d graphics accelerators, but do I need them? Is it only for gaming? I am watching HD clips via VLC player just fine.

What's the story with the ATI drivers - I have 7.1.0 installed through the pkg manager but I also see an entry their for 8.34.8 source and on the ATI site, 8.36.5 is available. Is it worth upgrading to the very latest? Why doesn't the pkg manager offer the latest? I am guessing it offers the last tried and true driver?

Thanks for your help!

---

### Post by kangol69 on 2007-05-03
I also have a dv8000 and I installed XGL and Beryl. Beryl is an OpenGL accelerated desktop that basically makes cool animations happen when you interact with windows and your desktop.  Like on a mac when you minimize your window and it gets sucked into the Dock. It really doesn't really have too much of a purpose except to make your comp look really sweet. If you want to install Beryl and XGL I recommend following this guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29")

If you want to see some of the cool effects Beryl can do look Beryl up on google images or even youtube.

---

### Post by hypersire on 2007-05-03
Thanks very much for the explanation kangol69!

So would Beryl replace my current XFCE desktop or does it work on top oif it adding some extra pizaaz?

What about XGL - I believe it is a layer that separates the ATI drivers from Beryl so Beryl interacts with XGL and not the ATI drivers directly?

One last ? - did you upgrade to the latest ATI drivers as well?

Thanks!

---

### Post by kangol69 on 2007-05-04
I don't know too much about Xfce but I'm pretty sure that beryl would just replace the window decorator part of Xfce (I have gnome and beryl replaces Meatacity, which is the gnome window decorator)  Also I don't know much about Xgl but I know I had to get it for the 200M to work with beryl. I couldn't just download the ATI drivers. And Yes I do have the newest version of drivers that you can get out of the repos. One thing I do know very well though is that if a friend of yours trys to show off his Windows comp with Aero or a Mac with some cool effects you can just show them that you can make your desktop become a cube and can have your windows appear like they're burning when you close them and they will shut up right away. Then you can always hit them with the "By the way.... it was all free (as in beer)"


P.s. If you use that guide I gave you, make sure you follow that part about disabling the universe repos while you install beryl. You can add them afterwards but the version of beryl on the ubuntu repos didn't work with my 200M. I'll put a script up on Friday that will stop Ubuntu telling you to update beryl files.

Good Luck!!!:guitar:

---

### Post by DaH-RaT on 2007-07-21
i am also confused about XGL beryl and the ati drivers

ive tried everything ive ran into and running into to keep trying until i get it working...

but my 9800 pro wont ever get it working, as far as i can get is XGL session beryl auto boot up, but the only desktop effects i cang et are the standard Ubuntu effects..

---

