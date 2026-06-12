---
title: "This distro is realy starting to p!$$ me off!"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by OldGaf on 2007-04-13
**************************************************************************************************************************************************

Issue 1 - lost "out of the box" wireless support on Kernel update from  2.6.17-10 to 2.6.17-11.... never came back.
Issue 2 - Sound went away. Found easy solution, but was never "fixed"
Issue 3 - Xorg freezes system....... on going.    [Here]("http://ubuntuforums.org/showthread.php?t=593607") and [here]("http://ubuntuforums.org/showthread.php?t=587905")

***************************************************************************************************************************************************

First of all, let me say I love linux and will never go back to winblows.

But,......  why the HELL do we keep loosing support for devices every time u/kubuntu releases a new kernel???????]

I have an Audigy 1 card. It worked great with both dapper and edgy. No fiddling........ no messing...... no tweaking...... it just worked...... 4.1 sound.

Now I have moved to Feisty and the card is detected and......... no sound! ](*,) 

OK, I know what some of you are going to say... "It's still beta, it's not done yet, chill out OldGaf"

NUT's TO YOU! I say. :-x 

This card is NOT brand new, it is well supported under linux. Nor is this card so old that it should no longer be supported. HOW FREEKIN HARD IS IT TOO MAINTAIN SUPPORT FOR A BASIC FREEKIN DEVICE BETWEEN KERNEL UPDATES?????? 

This is not the only sound issue I have had lately. I have been building PVR boxes for the last 6 months. In that time I have purchased at least 6 different flavors of motherboard with different chip sets trying to get one that worked as good as the Audigy 1 did...... I don't think it can be done with this distro now. When I do get sound, I only get 2 speaker stereo, and usually out of the headphone or line out channel. This is crazy. How long have they been making PC's with sound eather built in or with addon cards??????  I know that not every chip set will work and that linux is still not as good as winblows for driver support but come on......

If this distro wants to be THE distro to sway the masses away from winblow (or at least some), then at least make sure it can do the basics.

1) Video       (not even 3D..... just good video support)
2) Sound      (I don't mean 7.1...... just working stereo)
3) Internet   (Nic support, browser, java, flash)

That's it.....  3 BIG things. The rest is gravy. 
I could not care less how pretty the latest splash screen is if I can't get any sound out of my speakers, or my internet won't work today because I updated my kernel last night.

Don't get me wrong, I don't expect that all hardware will be supported. I don't expect that any software I could ever want will be available. I just expect that if It worked last year, last week, last night, with this distro, that it will today, tomorrow, next week and next year.

It is getting harder and harder to get people intrested in linux when it should be getting easier. I will soon have to find another distro to call home........ that is a very sad reality.

Thank you for taking the time to read my rant...... I feel better all ready.

---

### Post by taurus on 2007-04-13
Did you look to see if you have turned on the volumes for your soundcard?

```
alsamixer
```

---

### Post by daniel of sarnia on 2007-04-13
You should post a bug on [https://launchpad.net/](https://launchpad.net/) so this regression can be fixed. That's why their are beta tests. So new features can be stabilized and to fix any regressions that are a side effect from the new code base.

---

### Post by OldGaf on 2007-04-13
> **taurus said:**
> Did you look to see if you have turned on the volumes for your soundcard?

```
alsamixer
```

Thanks for your rely....... 

Yes, all channels are unmuted and volumes are up. If I turn the volume all the way up on the amp I can hear faint sound from the line out but is is very crackly. In edgy I never go above a third volume.

---

### Post by Slipmyknot101 on 2007-04-13
Lol not to play devils advocate here or anything but according to the second law of thermodynamics, disorder tends to increase with time when referring to a macroscopic object (such as a new version of linux.) It will take time but the errors will be solved. I think sound and sound specifically is something a whole lot of folks are going to have problems with when upgrading to Feisty...sort of like how the whole Broadcom wireless card was with earlier versions of Ubuntu. 

Yeah, so just to add to the main point made in this thread, I too am having sound card trouble. Though I think the problem is with the detection of the control buttons on my laptop.

Yes, I can feel your pain (not figuratively though).

---

### Post by hardyn on 2007-04-13
> 
If this distro wants to be THE distro to sway the masses away from winblow (or at least some), then at least make sure it can do the basics.

1) Video (not even 3D..... just good video support)
2) Sound (I don't mean 7.1...... just working stereo)
3) Internet (Nic support, browser, java, flash)


this has been discussed as 'restricted software' ad nauseam.  flash and java are available.
  
developers hands are tied as far as hardware goes, if a hardware company will not release programming specs. not much can be done; there are good reverse engineering projects, but the are long and difficult in the development.


I do believe you may have a point with the sound card though, the regression at all,.  as stated above, the developers do not check here, please post bugs to the launchpad.

---

### Post by OldGaf on 2007-04-13
> **daniel of sarnia said:**
> You should post a bug on [https://launchpad.net/](https://launchpad.net/) so this regression can be fixed. That's why their are beta tests. So new features can be stabilized and to fix any regressions that are a side effect from the new code base.

Done!

Bug #106380, first reported 0 seconds ago by OldGaf

[https://bugs.launchpad.net/ubuntu/+bug/106380]("https://bugs.launchpad.net/ubuntu/+bug/106380")

---

### Post by OldGaf on 2007-04-13
> **Slipmyknot101 said:**
> Lol not to play devils advocate here or anything but according to the second law of thermodynamics, disorder tends to increase with time when referring to a macroscopic object (such as a new version of linux.) It will take time but the errors will be solved. I think sound and sound specifically is something a whole lot of folks are going to have problems with when upgrading to Feisty...sort of like how the whole Broadcom wireless card was with earlier versions of Ubuntu. 

Yeah, so just to add to the main point made in this thread, I too am having sound card trouble. Though I think the problem is with the detection of the control buttons on my laptop.

Yes, I can feel your pain (not figuratively though).

Another saying comes to mind:

If it ain't broke.....

Sigh...... at least I am not alone. Thanks for feeling my pain...... I was getting tired of feeling it myself :wink:

---

### Post by findik1 on 2007-04-13
> **OldGaf said:**
> First of all, let me say I love linux and will never go back to winblows.

But,......  why the HELL do we keep loosing support for devices every time u/kubuntu releases a new kernel???????]

I have an Audigy 1 card. It worked great with both dapper and edgy. No fiddling........ no messing...... no tweaking...... it just worked...... 4.1 sound.

Now I have moved to Feisty and the card is detected and......... no sound! ](*,) 

OK, I know what some of you are going to say... "It's still beta, it's not done yet, chill out OldGaf"

NUT's TO YOU! I say. :-x 

This card is NOT brand new, it is well supported under linux. Nor is this card so old that it should no longer be supported. HOW FREEKIN HARD IS IT TOO MAINTAIN SUPPORT FOR A BASIC FREEKIN DEVICE BETWEEN KERNEL UPDATES?????? 

This is not the only sound issue I have had lately. I have been building PVR boxes for the last 6 months. In that time I have purchased at least 6 different flavors of motherboard with different chip sets trying to get one that worked as good as the Audigy 1 did...... I don't think it can be done with this distro now. When I do get sound, I only get 2 speaker stereo, and usually out of the headphone or line out channel. This is crazy. How long have they been making PC's with sound eather built in or with addon cards??????  I know that not every chip set will work and that linux is still not as good as winblows for driver support but come on......

If this distro wants to be THE distro to sway the masses away from winblow (or at least some), then at least make sure it can do the basics.

1) Video       (not even 3D..... just good video support)
2) Sound      (I don't mean 7.1...... just working stereo)
3) Internet   (Nic support, browser, java, flash)

That's it.....  3 BIG things. The rest is gravy. 
I could not care less how pretty the latest splash screen is if I can't get any sound out of my speakers, or my internet won't work today because I updated my kernel last night.

Don't get me wrong, I don't expect that all hardware will be supported. I don't expect that any software I could ever want will be available. I just expect that if It worked last year, last week, last night, with this distro, that it will today, tomorrow, next week and next year.

It is getting harder and harder to get people intrested in linux when it should be getting easier. I will soon have to find another distro to call home........ that is a very sad reality.

Thank you for taking the time to read my rant...... I feel better all ready.

I completely agree. While they try to be fancy and racing with windows, they maybe forgot to concentrate on basic things.  Simple example, when you install a music player (which is know as mp3 player even in its webpage) why do we have to install extra codecs to play mp3, why does not it start playing mp3 with very basic utilities (as like windows or puppy linux). Whoever wants extra functionalty, they can search and install those, some people really insterested in most upgrated or most fancy things but why for basic utilities we have to waste time?

And sometimes there is is issue about cpu speed, it is not optimized initially, so we need to tweak around to speed it up the processor. I just tried  puppy linux a couple of days ago, how quick it is and it found correct vide card with better reslution than ubuntu! That feature is really impressive rather than only saying that my desktop is now more fancy like windows. I know that ubuntu is much larger distro and I cannot many things with pupy linux (and that's why I am not using it, I tried to install a scientific program matlab but did not work there). You dont need to suggest me there is xubuntu,  I strongly believe that ubuntu can be much more efficient if developer concentrate on that.  Why do I have to waste time searching for video cards?  If 128 MB distro could do it, then 700 MB ubuntu distro should be able to do it!
Where is the ubuntu spirit ???????

---

### Post by findik1 on 2007-04-13
To Ubuntu: 
If you keep copying others you cannot be yourself, you loose your identity!

I am really pist of with this distro, I was learning linux much better on puppy linux, concentrating on linux commands. Now I am concentarting on finding drivers, installing, re installing, reinstalling fking software

---

### Post by findik1 on 2007-04-13
and I have not even started feisty yet, then show will start. I dont get it, is this distro for beginners or for advanced users? What do you understand by saying user friendly, just looking like windows?

How am I supposed to learn linux if I have problems on compatibility issues. Advanced users can solve those problems anyway. Is it too much to ask for a distro to have:
efficiency/practicality like WINDOWS, 
good graphic utility so that I can see clearly to protect my eyes LIKE WINDOWS 
and listen to music LIKE WINDOWS?

you are copying windows anyway...

---

### Post by findik1 on 2007-04-13
> **findik1 said:**
> and I have not even started feisty yet, then show will start. I dont get it, is this distro for beginners or for advanced users? What do you understand by saying user friendly, just looking like windows?

How am I supposed to learn linux if I have problems on compatibility issues. Advanced users can solve those problems anyway. Is it too much to ask for a distro to have:
efficiency/practicality like WINDOWS, 
good graphic utility so that I can see clearly to protect my eyes LIKE WINDOWS 
and listen to music LIKE WINDOWS?

you are copying windows anyway...

last thing: a lot of people showing how beautiful their desktop "looks". Show me how efficient you are using CPU and memory! Of course advanced users knows the answer! Well, we are the newbies, we dont know!

---

### Post by kallu_be on 2007-04-13
I too have some problems with my sound subsystem with my creative live 7.1 sound card. Alsa starts but wont work. OSS works but if an application is using the sound card ,it is having exclusive lock on it, any solution to it.

---

### Post by KrazyPenguin on 2007-04-13
I don't think Ubuntu should try to be like Windose!!!

That is NOT why we are here.

But Ironically , the more Sh!Ttier Ubuntu is lately the more it reminds me of Windose.

The thing is , this Fiesty distro is not finished yet, so don't judge it yet!!!

The other Ubunut distros had there problems before final release, and even at final release.

Then the distros stabilized quickly.

Fiesty WILL BE the best Ubuntu yet!!!

Just be patient and wait for the final release (and maybe a week or two after with proper upgrades).

"Sometimes man has to take a step back , before taking two steps forward.",
by somedeadguy. ;-)

---

### Post by tgalati4 on 2007-04-13
It's quite possible that the new kernel and sound architecture tweaks in Feisty have broken some things.  

It's also possible that Feisty has detected even more hardware (in your case) than Edgy and therefore an interrupt was assigned that caused a subtle conflict.

Examine dmesg from your previous working configuration and your latest configuration and note the differences.  lspci, aplay -a, /proc/interrupts are tools to discover how your resources are being assigned.

With such a large variety of sound and video cards available and the array of motherboards available, it's amazing that any of this works at all.

I use Dapper because it works reliably on older hardware.  I'm sure things will break when Fiesty Final comes out, but testing the Live CD is the only way to know for sure.

---

### Post by handy on 2007-04-14
Quoted from [http://www.ubuntu.com/products/WhatIsUbuntu](http://www.ubuntu.com/products/WhatIsUbuntu) :

***Ubuntu is and always will be free of charge. You do not pay any licensing fees. You can download, use and share Ubuntu with your friends, family, school or business for absolutely nothing.***

That is why closed source & proprietary software i.e. multimedia codecs & flash & the like have to be downloaded later.

Whilst ever the owners keep their source closed, that is how it will remain.

---

### Post by OldGaf on 2007-04-14
A new kernel has arrived! 
I am updating now. Maybe it will fix my sound..... maybe it will break something else.....

I will post the results shortly.

---

### Post by OldGaf on 2007-04-14
> **tgalati4 said:**
> 
It's also possible that Feisty has detected even more hardware (in your case) than Edgy and therefore an interrupt was assigned that caused a subtle conflict.


Yes, that may well be whats happening. 
But if it is, it comes back to my beef about it being an update problem. If this IS the problem, then k/ubuntu needs to handle interrupts better. Otherwise its claim of supporting more devices is not true. It can only detect more devices....... not support them, as the OS stomps on itself trying to initialize them.

> 
Examine dmesg from your previous working configuration and your latest configuration and note the differences.  lspci, aplay -a, /proc/interrupts are tools to discover how your resources are being assigned.


Thanks for the tip. 
I could do that, but I am not going to spend a bunch of time on this. I have got Feisty on just one of my PC's and I have not added anything to it yet. I will let the update process take it course and see if it fixes itself. At this point I should not have to tweak or fix this particulate device myself. If it is not supported in the end I will just move on....... don't want to keep inventing the wheel every time I get a new car.

> 
With such a large variety of sound and video cards available and the array of motherboards available, it's amazing that any of this works at all.

I use Dapper because it works reliably on older hardware.  I'm sure things will break when Fiesty Final comes out, but testing the Live CD is the only way to know for sure.

See..... that's just it. Linux is supposed to have solid support for old hardware and work on newer hardware as it evolves....... not break the old stuff and maybe work with new stuff....... if you fiddle with it.

That has always been the way with linux. You were supposed to be able to run it on older systems. Sure, with the more modern distros you may need more ram, a faster cpu and more storage to hold it all, but peripherals and basic devices are supposed to be supported. Once that support is in, it should always work and great care should be taken to insure this. Waiting for the comunity to tell them previously supported stuff doesn't work will eventually drive users away.

Sure, I could go with Dapper if I don't want support for anything new and don't require any fixes that later releases fixed. But most people want/need the latest support and software. That's what people are getting with other distros.

It is very difficult to buy a new system for this distro as it is. You have to research all the hardware to insure it is supported. (always has been the case with linux.... I can deal with that.) But now, your Google search may get 1000's of hits saying "realtek onboard sound cards work great with K/Ubuntu" , but when you install your system you find that it is no longer true. This is extremely frustrating not to mention expensive and time consuming.

---

### Post by OldGaf on 2007-04-14
Just booted with new kernel.

Still no sound :O(

---

### Post by Timbuck.3 on 2007-04-14
> **OldGaf said:**
> Just booted with new kernel.

Still no sound :O(
Kubuntu Feisty: Kernel 2.6.20-15-generic
Same sound card, same Problem........

**But now it works**

Go in **KMix **( or the same program on Gnome )
Uncheck ***Audigy Analog/Digital Output Jack*** 
:guitar: 
Works for me.............

---

### Post by OldGaf on 2007-04-14
> **Timbuck.3 said:**
> Kubuntu Feisty: Kernel 2.6.20-15-generic
Same sound card, same Problem........

**But now it works**

Go in **KMix **( or the same program on Gnome )
Uncheck ***Audigy Analog/Digital Output Jack*** 
:guitar: 
Works for me.............


**YES!**

Excellent catch! =D>

---

### Post by OldGaf on 2007-04-14
> **Timbuck.3 said:**
> Kubuntu Feisty: Kernel 2.6.20-15-generic
Same sound card, same Problem........

**But now it works**

Go in **KMix **( or the same program on Gnome )
Uncheck ***Audigy Analog/Digital Output Jack*** 
:guitar: 
Works for me.............


**YES!**

Excellent catch! =D> 

Now why would this be on in a Feisty install, but off in Breezy/Dapper/Edgy?

---

### Post by energiya on 2007-04-14
> **OldGaf said:**
> 
I have an Audigy 1 card. It worked great with both dapper and edgy. No fiddling........ no messing...... no tweaking...... it just worked...... 4.1 sound.
....................................................................................................................................
Don't get me wrong, I don't expect that all hardware will be supported. I don't expect that any software I could ever want will be available. I just expect that if It worked last year, last week, last night, with this distro, that it will today, tomorrow, next week and next year.

OldGaf, I'm just curious. If you manage to get a stable system, why are you updating? Stay with what you have and you will be happyer and have much more time ;)

---

### Post by Subw00fer on 2007-04-14
I have upgraded to Edgy  2.6.17-11-386 and I don't have any sound as well.  I checked to see if the sound is all the way up and it is.  As for the previous post, I don't have KMix program.  What do I do to get sound back?  I also tried an older kernel and that didn't work either

> 
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 [SB0240]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 [SB0240]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 [SB0240]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 [SB0240]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by OldGaf on 2007-04-14
> **energiya said:**
> OldGaf, I'm just curious. If you manage to get a stable system, why are you updating? Stay with what you have and you will be happyer and have much more time ;)

Well, I wanted a newer kernel then Edgy has because there is "supposed" to be better support for my webcam (which I never got working in edgy) and for the FM tuner in my hauppauge for starters. I also have a laptop that is "supposed" to have better support for the Fn keys etc. I don't want to start having to compile my own kernel to get the support I want. If I wanted to do that I would go with another distro.

This is also the same reason I went from Dapper to Edgy. It had support for my AR5005G 802.11abg NIC. I went to edgy and it work without any problems. Then Edgy went from 2.6.17-10 to 2.6.17-11 and away when my NIC. I had to get the Madwifi drivers to get it going again. Just another example of upgrading a kernel and loosing support for a previously supported device. 

[http://ubuntuforums.org/showthread.php?t=366107]("http://ubuntuforums.org/showthread.php?t=366107")

So..... now I figured that 2.6.20 would be better then 2.6.17.

---

### Post by jpyanowski on 2007-04-14
You know, trying a new kernel is always an...experience. Find out what's broken, post your angst to the forums, find the answers, get it fixed and wait for the next kernel.

---

### Post by Esben Kramer on 2007-04-14
So what about us poor GNOME-users? I have the excact same problem, but can't find anything that sounds like what you said...

---

### Post by Timbuck.3 on 2007-04-14
> **Esben Kramer said:**
> So what about us poor GNOME-users? I have the excact same problem, but can't find anything that sounds like what you said...

Should be GMix

---

### Post by kevinlyfellow on 2007-04-15
> **Slipmyknot101 said:**
> Lol not to play devils advocate here or anything but according to the second law of thermodynamics, disorder tends to increase with time when referring to a macroscopic object (such as a new version of linux.)

Only in a closed system.  Linux is open! ;-)

---

### Post by energiya on 2007-04-15
> **OldGaf said:**
> Well, I wanted a newer kernel then Edgy has because there is "supposed" to be better support for my webcam (which I never got working in edgy) and for the FM tuner in my hauppauge for starters. I also have a laptop that is "supposed" to have better support for the Fn keys etc. I don't want to start having to compile my own kernel to get the support I want. If I wanted to do that I would go with another distro.

This is also the same reason I went from Dapper to Edgy. It had support for my AR5005G 802.11abg NIC. I went to edgy and it work without any problems. Then Edgy went from 2.6.17-10 to 2.6.17-11 and away when my NIC. I had to get the Madwifi drivers to get it going again. Just another example of upgrading a kernel and loosing support for a previously supported device. 

[http://ubuntuforums.org/showthread.php?t=366107]("http://ubuntuforums.org/showthread.php?t=366107")

So..... now I figured that 2.6.20 would be better then 2.6.17.

Well, good point ...
Good luck ! and a stable system ;)

P.S.
Compiling a kernel is hard and time consuming only until you get the hang of it.

---

### Post by MetalMusicAddict on 2007-04-15
So wait. OldGaf, all this has been about Feisty? Why are you flipping out about a development version? It supposed to be in constant flux. You dont like that dont use it.

That also means this thread is in the wrong section.

---

### Post by OldGaf on 2007-04-15
Well.... I was only flipping out at the peak of my frustration. And as I said, I do not expect it to perfect. I simply feel that even a development kernel at this stage should not loose something that was already working fine. This is not an alpha, it is just days away from going production. I got burned by the last edgy kernel upgrade that lost support for a NIC. It highlights a trend of working more on eye candy and loosing site of basic support and functionality. If you don't like my opinion....... don't read it.

BTW, as far as being in the wrong section, I simply went to Multimedia & Video as it was a sound issue. I see many Feisty related issues here and no one complaining about it not belonging here.

---

### Post by MetalMusicAddict on 2007-04-15
> **OldGaf said:**
> Well.... I was only flipping out at the peak of my frustration. And as I said, I do not expect it to perfect. I simply feel that even a development kernel at this stage should not loose something that was already working fine. This is not an alpha, it is just days away from going production.
Well thats the risk you take with development versions. Things break, even at this stage. :)
> I got burned by the last edgy kernel upgrade that lost support for a NIC.
So did I.
> It highlights a trend of working more on eye candy and loosing site of basic support and functionality.
I'd like you to post you proof of this otherwise your spreading uninformed FUD.
> If you don't like my opinion....... don't read it.
If you don't want comments don't make your opinions public. ;) Also someone has to read it first to know they don't like it. Come on. :)
> BTW, as far as being in the wrong section, I simply went to Multimedia & Video as it was a sound issue. I see many Feisty related issues here and no one complaining about it not belonging here.
You might see other Feisty issues here. That doesn't make posting in this section any less correct.

My point is ranting about things solves nothing. Learning who best to get your issue to does. Filing a bug is a great start. Sound is especially crazy. I know Ubuntu's ALSA maintainer personally and he does this for FREE. On top of being a professor. Many things are in flux with development versions right up until the end. You don't have to like it. I don't like it but its just the way it is. Best thing we can do is to report it properly so that others benefit.

---

### Post by vgrisham on 2007-04-15
> **KrazyPenguin said:**
> 
Fiesty WILL BE the best Ubuntu yet!!!


I'm afraid I have to give a big bullshit to that. Dapper still holds that honor in my mind. Things just worked in Dapper, and it was (is) incredibly bug free.

The hardware regression thing sucks big time. My atheros wireless card that worked out of the box in Dapper was never able to work in Edgy or now in Feisty. The bug was submitted and confirmed months ago. Dozens of people posted similar problems, yet NOTHING has been done. I finally dumped wireless in favor of an external buffalo ethernet converter just so I could upgrade. I would have stayed with Dapper, but I was starting to find software that wouldn't upgrade any further without upgrading Ubuntu.

I love Ubuntu's philosophy and it's community. The hardware regression thing is a major achilles heel however. What good are wobbly desktop effects and a new control panel when your computer won't make sound or connect wirelessly?

---

### Post by OldGaf on 2007-04-15
> **MetalMusicAddict said:**
> 
I'd like you to post you proof of this otherwise your spreading uninformed FUD.


I don't need to post proof...... the forums are full of it starting with edgy. You yourself say you got burned on the last Edgy update. How long has it been? - still not fixed and there are *TONS* of people complaining and reporting it. Internet access has got to be  *THE* most important part of any distro today. 

> 
My point is ranting about things solves nothing. Learning who best to get your issue to does. Filing a bug is a great start. Sound is especially crazy. I know Ubuntu's ALSA maintainer personally and he does this for FREE. On top of being a professor. Many things are in flux with development versions right up until the end. You don't have to like it. I don't like it but its just the way it is. Best thing we can do is to report it properly so that others benefit.


1) Actually, the rant made me feel better and I suspect it made others feel better who put in their frustrated two cents. The fact that something is free does not make it exempt from criticism. A boy scout can have the greatest intentions when helping a little old lady cross the street. But if he gets her killed on the way, on lookers are still permitted to voice their dismay. :wink: 

2) I did report the bug.

3) The somewhat brash title caught the eye of a few people and I was able to find a resolution to the problem, which in turn was passed on to others and tacked onto the bug report.

Now, don't get me wrong. I really do love this distro. But if you have a quick scan of the forums you will easily see a lot of complaints about regression that does not get fixed. Thats the REAL frustrating part. You fall in love with a distro like this and find it start to faulter where it used to shine. (I said *START* to faultier..... not all is lost :p )

---

### Post by kevinlyfellow on 2007-04-15
> **OldGaf said:**
> I don't need to post proof...... the forums are full of it starting with edgy. You yourself say you got burned on the last Edgy update. How long has it been? - still not fixed and there are *TONS* of people complaining and reporting it. Internet access has got to be  *THE* most important part of any distro today. 



1) Actually, the rant made me feel better and I suspect it made others feel better who put in their frustrated two cents. The fact that something is free does not make it exempt from criticism. A boy scout can have the greatest intentions when helping a little old lady cross the street. But if he gets her killed on the way, on lookers are still permitted to voice their dismay. :wink: 

2) I did report the bug.

3) The somewhat brash title caught the eye of a few people and I was able to find a resolution to the problem, which in turn was passed on to others and tacked onto the bug report.

Now, don't get me wrong. I really do love this distro. But if you have a quick scan of the forums you will easily see a lot of complaints about regression that does not get fixed. Thats the REAL frustrating part. You fall in love with a distro like this and find it start to faulter where it used to shine. (I said *START* to faultier..... not all is lost :p )

Well, after dapper, they kinda went into more experimental stuff and not as much work has been in fixing up those details.  I'm hoping that this changes with Gutsy and I think Mark said he expects Gutsy + 1 to be the next LTS, so they better start cleaning things up.  Feisty has been a bit frustrating for me too.  I updated to edgy, but it was way too unstable for me.  Went to feisty beta and everything was good, until I updated the kernel.  My sound stopped working.  Then upgrading it again, the kernel wouldn't boot.  But I'm not going to be too concerned, since they have gone through lots of changes since Dapper.  Let's just hope that Gutsy cleans up a lot of the kernel issues and starts to get these issues resolved.  If their next LTS is buggy (I doubt it will be though), I'll be looking into moving to debian.

---

### Post by MikeDK on 2007-04-16
hi, just want to add, that i got no problems with sound in 5.1 stereo in feisty with 2.6.20-15-generic
thou it was working fine maybe even better in 2.6.20-14-generic Mainboard is an MSI NEO FSR, but ill guess itll be better as final release of feisty's just around the corner cheers m8's

---

### Post by MetalMusicAddict on 2007-04-16
> **OldGaf said:**
> I don't need to post proof...... the forums are full of it starting with edgy. You yourself say you got burned on the last Edgy update. How long has it been? - still not fixed and there are *TONS* of people complaining and reporting it. Internet access has got to be  *THE* most important part of any distro today.

If you read again I said you need to post proof of them "working more on eye candy and loosing site of basic support and functionality."

All the "eye-candy" comes from upstream. Ubuntu didnt do anything but package it. That was MOTU even. ALL VOLUNTEER. Not the Ubuntu core guys at all.

> 1) Actually, the rant made me feel better and I suspect it made others feel better who put in their frustrated two cents. The fact that something is free does not make it exempt from criticism. A boy scout can have the greatest intentions when helping a little old lady cross the street. But if he gets her killed on the way, on lookers are still permitted to voice their dismay. :wink: 
So you rant to make yourself feel better and others worse? I'm telling you, posts like this do nothing but make me and other developers stay away from the forums and further the disconnect.
> 2) I did report the bug.
I know. Thats why I mentioned it.
> 3) The somewhat brash title caught the eye of a few people and I was able to find a resolution to the problem, which in turn was passed on to others and tacked onto the bug report.
Actually posting that way is against the rules. Thread titles about support should be clearly laid out.

Say someone is searching the titles having the same issue as you? They wont find the info in this thread.
> Now, don't get me wrong. I really do love this distro. But if you have a quick scan of the forums you will easily see a lot of complaints about regression that does not get fixed. Thats the REAL frustrating part. You fall in love with a distro like this and find it start to faulter where it used to shine. (I said *START* to faultier..... not all is lost :p )

I always found it funny that people are most critical of the things/ones they love. Doesnt make any sense to me. To me, those things should get the most slack.

Rants like this IMO only really go to make the OP feel better. Nothing really constructive. I'm sure the real info in this thread is contained other places as well. People here need to ask questions rather then ranting and jumping to bogus conclusions. You guys just have no clue what it takes to make this all work. If it doesnt work for you and you don't want to help constructively don't use it. Thats the beauty about GNU/Linux. Theres always someone else. ;) I use Fedora on my HTPC boxes. )

---

### Post by kazuya on 2007-04-16
Distro is working superbly for me still. It is simply remarkable and beautiful. It is not without its handicaps, but no OS is completely feasible for all machines or user needs. All the OSes I have used except windows have been very suitable for my needs. Feisty exceeds my needs.

---

### Post by paulcone on 2007-04-16
I have been running Xubuntu for 6 months on a Thinkpad X21 and the sound stopped working recently for no apparent reason, and lo and behold, I found this thread, so while it may not directly solve my problem, I am glad to know there is possibly a real reason that I suspected (i.e. updates broke it) and that I'm not alone, and if it seems to be generally symptomatic of a larger issue, it is good to know that, too.  Now I'm off to troubleshoot and possibly file a bug.  Thank you OldGraf, even if you didn't fit the exact standard for posting.

---

### Post by kevinlyfellow on 2007-04-16
> **paulcone said:**
> I have been running Xubuntu for 6 months on a Thinkpad X21 and the sound stopped working recently for no apparent reason, and lo and behold, I found this thread, so while it may not directly solve my problem, I am glad to know there is possibly a real reason that I suspected (i.e. updates broke it) and that I'm not alone, and if it seems to be generally symptomatic of a larger issue, it is good to know that, too.  Now I'm off to troubleshoot and possibly file a bug.  Thank you OldGraf, even if you didn't fit the exact standard for posting.

Haha, nope your not alone... A cursory search on launchpad brings up these bugs
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88332](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88332)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92992](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92992)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93263](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93263)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93945](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93945)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94036](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94036)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94373](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94373)

Until they get these audio problems fixed, I'm just going to be sitting on an old kernel

---

### Post by OldGaf on 2007-04-17
> **paulcone said:**
> I have been running Xubuntu for 6 months on a Thinkpad X21 and the sound stopped working recently for no apparent reason, and lo and behold, I found this thread, so while it may not directly solve my problem, I am glad to know there is possibly a real reason that I suspected (i.e. updates broke it) and that I'm not alone, and if it seems to be generally symptomatic of a larger issue, it is good to know that, too.  Now I'm off to troubleshoot and possibly file a bug.  Thank you OldGraf, even if you didn't fit the exact standard for posting.

I am sorry to hear you lost your sound, but happy that my rant may have given you a small degree of help. Hope you get it straightend out. This forum has alot of good people posting alot of good info.

---

### Post by OldGaf on 2007-04-17
> **kevinlyfellow said:**
> Well, after dapper, they kinda went into more experimental stuff and not as much work has been in fixing up those details.  I'm hoping that this changes with Gutsy and I think Mark said he expects Gutsy + 1 to be the next LTS, so they better start cleaning things up.  Feisty has been a bit frustrating for me too.  I updated to edgy, but it was way too unstable for me.  Went to feisty beta and everything was good, until I updated the kernel.  My sound stopped working.  Then upgrading it again, the kernel wouldn't boot.  But I'm not going to be too concerned, since they have gone through lots of changes since Dapper.  Let's just hope that Gutsy cleans up a lot of the kernel issues and starts to get these issues resolved.  If their next LTS is buggy (I doubt it will be though), I'll be looking into moving to debian.

I totally agree with you.

---

### Post by OldGaf on 2007-04-17
> **MetalMusicAddict said:**
> 
Rants like this IMO only really go to make the OP feel better. Nothing really constructive. I'm sure the real info in this thread is contained other places as well. People here need to ask questions rather then ranting and jumping to bogus conclusions. You guys just have no clue what it takes to make this all work. If it doesnt work for you and you don't want to help constructively don't use it. Thats the beauty about GNU/Linux. Theres always someone else. ;) I use Fedora on my HTPC boxes. )

Ya, OK. You don't like complaining and none of us know as much as you.

But ya know what? lots of people have read this and quite a few have left comments. Some people agree and some people (including myself) got something out of this. In fact, you are the only one complaining about the thread. It could be said that comments like yours only go to make you feel better. Your only contribution has been to say I have no buisness expressing my opinion, or that my opinion is wrong. Well, thats the beauty about these forums. if you don't like a thread, there is always someone else's!

---

### Post by Jarn on 2007-04-17
The problem is that you didn't express it as an opinion. You said it is a problem that they're focusing more on eye-candy than sound.

I can see why threads like yours would drive the heart right out of developers who do things for free. They try as hard as they can, on their own time, with no reward. And then you rant about it. Worst of all, it's a minor problem - a simple checked setting. And yet you rant as if the Four Horsemen of the Apocalypse are at your door.

It shows a lack of respect for everyone but yourself. A lot of people put a lot of time and effort into projects like Ubuntu and if there is a setting somewhere that is checked by default, oh well. It's no reason to go on a rant. Simply find the solution, fix it, and move on.

---

### Post by MetalMusicAddict on 2007-04-17
> **OldGaf said:**
> Ya, OK. You don't like complaining and none of us know as much as you.

But ya know what? lots of people have read this and quite a few have left comments. Some people agree and some people (including myself) got something out of this. In fact, you are the only one complaining about the thread. It could be said that comments like yours only go to make you feel better. Your only contribution has been to say I have no buisness expressing my opinion, or that my opinion is wrong. Well, thats the beauty about these forums. if you don't like a thread, there is always someone else's!

You keep fightin' the good fight. ;) I'm sure you'll reach someone with these posts who can do something. Someday.

PS - You still never provided proof that the Ubuntu devs are: "working more on eye candy and loosing site of basic support and functionality." ;)

/me goes back to developing more useless eye-candy.

---

### Post by MetalMusicAddict on 2007-04-18
> **Jarn said:**
> Worst of all, it's a minor problem - a simple checked setting.

Ya know whats funny? The other half of people with this card have to make sure **Audigy Analog/Digital Output Jack** is *checked*. :)

Ahh... Aint Free software grand. :)

---

### Post by OldGaf on 2007-04-18
> **Jarn said:**
> The problem is that you didn't express it as an opinion. You said it is a problem that they're focusing more on eye-candy than sound.

Sigh...... I did not say that they are focusing more on eye candy then sound. What I said was:
> 
It highlights a trend of working more on eye candy and loosing site of basic support and functionality. 

THAT is my opinion.

I do not mean to imply that developers are actually "creating" the eye candy. They are adding new things to the distro from upstream like a newer KDE, nicer default artwork and the like. These things are cool to have and most people want the latest and greatest stuff (including me).

My point is that IMHO, more focus is needed on insuring that basic devices that are supported in earlier kernels are still supported in newer ones, that a kernel update will not break one of the 3 basic things that the majority of users need: Video, connectivity and sound. And, if it does, fix the problems before spending time and resources adding the new cool stuff.

> 
Edgy had support for my AR5005G 802.11abg NIC. I went to edgy and it work without any problems. Then Edgy went from 2.6.17-10 to 2.6.17-11 and away when my NIC. I had to get the Madwifi drivers to get it going again.


Also see [http://ubuntuforums.org/showthread.php?t=358004]("http://ubuntuforums.org/showthread.php?t=358004")
 
And from this thread:
> 
The hardware regression thing sucks big time. My atheros wireless card that worked out of the box in Dapper was never able to work in Edgy or now in Feisty. The bug was submitted and confirmed months ago. Dozens of people posted similar problems, yet NOTHING has been done. I finally dumped wireless in favor of an external buffalo ethernet converter just so I could upgrade. I would have stayed with Dapper, but I was starting to find software that wouldn't upgrade any further without upgrading Ubuntu.

I love Ubuntu's philosophy and it's community. The hardware regression thing is a major achilles heel however. What good are wobbly desktop effects and a new control panel when your computer won't make sound or connect wirelessly?


> 
I can see why threads like yours would drive the heart right out of developers who do things for free. They try as hard as they can, on their own time, with no reward. And then you rant about it. Throws experiences are want led to my little tantrum.  

OK...... lets get something strait here. Canonical is a company that makes money. Canonical sells support for the very same distros we use. These versions are touted as being Enterprise level. Not all developers work for free. The core team, who are ultimately responsible for the final product are paid. If a volunteer misses something, big deal. As you said they are doing this for free on their own time. But before anything goes out the door, the PAID developers who WORK for Canonical who MAKE MONEY from this product are responsible to insure that users are not effected by new releases.

This link: [ UbuntuDevelopers]("https://wiki.ubuntu.com/UbuntuDevelopers")  explains the role of developers in the Ubuntu project.

This link: [Support]("http://www.ubuntu.com/support/paid")  Shows their support pricing.

This link: [Services]("http://www.canonical.com/services")  Shows the other ways Canonical makes money off ubuntu and other services.

Canonical also has a bounty system. This is essentially an outsourcing program to pay developers for working on specific projects while avoiding having to hire them full time. I am not a fan of this trend but it is a common practice in todays business market.
Look here: [bounties]("http://www.ubuntu.com/community/developerzone/bounties")

Some people seem to think that K/Ubuntu was "made" by a bunch of volunteers like some kind of Club. This is not true. You are getting it confused with Debian. Thats where the real heroes are.
Have a [look.]("http://www.debian.org/intro/about#what")
In case you didn't know, or you forgot, there would be NO Ubuntu if not for Debian.
This link: [blog]("http://blog.madduck.net/debian/2006.05.24-ubuntu-and-debian")  will take you to some interesting Debian / Ubuntu information.

> 
 Worst of all, it's a minor problem - a simple checked setting. And yet you rant as if the Four Horsemen of the Apocalypse are at your door. It shows a lack of respect for everyone but yourself. A lot of people put a lot of time and effort into projects like Ubuntu and if there is a setting somewhere that is checked by default, oh well. It's no reason to go on a rant. Simply find the solution, fix it, and move on.


Hey, I was frustrated. And besides, do we need to check every setting of every device after every update? If it worked "as is" before it should continue to work. Ya, it was a simple fix and I am very glad of that. But other issues from other upgrades / updates have not been fixed. On the surface there is no way to tell if this was going to be another one of those issues. All I did was apply an update released by my distro provider. The next morning I turned on my computer and I had no sound. Given the other experiences I have had, I had every right to be p!$$ed off.

Bottom line:
Why do Developers work on Ubuntu? - Because they like doing it and/or they hope to make money at it. Great, hats off to them.
Why do I use K/Ubuntu ? Because I like it and because Canonical tells me that it is perfect for laptops, desktops and servers. It contains all the applications you need - a web browser, presentation, document and spreadsheet software, instant messaging and much more.

If something Canonical releases breaks something on my system, I have a right to be p!$$ed. The fact that Canonical does not pay some of its Developers is not my concern. (sorry if that hurts, I do appreciate their commitment) But in reality, if the Ford company releases an update for my cars computer and then my car won't start, they better not tell me to calm down because their tech department is run by volunteers!  

And before you point it out, yes, the sound issue was caused by a development release. The above statement goes more to the other issues I and others have had with production releases. Those are what lead me to my little tantrum over my sound.

---

### Post by GadgetsGuy on 2007-04-18
since the new kernel update - after 5 days of searching posts, and adding a few of my own, I am still soundless :(

my sound card is intel 82801 integrated  :  (Intel Corporation 82801BA/BAM AC'97 Audio (rev 02))

if ANYBODY can help me, I'd be very appreciative

---

### Post by OldGaf on 2007-04-18
> **GadgetsGuy said:**
> since the new kernel update - after 5 days of searching posts, and adding a few of my own, I am still soundless :(

my sound card is intel 82801 integrated  :  (Intel Corporation 82801BA/BAM AC'97 Audio (rev 02))

if ANYBODY can help me, I'd be very appreciative

Are you using Gnome or KDE?

Have you tried all other ports on your sound card? Some times the output gets changed to one of the other ones. (not speaker out)

Does the system still detect your card?

---

### Post by Mjolniir on 2007-04-20
I upgraded to Ubuntu feisty today.  It detects my soundcard fine, but will not play anything.  If I hit the test button it gives me this little window:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

I have no clue but I will probably just reinstall edgy.  My sound worked fine when I was running it and I have everything backed up I can restore all my stuff easily.

---

### Post by rcatman on 2007-04-20
Hey,
I have an audigy 1 card as well, sound did not work initially when I installed Fiesty. Heres how I got it working...

Goto the Volume Control (Alsa mixer)   

Note: My volume control is title "Volume Control: Audigy 1 [SB0090] (Alsa mixer)"

Theres two tabs, Playback and Switches. Goto switches. Uncheck "Audigy Analog/Digital Output Jack".  Booya! It worked for me, I hope it does for you!

---

### Post by orb9220 on 2007-04-20
> **GadgetsGuy said:**
> since the new kernel update - after 5 days of searching posts, and adding a few of my own, I am still soundless :(

my sound card is intel 82801 integrated  :  (Intel Corporation 82801BA/BAM AC'97 Audio (rev 02))

if ANYBODY can help me, I'd be very appreciative

Have the Exact same and found to open volume control and make sure that PCM was not muted and sliders up.

Also right-click speaker and select  preferences and see if Master is set to Intel 82801BA-ICH2 (Alsa-Mixer)

Also a troubleshoot link
[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound)

Sorry that is all I have fer You now.

---

### Post by just learning on 2007-04-20
i was having the same problem. i read what timbuck.3 said, so i went in the volume control and muted pcm and sound came back. simple but it worked thanks timbuck.3. i hope yours gets fixed to old gaf.:) [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by bluntu on 2007-04-20
> **Mjolniir said:**
> I upgraded to Ubuntu feisty today.  It detects my soundcard fine, but will not play anything.  If I hit the test button it gives me this little window:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

I have no clue but I will probably just reinstall edgy.  My sound worked fine when I was running it and I have everything backed up I can restore all my stuff easily.

Same here. Everything worked fine when I first installed, after I install stuff to view WMV movies things got out of control. hmm...

---

### Post by nomeat on 2007-04-22
Unchecking "Audigy Analog/Digital Output Jack"  in Kmix did not work for me, even after reboot.
PCM and other faders are up. Onboard sound is disabled in Bios.
Sound worked on Dapper.

No sound and no midi control although I can choose the Audigy and Alsa midi Uarts
Did a total reinstall especially just for Ubuntu Studio :(

The Audigy ZX would be the most useful but still affordable Soundcard for the creative music enthusiast and was available to a broad market. I can't understand why go through all the trouble of developing Ubuntu studio when this important soundcard is neglected :(

---

### Post by nscerri on 2007-04-26
KMIX WORKED PERFECTLY. JUST REMOVED THE ANALOG/DIGITAL AND WORKED FINE.

:guitar:

---

### Post by mvsjes2 on 2007-04-28
I have to agree with the title of this thread. You have no idea how much time I've wasted trying over the last few months to get a sound card to work consistently with this distro. I read so many comments in books and on the web that on-board sound should "just work" with no issues. Yeah right!

I've had very low output, I've had no output, I've had only stereo without surround, I've had partial surround, and now this: I upgraded to feisty hoping that these issues would go away, and now amarok plays one song then the whole sound system dies. Same with mythmusic when I back out to the myth menu: I get a loud pop and that's it for sound.

I've run into these with at least three motheroards and now a chaintech av-710, which I purchased because I read so many reports that it just worked "out of the box".

2007-04-28 12:46:56.244 Opening ALSA audio device 'default'.
2007-04-28 12:46:56.245 AudioOutput Error: snd_pcm_open(default): Device or resource busy

If someone could point me to a sound card that actually works (with surround) without constant babying in this distro, I'd like to hear about it.

---

### Post by OldGaf on 2007-11-01
Oh look....... I'm back and pi$$ed off again!

This time it is the system freezes that many of us are having. Mine started with Feisty a few months ago and have followed me to Gusty.

If I leave the system idle, Xorg slowly uses more and more CPU until Xorg freezes. I can still move the mouse but can not open anything new, or close anything that is open. All I can do is Ctrl+Alt+Backspace to kill X.

[ Xorg climbs to 100% and system freezes.]("http://ubuntuforums.org/showthread.php?t=593607")

[Gutsy will just freeze / lock up / crash]("http://ubuntuforums.org/showthread.php?t=587905")
(The above turns out to affect more then just Gusty 64)

I cut a bug report on this as did many others but never heard anything back. Not even  "we are aware of the issue and are looking into it".

So...... here goes:
<rant>
I really love this distro, but I am getting too tired of these issues on every upgrade that don't get fixed. The original issue I had in this thread was never fixed. Not that it is a big issue once you know what it is, but the VAST majority of everyday users do not use digital out. Why would you leave this on by default? How much time and effort would it take to fix it? The problem was reported over 6 months ago and one release ago, and still it causes new users unnecessary grief and reinforces the false belief that Linux still doesn't work well. POLISH YOUR DISTRO PEOPLE IF YOU WANT IT TO BE THE DISTRO OF CHOICE!

Now with this new problem, I turns your system into a brick if you want it to do any long running task. With not even an acknowledgment of the bug (which I did get on the far more frivolous sound issue) why should we believe this is going to be addressed any time soon? 
</rant>
Out of desperation and dissolution I am going to partion my drive today and install Debian unstable and PCLinuxOS.

Phew...... that feels better. Thank you for taking the time to read my rant. I hope anyone who shares my opinion / feeling on this matter can take some comfort in knowing they are not alone.

---

