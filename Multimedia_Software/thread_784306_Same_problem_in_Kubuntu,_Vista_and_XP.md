---
title: "Same problem in Kubuntu, Vista and XP"
date: 2008-05-06
forum: Multimedia Software
---

### Post by ynnek63 on 2008-05-06
Here is an interesting problem I have been having when looking at xtube:

OK...spare me the judgment, I do look at xtube on occasion.
Here is my problem. I have recently built a new computer (specs are below). It worked fine for about a month. Then suddenly it started having random crashes and BSOD in both XP and Vista Ultimate. When I would boot back up, Windows would tell me I have recovered from a serious error and when it returned the error report, it suggested my RAM was bad.So, I ran memtest86 on each 1Gig module individually and sure enough, one RAM module was bad. I numbered each one beforehand. I thought problem solved, but I still kept having serious crashes. I installed and reinstalled various OSes and Linux seems to be the most stable now. Well, I had noticed early on that when watching vids in xtube, it caused Xp to lock up tight. Had to hold the power button in to shut it down. So, I rebooted, tried it again, same thing. OK, this is interesting, no other "tube" sites like youtube or google video caused this, just xtube. So, I booted into Vista and tried xtube. I was amazed when it locked up tight! The next time I tried it in Vista, I got a BSOD. Tried again, locked up tight. So, I decided to reformat my hard drive and install Kubuntu linux, the newest 8.04. I decided to try xtube again just to see, and to my amazement, it locked my linux OS up tight! Now on XP and Vista, it locked up whether I was using Explorer or Firefox and in linux, I am using firefox. So, what gives here? What could be wrong with my system that would cause lock-ups in three different OSes? It must be hardware related. Any thoughts? Now, I am not that concerend about looking at xtube, so just spare me the jokes. ;) It's just that with xtube, it WILL ALWAYS lock-up regardless of which OS I am using, so it is easily reproduced. I just want to know what is going on. I have never seen anything like this problem.

I have looked in the system logs in KDE and nothing shows up as far as any lock-ups are concerned. It's as if nothing happened.

Here are my specs:
Asus M2N32-SLI deluxe Wireless edition MoBo
eVga (nvidia) 8800GTS 320MB graphics card
4 1Gb sticks of Crucial ballistic PC6400 RAM (only 2Gb installed)
400GB WD SATA HDD
AMD Athlon X2 6400+ CPU
Antec True Power Trio 550W Power supply
Lite-On DVD/CD burner
The OS's I have used have been 32bit.

BTW...I updated my BIOS with a new rev today to see if that helped. It didn't. I have also checked all the BIOS settings.

Any thoughts or suggestions would be greatly appreciated.

---

### Post by kebes on 2008-05-06
I'm assuming the sites that cause crashing all use a flash-based video player. Is that true? That might explain why the problem occurs on all three platforms. If so, you could try using a different flash player.

On Linux, at least, you can use the the Adobe-provided flash-nonfree (which is probably what you're using), but you could also try using gnash (mozilla-plugin-gnash), or libflash-mozplugin, and see if that works better.

However, getting a full system freeze on all 3 operating systems strongly suggests that it's a hardware issue. In Kubuntu, when it freezes, can you use Ctrl+Alt+Backspace to reset X Windows? (Or does the computer only respond to a hard reset using power switch?)

---

### Post by ynnek63 on 2008-05-06
> **kebes said:**
> I'm assuming the sites that cause crashing all use a flash-based video player. Is that true? That might explain why the problem occurs on all three platforms. If so, you could try using a different flash player.

On Linux, at least, you can use the the Adobe-provided flash-nonfree (which is probably what you're using), but you could also try using gnash (mozilla-plugin-gnash), or libflash-mozplugin, and see if that works better.

However, getting a full system freeze on all 3 operating systems strongly suggests that it's a hardware issue. In Kubuntu, when it freezes, can you use Ctrl+Alt+Backspace to reset X Windows? (Or does the computer only respond to a hard reset using power switch?)

It only responds to a hard reset using the power button. The keyboard is locked up tight.
 
If it is a hardware issue, what piece of hardware might it be? I have ran memtest86 for 12 hours straight on the remaining 2 gigs of RAM with no errors.

Even if it is a hardware issue, it seems odd that it would present itself in the same way across three different OSes and multiple reformats and reinstalls. Could the BIOS be corrupt somehow? Even after a reflash?

On a side note, when I tried to play a high def (.mkv) Speed Racer trailer in mplayer, the system locked up and I had to do a hard reset. that might have just been a random thing though.

Is there some type of diagnostic software for Linux that I could run on my system?  

I'll try the flash alternatives you suggested and see what happens.

Thanks for the reply.

---

### Post by mc4man on 2008-05-06
i would take a look at the memory timings, and also see if there are any settings in bios concerning epp

---

### Post by ynnek63 on 2008-05-06
> **mc4man said:**
> i would take a look at the memory timings, and also see if there are any settings in bios concerning epp

epp? I think that is for the parallel port. You mean ecc? This memory is non-ecc and ecc is disabled in the BIOS. The timings are correct.

Thanks for your response!

---

### Post by ynnek63 on 2008-05-06
> **kebes said:**
> I'm assuming the sites that cause crashing all use a flash-based video player. Is that true? That might explain why the problem occurs on all three platforms. If so, you could try using a different flash player.

On Linux, at least, you can use the the Adobe-provided flash-nonfree (which is probably what you're using), but you could also try using gnash (mozilla-plugin-gnash), or libflash-mozplugin, and see if that works better.

However, getting a full system freeze on all 3 operating systems strongly suggests that it's a hardware issue. In Kubuntu, when it freezes, can you use Ctrl+Alt+Backspace to reset X Windows? (Or does the computer only respond to a hard reset using power switch?)

I tried the libflash-mozplugin and used the Konqueror browser and it did actually let me play a couple vids on xtube, but on the third one it locked up tight. On a second attempt it locked on the first vid.

---

### Post by ynnek63 on 2008-05-06
I tried a different graphics card to no avail Still locked up on me.

---

### Post by kebes on 2008-05-06
You mentioned that you removed some RAM sticks because they gave errors during a memtest. If I were you, I would run more memtests on all of the RAM sticks.

If they give inconsistent results (you get an error on one scan but not the next), then my guess would be that the motherboard is broken (maybe it's the RAM slots, or the memory controller, etc.).

---

### Post by ynnek63 on 2008-05-06
> **kebes said:**
> You mentioned that you removed some RAM sticks because they gave errors during a memtest. If I were you, I would run more memtests on all of the RAM sticks.

If they give inconsistent results (you get an error on one scan but not the next), then my guess would be that the motherboard is broken (maybe it's the RAM slots, or the memory controller, etc.).

I'm beginning to think it's the motherboard myself. I was just messing around in the BIOS. I decided to set the DRAM timings to auto where-as before I had set the timings myself. According to the Crucial website, my timings should be set at 4-4-4-12, but on auto the motherboard selects 5-5-5-18. I am pretty sure in the past it had selected to correct timings. 

I guess I'll contact newegg and see about getting an RMA for the mobo.

---

### Post by mc4man on 2008-05-06
> epp? I think that is for the parallel port
epp is Enhanced Performance Profiles which is supported by your mobo (with sli compliant memory) Short info [http://www.simmtester.com/PAGE/news/showpubnews.asp?num=151](http://www.simmtester.com/PAGE/news/showpubnews.asp?num=151)
your system seems unstable - memory is usually the best place to start
In the JumperFree configuration is A1 tuning set to manual (vs. auto)

---

### Post by ynnek63 on 2008-05-06
> **mc4man said:**
> epp is Enhanced Performance Profiles which is supported by your mobo (with sli compliant memory) Short info [http://www.simmtester.com/PAGE/news/showpubnews.asp?num=151](http://www.simmtester.com/PAGE/news/showpubnews.asp?num=151)
your system seems unstable - memory is usually the best place to start
In the JumperFree configuration is A1 tuning set to manual (vs. auto)

ahhh...ok. Sorry about that. But I do have all the OC stuff disabled. One interesting thing I just noticed. As stated in my last post, the auto timing setting for the mobo would choose the wrong memory timings. I went ahead and let it boot up with the wrong settings and when I played a vid no lockup! Now I know the crucial website calls for 4-4-4-12. I just checked for part number BL2KIT12864AA804. But the motherboard selects 5-5-5-18. Whats' up with that?

---

