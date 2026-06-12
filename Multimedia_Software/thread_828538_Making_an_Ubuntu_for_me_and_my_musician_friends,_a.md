---
title: "Making an Ubuntu for me and my musician friends, any tips?"
date: 2008-06-13
forum: Multimedia Software
---

### Post by ArnsteinK on 2008-06-13
After I found out how to make an own Ubuntu-setup then minutes ago(in this thread: [http://ubuntuforums.org/showthread.php?t=828464](http://ubuntuforums.org/showthread.php?t=828464) ), I decided to make an Ubuntu designed for me and my musician friends. :guitar: (just HAD to put that in there(don't think of that sentence in a sexual way))

Well, what programs do you think musicians need? Some of the apps I got is Rhythmbox(obvious one I guess), NoteEdit, Hydrogen and Rosegarden. 

What more do I need? When I'm done I can upload it if anybody wants it.

---

### Post by markbuntu on 2008-06-13
Ubuntu Studio already beat you to it. It has some of everything as far as sound/music apps go and it has the real time kernel which is critical for sound/video recording/mixing.

---

### Post by ArnsteinK on 2008-06-13
Well, I would like to customise one for myself, and I dont want to reinstall Ubuntu!

---

### Post by markbuntu on 2008-06-14
You could look at the list of apps that come with Ubuntu Studio and pick and choose the ones you want. The rt kernel is a must though for real time recording etc.

---

### Post by Spaceman9 on 2008-06-14
You install Ubuntu Studio from Synaptic. Jus do a search in Synaptic for Ubuntu and scroll down to Ubuntu Studio. That's the easy way to get music apps and you don't have to deal with setting up most of the apps. Rosegarden and MuseScore might need some setting up though. 

Also Ubuntu Studio installs and sets up the rt kernel and rewrites your menu.lst file so you don't have to do that yourself either.

You won't have to reinstall Ubuntu 8.04. Ubuntu Studio is Ubuntu 8.04 with music apps added but it has the rt kernel. If you install Ubuntu studio just scroll down to the rt kernel when you boot Ubuntu and hit Enter. The other kernel that installed with Ubuntu 8.04 will still be in the GRUB Menu and if you have another distro that your Ubuntu GRUB boots that will still be there too.

---

