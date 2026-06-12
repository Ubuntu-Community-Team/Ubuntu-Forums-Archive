---
title: "Streaming Video Is Choppy...Still. Have Tried Everything I can Find"
date: 2011-05-16
forum: Multimedia Software
---

### Post by CharleyGnarlyP290 on 2011-05-16
I have been messing with Ubuntu for about a week now. Mostly I really dig it, but streaming video is really frustrating me.
I have been using Firefox, since I can't seem to find Chromium that I loaded. the two forms of streaming video I tried were YouTube and Hulu.
They both play videos superbly in the default screen size, but when I switch to full screen, it gets choppy. It is still viewable, but not as smooth as it is on Windows 7.
What can i do to correct this? I have tried a bunch of things from the tutorials I have read, but nothing is working.
I really like Ubuntu otherwise, but don't want to become frustrated, and be stuck with Windows.
Thanks.

---

### Post by walt.smith1960 on 2011-05-16
It could be a lack of CPU or video card capability.  I have a 2002 vintage notebook that won't play flash video at all--it's like watching stop action animation.  I also had an AthlonXP (P4 equivalent) which performed about like yours, it sounds like.  It might be worth running LovingLinux' firefox addon "Flash-Aid" which should make flash perform as well as possible.  You do have to run Flash-Aid from an account with administrative privileges.

---

### Post by CharleyGnarlyP290 on 2011-05-16
Thanks for the reply. 
Would the OS make a difference? In Windows 7 I can play streaming video in full screen, Hi Def video, etc., no problem.
I only have the problem in Ubuntu. And I did load Flash Aid, and it helped some, but still not smooth.
Is this just something one has to live with using Ubuntu? I have read of people getting the problem figured out and streaming working like a champ, I have just had no luck.

---

### Post by snowpine on 2011-05-16
Tell us about your hardware.

And yes, it is well known that the Adobe Flash plugin has higher system requirements in Linux than in Windows, as you can read here: [http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

---

### Post by CharleyGnarlyP290 on 2011-05-16
I did not know about Adobe requiring more system.
Here are my system specs:
AMD Athlon 64 X2 Dual Core 4200+ 2.20 GHz
2.00 GB RAM
Nvidia GeForce 8800 GT 512 MB

I should add that I installed Ubuntu under the impression that my system is 32bit. that is the way I installed Win 7. Does that make a difference?

---

### Post by Shibblet on 2011-05-16
There is an app called MiniTube for Ubuntu that plays YouTube videos flawlessly at whatever screen rez your computer can handle.  It's a work-around, but a great program none-the-less.

It works better, I believe, because it doesn't use flash for video playback.

---

### Post by snowpine on 2011-05-16
> **CharleyGnarlyP290 said:**
> I did not know about Adobe requiring more system.
Here are my system specs:
AMD Athlon 64 X2 Dual Core 4200+ 2.20 GHz
2.00 GB RAM
Nvidia GeForce 8800 GT 512 MB

I should add that I installed Ubuntu under the impression that my system is 32bit. that is the way I installed Win 7. Does that make a difference?

Your specs should be adequate for up to 1080p according to the Adobe page.

However I see you have an Nvidia card, you'll need to make sure you have the correct drivers installed. I am not an expert on Nvidia personally but it is very well documented on the Ubuntu Wiki and on these forums, hope that points you in the right direction!

---

### Post by sgtGarcia on 2011-05-16
It would help if You write what Ubuntu You use ( 11.04/10.10 or other & if it's 32 or 64 bit ), what graphic drivers do You use ( proprietary or open ).

But beside, did You try this :

[http://www.omgubuntu.co.uk/2010/11/force-flash-gpu-acceleration-in-linux-improve-performance/]("http://www.omgubuntu.co.uk/2010/11/force-flash-gpu-acceleration-in-linux-improve-performance/")

---

### Post by walt.smith1960 on 2011-05-16
I agree, that system should have the ability to play flash videos without a problem.  Agree with checking to make sure the Nvidia drivers are enabled.  If there is more than one version listed under "additional drivers" you might try a different one.  Full screen does take more CPU power.  I just played some goofy thing in Youtube.  Windowed it was running 41-45% on both cores.  Full screen looked to be using about 65-70% on both cores.  Of course my system (AMD Athlon(tm) II X2 240 Processor) is set with all the settings auto-no effort to get max performance so CPU % may not be representative but full screen does take more CPU power.  My GPU is an Nvidia 8400GS /w 512.

---

### Post by CharleyGnarlyP290 on 2011-05-16
As far as the Nvidia driver I used there were three options when I loaded Ubuntu and I was downloading drivers. Of the three one had recommended bhind it so that is the one I used.

---

### Post by CharleyGnarlyP290 on 2011-05-20
Simple fix. Switched to Chromium. Problem solved. Streaming video smooth as butter small or full screen.
Thanks for all of the replies.

---

