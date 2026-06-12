---
title: "compaq help! Simple but i dont know!"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by Dibbs on 2008-03-11
Hey,

I was really hoping to get some help! For a friend!

I wanted to show him the compiz on Ubuntu on his Compaq Laptop- So i went to his ''screen and graphics'' settings, where Ubuntu set it as a 'Glint - 3D labs' card. Now his real graphics accelerator (i think) is an intel 9 something. 

I cant remember much Im sorry =( and this sounds so simple to fix but i just cant find the right words to find help with.

So me being a tart, i changed it to an Intel 9 something, and then he restarted his laptop, and now it boots up the Ubuntu partition, but cant load the GUI ('startx' command does nothing either). it gives out an error, i cant remember what exactly i will try and get my friend to write it now soon, and it keeps repeating the error, making the screen blink, then after a while, the laptop just restarts.


**Basically, is there a way, to change the graphic settings back to the 'Glint' card? Through command line perhaps? Or maybe through a live CD?**

I really wanted to change it back- i feel terrible, even though its not a major problem.

Please excuse my .um..lingo..it sounds really nooby..especially as i don't know the errors and such about this..ill get them down when i can!

Thanks for any help!

---

### Post by scragar on 2008-03-11
before you do anything I'm suggesting back-up your config file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
to restore it run:```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```at any time.

firstly, see if ubuntu can quickly fix itself:
```
sudo dpkg-reconfigure xserver-xorg
```
if that doesn't work you may have to edit the xorg config file manualy...

---

