---
title: "Fullscreen Hulu is &quot;jumpy&quot;"
date: 2009-05-31
forum: Multimedia Software
---

### Post by the_joey_o on 2009-05-31
I've been searching the forums for a while now, and I can't find a solution to the jumpy fullscreen problem with Hulu. So, I have 2 questions:

My first question is: Has anyone found a solution to this problem? 
(I've already installed Flash and Java. I've also installed the non-free flash plugin. I've uninstalled gnash. I've reinstalled all flash related packages. And, I've turned off all visual effects. I did some other things that I cannot remember at this moment too.)

My second question is: If noone has found a solution, has anyone found a workaround?
(For example: Is this a firefox only problem? Has anyone found that the problem doesn't occur in Opera or another browser? Does the problem go away playing hulu through a media center? etc.)

---

### Post by overdrank on 2009-05-31
Hi and welcome, what is the model of the graphics card and I assume you have the drivers installed as you are able to use the desktop effects?

---

### Post by the_joey_o on 2009-05-31
> **overdrank said:**
> Hi and welcome, what is the model of the graphics card and I assume you have the drivers installed as you are able to use the desktop effects?

Actually, I do not have any proprietary drivers installed. The effects worked nonetheless. I normally know my system's info like the back of my hand, but I'm working with my wife's tablet PC. I'm not sure how to go about finding my system's info in Ubuntu other than through a System Test (and then I'm not 100% sure what I'm looking at). So, can you walk me through where to find that info and perhaps update my driver(s)?

---

### Post by overdrank on 2009-05-31
Hi and you may use the command ```
lspci | grep VGA
``` in the terminal which is located under applications, accessories. This will identify your graphics.
Also which version of Ubuntu are you using, Jaunty 9.04? This can be found under system, about Ubuntu.

---

### Post by the_joey_o on 2009-05-31
My video card: 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

I'm using Jaunty 9.04.

---

### Post by overdrank on 2009-05-31
> **the_joey_o said:**
> My video card: 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

I'm using Jaunty 9.04.

Ok you may look at the link in my signature about intel graphics in Jaunty.

---

### Post by the_joey_o on 2009-05-31
> **overdrank said:**
> Ok you may look at the link in my signature about intel graphics in Jaunty.

Worked like a charm. Thanks!

---

### Post by auroraborealis on 2009-07-06
Is there an equivalent solution for Nvidia cards running the proprietary drivers (rev 180)?

Edit: I don't have any visual effects enabled and I have a 3GHZ dualcore Opteron/4GB RAM.

---

### Post by Tteddo on 2009-07-07
How about ATI cards running the proprietary driver? I am running MythTV (XBuntu) and everything is great except for Hullu in full quality/screen mode. It pauses every few seconds.

---

### Post by caeroe on 2009-07-09
I'm a unique case I guess.  Everyone has issues with Intel and ATI hardware.  I have issues with Nvidia.

I thought I found a solution on the x64 subforum, but it was shortlived.

AMD 64bit Desktop with Nvidia 8800GT 512mb card:  Fullscreen Google video runs fine.  Fullscreen Youtube is horrible and takes forever to exit out of.  Fullscreen Hulu doesn't (nearly) freeze me, but is unwatchable.
Tried disabling effects, using Fluxbox, trying Flash non-free, 64bit alpha software.... nothing worked (satisfactory) in any browser.

AMD 64bit Notebook with dedicated ATI 64mb card:  Everything runs great, including fullscreen.  Great, considering the weaker system.

Both with 9.04 64bit.

---

### Post by pete on 2009-08-18
Fwiw, leaving the Hulu vid in the standard browser window and then using  Compiz "Enhanced Zoom Desktop" has turned out to be a pretty reasonable work-around for me w/nvidia drivers.

---

