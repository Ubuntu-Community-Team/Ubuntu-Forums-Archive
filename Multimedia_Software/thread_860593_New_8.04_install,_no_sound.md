---
title: "New 8.04 install, no sound"
date: 2008-07-15
forum: Multimedia Software
---

### Post by Drott on 2008-07-15
I am a Linux noob and am just getting started with it all. I have installed Ubuntu 8.04 and everything went perfect, except I noticed that I do not hear any sound from anything. 

I have an Intel D945Psn motherboard (which has integrated sound on it) but I also have a Creative X-Fi sound card. I have the system set up to duel boot between XP pro and Ubuntu using the Grub app. When in Windows the sound is perfect, but when in Ubuntu, nothing comes out of the speakers. Being as this is my first experience with Ubuntu and Linux in general (OH NO, a Linux virgin) are there any suggestions out there that can help me resolve this issue? The help would be greatly appreciated.

---

### Post by intimatewipe on 2008-07-15
Me too please,just installed ubuntu on my other pc(cause its sexy:) )and this has a creative x fi fed into a 5.1 creative speaker system,once again it was a smooth install and its a dual boot with vista(in fact it has hyperos so there are 5 versions of vista on it (you need at least 5 to get one working properly:(),had a look about for info but I am also a noobie,(have had a great time learning though.

---

### Post by intimatewipe on 2008-07-15
might try this in the newbie section Drott,

---

### Post by Drott on 2008-07-15
> **intimatewipe said:**
> might try this in the newbie section Drott,

At the risk of sounding like a complete idiot, which section is that?

General Help?

---

### Post by Cone on 2008-07-15
> **Drott said:**
> At the risk of sounding like a complete idiot, which section is that?

General Help?

Absolute Beginner Talk.

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

As for the sound issues: Have you tried plugging the speakers into the sound port on the motherboard?  Creative has horrid Linux support and I have no experience with getting a X-fi to work, BUT the integrated audio should be up and functioning at least.

If plugging speakers into the various outputs on the motherboard doesn't work, I guess throwing up a "lspci -v | grep Audio" and "aplay -l" would help.

**BUT** you have a X-Fi and most likely won't settle for integrated audio (I understand, I spent way too much time getting my ASUS Xonar set up) -- try [http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx](http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx)

---

### Post by Francewhoa on 2009-05-22
If your sound card isn't automatically detected by Ubuntu 8.04.2 Desktop 32bits the below installation script is the **easiest way that I know of** to install & configure any sound card. It's a script made by *soundcheck*. It does all the hard manual setup process for you. ** [Click here to open the post]("http://ubuntuforums.org/showthread.php?t=1167242&highlight=xonar"), then find the latest installation script attached at the bottom. **Current installation script is title *AlsaUpgrade-1.0.x-rev-1.17.tar*.


If the script works for you please add your results here:

[LIST]
[*][https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)
[*][http://www.ubuntuhcl.org/browse/search+sound-cards?category=27](http://www.ubuntuhcl.org/browse/search+sound-cards?category=27)
[/LIST]

---

