---
title: "Major problems with nVIDIA / X - HALP!"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by adamz70 on 2007-03-27
Hey guys, help a noob out!

On another forum I post on, we have an acronym "DAFSFFS". The first part means Do A F---ing Search... you can guess the rest. I have DAFSFFS, and have tried some of your solutions, and Ubuntu will not start. 

Basically, I'm running Ubuntu 6.10 with ye olde nVIDIA Geforce Ti 4200 128mb.

Having gone thru hell on earth getting ADSL and sound working, I ran the popular Envy program to ensure I had the right nVIDIA drivers before proceeding with a Compiz install. Automatix2 had already seemed to have installed nVIDIA drivers, but thought I'd run it anyway.

BIG MISTAKE! Ubuntu failed to restart and I got the ugly "failure to load X server" screen, with the 'no screens found message'. 

I then rebooted in recovery mode and tried "sudo envy" and variations on the options: uninstalling, reinstalling drivers and the other one. 

Then i tried "dpkg-reconfigure xserver-xorg", which along with being confusing did nothing - i tried using nv as well. 

Now when I run Envy it gives me: "build of package nvidia-kernel-source failed" and various other error messages.

Any (simple) suggestions? I've spent an entire night on this, and am now thinking either:
a) try to edit X out of Ubuntu startup scripts (googling has given me nothing on how to modify ubuntu's startup script from terminal in recovery mode)
b) try to boot ubuntu from a live disk and re-install Automatix2's nvidia drivers over Envy's
c) start from scratch  :( 

THANKS FOR ANY HELP YOU CAN GIVE!

---

### Post by tgunner on 2007-03-27
Go into Synaptic, and try installing the nvidia drivers from there. After that, go into your xorg.conf, and change the driver to nvidia. Press Ctrl + Alt + Backspace to restart X.

---

### Post by adamz70 on 2007-03-27
Hi there, many thanks for your help!

I've been to this site: [http://www.nongnu.org/synaptic/index.html](http://www.nongnu.org/synaptic/index.html).

I assume I get "the latest version (bzr)", and figure out a way to get it to run off flash drive from my broken Ubuntu command line... ? I'll do some more Googling and get back with any results in case it helps some other poor fool.

Subsequent efforts to get Envy to 'fix' the drivers - or to get it to revert to my previous (working) setup - have made things worse, I think...

Anyone else have this problem?

---

