---
title: "video glitches on a Dell XPS m1330 (Nvidia GeForce 8400M GS card)"
date: 2008-06-08
forum: Multimedia Software
---

### Post by potiphera on 2008-06-08
Hi, I have a Dell XPS M1330 laptop running Ubuntu Hardy (32-bit generic kernel), and I keep getting video glitches that freeze it.  Basically what happens is that the colors go all weird and then the screen freezes.  Then when I try to restart, the computer does nothing, or at least nothing happens on the screen, until I've rebooted it a dozen or so times.  The video card on this computer is a 128MB Nvidia GeForce 8400M GS.

Originally I had Compiz Fusion and the EnvyNG drivers installed, but after I became aware of the problems, I uninstalled both Compiz and the drivers and then installed the Nvidia driver from linux-restricted-modules.  That didn't solve the problem either, so I also tried two drivers from the Nvidia website: first 173.14.05, and then 169.07 (per the advice [here]("http://ubuntuforums.org/showthread.php?p=4108080&highlight=8400m#post4108080")).  It still didn't work.  Finally I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=797270"), and now I can't seem to get anything to happen beyond the Ubuntu loading screen.  Please keep in mind that I may have done some stuff wrong, as this is only the second computer I've installed Ubuntu on.

A friend says that this sounds like a hardware problem, since after a video glitch, it sometimes takes a lot of rebooting before I can even get the Dell loading screen to work.  But I never had these problems in Windows Vista (although Vista, of course, came with a completely different set of problems that led me to install Ubuntu).  So is there anything else I should try?  How can I ascertain whether it's the hardware or software?  Thanks!

---

### Post by potiphera on 2008-06-09
bump!

---

### Post by squee on 2008-06-10
I HAD the same problem.

First of all back up all your data immediately. If not, sooner.

I had that problem on the vista side of my dual boot when running games. It is the first sign of the gfx card breaking. A friend of mine has exactly the same laptop Hp dv2535ea and had the same problems. He had to get his sent off for repair. 

Im currently searching for a way to back up a harddrive when the gfx card is broken without taking out the harddrive (voids warrantee).

If anyone knows how, please contact me asap.

my own post is here. [http://ubuntuforums.org/showthread.php?p=5156329](http://ubuntuforums.org/showthread.php?p=5156329)

---

### Post by potiphera on 2008-06-10
Thanks for the response!  So I guess I will have to replace the graphics card (and see if it's still under warranty).  The thing is that I can SOMETIMES get into recovery mode and a terminal, but I can never get into Gnome, unless someone can tell me a way to temporarily turn off all fancy video stuff through the terminal so the GUI will start in 256-color mode or whatever it does before you install drivers.  So I guess I'll have to back up data with cp commands in the terminal.  Luckily there isn't that much on there that needs backing up.

---

### Post by squee on 2008-06-10
Have you tried starting in safe mode? Or using the Live CD? That might work since they use minimal graphics and put less strain on the card. I found the my laptop crashed faster on vista than on ubuntu, I presume due to the graphical strain.

Or maybe Ubuntu is just better!

---

### Post by potiphera on 2008-06-10
I wrote over Vista when I installed Ubuntu, as Vista had caused a variety of other problems, so I don't think I can do safe mode... or is there an Ubuntu one that I don't know about?  I have tried the live CD though, and the odd thing is that while it usually doesn't work, often it makes it possible to start the computer again immediately afterwards.  At that point it's still impossible to start the GUI, but I can usually get into a terminal.  I just found [this thread]("http://ubuntuforums.org/showthread.php?t=35087") on backing up a system in the terminal, so I think I'll try that before I call up Dell and find out their policies.

---

### Post by phylae on 2008-06-14
I have the same problem! ([http://ubuntuforums.org/showthread.php?p=5181764](http://ubuntuforums.org/showthread.php?p=5181764))

I am also running a Dell XPS M1330 with GeForce 8400M GS.

I have only only had it crash two or three times in Windows (I rarely use Windows, thankfully). In Ubuntu it will crash far more often. Sometimes I can go all day without a crash; sometimes it will only take a few minutes.

I called Dell support, and they basically said they would ignore the Ubuntu crashes because I installed Ubuntu by myself (can't get Ubuntu pre-installed in Canada). The guy had me reinstall the Vista drivers and because it didn't crash we left it at that.

I guess I will need to run Windows for a while to prove to the dell guys that this really is a hardware problem.

If anyone doesn't think it is a hardware problem, what settings/configuration should we check?

---

### Post by phylae on 2008-06-17
I am getting the same kind of error/crash in Windows Vista. Here is what it looks like:
[http://ca.youtube.com/watch?v=g02hJQ5ZE8w](http://ca.youtube.com/watch?v=g02hJQ5ZE8w)

I am fairly convinced that this is a hardware problem. I have contacted Dell; if I don't post what Dell says/does then send me a private message to remind me :)

---

### Post by phylae on 2008-06-17
> **phylae said:**
> I have contacted Dell; if I don't post what Dell says/does then send me a private message to remind me :)

Dell is sending out a technician to replace my video card. Well actually they need to replace the whole motherboard since it is all one piece.

---

### Post by potiphera on 2008-06-19
Thanks for sharing your experience, **phylae**! Good to know that two other people had the same problem, so it wasn't due to human error on my part.  What happened with my situation was that I called Dell and the guy said that it was either the video card or the motherboard, so we sent it in to the depot (it's within warranty) and they replaced the motherboard.

It seems to be working fine now, but I'm crossing my fingers.  I think all the troubleshooting I did before also messed up xorg.conf or some other configuration, so I went back to the 173.14.05 Nvidia driver.  The only problem is that it made me compile it for the kernel, so it breaks with every kernel update -- so now I'm going to [disable them]("http://ubuntuforums.org/showthread.php?t=242242").

---

### Post by squee on 2008-06-19
Another reminder to any one who gets screen glitches like that...

BACK UP EVERYTHING IMMEDIATELY

on a remote devise too if possible as when you send your machine off for repair they may format the entire drive back to factory defaults. I included a note with mine saying "please do not format" and then a quick explanation of the problem. They didnt format it.

its a lot easier to back up stuff when you can see it on screen than when you cant!

---

### Post by tribaal on 2008-06-19
Does the problem happend on specific events? I have the same models of laptop/GFX card and so far so good... 
I also use the latest driver from envyNG (with the "proposed" repositories enabled - the driver is **173**.14.05).

Compiz fusion runs fine, no lockups.

Can I do anything to help? Or is the issue just bad hardware?

Cheers

- Trib'

---

### Post by phylae on 2008-06-19
> **potiphera said:**
> The only problem is that it made me compile it for the kernel, so it breaks with every kernel update[/URL].

Take a look at [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
You should be able to find it in the repositories.

I am still waiting to hear from the Dell service guys about when they will replace my motherboard. Last night I had it crash while running a backup. I booted from SystemRescueCD ([http://www.sysresccd.org](http://www.sysresccd.org)) and used `dd` to get an image of the hard drive. It was just the command line and it failed. However, it **might** just be that the plug fell out and the battery died!

---

### Post by phylae on 2008-06-23
> **phylae said:**
> Dell is sending out a technician to replace my video card. Well actually they need to replace the whole motherboard since it is all one piece.

The Dell technician came to replace the motherboard today. So far everything is working!

---

### Post by longan on 2010-05-18
Hi there,

I am another victim and a Dell engineer installed a new motherboard for me last month. However, I'm afraid that the 8400M graphics chip of the new motherboard will also die after one or two years. In fact, just yesterday my computer got frozen again after being used for 15 hours continuously.

I have an idea now --- Can my computer's life be longer if using the Windows 7 instead of Windows Vista?

---

### Post by mc4man on 2010-05-18
> Can my computer's life be longer if using the Windows 7 instead of Windows Vista?

I don't think that will particularly matter.. (only based on having 2 1330's from affected time - got in 2008

It may be more a matter of 'luck of the draw' and usage/care (keeping relatively cool

If you're using windows then most likely you'll be using the dell nvidia drivers which probably will be the same for either.

Out of the 2 we have - mine has been fine for 2+ years, been using ubuntu on it for about 2 years and it generally runs cool. While vista is still installed I hardly ever use - when I do it also runs pretty cool - I never updated the dell nvidia drivers.

(I suspect the driver update was designed to help get the laptops thru warranty by running the fan harder.

My son's card delaminated after about 18 months, has been fine since though just last week the lcd was replaced. 

His has always seemed to run a bit hotter from day one, plus I'm not too sure him and his friends pay attention to not block the fan.(and they probably 'stress' it a bit more.

What's not clear is if recent mobo replacements are using the 'known to possibly have a shortened lifespan' chips or better made ones.

I've had a couple of discussions with dell about this - did make the suggestion that since the potential defect was known, widespread and considering nvidia has already set aside funds for replacement then why not just replace them before they failed...
(or at least on mine

They obviously declined to do so though was told just recently that the warranty on the nvidia chip has been extended by 1 yr. ( in our case to 4 years 

So here I figure with a bit of care and luck 4+ years will do. 
( though the whole deal is a bit unfortunate

---

### Post by longan on 2010-05-18
[IMG]http://www.pizza-station.com/GPU-Z_NVIDIA-8400M-GS.jpg[/IMG]

I now use a tool software named GPU-Z to monitor my graphics chip. (See the above attached screen shot picture) The maximum GPU Temperature is 73c so far.

I have NOT run any Flash game since my powering on my M1330 computer today. I am afraid that the Flash game will 'kill' my graphics chip fast.

I don't know why the Fan Speed is always 100%. I don't know if it means the fan over the graphics chip.

And, I am surveying a practical cooling pad. I think maybe the graphics chip can have a long life if I can keep the GPU temperature under about 70c.

---

### Post by longan on 2010-05-23
[IMG]http://www.pizza-station.com/GPU-Z_NVIDIA-8400M-GS__70-to-61_niceCoolingPad_Logitech-N700.jpg[/IMG]

I just bought the Logitech N700 cooling pad. The average temperature is now under 65c, compared to 70c before using the cooling pad.

p.s. Another (expensive) cooling pad without the fan, Waving Cooling Pad, is useless at all.

---

### Post by potiphera on 2010-06-05
Since this thread has been resurrected, I figured I should mention that in my case, Dell replaced like 5 motherboards, then replaced the computer with a Studio XPS 1340.  Then that one started smoking, at which point they couldn't find another 1340 to replace it, so they sent a 1640, which has an ATI card instead.

---

### Post by longan on 2010-06-06
5 motherboards and then 1640. ha ha ha ha. very interesting.

My case also has some update: 

Although with my very good cooling pad, the death blue screen still came out while loading a big Flash (web) game which resulted in almost 80 degree C temperature of the NVIDIA GPU. The system's temperature was low. Only the GPU's temperature went high sharply.

So,

(1). I believe that 80 C is the boundary temperature for this NVIDIA GPU. (according to the NVIDIA spec, the GPU should support more than 100 C )

(2). Unless Dell will also give me a 1640, I have to buy a new computer in the near future, to play some 'big' Flash games or some games with high GPU loading.

---

