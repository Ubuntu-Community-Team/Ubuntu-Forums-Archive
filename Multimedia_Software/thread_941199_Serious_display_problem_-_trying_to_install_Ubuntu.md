---
title: "Serious display problem - trying to install Ubuntu 8.04"
date: 2008-10-07
forum: Multimedia Software
---

### Post by titan441 on 2008-10-07
Hi, I'm trying to install Ubuntu on my T500 thinkpad that already has Vista. I defragmented the disk with vista and then rebooted with ubuntu CD. At this point everything is ok, I select install ubuntu, and after a moment I see a window with the peach color ubuntu background behind. The problem is that I can see anything, the screen is all messed up, it looks a bit like the screen would have been cut into many horizontal and vertical slices and then superposed. Its hard to explain, but it is very WEIRD. Impossible to complete installation cuz I can't read anything that seems to be written. I can see the pointer and I can move it, I can barely see my selection change when I press tab. It looks like everything works well and that the problem is limited to the display. 

The CD is ok, it works on my other comp. here are my computer specification. could it be a drive problem?

Intel Core 2Duo P8400
15.4" WXGA TFT
Intel GMA X4500
2 GB RAM

I'm new with linux, please help me!

Thank you!!

---

### Post by titan441 on 2008-10-07
Hi, I'm trying to install Ubuntu on my T500 thinkpad that already has Vista. I defragmented the disk with vista and then rebooted with ubuntu CD. At this point everything is ok, I select install ubuntu, and after a moment I see a window with the peach color ubuntu background behind. The problem is that I can see anything, the screen is all messed up, it looks a bit like the screen would have been cut into many horizontal and vertical slices and then superposed. Its hard to explain, but it is very WEIRD. Impossible to complete installation cuz I can't read anything that seems to be written. I can see the pointer and I can move it, I can barely see my selection change when I press tab. It looks like everything works well and that the problem is limited to the display.

The CD is ok, it works on my other comp. here are my computer specification. could it be a drive problem?

Intel Core 2Duo P8400
15.4" WXGA TFT
Intel GMA X4500
2 GB RAM

I'm new with linux, please help me!

Thank you!!

---

### Post by titan441 on 2008-10-07
Hi, I'm trying to install Ubuntu on my T500 thinkpad that already has Vista. I defragmented the disk with vista and then rebooted with ubuntu CD. At this point everything is ok, I select install ubuntu, and after a moment I see a window with the peach color ubuntu background behind. The problem is that I can see anything, the screen is all messed up, it looks a bit like the screen would have been cut into many horizontal and vertical slices and then superposed. Its hard to explain, but it is very WEIRD. Impossible to complete installation cuz I can't read anything that seems to be written. I can see the pointer and I can move it, I can barely see my selection change when I press tab. It looks like everything works well and that the problem is limited to the display.

The CD is ok, it works on my other comp. here are my computer specification. could it be a drive problem?

Intel Core 2Duo P8400
15.4" WXGA TFT
Intel GMA X4500
2 GB RAM

I'm new with linux, please help me!

Thank you!!
titan441 is online now Report Post   	Edit/Delete Message

---

### Post by pieisgood4589 on 2008-10-07
What graphics card does your other computer have? It's interesting that the graphic error starts only when you begin installing... Try starting the LiveCD with the option "Start in Safe Mode."

---

### Post by titan441 on 2008-10-07
Its a Gforce 8600 GT, but Ibefore installing unbuntu on my laptop, I tried the "try ubuntu without any change to my computer"(or so) and it did the same thing, I rebooted and clicked "install ubuntu" thinking that once installed it might not do it.

:|

---

### Post by Athanasius on 2008-10-07
it is quite possible that ubuntu is not compatible with your graphics card yet.  You might try 8.10 when it comes out at the end of the month.  You could try it now but it is still in development and not quite stable yet.

---

### Post by Nasaki on 2008-10-07
Hmm...my room mate has that same chipset, with that same problem. I have heard that 8.10 beta should help you with your problem, but don't quote me.

The other thing you could do is compile the latest Intel Graphics drivers from their [site]("www.intellinuxgraphics.org/"). Obviously, you would do this from another computer (live cd will work fine). Intel drivers are a pain to compile but read the "README" file and you should be Ok. 

Best of luck.

---

### Post by cariboo on 2008-10-08
Before you try installing beta software on you laptop try starting the LiveCD in safe graphics mode. At the menu screen press F4 and select safe graphics mode. I wouldn't advise trying 8,10 if 8.04 won't load with out options.

Jim

---

### Post by titan441 on 2008-10-10
I'll try that, thanks, I'm happy I'm not the only one with this problem

---

### Post by titan441 on 2008-10-10
WOW! it actually works. But now what do I do, I can't run it into save graphic mode foreever? thanks for answering

---

### Post by titan441 on 2008-10-10
Hi, I want to install ubuntu, but the only way I get it to work when I click "try ubuntu without any change to my computer" is to boot it into safe graphic mode. If I boot it normally, the screen is all messed up and i can't see anything. I can't boot into safe graphic mode forever...Is there a way to make it work on default start settings?

my graphic card is an Intel GMA X4500

I'm new with linux and I really don't know what to do..plz help me!
Thanks a lot!!!

---

### Post by phidia on 2008-10-10
Open a terminal from Applications > Accessories and try this command:

> sudo dpkg-reconfigure -phigh xserver-xorg

If that doesn't work you may need to edit your /etc/X11/xorg.conf

Note: I'm guessing threads were merged as this isn't the post I responded to.

---

### Post by Pumalite on 2008-10-10
You could save the xorg.conf file of your Live CD and later replace your xorg.conf of the installation with the one you have saved.

---

### Post by thiefunu on 2008-10-17
i have the same problem i tried to install Ubuntu , Kubuntu , Suse but no result , i have an **Intel GMA 3100** video card ( integrated ) is there any other resolve for this problem ? :(

sorry for my bad english !

---

