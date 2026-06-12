---
title: "System recognizes only one video card"
date: 2009-11-02
forum: Multimedia Software
---

### Post by jeukel on 2009-11-02
Hi! :D Been here a lot but this is my first post so...on to basics... I just upgrade to karmic koala and been already through x64 and i386 platforms... First because i had problems with my wireless and my video. Because i386 is more often used, i, with my head down, left x64 for a platform of 32bits... Now, in i386 i face the same as i did in x64. The video works fine (It has an output and all) but, with:

lspci

it shows me only one video card when i have tow video cards installed. They are RadeonHD 3870 using the propietary driver. Even with 

aticonfig --lsa 

it still shows me only one device... I thought it might be that the system blacklisted the card but it would mean that it would be the driver but i have video output so, it wasn't. The fan of my second video card it's about to get me crazy cause it's working at 100% of its speed and since the system it's unable to see the card it self, i can't go into any tweaking... I know that out there they are more serious collateral damages but it would be very appreciated if someone could help me figure out why the system it's making blind of my second video card.

---

### Post by jeukel on 2009-11-03
:popcorn: I believe on ubuntu as a gaming machine that's why i wanna find out everything about its configuration regarding video and sound... Anyone? Please... Been over the net and cant find a thing...:(

---

### Post by red13 on 2009-11-03
First I would drop the ati drivers and get the drivers in the repositories or instal envy.If then they don't both work I would try pulling the one that works and botting with the nonworking one in the original slot don't move it.If I got video then I would know that its not hardware but software.
I would then put the other one in and boot to see if they both show up.
Then if still unsucsessful I would just use the one and keep searching for answers.

---

### Post by jeukel on 2009-11-03
Thanks Red, I'll then answer to part of what you said. I'm using the ati drivers cause the repositorie ones give me already the same issue. Now, already installed envy and apparently it says everything works fine. I know that is software cause i'm booting on vista x64 and it doesnt give me any issue like the one i presented here (still vista so.. hahaha)... But the main thing is that both cards worked fine for me... Besides, on 8.10 i386 it worked just fine so... But still i;ll try to boot only with the second one and let you know... thanks again.

---

### Post by jeukel on 2009-11-03
Mmmm... funny, did what you said and didn't start X. Startup dropped at login on the black screen. It was the same bug that it gave me with 9.10 Beta. The only way to make it work was removing the second card out and it worked fine, I though that it was because of being beta. Also it blinks and i could even login because apparently the system doesn't get the keys of the keyboard when pressed. :s... It kind of disturbed me...

---

### Post by markbuntu on 2009-11-03
Have you tried

sudo aticonfig --adapters=all --initial -f

If those are 3870x2 cards the release notes say they they are specifically not supported but the other 3870s are.

You may have a pci id conflict with the cards having the same address, you should check your bios..

---

### Post by jeukel on 2009-11-09
Havent try that one, i will markbuntu. Mines are not x2 but i encountered one hardware problem with the card and for now i cant continue this thread... Thanks for now, i'll solve the issue an then repost to say resolved or not... ;)!!

---

### Post by jeukel on 2010-09-28
Well, centuries later I re-post to tell what happend in the end.
The problem I wrote about started little bit later after i opened the fan's cover for a clean up. In the process the damned heat-spreader broke... It was as we call it, pasted with "snots"... So, in the end, the only screws that were holding the card were all the others but the ones that are close to the gpu chip (overheating).
At last, ressently i bought a water cooling system for the card and its been workin pretty good. I'm running ubuntu 10.04 and just enabled the crossfire link succesfully. Guess the threat it's over on the side of recognizing the card and now i've got the problem that i cant read the temp in the second card... :P! d'ouh!

---

