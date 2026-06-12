---
title: "Skype Issues"
date: 2010-02-27
forum: Multimedia Software
---

### Post by sHoIoKs on 2010-02-27
After some experimenting, I finally got Skype to work from my machine with 9.10, and my girlfriend's, who is running Windows 7.  In a video chat, I can see and hear her with almost no lag.  In a 4 hour call, I noticed rough spots on her stream maybe 3 times.  However, both on the area where I can view my own stream, and on her machine, my video was very laggy.  I had about a 2-4 second video delay, and the occasional minor audio delay as well.

My specs are:
2.26 Core 2 Duo
4gb DDR3 ram
nVidia 9800m gts 
and a 1.3 megapixel webcam that is built in
I don't know any other info off the top of my head, but i figured those would be the most important.  
I'm also running Cairo Dock, but i made skype's launcher command:
export XLIB_SKIP_ARGB_VISUALS=1 && skype
which I was told would fix any compatibility issues.

I'm using optonline as my isp, with the speed boost package they offer.  I am on a wireless connection, but I am about 30 feet from the router.  

I also noticed that when I go into my skype settigs, and go to video devices, and test my device, the video there is almost flawless.  there is a slight trail on my hand when i wave, but it is milliseconds of delay, at most, nothing like what i am experiencing over a video call. 

I'd greatly appreciate any insight, I'm at a loss with what to do about this. If no fixes exist, could anyone possibly recommend a better video chat program that works between ubuntu and windows 7?

---

### Post by gordintoronto on 2010-02-27
Run system monitor and view the CPU load while you are doing Skype video.  In my experience, Skype video is a major consumer of CPU -- and my (cheap/crummy) webcam produces smaller images.

You might be able to set your webcam to run at 640 by 480. I don't know if that will make a difference.

---

### Post by sHoIoKs on 2010-02-27
well i went back and looked at the test video in skype again, and it actually is pretty delayed.  When using Cheese, the webcam works perfectly, but for some reason even locally skype has an issue with it. 
The system monitor stays around 50% with cairo and compiz on.  When I turn them off, the problem still persists, but the cpu reads at about 20-30&.

---

