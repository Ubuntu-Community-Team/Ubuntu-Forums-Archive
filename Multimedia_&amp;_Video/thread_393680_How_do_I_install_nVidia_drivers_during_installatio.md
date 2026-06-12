---
title: "How do I install nVidia drivers during installation"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by Buk on 2007-03-26
Ok before somebody gets on my case for posting a new thread for something everyone here seems to have posted to death, let me explain...

I want to install Ubuntu 6.10 64 bit version but I don't seem to understand how you are installing a nVidia video driver at the same time Ubuntu is being installed from the cd.

I can't install Ubuntu to my system without a video driver because when Ubuntu loads my screen is "scrambled".  Ubuntu is loaded because I hear the startup tune.  I just can't see anything except a bunch of vertical lines.  I've tried all of the installation graphics modes and safe graphics mode.  Makes no difference.

I see in a lot of these threads to edit a file called xorg.  But how can you edit a file on a cd-rom?  I can't edit it on my hard drive because I can't get that far into the installation to get the system installed.

I've tried various things that I've found in various posts here but nothing has worked.  Most assume that I'm working with Ubuntu installed and are trying to install video drivers to the installation on the hard drive.

My system has a Gigabyte nForce4SLI GA-K8N Pro-SLI motherboard, AMD Athlon 64 X2 4200+ dual-core processor, 2Gig DDR400 memory and an eVGA e-GeForce 6800GS graphics card.  I'm trying to install Ubuntu to a SATA drive that is a "sub drive" on the system.  The main/boot drive is a UATA-133 formated with Windows XP Professional installed on it.  

Can somebody point me in the right direction here?  Am I doing something wrong?

Buk

---

### Post by daynah on 2007-03-26
I'm gonna ask some more questions just so I know exactly where you are in the process, okay?

This is the ideal situation: You pop in a cd. Ubuntu asks some keyboardy questions and starts running (will make a noise) off of the cd and you will see a desktop. Then, you click on an icon on the desktop ("install" or something") and Ubuntu asks you more questions about partitioning and such and it begins installing. You reboot and it makes the sound again as you log into ubuntu.

Can you tell me where you stopped, where it started getting scrambled? (basically, I can't tell by your post if it was the first log in chimes or the second :) )

Did you ever see this... [http://i71.photobucket.com/albums/i136/beefaroni5/2.png](http://i71.photobucket.com/albums/i136/beefaroni5/2.png)

If it is what I think it is (and we're all thinking it's your xorg) try this. This is what I did while I installed ubuntu off of my live cd, except it was for ATI, and I saw screen I saw above. I don't know when you'd start pressing these buttons if you're not getting that screen so... Try it?

Ctrl + Alt + F1 (This opens the "big scary void hacker" terminal when things go wrong)

Then do this... [https://help.ubuntu.com/community/NvidiaPCI](https://help.ubuntu.com/community/NvidiaPCI)

---

### Post by Buk on 2007-03-26
I start the computer with the cd in.  The initial Ubuntu screen appears.
It has 5 options midscreen:
1. Start or Install Ubuntu
2. Start Ubuntu in safe graphics mode
3. Check CD for defects
4. Memory test
5. Boot from first hard disk

Options 3,4 and 5 work fine.  If I use either option 1 or 2,  Ubuntu begins to load.  The Ubuntu logo will remain on the screen.  With option 1 that's all that is on the screen.  With option 2 it looks like it's trying to display a bar to indicate how far along the loading process has gone.  But it only half displays with a bunch of dots on the right of it.  In either case the screen will then display (after a minute or so) several hundred (a guess) vertical lines.  Soon after those vertical lines appear I hear the Ubuntu tune.  Once I've heard that tune, loading is complete but I can't see anything (except vertical lines).  There is no mouse or anything that moves when the mouse is moved.

I have a little bit better luck with the 32-bit version of Ubuntu.  With that version and some finessing I can get all the way to the Ubuntu "desktop".  With that version I have no visible mouse or maybe I should say that I have an invisible mouse.  That version will usually lockup after a few minutes while trying to open menus with the invisible mouse.  

But I have a 64-bit machine.  I don't want to mess with trying to load the 32-bit version.  I just tried it out to see if it loaded any better.  I guess it did but not by much.

I don't know if it makes a difference but my graphics card is a PCI-e card.  I noted some posts referring to AGP cards but didn't notice anything for PCI-e.  I see one of the links in your response it talks about knowing which slot the graphics card is installed in.  Well my motherboard is SLI capable so it can have up to 2 PCI-e cards with a SLI bridge.  Of course I only have one card and it's in the 1st slot available for the graphics card.
***********
"Did you ever see this... http://i71.photobucket.com/albums/i136/beefaroni5/2.png"
No.  

Thanks for your reply.

Got any ideas?

---

