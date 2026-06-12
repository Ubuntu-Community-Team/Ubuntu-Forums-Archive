---
title: "Root Password for Ubuntu Fresh Installation"
date: 2010-06-05
forum: Multimedia Software
---

### Post by ghous on 2010-06-05
Dear Ubuntu Community, 

I just installed Ubuntu 10.0.4 and it asked me only set up one application / os user credentials (which I did). After the installation, I came to know that I wasn't able to listen sound from the speakers. Now, in order to fix that issue; I've to install an upgraded driver for my sound card (which I got) but when I run the following command:

make install

it is to create / remove some directories in usr/include/sound directory. user of this directory is root and i get the permissions denied message. I tried to switch as root user but authentication gets failed every time. 

will appreciate if somebody could help me out of this as there was no intimation to set any password for Root while installing ubuntu.

Regards
Ghous

---

### Post by ajgreeny on 2010-06-05
Are you certain you need a new driver?

Run ```
alsamixer
``` in terminal to check that sound levels are not muted, as is often the case after installing for some weird reason, nor set too low.  Use cursor keys to navigate and raise and lower levels, and "M" to mute/unmute, (MM below the slider means it's muted).  Use Esc to quit and save settings.

If you really do need to compile, use sudo before the command in terminal.  You may also need to install **build-essentials**

For more info on root/sudo see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Breambutt on 2010-06-06
Like our friend here said, run *sudo make install* instead. The root password is disabled by default in Ubuntu and it's for the good of every rookie. Most people will never need to enable it, but it can be done with *sudo passwd* which will prompt you for your regular user password and afterwards the new root password twice.

And that's why they call me the link recap man.

I also refuse to believe that you'd need to install any drivers for a sound interface. What kind of a card is it anyway? Some onboard chips seem to have mystical issues, certain cards are muted by default and a bunch of musician-oriented cards just won't work properly with PulseAudio.

If the alsamixer suggestion didn't do the trick, try killing PulseAudio with *pulseaudio -k* (I think... *killall pulseaudio* should work anyway) and see if you get sound then. PA will probably relaunch itself randomly in a few seconds because it was designed and engineered after a cockroach.

---

### Post by ghous on 2010-06-06
Hi everybody, 

Well, the good news is that my both problems have been solved. I followed the instructions given as per the link to fix sound issue:
[COLOR=Blue]**[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)**[/COLOR]

Also, the command **[COLOR=Blue]' sudo passwd' [/COLOR]**allowed me to change password for the root. :popcorn:

Thanks everybody to help me out. 

Regards
Ghous

PS: please mark this thread as solved.

---

