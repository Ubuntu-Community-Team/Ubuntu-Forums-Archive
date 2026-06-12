---
title: "Flash Video Flickering in Karmic?"
date: 2009-11-03
forum: Multimedia Software
---

### Post by jasonditz on 2009-11-03
Since upgrading to Karmic last week I notice some new issues with Flash video playback. 

About: Running Karmic 64-bit on a quad core system with 8 GB of ram. Using Metacity. 

Problem: Some sites (NBA.com league pass, Hulu) video playback flickers intermittently, rendering it virtually unwatchable. When watched in full screen the flickering disappears entirely in both cases, it's only there when watching in a window. Other video sites (Youtube) aren't affected. 

Watching Hulu videos in a window didn't experience this problem before installing Karmic.

Tried uninstalling and reinstalling Flash in synaptic, didn't help.

---

### Post by wWales on 2009-11-10
im using amd64 version of the kernel and the flashplugin-nonfree packadge.

Ive noticed this too, but only on embedded videos. it seems there are some details about the embedded video that flickers in the "background"

---

### Post by cmdrtebok on 2009-11-11
I have been having this same problem too. I am running 32bit ubuntu 9.10 on an AMD64X2 processor with the nvidia drivers on the repos. It happens most often on embedded videos like wWales but the same kind of flickering happens with some flash games.

I tried uninstalling flash and reinstalling adobe-flashplugin but that did nothing. Turning off compiz/desktop effects doesn't help either.

---

### Post by nunovi on 2009-11-21
Hi,

It's a well known problem that flash on Linux performs horribly slow, especially on Atom-based system as the GPU is not used. I don't want to discourage you but there is really no solution other than Adobe to fix Flash on Linux.

If we make this issue big enough, we can gain a higher priority for Adobe to solve this issue. Please go to [https://bugs.adobe.com/jira/browse/FP-1692](https://bugs.adobe.com/jira/browse/FP-1692), register and vote for this issue. If we all take 5 minutes to do this, I'm sure we can reach a very high number of votes and let Adobe know Linux is an important community to take into consideration.

Nuno

---

### Post by ubun_two on 2009-12-13
> **nunovi said:**
> Hi,

It's a well known problem that flash on Linux performs horribly slow, especially on Atom-based system as the GPU is not used. I don't want to discourage you but there is really no solution other than Adobe to fix Flash on Linux.



But if that's true, it doesn't make sense that Flash didn't flicker at all when I was on Jaunty on the same machine, watching the video from the same site.

Doesn't that mean there was changes in Karmic that made Flash act slower? :-k

---

### Post by Libra289 on 2009-12-17
Same problem guys, since when I upgraded to Karmic have the flash flickering problem when playing in pop out window and the bigger the window the worst the problem. The problem appears to be as described by wWales (details about the embedded video that flickers in the "background")
Have followed nunovi advise and voted for the issue to be fixed by Adobe on [https://bugs.adobe.com/jira/browse/FP-1692](https://bugs.adobe.com/jira/browse/FP-1692).
How long for a solution? There are so many posts around but so far nothing useful or applicable to my system.

I'm using Flash plugin v. 10,0,42,34 (according to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) ) 
Ubuntu 9.10 (Karmic Koala) 
Browsers: Firefox and Chrome
lspci -nn | grep VGA 
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] [10de:01d7] (rev a1)

---

### Post by jstapels on 2009-12-19
For what it's worth, I tried the latest prerelease (10,1,51,66), and I still have the flickering problem. :(.

I feel like this problem is somewhat recent, and didn't happen before the latest flash security update.

---

### Post by DrJohn999 on 2009-12-20
My latest system, Karmic x64 on a Phenom II x4 945 (3.0GHz) with 4 GB DDr3 1600 RAM on Asus M4A78T-E and a nVidia 9500 GT 512 MB card runs Flash and Hulu Desktop fairly well; good enough to watch. But, this eats up to 75% of the CPU time, which is amazingly high usage considering the speed of this system.

Another system I have is not as fast and doesn't work at all well with Flash: Karmic x64 on a Phenom 9600 (2.3 GHz) quad core with 2 GB Ram on Asus M3N78-EM using the built-in GEForce 8300 GPU. It goes right to 100% and isn't viewable. It's not the GPU, either; I tried the 9500 GT card from the above system in this one but that made no difference.

Interestingly, running Flash inside a Windoes 7 x64 VirtualBox with two cores was even worse than the slower Karmic system. Didn't matter whether in Firefox, IE8, or Hulu Desktop. Considering that the VM is not offered any GPU H/W acceleration, I wonder if Windoes has the same problems on low-end non-accelerated boxes? Also makes a case for Adobe not detecting the GPU correctly in Karmic.

Looks like one solution would be brute-force computing power, but come on, Adobe, just fix it like it used to run!

I registered, voted, and commented on this issue at [https://bugs.adobe.com/jira/browse/FP-1692](https://bugs.adobe.com/jira/browse/FP-1692)

---

### Post by danbh on 2010-01-02
hey guys, I found some answers for the flash flickering.

I post my findings on my blog: [http://chogydan.blogspot.com/2010/01/flashy-flash-flashin-ubuntu-karmic.html](http://chogydan.blogspot.com/2010/01/flashy-flash-flashin-ubuntu-karmic.html)

---

### Post by yochaigal on 2010-01-11
Disabling global tooltips in gconf (as per the previous posts' link) fixed the problem for me.

Thanks!

---

### Post by goebbe on 2010-01-13
Unfortunately, disabling global tooltips didn't change anything for me. :-(
Guess I have to poke around with the kernel.

---

### Post by Anuovis on 2010-01-13
> **goebbe said:**
> Unfortunately, disabling global tooltips didn't change anything for me. :-(
Guess I have to poke around with the kernel.

I am not sure about the kernel thing. Unless you know what you are doing and absolutely need normal flash performance right now, you could just wait for Lucid Lynx. It comes out in 3 months and hopefully will get these things right since it is an LTS version. Hopefully.

---

### Post by boriskarloffinablender on 2010-01-13
> **jasonditz said:**
> Since upgrading to Karmic last week I notice some new issues with Flash video playback. 

About: Running Karmic 64-bit on a quad core system with 8 GB of ram. Using Metacity. 

Problem: Some sites (NBA.com league pass, Hulu) video playback flickers intermittently, rendering it virtually unwatchable. When watched in full screen the flickering disappears entirely in both cases, it's only there when watching in a window. Other video sites (Youtube) aren't affected. 

Watching Hulu videos in a window didn't experience this problem before installing Karmic.

Tried uninstalling and reinstalling Flash in synaptic, didn't help.

are you using ati?

---

### Post by sleepee on 2010-01-16
i'm  having the same problem with 64 bit 9.10..
my understanding is that flash has sketchy support for 64bit and that's the cause of the problem...
you can download the 64 bit flash beta from adobe's site and try it out, but from my experience... it's not working too well..

---

### Post by yochaigal on 2010-01-21
I should mention that the problem persists on embedded flash videos; I added myself to the "video" group but didn't see too much success...

---

### Post by boteeka on 2010-02-04
This is happening for at least the last two versions of Ubuntu, including Karmic.

I have integrated Intel GMA965 graphics.

One interesting observation: if I keep moving the mouse cursor while the video is playing the flickering stops, but once I stop moving the mouse the flickering returns.

---

### Post by apirec on 2010-02-05
I experience exactly the same things including the "mouse-moving-workaround" :-)
I have a radeon 9000 mobility.

---

### Post by Anuovis on 2010-02-06
Yes, mouse helps a bit :D
ATI Mobility Radeon 1400 here.

---

### Post by 4ebees on 2010-02-06
> **Anuovis said:**
> Yes, mouse helps a bit :D
ATI Mobility Radeon 1400 here.

I have Karmic on a Quad Asus with the latest (repo) Firefox 3.6.1 pre Namoroka.

I had no prob with 8.04 (on this or my other machines).

I'm going to try the tool-tips suggestion and report back.

Some additional information:

When using Chrome I do not have the same problem with flickering!

---

### Post by Madmoose on 2010-02-10
I turned off tooltips, and I still have the issue myself. I'll wait for the next release.

---

### Post by wyild1 on 2010-02-25
Using Kubuntu 9.10 Having the problem on embedded more than inside Youtube.

Here are my examples:
[http://arstechnica.com/gaming/news/2010/02/super-mario-galaxy-2-hits-523-yoshi-drills-2d-gameplay.ars](http://arstechnica.com/gaming/news/2010/02/super-mario-galaxy-2-hits-523-yoshi-drills-2d-gameplay.ars)

That video flickers but when you go to the video on YouTube:
[http://www.youtube.com/watch?v=wgHgQF4uWcA&feature=player_embedded#](http://www.youtube.com/watch?v=wgHgQF4uWcA&feature=player_embedded#)

It plays great! I am using an eeepc 900HA (1.6Ghz Atom) and i find that the "mouse movement" trick during the embedded versions slows down the playback.

So ya its something with those embedded ones and whatever that is behind the videos is causing the flickering.  Not ready to just try a different kernel yet, so i guess ill wait for the upgrade!

Cheers!

---

### Post by crparis on 2010-03-03
I seem to notice it more on flash games than videos.  The best way to describe it is that the flash "layers" are flickering.  When playing Bloons Tower Defense 4, there is LOTS of flickering that I do not get on a Windows box.  I recorded a video of it (with recordmydesktop) and the video recording captures the unpleasant flickering experience perfectly:

[http://drop.io/2zjos9y]("http://drop.io/2zjos9y")

I'm not in a position that I can install Lucid to test and see if it goes away, and the "disable tooltips" suggestion did not work for me.



Edit to add some spec info:

Ubuntu 9.10
lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: nVidia Corporation G73 [GeForce 7600 GS] [10de:0392] (rev a1)
compiz off

---

### Post by kozjegyzo on 2010-03-09
> **crparis said:**
> I seem to notice it more on flash games than videos.  The best way to describe it is that the flash "layers" are flickering.  When playing Bloons Tower Defense 4, there is LOTS of flickering that I do not get on a Windows box.  I recorded a video of it (with recordmydesktop) and the video recording captures the unpleasant flickering experience perfectly:

[http://drop.io/2zjos9y]("http://drop.io/2zjos9y")

I'm not in a position that I can install Lucid to test and see if it goes away, and the "disable tooltips" suggestion did not work for me.



Edit to add some spec info:

Ubuntu 9.10
lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: nVidia Corporation G73 [GeForce 7600 GS] [10de:0392] (rev a1)
compiz off


Same thing here. Videos are ok, but the flash games that I like to kill ample time with are horribly flickering. You described it great, it seems like the layers are fighting each other. Interestingly there are games where everything seems to be ok.
An other thing is global video playback seems to be affected as well, with horizontal lines appearing when there's fast movement in the video. Turning Compiz off helps a bit, but it's not a definite solution.

I hope the next release will cure these problems...
Until then, I'm open for solutions :)

Specs:

Dell XPS M1530
Intel Core 2 Duo T9300 @ 2.50 GHz
Ubuntu 9.10
NVIDIA GeForce 8600M GT
NVIDIA Driver Version: 185.18.36

---

### Post by Dalle85 on 2010-03-15
I have been seeing this issue too for months (since I upgraded to Karmic I think) and haven't been able to aid it! I've tried the various solutions I've come across (haven't poked around with different kernels though don't want it that bad) and nothing have helped!

So, as I was reading through this thread, I thought of something I haven't tried before - another browser! And wouldn't you know it: I ran Opera and every flash game and video - embedded or not - renders perfectly! Not a flicker in sight... So can anyone confirm this or is it just me? It seems to be a Firefox issue then (Which would coincide with the upgrade of Firefox together with my Karmic update)!
I'm going to poke around in Firefox and see if I can fix the issue... More latter on!

---

### Post by kozjegyzo on 2010-03-16
> **Dalle85 said:**
> I have been seeing this issue too for months (since I upgraded to Karmic I think) and haven't been able to aid it! I've tried the various solutions I've come across (haven't poked around with different kernels though don't want it that bad) and nothing have helped!

So, as I was reading through this thread, I thought of something I haven't tried before - another browser! And wouldn't you know it: I ran Opera and every flash game and video - embedded or not - renders perfectly! Not a flicker in sight... So can anyone confirm this or is it just me? It seems to be a Firefox issue then (Which would coincide with the upgrade of Firefox together with my Karmic update)!
I'm going to poke around in Firefox and see if I can fix the issue... More latter on!



Wow I'm confirming this, but not believing it :D
Opera does do flash without flicker!
This is strange... Why does Firefox and Chrome have problems then?
Global video playback is still an issue though, but I guess when I feel like playing some flash games, I'll do it in Opera, but for general use Chrome is still my number 1 :)

---

### Post by Dalle85 on 2010-03-16
So, I think the issue is due to Flash 10.0 r45 which is used by Firefox - Opera apparently isn't supported by 10.0 r45 in Linux yet, so it use its own build called 10.0 r12 (again, maybe someone could confirm?) installed as a Opera-specific plugin - not the global Flash-plugin.

Unfortunately, I can't force the global plugin to the earlier build as it isn't in the Karmic-repo - so I can't really check it by reverting to an earlier version. I'll mess around with the repos and see if I can get it to include the old version.

---

### Post by kozjegyzo on 2010-03-16
I hope you can find a solution. I have nothing against Opera, but I prefer Chrome and it would be nice to have flash working there too :)

---

### Post by marius311 on 2010-03-25
Karmic 64bit here with the same problems. I have Firefox/Chrome flickering, but Opera working fine! You can download old versions of flash from [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html), and switching to 10r12 does NOT fix the problem in Firefox/Chrome, so Opera must be doing something different. I've also tried the 64bit version 10, as well as 10.1 using nspluginwrapper, but they all flicker. HOWEVER, version 9 seems to be working pretty well. I can't verify this because the only site that flickered for me (mlb.tv) doesn't work at all with 9, but in general I was actually getting much better performance with 9. Maybe other people can try installing 9 and see if they get any results?

---

### Post by marius311 on 2010-03-26
I have no idea what this has to do with the kernel, but upgrading to >= 2.6.32 made the flickering go from several times a second and pretty much unwatchable to maybe once every ten seconds or so, so you guys could try that.

---

### Post by iwbcman on 2010-03-26
Purely anecdotal and perhaps unrelated:


On my machines (using both Ubuntu 0.10 and Fedora 12) playing flash facebook games like cafe world has been a testament in frustration.

The CPU usage has been staggering, on my macbookpro with intel dual core running Ubuntu I simply had to stop trying-the machine became unuseably slow and it started getting seriously hot, probably could have fried an egg on it. Not good.

On my main machine which has a intel quad-core 9500 I was getting +50% CPU usage across all 4 cores. Ouch

Now it should be noted I do love my desktop effects, so in both cases my machines were using fully decked-out desktop effects.

I alo have been using the very latest 64bit adobe flash plugin.

Well I read somewhere that they had had some luck with midori. On my machine at least Midori starts up pathetically slow(come on Fedora build devs-where did you guys learn to compile ;) ). So I said what the heck, why not try Epiphany, you know that other GNOME browser which has been all but forgotten.

Good news. On my machine at least, Epiphany + Facebook = 1/2 cpu usage in comparison to Firefox and Chrome/Chromium...

Give it a try, it might work for you....

---

### Post by yochaigal on 2010-04-06
This problem seems to have vanished in 10.04 after I upgraded (not a clean install). I can now watch embedded flash videos WITHOUT flickering on my intel 915 chipset laptop (hp dv4000).

So yeah.

---

### Post by bdws1975 on 2010-04-07
I love you man!  Seriously, you just made my year!  Opera works like a charm!!!!!!!!!!!!!!!!!!!


BRett> **Dalle85 said:**
> I have been seeing this issue too for months (since I upgraded to Karmic I think) and haven't been able to aid it! I've tried the various solutions I've come across (haven't poked around with different kernels though don't want it that bad) and nothing have helped!

So, as I was reading through this thread, I thought of something I haven't tried before - another browser! And wouldn't you know it: I ran Opera and every flash game and video - embedded or not - renders perfectly! Not a flicker in sight... So can anyone confirm this or is it just me? It seems to be a Firefox issue then (Which would coincide with the upgrade of Firefox together with my Karmic update)!
I'm going to poke around in Firefox and see if I can fix the issue... More latter on!

---

### Post by abumaia on 2010-10-30
I'm now having this problem in 10.10, Firefox 3.6.12, Flash 10.1r85.  The mouse-wiggle trick still works, too.

---

### Post by ByteTraveler on 2011-02-27
Guys - Same here, and while it's nifty that I can "work around" the bug by changing browsers, I'd rather not.

Can someone please give me some sense of when this bug will be corrected (currently affecting Firefox, Chrome & Chromium for me).

Thanks!

---

### Post by linuxyogi on 2011-06-25
11.04 (32Bit)

Firefox 5.0

Flash ver. 10.3

Nvidia 9500 GT || NVIDIA Driver Version: 270.41.06

Same problem of flickering in FF.

---

