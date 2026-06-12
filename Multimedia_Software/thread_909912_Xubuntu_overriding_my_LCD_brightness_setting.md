---
title: "Xubuntu overriding my LCD brightness setting"
date: 2008-09-04
forum: Multimedia Software
---

### Post by slumbergod on 2008-09-04
I can't seem to find any existing threads about this so perhaps someone who knows a bit more can help.

I like my laptop display dimmed as far as I can (I use Fn + left and right arrow keys for this). Everytime I go to play a movie in VLC, suddenly the screen jumps back to being too bright (I presume the normal setting).

I don't know if this is something unique to VLC, Xubuntu in general, or perhaps just the way my hardware works (onboard Intel X3100). Something similar happened when I I unlocked the screen following the screensaver kicking in.

Any ideas on where this sort of thing is controlled from?

Cheers

---

### Post by touchlikefire on 2008-09-04
First, to perhaps give you some more information on your question:

The power management (System > Preferences > Power Management) settings have controls that can dim screen on battery power, and dim screen when idle.  When the computer detects that it has stopped being idle, it resumes to the "normal" level of brightness.  I suspect what's happening to you is that linux is reverting back to the 'normal' setting as if it had stopped being idle.

**My question to other users**, which I believe is on topic: is there any configuration settings (or more likely, file) where I can manually define the brightness level I would like to be 'normal' or default?

The answer to this I believe will help the OP since then they can set that brightness level as normal, and linux won't brighten it further when it senses the laptop is no longer idle.

---

### Post by notorisch on 2008-09-04
Hi,

I have a similar problem but the other way around. When I start playing a Video with VLC but also sometimes with mplayer the screen gets darker.
I run Ubuntu 8.04 hardy on a Acer Aspire 2920z.

Any ideas?

Thanx

---

### Post by Halbarad on 2008-09-12
@Notorisch This is a very old and nasty bug. See: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/12637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/12637)

There may even be several related bugs, everyone of which differs from the others. What they have in common is an unwanted change in the screen brightness, mainly in connection with the booting process, running Mplayer and VLC, and more. 
A very rough fix is to use your brightness function keys: try the combinations ALT-F... 5 to 7. Be careful about ALT-F1 because this might send your PC into suspend mode.

Otherwise, you can find some proposed patches in the thread mentioned above, but do not expect too much from them...
You could perhaps try chourave's fix, which is easy to set and to remove in case it doesn't work. 
Type in a terminal

```
echo blacklist video | sudo tee -a /etc/modprobe.d/local
```
(This sends the string "blacklist video" into the newly created file /etc/modprobe/local. You must use "sudo" because you need root privileges to write into directories which are not /home/<user>. Sorry for being so verbose! Perhaps you have won a couple of Nobel Prizes in computer science or you are Linus Thorvald visiting in here -- just smile and forgive me then!)
This file forces your pc not to load the video drivers that handle brightness etc. on boot. This means that your keyboard brightness controls would not work any more. Now reboot. If you are lucky, your screen will be permanently bright, just until Intrepid (the new version of Ubuntu) hopefully fixes the problem. If you are unlucky, you get stuck at minimum brightness (@slumbergod: just replace "lucky" with "unlucky" and you have it...). In this case, you'd immediately open a Terminal and remove the file created above:
```
sudo rm /etc/modprobe.d/local
```
Be careful not to remove anything else!
One thing you could do with these lines of code is to select them, copy them and paste them into your terminal -- you thus minimize the danger of giving unwanted orders.


It would be interesting to know some data about your systems.
1. which graphics card you have: type in a terminal
```
sudo lshw -C display
```
(this lists the hardware in the class "display")
2. what your xorg.conf file looks like:
```
gedit /etc/X11/xorg.conf
```
(these are the configuration settings of Xorg, the Linux graphics server).

---

### Post by Halbarad on 2008-09-13
@ touchlikefire: in Intrepid, you shall get the configuration settings you talk about. They are in System/Preferences/Power Management, where you can set the normal display brightness.

---

### Post by touchlikefire on 2008-09-16
@Halbard: thanks, I'm gonna see if I can find a package for that on launchpad.

---

