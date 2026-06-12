---
title: "NFL Gamepass HD on Ubuntu"
date: 2008-08-19
forum: Multimedia Software
---

### Post by Mughoj on 2008-08-19
Hi all,

I'm totally new to Ubuntu and it's years since I last used linux and I never were much of a guru :)

I'm setting up a media pc (hooked up to my projector) and wanted to use Ubuntu if possible. But I need to be able to watch the NFL Gamepass HD stream (demo of the stream [here]("http://gamepass.nfl.com/nflgp/move/player/demo.htm")) and it requires Windows (or Mac) os and either IE or firefox.

I managed to install a Windows firefox version under Wine and was able to actually start the stream, but it totally messed up the videocard and all colors shifted and I had to reboot to get it in order again.

So, is there a better way of emulating either IE or firefox running on Windows OS under Ubuntu? Something that might work with this stream?

I apologize if I should be able to figure this out myself, but as said I'm totally new and even though I'm interested in learning, I'm not so eager to spend hours or days figuring out Ubuntu to realize it's not even possible.  

Mugge

---

### Post by cariboo on 2008-08-19
The only thing I can suggest is to run windows in a vm using either VirtualBox or VMWare. You should also write to the producers and suggest they are losing business because they have no client for Linux.

Jim

---

### Post by Mughoj on 2008-08-20
> **cariboo907 said:**
> The only thing I can suggest is to run windows in a vm using either VirtualBox or VMWare. 


Ok, I'll look into that.

> **cariboo907 said:**
> You should also write to the producers and suggest they are losing business because they have no client for Linux.

I did that already. I asked if they planned to support linux and suggested that they did. It didn't take them much more than an hour to reply. 

*[COLOR="Red"]The NFL Game Pass HD is not supported on Linux at this time. Thank you for your interest in the NFL Game Pass HD.[/COLOR]*

I kinda figured that out myself, but it certainly shows that they have no interest in linux :(

Mugge

---

### Post by marduk667 on 2009-08-11
I also wrote an email to them, their answer:

Dennis,

NFL Game Pass requires plug-ins for Windows Media Player, Move Networks Media, and Adobe Flash. If you have means to make these plug-ins work in a Linux environment, by all means do so, but we do not provide support for any linux-based platform, so you do so at your own risk, and we will not be able to offer troubleshooting in the event something does not work.

NFL Web Support 

Did anyone try this with wine/ie?

---

### Post by Treepwood on 2009-09-18
Has anyone found a solution to this?

---

### Post by Treepwood on 2010-07-30
It works!!! 
 
The new player for the upcomming season is fully flashbased.

---

### Post by marduk667 on 2010-08-11
REALLY? Have to try!

---

### Post by marduk667 on 2010-08-11
okay so gamepass works but very bad performance with the flash player, any hints?

---

### Post by fyo on 2010-08-11
> **marduk667 said:**
> okay so gamepass works but very bad performance with the flash player, any hints?

I'm curious as to your system specs and browser / flash versions. I tried the demo stream and it worked fine at 3Kbps (max):

[https://gamepass.nfl.com/nflgp/secure/registerform](https://gamepass.nfl.com/nflgp/secure/registerform)

It did swallow a lot of resources, I'll grant. My system is about 3 years old (2.6GHz dual-core AMD X2) and the npviewer.bin process run well over 100% (200% being both cores), spiking to the 140% range.

Still played fine, though.

Btw, is it me or is there no way to maximize the video?

---

### Post by marduk667 on 2010-08-11
Still have an "AMD Athlon 64 3000+" so maybe i really should consider upgrading. Fullscreen is available in paid version, just scroll down a bit and you will see it.
Sad for me, i can watch anything below 720p with this hardware, also veetle.com never was a problem...i just hate flash :(

---

### Post by fyo on 2010-08-11
> **marduk667 said:**
> Still have an "AMD Athlon 64 3000+" so maybe i really should consider upgrading. Fullscreen is available in paid version, just scroll down a bit and you will see it.
Sad for me, i can watch anything below 720p with this hardware, also veetle.com never was a problem...i just hate flash :(

Using flash for something like this is beyond dumb, but on the other hand, we probably wouldn't get a Linux client without a "web only" solution.

(Playing a video via a browser is always going to require a lot more resources than in a dedicated player, mainly due to the compositing requirements)

---

### Post by lech@ibcl.at on 2010-08-22
> **Treepwood said:**
> It works!!! 
 
The new player for the upcomming season is fully flashbased.

It still does not work for me.

I have the newest firefox, flashplugin, and google-chrome packages but when I click on "Demo" I just get an error message that "automatic installation" is not supported for my operating system and a link to a flash player download page ;-((

I was happy with GamePass when it was at Yahoo, and I used it with a borrowed Windows Laptop last year (half season pass for 2nd half, both times), but I'm not willing to use Windows again.

I hope the will Support pads next year. Not iPad (I hate Apple) but rather Android/ChromeOS and/or MeeGo.

---

### Post by lech@ibcl.at on 2010-08-22
> **lech@ibcl.at said:**
> It still does not work for me.


It works in 32bit installations!
I just created a 32bit lucid installation in a chroot, and it works at least with firefox.

So it probably is just a problem of the damn gamepass site's environment detection, and it should be fixable somehow.

If I found a solution better than the 32bit chroot I'm gonna report back here.

---

### Post by mulluysavage on 2010-09-29
I can't get Game Rewind to work, I've tried it on both puppy and ubuntu; I go to the rewind page and no video comes up. I also can't watch hightlights. I can see the ads and then the highlights don't come up.

Runnning ubuntu 10.04 off live cd, AMD Quad-core 2.3ghz 4gb ram. asus m3n78pro mobo

---

