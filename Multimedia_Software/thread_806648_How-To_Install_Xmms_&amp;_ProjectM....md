---
title: "How-To Install Xmms &amp; ProjectM..."
date: 2008-05-25
forum: Multimedia Software
---

### Post by TenPlus1 on 2008-05-25
After many attempts to get ProjectM working in Hardy and many failures, I gave in and downloaded the older 0.99 versions of the software I needed and managed to get a working visual plugin for Xmms player:

1.) Get Xmms from here: [http://ubuntu.cs.uaf.edu/ubuntu/pool/universe/x/xmms/](http://ubuntu.cs.uaf.edu/ubuntu/pool/universe/x/xmms/)
2.) Go here: [http://sicherheitsschwankung.de/~jluebbe/debian/unstable/](http://sicherheitsschwankung.de/~jluebbe/debian/unstable/)
3.) Get libprojectm1_0.99-1_i386.deb, libvisual-projectm_0.99-1_i386.deb
    and xmms-projectm_0.99-1_i386.deb.
4.) Install Xmms then libprojectm, libvisual and finally xmms-protectm deb's.

Now you should have a working ProjectM under the visualisation plugins for Xmms, be warned though, you need a good working 3D card and a decent processr for smooth playback. (config file is in ~/.projectM)

Note:  As much as I would love fancy visuals on Ubuntu to showcase my music, projectM doesn't quite look as good as Milkmod on WinAMP...  I just dont feel the music on screen as I do with WinAMP...  Just my 2 cents...

---

### Post by struktured on 2008-05-25
If you want help getting projectM 1.x, why not post your problems here and I can assist you? You shouldn't be using xmms by the way. It is unmaintained and deprecated. Try audacious or amarok for instance.

And as for milkdrop looking better, I agree. If you are running anything less than projectM 1.x it won't even have smooth preset switching! Not to mention *many* milkdrop compatibility fixes.

On the other hand, with the right configuration settings in the projectM config file on a decent pc, the projectM 1.x series does an excellent job of rendering presets just as good as milkdrop the majority of the time. 

Furthermore, little or no work has been done by preset authors to take advantage of our unique features- like infinite custom shapes or waves, and an image texture loading system built into the preset language. We are slowly working on this "lack of projectM preset authors" problem.

- struk

---

### Post by Chr0mis on 2008-05-25
Why on earth would you, instead of just helping the guy out, lecture him on his choice? Xmms might be old and abandoned by the developers, it still is a very simple and basic music player who does exactly what it should: it plays music. Amarokk and Rhytmbox are bloated in comparison to xmms. 

Just my 2 cents.

---

### Post by struktured on 2008-05-25
It's for purely technical reasons. 

(1) xmms development has ceased.

(2) it may be easier to get projectM working without xmms.

(3) the projectM developers do not want to encourage the use of xmms.

(4) he didn't seem particular concerned about xmms, he seemed concerned about  some sort of winamp + milkdrop combo in linux he found acceptable enough to show off at parties :)

In any event, let's hope we can get projectM 1.x working for him!

---

### Post by TenPlus1 on 2008-05-26
I've tried every guide in compiling projectM on my Hardy system and none have ever worked, the window generally appears then quickly closes on every compile/fix/build...

Xmms works for me since it's a nice little player and 0.99 getss long well with it...  Amarok is frikken huge with all the kde libs and I'd much rather get the PulseAudio part working so I can continue using MPD and Gimmix...

---

