---
title: "Big mistake!"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by topic58 on 2007-11-10
Hello all, I need some help badly here. Running Breezy 5.10, AND yesterday I tried updating VLC. It didn't work out, so I had to correct that in Synaptic. BUT I erased VLC completely! :(  So please - Is there any way I can get it back?? Using Synaptic is no option. Tried newer VLC, but problems with dependings. Anyone PLEASE?? Totem doesn't work so good, mplayer is okay, but VLC is the one for me.

---

### Post by miwaypet on 2007-11-10
Have you tried downloading restricted dependencies. Use automatix2 for restrictred and non-free codecs. Use it to install totem xine. You wil have no probs playing anything. If you want VLC, after installing the dependencies go to thier website and download player. Follow the instructions for installing. Should have no probs.

To save yourself future headaches get aptoncd and back up your packages! Good luck.

---

### Post by JBAlaska on 2007-11-10
Here's a deb of version 0.8.5 for Breezy
```
http://nightlies.videolan.org/build/breezy-i386/vlc/0.8.5-svn20060208/
```

---

### Post by topic58 on 2007-11-10
Bump... Installing Feisty right now... :mad:

---

### Post by JBAlaska on 2007-11-10
You need to check that you have a "universe" mirror in your /etc/apt/sources.list.

Then paste the below lines in a terminal:
```
% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

Big mistake #2:Not installing Gutsy LOL!

---

