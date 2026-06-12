---
title: "Handbrake crashes"
date: 2010-04-02
forum: Multimedia Software
---

### Post by alexeix on 2010-04-02
Hi, 

I've done a fresh install of Kubuntu 9.10 on a faster machine than my old PC.

Having installed Handbrake (latest version), I've tried to rip a DVD which I own, in order to stream it to my Xbox - less noise, since no DVD spinning in the console.

Anyway, when adding the 'Source' in Handbrake (click on cdrom0, press OK), the application starts running through the chapters and then crashes.
No errors are reported.

I previously tried on my old machine with the same DVD, so I know it should work.

Have I forgotten to install something?  I added VLC as well as Handbrake, so libdvdcss2 is already installed.

After trying a few times with the same result, Handbrake has completely hung, so I will have to re-boot the PC.

Any ideas?

Thanks.

---

### Post by JohnAStebbins on 2010-04-02
Sounds like the problem that was fixed recently with gstreamer plugins.
[http://trac.handbrake.fr/changeset/3166](http://trac.handbrake.fr/changeset/3166)

You can work around it by making sure the gstreamer and it's base plugins are installed.  Or you can build the most recent code from source.  

You need gstreamer and at least the gstreamer-ffmpeg package in order for the live preview feature to work anyway.  It gets disabled if these things are not available.

---

### Post by alexeix on 2010-04-02
I double-checked and kubuntu-restricted-extras (including Gstreamer, I believe), had not installed for some reason.

I tried again several times through the software manager, but it would not install - I don't know why.

Once I used a command in the Terminal, it installed and now I can get past the problem in Handbrake.

Thanks  for pointing me in the right direction! :D

---

