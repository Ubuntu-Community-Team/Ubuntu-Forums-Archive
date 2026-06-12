---
title: "Any issues with 64bit Mythbuntu?"
date: 2008-09-15
forum: Mythbuntu
---

### Post by bmathis on 2008-09-15
I am upgrading my box from an old P4 1.7GHz box to a AMD Athlon 64 3700+ box and wanted to know if there are any hiccups that I might encounter in going the 64bit route?

Thanks! :popcorn:

---

### Post by db260179 on 2008-09-15
The only cripe i have is the Java issue. The 64bit version doesnt work properly. Apart from that there is no real major issues i have found

> **bmathis said:**
> I am upgrading my box from an old P4 1.7GHz box to a AMD Athlon 64 3700+ box and wanted to know if there are any hickups that I might encounter in going the 64bit route?

Thanks! :popcorn:

---

### Post by Markus72 on 2008-09-15
Is there a reason why Java is useful with MythBuntu?

On the other hand: what are the advantages? Better performance when postprocessing the videos?

---

### Post by budge31 on 2008-09-15
I am running Mythbuntu 8.04 64bit on an AMD 4200+ dualcore as my backend, Mythbuntu 64 on one of my frontends and Mythbuntu 32 bit on 2 others. They all work fine.

---

### Post by managementboy on 2008-09-16
> **Markus72 said:**
> Is there a reason why Java is useful with MythBuntu?

On the other hand: what are the advantages? Better performance when postprocessing the videos?

everything works well on 64 bit (I use it because I have 8gigs of ram in the Server). Java works fine for me (Azureus client). 

What I have not been able to get to work are the ProjectM visualisations, and I think its because of 64 bit..

---

### Post by aross01 on 2008-09-16
CPU: AMD Phenom 9850 Quad Core Socket AM2
MB: ASUSTek M3N-HT Deluxe/HDMI
MythBuntu 8.10 Alph 5

I installed 32bit Mythbuntu and want to change to 64bit
Do I need to reinstall or is there a way perform a upgrade from 32bit to 64bit?

Thanks 
AR

---

### Post by tgm4883 on 2008-09-16
> **aross01 said:**
> CPU: AMD Phenom 9850 Quad Core Socket AM2
MB: ASUSTek M3N-HT Deluxe/HDMI
MythBuntu 8.10 Alph 5

I installed 32bit Mythbuntu and want to change to 64bit
Do I need to reinstall or is there a way perform a upgrade from 32bit to 64bit?

Thanks 
AR

You have to reinstall

---

### Post by bmathis on 2008-09-17
Thanks for the feedback everyone... I should receive my processor shortly and have my upgraded box working!!!

---

### Post by Lester_Burnham on 2008-09-17
I think I had issues with LVM2 on AMD 64. I went back to i386 and it was fine.

---

### Post by Will May on 2008-09-19
I've got 64 bit installs of both Ubuntu and Mythbuntu and the only issues I've ever had with either of them is Adobe Flash (fairly unstable when using it through nspluginwrapper) and Java (haven't really spent much time trying to fix it to be honest).

---

### Post by alexeix on 2008-10-01
What are the benefits of using 64 bit over 32 bit (other than if you have a lot of memory installed)?

For example, I have a simple machine with an Athlon64 3200 CPU and 1GB DDR2 RAM; will Mythbuntu 64 bit run any better/faster on my machine?

---

### Post by tgm4883 on 2008-10-01
> **alexeix said:**
> What are the benefits of using 64 bit over 32 bit (other than if you have a lot of memory installed)?

For example, I have a simple machine with an Athlon64 3200 CPU and 1GB DDR2 RAM; will Mythbuntu 64 bit run any better/faster on my machine?

People have seen a 30% decrease in transcoding time.  Not sure about other benefits though

---

### Post by bmathis on 2008-10-02
I installed the 64bit version 2 weeks ago after starting this thread and I havent seen any issues at all. I'd have to say its super fast compared to my old box.

---

### Post by RockyMountain on 2008-11-06
I'll ask the flip-side question.  What does one gain by going to 64-bit in a Myth machine?

I chose 32-bit thinking that it might be more stable/mainstream, but was tempted to try 64 instead.  The deciding factor was that I didn't know of any concrete reason to favor 64, and so took the presumably more conservative 32-bit route.

Does Myth run any better on 64 vs 32?  Would it lower my 90%+ frontend CPU utilization for liveTV?  I have only 2GB of memory, so the ability to address more memory is not an issue for me. And I run nothing but Myth on it, so better performance in other areas wouldn't help me either.  I run an Intel Core 2 Quad(*) CPU, 2.1(?) GHz if I recall correctly.

Thanks,
Derek.

---

### Post by whosmatt on 2008-11-06
None here.  I'm running on old hardware too - 3GHz prescott.

and when i say "none" i mean "no more than any 64 bit Ubuntu" meaning that flash is very unstable through the wrapper and java doesn't really work as advertised at least in the browser.

---

### Post by alexeix on 2008-11-06
> **RockyMountain said:**
> Would it lower my 90%+ frontend CPU utilization for liveTV?  I have only 2GB of memory, so the ability to address more memory is not an issue for me. And I run nothing but Myth on it, so better performance in other areas wouldn't help me either.  I run an Intel Core 2 Quad(*) CPU, 2.1(?) GHz if I recall correctly.


I'm no expert, but doesn't 90% CPU utilisation for live TV sound a bit high, on a machine with those specs?

See above for my lowly PC specs (3.5 year old, single core CPU), but my CPU usage is not as high.
I am testing the 64bit version, but is that really relevant here?

Maybe a techie expert can give an opinion?

---

### Post by buu700 on 2008-11-08
It's possible that he's decoding without a dedicated GPU and/or running additional processes such as transcoding and commercial flagging in the background.

---

### Post by whosmatt on 2008-11-10
> **RockyMountain said:**
> I'll ask the flip-side question.  What does one gain by going to 64-bit in a Myth machine?

I chose 32-bit thinking that it might be more stable/mainstream, but was tempted to try 64 instead.  The deciding factor was that I didn't know of any concrete reason to favor 64, and so took the presumably more conservative 32-bit route.

Does Myth run any better on 64 vs 32?  Would it lower my 90%+ frontend CPU utilization for liveTV?  I have only 2GB of memory, so the ability to address more memory is not an issue for me. And I run nothing but Myth on it, so better performance in other areas wouldn't help me either.  I run an Intel Core 2 Quad(*) CPU, 2.1(?) GHz if I recall correctly.

Thanks,
Derek.

I don't think 64 bit would make a difference in your CPU utilization, at least not a significant one.  I would look at your video hardware first.  For example, I switched from the stock ATI board in my Dell Dimension 8400 to a $30 Nvidia card (fanless 7300 if I remember correctly) and my CPU utilization during live HD viewing went from around 70% to 25% or so.

I can imagine that integrated graphics would put quite a strain on your CPU.  If you've got four cores, however, it might be just fine to leave one of them to the task of decoding your video.

-M

---

### Post by buu700 on 2008-11-10
> **whosmatt said:**
> I don't think 64 bit would make a difference in your CPU utilization, at least not a significant one.  I would look at your video hardware first.  For example, I switched from the stock ATI board in my Dell Dimension 8400 to a $30 Nvidia card (fanless 7300 if I remember correctly) and my CPU utilization during live HD viewing went from around 70% to 25% or so.

I can imagine that integrated graphics would put quite a strain on your CPU.  If you've got four cores, however, it might be just fine to leave one of them to the task of decoding your video.

-M

Don't quote me on this, but I'm pretty sure that anything multimedia-related gets a pretty significant performance boost on 64-bit; however, you also have to take into account if your 64-bit video drivers are lagging behind the 32-bit ones.

---

### Post by chrisinspace on 2008-12-10
> **Will May said:**
> I've got 64 bit installs of both Ubuntu and Mythbuntu and the only issues I've ever had with either of them is Adobe Flash (fairly unstable when using it through nspluginwrapper) and Java (haven't really spent much time trying to fix it to be honest).

I'm about to make the switch myself.  I'm retiring my 32-bit Myth system and reconfiguring my old gaming box to be my Myth front- and backend machine.  Just so you know, Adobe has recently begun to address the Flash 64-bit issue and they actually started in Linux!  It looks like they may be back on board with Open Source.  It's still in the testing phase, but it sounds like it's already more stable than 32-bit in the nspluginwrapper.  Flash definitely is not a priority on my Myth installation, but it's fun to watch YouTube videos on the TV in the living room sometimes.

[http://blogs.computerworld.com/64_bit_linux_adobe_flash_player_surprisingly_good](http://blogs.computerworld.com/64_bit_linux_adobe_flash_player_surprisingly_good)

---

### Post by chrisinspace on 2009-01-13
So, I completed my upgrade, but I have been seeing an issue.  I'm honestly not sure if it's related to the 64bit OS.  My system often locks up during DVD playback.  The first couple of times I thought it was a problem with the disk, but the problem has continued.  I think my next step will be to swap out the DVD-ROM for another one that I have.  It isn't that old and I never had problems with it before I upgraded the machine from Vista 64bit to Mythbuntu 64bit, but I figure that's a quick way to troubleshoot the problem.  Has anyone else heard of any problems like this?

---

### Post by managementboy on 2009-01-14
> **chrisinspace said:**
> So, I completed my upgrade, but I have been seeing an issue.  I'm honestly not sure if it's related to the 64bit OS.  My system often locks up during DVD playback.  The first couple of times I thought it was a problem with the disk, but the problem has continued.  I think my next step will be to swap out the DVD-ROM for another one that I have.  It isn't that old and I never had problems with it before I upgraded the machine from Vista 64bit to Mythbuntu 64bit, but I figure that's a quick way to troubleshoot the problem.  Has anyone else heard of any problems like this?

I have had these issues and got them fixed with new firmwares.

---

