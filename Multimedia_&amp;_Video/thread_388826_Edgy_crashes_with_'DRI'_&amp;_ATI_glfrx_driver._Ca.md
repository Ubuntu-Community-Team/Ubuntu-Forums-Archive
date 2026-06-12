---
title: "Edgy crashes with 'DRI' &amp; ATI glfrx driver. Can't even glxinf!"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by imluxwhoru on 2007-03-20
Hey guys. I came across this one while trying to get Beryl running on my system. I have a dual monitor system with an AGP (BusID 1:0:0) Ati Radeon 9250 & a PCI (BusID 0:9:0) Ati Radeon RX200 (7000) card. I have both screens up and running just fine in Kubuntu using TwinView. Both screens worked just fine, and then I saw a sweet vid on youtube of a guy running a dual monitor setup & Beryl. Well, of course, being the Linux dork I am, I decided I had to do it myself. 

So, I installed beryl, and everything seemed to be fine. But, it wouldn't start up. It gave lots of errors on startup (such as RandR extension not found, and XFree86 extension not found), so I started poking around in my xorg.conf to try and get things going.... I managed to tweak it to the point where I was only getting the RandR error, and I know that means Direct Rendering is screwed up, so I added load "dri" to the modules section, and Section "dri" to xorg.conf

Well I restarted xserver with a coy smile, thinking I had done it, but lo and behold, when I tried to start beryl, the whole system froze. I couldn't even ALT-1 into a terminal! So I rebooted into the GUI and started googleing my problem and before I knew it, the system froze up! And this time I didn't even do anything! So, after another reboot, I decided to check out glxinfo to see what was going on. Well, that was a mistake, because no sooner did I hit enter then my computer froze... again! After yet another reboot, I took the DRI stuff out of my xorg.conf and the freezing stopped. 

*Sigh*

Well, that's all fine and dandy, but now I can't run beryl. I'm currently upgrading to feisty hoping that will solve the problem (I've read a few places that it will) but I've been downloading the update for a half hour, I'm bored, and I thought I would ask anyways. Any ideas?

---

### Post by adam.tropics on 2007-03-20
The trick with this stuff is to get dri etc working properly before you go near Beryl. Trying to solve one problem gets harder each time it's compounded by the next one. 

I would probably (if you're still having problems) start in recovery mode, uninstall beryl etc and then when you reboot, start a non-xgl session (normal gnome/kde) then work on getting dri etc working properly first. (You 'may' need to 'sudo dpkg-reconfigure xserver-xorg' and select another driver to get into x if your problems are serious, try radeon, but vesa is always a safe option)Best guide for that is [here.]("http://wiki.cchtml.com/index.php/Ubuntu") Then once that's all up and runnng have another go at Beryl.

Anyway, how'd the upgrade go?

---

### Post by imluxwhoru on 2007-03-22
So, I finished the Feisty upgrade, and it's great. But, my system still crashes with I glxinfo. So, I decided to try what Adam said, and I tried some new drivers in different combinations on each of my video cards. Every single time... glxinfo still completely freezes the system (When I run if from Konsole my system hangs. No mouse, no keyboards.No alt-F# into a terminal... cant even ctrl-alt-del). But, as always, if I nix the dri from modules, all is good. I tried 'ati', 'radeon' & 'fglrx'. All of those worked just fine until I added dri to xorg.conf. And, I tried 'vesa' as Adam suggested, and my monitor was completely dead. 

I'm not even really tryin' to get beryl up yet. I'm just trying to get dri loaded, and to be able to glxinfo. If that doesn't freeze the system, I know I'll be able to get the rest of the beryl bugs ironed out. I'm just completely at a loss for why glxinfo would freeze up kubuntu with an ati card and dri loaded. Grrrrrrr.

> Anyway, how'd the upgrade go?

Anyways, Feisty is runnin' great (I even loaded it on my uber-crappy laptop). And while I was poking around in the repositories I stumbled unto UbuntuStudio. For anyone doing Audio (engineering, recording, midi, yadda yadda) or Video editing, it's amazing. And sense I run a Music Store & a recording studio, I'm blown away. Finally, I can totally squash windows from my hda! 

So, anywhoo... And ideas on the dri thing?

---

### Post by adam.tropics on 2007-03-22
So exactly where are you at now. You have a fresh Feisty (good stuff!), did you install fresh or upgrade from where you were. If upgraded, did you change your startup back to non xgl. Which driver are you using? (atiI, fglrx, radeon) . The fglrx is certainly your best bet for dri. (dri will not show up as running by the way if you are in an xgl session, it will only 'currently' work in a normal xorg session, though it shouldn't freeze your system either!)

I have attached my xorg.conf. Clearly don't use it as is, but have a look through. That works fine for dri in an xorg session, and xgl runs fine with it for Beryl. It's not dual monitor though, but may give you some clues.

---

### Post by imluxwhoru on 2007-03-22
Hmmm. Now we're talkikn'.

I'm currently running Feisty from an upgrade (yes, good stuff), on a non-xgl session. Now, insterestly enough, I've never been able to get a xgl session to work right. When I try to log into the xgl session from the logon, it will either crash me back to the logon screen, or crash completely (Although I can still Alt into terminal to reboot).

Now, way back when I was just running one monitor & beryl, I was able to get beryl up without actually running an xgl session. I'm not exactaly sure how I did it (I was still quite the n00b) but with a little coaxing I could get it up. So, I know it's possible on my computer with my configuration. It's just a matter of getting it to work dual monitor style. And I know it's the dual Ati card config that's making dri freeze when I glxinfo, or anything else that calls on direct rendering. Dang you Ati and your closed source drivers!

And, it gets better. I've read that Ati cards hate the 'Composite - enable' string in the extensions section of xorg.conf. And, I noticed that you have yours disabled in your xorg.conf, Sooo... How do you get beryl running with that setting? Every time I try to run  beryl without Composite enabled, it yells at me, and threatens to kill my dog unless I enable it.  I know, that's another problem altogether, but how'd ya do it? It might be handy to know just in case I decide to boycott ati and go get a pair of NVidia cards.

And thanks for actually responding (in a hurry too!!). Yet another reason why Ubuntu kicks butt, people actually care!!

---

### Post by adam.tropics on 2007-03-22
> **imluxwhoru said:**
> 

And, it gets better. I've read that Ati cards hate the 'Composite - enable' string in the extensions section of xorg.conf. And, I noticed that you have yours disabled in your xorg.conf, Sooo... How do you get beryl running with that setting? Every time I try to run  beryl without Composite enabled, it yells at me, and threatens to kill my dog unless I enable it.  I know, that's another problem altogether, but how'd ya do it? It might be handy to know just in case I decide to boycott ati and go get a pair of NVidia cards.

The 2 options  for composite are xgl, or aiglx. Aiglx has certain driver requirements, hence you need it enabled in xorg.conf. Xgl runs on top of a normal xorg session, I guess you could think of it as an extra layer. It doesn't require composite enabled in xorg.conf. Anyway, could you point me to the guides you have used. It may be easier to figure this thing out that way. Also, have a look in the file I attached at the Device section. If you are using fglrx, the extra line in there is there to actually stop a freezing issue I had.
> 
And thanks for actually responding (in a hurry too!!). Yet another reason why Ubuntu kicks butt, people actually care!!Welcome.

---

