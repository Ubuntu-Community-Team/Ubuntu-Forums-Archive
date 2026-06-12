---
title: "Firefox Flash performace = poor - very poor"
date: 2009-07-07
forum: Multimedia Software
---

### Post by SlugSlug on 2009-07-07
Firefox 3.0.11 and now firefox 3.5 both suffer a major performance problems on my machine, an example site is
[http://www.national-lottery.co.uk/player/p/results.ftl](http://www.national-lottery.co.uk/player/p/results.ftl)
am wondering if its an ATi issue am currently using a x800 but it plays DIVX and 720 HD AVI's alright...

it's really getting annoying now, any help is appreciated

---

### Post by AnimeOmega on 2009-07-07
Try other browsers,

sudo apt-get install midori
sudo apt-get install arora
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

If flash is still sufering, it maybe your video card, make sure your using the latest drivers. I dont have an ATI card (or Ubuntu for that matter), but check if this helps: [http://wiki.archlinux.org/index.php/ATI](http://wiki.archlinux.org/index.php/ATI) . Try the open source drivers and the closed source ones.

Good luck.

---

### Post by dlmarti on 2009-07-07
> **SlugSlug said:**
> Firefox 3.0.11 and now firefox 3.5 both suffer a major performance problems on my machine, an example site is
[http://www.national-lottery.co.uk/player/p/results.ftl](http://www.national-lottery.co.uk/player/p/results.ftl)
am wondering if its an ATi issue am currently using a x800 but it plays DIVX and 720 HD AVI's alright...

it's really getting annoying now, any help is appreciated

I noticed the same when I upgraded from Intrepid to Jaunty.
I solved the issue by getting a faster PC, and upgrading the video card to a Nvidia.

If you can't upgrade the hardware I would suggest down grading to Intrepid.

I think this is just a sad case of code bloat.

---

### Post by SlugSlug on 2009-07-07
> **AnimeOmega said:**
> Try other browsers,

sudo apt-get install midori
sudo apt-get install arora
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

If flash is still sufering, it maybe your video card, make sure your using the latest drivers. I dont have an ATI card (or Ubuntu for that matter), but check if this helps: [http://wiki.archlinux.org/index.php/ATI](http://wiki.archlinux.org/index.php/ATI) . Try the open source drivers and the closed source ones.

Good luck.

cheers, but i kinda like firefox..   and the ATi drivers are not available for jaunty yet...

---

### Post by SlugSlug on 2009-07-07
> **dlmarti said:**
> I noticed the same when I upgraded from Intrepid to Jaunty.
I solved the issue by getting a faster PC, and upgrading the video card to a Nvidia.

If you can't upgrade the hardware I would suggest down grading to Intrepid.

I think this is just a sad case of code bloat.

so your jaunty plays this site ( [http://www.national-lottery.co.uk/player/p/results.ftl](http://www.national-lottery.co.uk/player/p/results.ftl) ) fine with nvidia? 

my PC should be more than capable of a flash site
3gig P4
2GB ram
ATI Technologies Inc R420 [Radeon X800 PRO/GTO]

---

### Post by AnimeOmega on 2009-07-07
> **SlugSlug said:**
> cheers, but i kinda like firefox..

Trying another browser could help isolate the problem, you'll know if it's firefox or something else.

---

### Post by SlugSlug on 2009-07-07
> **AnimeOmega said:**
> Trying another browser could help isolate the problem, you'll know if it's firefox or something else.

midori quits to desktop when i hit the said site

---

### Post by martinbaselier on 2009-07-07
@slugslug, ATI does not support your card (just like mine) anymore. So there won't come an ATI driver for your card. 
The drivers for jaunty have been out there for months.

By the way: The site works fine with me (I have an X700 - 1,9GHz CPU (running on 800MHz)-768MB I use xfce instead of gnome though.

---

### Post by SlugSlug on 2009-07-07
> **SlugSlug said:**
> midori quits to desktop when i hit the said site


arora works on the site but is jerkey and flash jumps some what

---

### Post by SlugSlug on 2009-07-07
> **martinbaselier said:**
> @slugslug, ATI does not support your card (just like mine) anymore. So there won't come an ATI driver for your card. 
The drivers for jaunty have been out there for months.

yep I have the 'jaunty drivers' 

how does your firefox perform on [http://www.national-lottery.co.uk/player/p/results.ftl](http://www.national-lottery.co.uk/player/p/results.ftl)


PS am no mad crazy lotto gambler it's just easer to point to this site :)

---

### Post by blackgr on 2009-07-07
A bad coded flash by adobe in combination with your lack in ati drivers gives you this bad resoult. Changing browsers wont do any good. Its not about browser, its about adobe flash.

---

### Post by SlugSlug on 2009-07-07
> **blackgr said:**
> A bad coded flash by adobe in combination with your lack in ati drivers gives you this bad resoult. Changing browsers wont do any good. Its not about browser, its about adobe flash.

I have tried the flash alternatives, but there no good, can you suggest anything to solve it?

---

### Post by blackgr on 2009-07-07
hm i didnt see this before "3gig P4" .My friend also had flash problem with an old amd cpu and when he upgraded it he was ok. I know... you'll propably say.. "but in windows it worked fine". Its all about bad flash players in linux. When i visit the site you provided and i navigate around, my cpu usage goes to 20-30% in Quad Core 2.4 Intel. Well i cant suggest anything. A system upgrate i dont think is an option.

---

### Post by martinbaselier on 2009-07-07
You misunderstood. I tested the site you pointed to and it works fine for me. I meant that there will be no more official ATI drivers for us, just the open source ones. If you want to use the drivers from ATI you either would have to manually downgrade xorg or go back to intrepid.

---

### Post by SlugSlug on 2009-07-07
> **martinbaselier said:**
> You misunderstood. I tested the site you pointed to and it works fine for me. I meant that there will be no more official ATI drivers for us, just the open source ones. If you want to use the drivers from ATI you either would have to manually downgrade xorg or go back to intrepid.

well it works fine for you, and your using  an ATI x800?? with jaunty and firefox 3?

---

### Post by martinbaselier on 2009-07-07
I'm using an X700 with jaunty and firefox 3.

---

### Post by SlugSlug on 2009-07-07
> **martinbaselier said:**
> I'm using an X700 with jaunty and firefox 3.

hummm so why is mine so bad...?

would you mind doing a 
cat /etc/X11/xorg.conf

---

### Post by dlmarti on 2009-07-07
> **SlugSlug said:**
> so your jaunty plays this site ( [http://www.national-lottery.co.uk/player/p/results.ftl](http://www.national-lottery.co.uk/player/p/results.ftl) ) fine with nvidia? 

my PC should be more than capable of a flash site
3gig P4
2GB ram
ATI Technologies Inc R420 [Radeon X800 PRO/GTO]

Yes, but like I said, I upgraded the motherboard and video card.

This is just a code bloat problem (Linux is not immune).  Every Ubuntu version gets slower and slower (just like every other OS).  You need to make the decision to upgrade your hardware, or to stay with the older versions.

I switched from an old P4 with an ATI card, to a Xeon and an Nvidia card.

With my old machine I could watch CNN videos under Intrepid (90% CPU utilization), but not with Jaunty (the video was jerky as hell with Jaunty) (100% CPU utilization).

With my new machine I can watch CNN videos with Jaunty (40% CPU utilization).

I went from a 3GHz P4 to a 3.6GHz Xeon, so I doubt that is really the issue since the bus speeds are the same.  I think the real benefit came from switching from an ATI card to an Nvidia based card.

---

### Post by dlmarti on 2009-07-07
Bottom line is a decent Nvidia based card is about 30-40 dollars, thats really cheap given all the problems is solves.

edit: I just found one for less than 18 bucks:  [http://www.geeks.com/details.asp?invtid=188-01N01-02CLG&cat=VCD](http://www.geeks.com/details.asp?invtid=188-01N01-02CLG&cat=VCD)

---

### Post by SlugSlug on 2009-07-07
> **dlmarti said:**
> Yes, but like I said, I upgraded the motherboard and video card.

This is just a code bloat problem (Linux is not immune).  Every Ubuntu version gets slower and slower (just like every other OS).  You need to make the decision to upgrade your hardware, or to stay with the older versions.

I switched from an old P4 with an ATI card, to a Xeon and an Nvidia card.

With my old machine I could watch CNN videos under Intrepid, but not with Jaunty (the video was jerky as hell with Jaunty).

With my new machine I can watch CNN videos with Jaunty.

I really struggle to believe its a Hardware fault, am on a fairly new install of ubuntu 9.04, on the machine i have had vista running flash better...

I agree Nvidia would more than likley solve the problem but then again so would bootin windows...  there must be a way to fix jaunty with an old ati to play flash - if not then that just aint ubuntu....

---

### Post by dlmarti on 2009-07-07
> **SlugSlug said:**
> I really struggle to believe its a Hardware fault, am on a fairly new install of ubuntu 9.04, on the machine i have had vista running flash better...

I agree Nvidia would more than likley solve the problem but then again so would bootin windows...  there must be a way to fix jaunty with an old ati to play flash - if not then that just aint ubuntu....

I never said it was the hardwares fault, I said it was code bloat.  I just said that hardware would fix the problem.

As for working under Windows and not under Linux....
1. Your running an old as hell version of windows, and a cutting edge version of Linux.
2. The Flash app was written by a bunch of monkeys at Adobe, Ubuntu has nothing to do with them.
3. ATI hates Linux, and the drivers reflect that.

---

### Post by SlugSlug on 2009-07-07
> **dlmarti said:**
> I never said it was the hardwares fault, I said it was code bloat.  I just said that hardware would fix the problem.

As for working under Windows and not under Linux....
1. Your running an old as hell version of windows, and a cutting edge version of Linux.
2. The Flash app was written by a bunch of monkeys at Adobe, Ubuntu has nothing to do with them.
3. ATI hates Linux, and the drivers reflect that.

1. what ?? vista since when has that been old as hell or stable ??

2. its just not that flash app its a load i have prob with 

3. yer some other guy on same card claimed no prob...


downgrading to 8.10 would solve this - but its a massive ball ache i just wanna get 9.04 working for me...

---

### Post by estyles on 2009-07-07
Try disabling compiz to give it a try ```
metacity --replace &
```

My flash is still a little sluggish, but works much better with metacity than compiz.  Note - don't close your terminal window after running the above command.  If you want to turn compiz back on, do ```
compiz --replace &
```  I think you can close the terminal window after that command, but I usually just restart my session after switching to metacity when I want to switch back - it restarts my transparent desktop console which I use compiz for and which I usually close after starting metacity.

If that works, and you're okay with disabling compiz in order to do flash stuff, you can make a launcher on your desktop for the above commands.

---

### Post by SlugSlug on 2009-07-07
> **estyles said:**
> Try disabling compiz to give it a try ```
metacity --replace &
```

My flash is still a little sluggish, but works much better with metacity than compiz.  Note - don't close your terminal window after running the above command.  If you want to turn compiz back on, do ```
compiz --replace &
```  I think you can close the terminal window after that command, but I usually just restart my session after switching to metacity when I want to switch back - it restarts my transparent desktop console which I use compiz for and which I usually close after starting metacity.

If that works, and you're okay with disabling compiz in order to do flash stuff, you can make a launcher on your desktop for the above commands.

metacity --replace made no difference for me

---

### Post by dlmarti on 2009-07-07
> **SlugSlug said:**
> 1. what ?? vista since when has that been old as hell or stable ??

2. its just not that flash app its a load i have prob with 

3. yer some other guy on same card claimed no prob...


downgrading to 8.10 would solve this - but its a massive ball ache i just wanna get 9.04 working for me...

Vista is 3.5 years old, and targeted at 4.5 year old hardware.

---

### Post by lovinglinux on 2009-07-07
I haven't read all the posts, but I agree. It sucks.

Here are my personal recommendations:

[url=http://ubuntuforums.org/showthread.php?t=1152095]
Tips: Things that might improve Jaunty performance[/url]

[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

Flash is not playing the way I would like, but is far better than when I installed Jaunty.

---

### Post by martinbaselier on 2009-07-07
@slugslug. The problem with the open source video driver is bad 3D performance. Having compiz without proper 3D hardware acceleration will make the system sluggish. I use xubuntu, so the xfce desktop without compiz.
about xorg.conf. I just use the standard configuration. If you want to see if your configuration is ok, open a terminal and type "glxinfo | grep render" I should output something like : 

direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL

use
cat /var/log/Xorg.0.log | grep EE
to check if there are any errors. 

Try running top to see if anything is using a large amount of your cpu(s)

And you might want to check the performance threads from lovinglinux. I haven't read them yet, but I'm planning to. Also keep in mind that ubuntu is not the fastest distribution around. Though it is one of the user friendliest. 


Als

---

### Post by lovinglinux on 2009-07-07
> **martinbaselier said:**
> @slugslug. The problem with the open source video driver is bad 3D performance. Having compiz without proper 3D hardware acceleration will make the system sluggish.

Here is another discussion, that ended without an explanation, about the performance off html5 video and embedded flash, compared to playing the same videos locally on the same machine with gnome-mplayer.

> **lovinglinux said:**
> [QUOTE=HavocXphere;7547606]You're right in that theora does in principle use more cpu cycles....

*....removed to spare some space...*

...

And finally, h264 (which youtube uses) can be GFX card accelerated. So I'd expect the flash variation to use less CPU cycles since it is *probably* being off-loaded to the gfx card. Theora is not gfx accelerated.


Thanks for this excellent explanation. I guess you might be able to explain why the theora video uses 66% of my CPU (sum of [color=#CC0000]firefox[/color]+xorg cpu usage), while the same video/codec uses 14% of my CPU (sum of [color=#33CC00]mplayer[/color]+xorg cpu usage), when downloaded and played with gnome-mplayer?

Also why the same video using h264 codec uses 45% of my CPU (sum of [color=#CC0000]firefox[/color]+xorg cpu usage), while the same video/codec uses 9% of my CPU (sum of [color=#33CC00]mplayer[/color]+xorg cpu usage), when downloaded and played with gnome-mplayer?

Most of the extra CPU usage while viewing theora in Firefox goes to xorg cycles. I believe this in line with your explanation, but it doesn't invalidate the fact that both video technologies are much more CPU intensive when viewing through Firefox than viewing with gnome-mplayer. In this scenario, the extra load of theora codec makes the html5 video worse than flash in terms of CPU usage and user experience.

Don't get me wrong. I admire the initiative of Firefox to enable html5 video already and I do understand the benefits. Who would want flash when you can play videos natively, using open source codecs? But for someone who loves Firefox (yes I do, I can't live without it for years, even when I was a Windows user), Ubuntu and videos, this is disappointing, specially because I thought it could improve my video experience.[/QUOTE]

The comparison above was made using nVidia prorietary drivers with compiz. If that was the problem, then I shouldn't get much better preformance while playing the videos locally. My system is not sluggish, just flash and html5 videos embedded in Firefox.

---

### Post by SlugSlug on 2009-07-08
> **martinbaselier said:**
> @slugslug. The problem with the open source video driver is bad 3D performance. Having compiz without proper 3D hardware acceleration will make the system sluggish. I use xubuntu, so the xfce desktop without compiz.
about xorg.conf. I just use the standard configuration. If you want to see if your configuration is ok, open a terminal and type "glxinfo | grep render" I should output something like : 

direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL

use
cat /var/log/Xorg.0.log | grep EE
to check if there are any errors. 

Try running top to see if anything is using a large amount of your cpu(s)



And you might want to check the performance threads from lovinglinux. I haven't read them yet, but I'm planning to. Also keep in mind that ubuntu is not the fastest distribution around. Though it is one of the user friendliest. 


Als

cheers, no errors there and when i hit the said site firefox and Xorg are at the top of cpu usage Xorg more so......

---

### Post by SlugSlug on 2009-07-08
> **lovinglinux said:**
> Here is another discussion, that ended without an explanation, about the performance off html5 video and embedded flash, compared to playing the same videos locally on the same machine with gnome-mplayer.



The comparison above was made using nVidia prorietary drivers with compiz. If that was the problem, then I shouldn't get much better preformance while playing the videos locally. My system is not sluggish, just flash and html5 videos embedded in Firefox.

yes this does seem to be the case with me :(

---

### Post by SlugSlug on 2009-07-08
> **lovinglinux said:**
> I haven't read all the posts, but I agree. It sucks.

Here are my personal recommendations:

[url=http://ubuntuforums.org/showthread.php?t=1152095]
Tips: Things that might improve Jaunty performance[/url]

[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

Flash is not playing the way I would like, but is far better than when I installed Jaunty.

cheers I'll take a look at these tonight

---

### Post by martinbaselier on 2009-07-08
@slugslug. Your problem is not with HTML5. The site you pointed to does not have the new HTML5 video tags in it,  that lovinglinux spoke about.(as far as I know ff3.5 is the first to support it) 

Because of some other problems, I just started firefox with a clean profile, no add-ons (except for the previously installed plugins), no ad block. 

I opened the site and firefox stayed around 50% cpu (of 800Mhz) I already had 5 pages open. Xorg is somewhere between 2-5% procent with a few peaks upto 10%.

---

### Post by SlugSlug on 2009-07-08
> **martinbaselier said:**
> @slugslug. Your problem is not with HTML5. The site you pointed to does not have the new HTML5 video tags in it,  that lovinglinux spoke about.(as far as I know ff3.5 is the first to support it) 

Because of some other problems, I just started firefox with a clean profile, no add-ons (except for the previously installed plugins), no ad block. 

I opened the site and firefox stayed around 50% cpu (of 800Mhz) I already had 5 pages open. Xorg is somewhere between 2-5% procent with a few peaks upto 10%.

just tried it from new profile - same prob

---

### Post by SlugSlug on 2009-07-08
- I also notice a pretty major lag when I visit a site with a load of jpegs....  ( download speed is not the problem)

---

### Post by martinbaselier on 2009-07-09
To pinpoint the location of the problem you'd need to give a bit more information. The problem can be caused by many factors or even a combination.

What's the CPU usage approximately for firefox and for xorg and if evident for other backgroundprocesses? What kind of cpu do you have? Single core, dual core, how fast? 

Is there a lot of harddisk activity? If so, how fragmented is your disk? To see the fragmentation, reboot, start in recovery mode, run fsck and it will show you the percentage. 

Have you tried any of the tips of the links provided by lovinglinux? If so which ones did you trie and did you notice any difference after applying them? What's your score on the diskkeeper benchmark? (after rebooting with only firefox opened and no other pages)

@lovinglinux. Firefox 3.5 handles the video differently. You can apply javascript and all kind of filters to it. I don't know how that's implemented, but I can imagine if certain filters are already loaded, it would take more cpu-power than using a regular player. [Watch this.]("(http://www.youtube.com/watch?v=3tLBLVtIk3A)")

---

