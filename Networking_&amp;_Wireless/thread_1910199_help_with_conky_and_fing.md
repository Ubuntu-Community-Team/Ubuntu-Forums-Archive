---
title: "help with conky and fing"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by stellarsky on 2012-01-16
I just did a restall of ubuntu and am having some problems:
I installed conky but I'm not using devilspie and I cannot change the config files, I was attempting to delete old parameters and copy and paste new ones in the file but I get a error that I dont have privileges,I'm logged in as root in the terminal but trying to do this through the gnome desk top.
Before I reinstalled ubuntu I had overlook fing downloaded and running in the terminal
but now ubuntu software center says fing is the wrong arch. regardless of tgz or deb 32 or 64 bit, I was going to try force architecture in terminal but says it cant get the package using apt-get and I dont see it in synaptic package manager 
any help would be awesome.
Thanks much.
oh FYI I did the reinstall with the intention of downgrading my ubuntu to back 10.04 which I had conky and devilspie running and which seemed to work with more software and has LTS but ended up with 11.0x again by mistake but in 11.04 is where i had fing running but after the reinstall of 11.04 it now seems impossible,I even attempted to download the windows version and run it through wine but it crashes.
Again thanks for any help.

---

### Post by a1an on 2012-03-21
Just tried to install .deb of fing 1.4 and got the same message from ubuntu software center: "wrong architecture" for both 32 and 64 bit versions.

Release:	11.04
Codename:	natty

2.6.38-13-generic-pae #56-Ubuntu SMP Tue Feb 14 14:32:30 UTC 2012 i686 i686 i386 GNU/Linux

It seems the arch is not specified in the package metadata

Use dpkg --force-architecture to install anyway

---

### Post by sysop on 2012-05-02
Just wanted to say, "Thank you!"

I was having the same issue installing Fing 1.4 and the "dpkg --force-architecture" worked perfectly.

---

