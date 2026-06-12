---
title: "Can two users use the same computer at the same time?"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Smivs on 2009-11-10
I have a network consisting of a Ubuntu computer and two running XP, one of which is my Wifes. I would like her to be able to use the Linux box via VNC from her XP box while I'm still working on on it. I have set up  RealVNC but this only accesses whatever I've got running.
As far as I can tell, TightVNC is my best bet. I'm a bit new to this but my understanding is that a TightVNC server on the Linux box should generate a completely separate desktop (which can be used independently of but simultaneously with the 'main' desktop) when accessed via remote desktop from my wifes' XP box.
Has anyone else done this? Will it even work?
Any advice gratefully received.

---

### Post by honestguvnor on 2009-11-10
[B]> Can two users use the same computer at the same time?
[/B]Yes but a computer usually only has one screen.

One of the main features of X Windows going back to the 1980s is that it can run over the network. A graphical program running on machine A can draw on the screen of machine B if the user on machine gives permission. What is required is that your wife runs an X Windows server on her XP box which can be done but I do not know the details.

If you want her to run the whole desktop why don't you simply install Linux on her machine as an alternative to Windows?

What programs do you want your wife to run?

---

### Post by Smivs on 2009-11-10
Our linux box is much more powerful than the XP box (which incidently is a dual boot with Red Hat) and is perfect for editing the hours of video she produces of our kids. Ideally, she can do this via VNC from her computer upstairs while I continue to use the linux box which lives in the lounge and is linked into my A/V setup.

---

### Post by honestguvnor on 2009-11-10
To play video efficiently one simply needs to off load the video processing onto dedicated video chips rather than running software inefficiently on the main general purpose processor. I recently bought a small cheap PC with a 1.6GHz Atom processor and an Ion graphics chip and it happily displays 1920*1080 movies while using about 3% of the main CPU. You might be better off putting a modern cheap graphics card optimised for video in the old PC.

---

