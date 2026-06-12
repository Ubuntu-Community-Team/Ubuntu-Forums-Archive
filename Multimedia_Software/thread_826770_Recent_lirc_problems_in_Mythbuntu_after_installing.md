---
title: "Recent lirc problems in Mythbuntu after installing updates"
date: 2008-06-12
forum: Multimedia Software
---

### Post by bthoward on 2008-06-12
Ok so I'm an idiot...  After installing updates on my laptop and all was still fine I logged into the mythbuntu box and installed updates w/o really looking via an ssh session.  

After that the video and remote control stuff quit working on me.  After a few quick small tweaks the tv-out and the digital panel was working how I like it again so the computer can be used in the office and myth can be used in the living room without anyone having to worry about the what is going on there.  

However the remote stuff seems to still be having problems.  After a fresh reboot if I run irw I get:

connect: No such file or directory

Now I've googled for this stuff and I've found many people having all sorts of different issues but none of them seem to help out.  The strange thing is if I simply restart lirc "sudo /etc/init.d/lirc restart" and then just close mythfrontend.real and reopen it then all works just fine.  But rebooting breaks things again.

I should mention that I do have a non standard lirc setup.  I have a microsoft MCE ir box in the living room connected to the computer via a USB extension nugget.  Then in the office there is a CommandIR unit which I use to control 4 digital cable boxes.  All of this is working flawlessly including remote translation to do direct control of the cable boxes when needed.  The only issue is that I have to restart lirc and mythfrontend.real everytime the box is restarted.  At the moment I'm going to have to write a script and put it on the desktop to allow others in the house to fix things if I'm gone and they end up having to reboot that machine..  Anyone have any tips and tricks on how to get back to the perfection I once had?

---

