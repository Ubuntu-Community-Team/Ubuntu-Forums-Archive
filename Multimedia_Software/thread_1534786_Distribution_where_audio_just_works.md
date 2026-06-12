---
title: "Distribution where audio just works?"
date: 2010-07-20
forum: Multimedia Software
---

### Post by balise on 2010-07-20
Is there a Ubuntu distribution in which sound "just works"?  I'm booting into Windows 7 far too much.

-jae

Background: I am running both Jaunty (on an old P4V533-MX desktop) where for some reason my sound went away, and Lucid, on a new Dell laptop (all-Intel Studio 14).  I thought a new installation of Ubuntu 10.04 on modern hardware would give me rhythmbox back, but I get no sound of any kind from the Dell laptop after installation, although everything works Ok if I boot into a W7 (came with the purchase) partition.

I don't want to fiddle with configuration files any more - just wondering if there is a "most-dependable" Ubuntu with respect to audio.  Which I will install.  Frustrated and impatient after weeks of this.

I am an old (hairy eared) Unix fan but IMO if Linux continues to complicate itself so freely (i.e. Pulseaudio - I don't know an audio mixer from a can opener and would prefer to remain that way), then the small market share it has will slip away rather than grow.

---

### Post by sikander3786 on 2010-07-20
I am using Ubuntu since Hardy and never had any problems with sounds. Sad you got many of those problems.

Have you tried Ubuntu Netbook Edition? That might work better on your laptop. Here are some useful links.

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

And for hardware compatibility

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

Regards.

---

### Post by Linuxforall on 2010-07-20
Never had any issues with audio not working, try KDE based Kubuntu which comes without Pulse, maybe that could be the reason.

---

### Post by TBABill on 2010-07-20
Depends totally on your hardware whether it will work or not. All my machines except one just work with any distro and no need to tweak. But my newest desktop is an HP Touchsmart and I have to edit the modprobe file in order to get the internal speakers working. Headphone jacks work fine, which is great if you have external speakers you want to use, but the Touchsmart has nice internal sound with great bass. So i was forced to edit the file to get it to recognize it as an Intel HDA on a Touchsmart model machine.
 
Sorry for such a crappy answer, but even the "it just works" distros like Mint and PCLinuxOS required the same fix in some form. For me it was just deleting one line and adding another, but finding out what to do was a pain to such a degree I emailed myself the steps so I'd never have to find it again.
 
If you post a "how to" there is one user here that has provided outstanding help and was able to fix mine. So if you are willing to tolerate a walk-through you'll get there pretty easily. I know that your desire is to avoid doing that, but in some cases I don't know of a GUI workaround.
 
Have you tried another distro? PCLinuxOS is like Mint - preconfigured with codecs and most things really do just work out of the box. Latest version is 2010.07 and has the 2.6.33 kernel as its base. Well worth a shot if other configuration things also bug you and it comes in KDE, Gnome, Gnome-mini, Xfce, LXDE and E17. Mint 9 may also be easy to setup, but I think sound configuration will just mimic what you find in Ubuntu 10.04.

---

### Post by balise on 2010-07-20
Thanks very much for the answers, to a unhappy question.  Actually, I managed to get rhythmbox going on the laptop this morning, although I'm not quite sure how I managed to do it.  Too many switches and dials for me.  I do wish there were more Linux developers that keep the impatient / stupid in mind.

That's one place where Microsoft shines.

---

