---
title: "Netflix Online"
date: 2009-05-06
forum: Multimedia Software
---

### Post by DLG102282 on 2009-05-06
Has anyone figured a way to watch movies from netflix online in Ubuntu? I was told they werer going to support Linux starting last february, but that hasn't happened.

---

### Post by lvleph on 2009-05-06
Nope, I just decided to not use Netflix anymore. But that also had to do with deciding I was wasting too much time watching movies.

---

### Post by orange-wedge on 2009-05-07
The short answer is that there is no work around if you want to watch Netflix natively in Ubuntu/Linux.

Actually I have just installed Windows XP+Netflix on my Mythbuntu media server using VMWare Player this evening.  It runs Netflix with issues though... occasionally the video will freeze while the audio still plays.  And I have gotten a few BSOD while watching online videos.  Most of these are problems inherent to the VM host not being able to process the virtual session fast enough.  My machine turned 3 years old this month with 4 gigs of ram and an Athlon 64 1.8Ghz, so you might have success with a machine with more horsepower.

The best thing I can suggest, which I've been meaning to do, is to call Costumer Support and request that they support Linux platforms.  Since they are rolling out support for Intel Macs there is almost no reason why M$ can't port a version of Silverlight 2.0 to Linux distros.  While your on the phone with Customer Support suggest PS3 support as well...  :)

---

### Post by jwbwater on 2009-05-28
I'm also using vmplayer to run windows xp just for netflix watch instantly.  Just got this working last night, but haven't noticed any problems with the frame rate.

I tried Virtualbox first, but it was too slow to get the job done on my system.

I have a 1920 by 1080 display and a Pentium dual core E2180 (2 MHz) with 3 GB of ram.

The process I followed for installing vmplayer and vmware-tools (which I needed just to get the network interface working) are described in the following links:

[https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

[http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html)

---

### Post by sxe4ever on 2009-05-31
Is anyone able to watch Netflix through Linux yet??? I would imagine that there's a way to disguise your operating system, isn't there??? I think the only problem is that Netflix's site just doesn't allow Linux.... Or I could be wrong

---

### Post by sirjoebob on 2009-06-01
> **sxe4ever said:**
> Is anyone able to watch Netflix through Linux yet??? I would imagine that there's a way to disguise your operating system, isn't there??? I think the only problem is that Netflix's site just doesn't allow Linux.... Or I could be wrong

Unfortunately, you are mistaken. 

Netflix makes use of silverlight and windows Media Player 11 plugins to render the watch now videos. These are proprietary delivery methods that are not working with wine or any other solution at this time. AFAIK, Linux watch now is way far off.

---

### Post by sxe4ever on 2009-06-06
Yeah, I tried to disguise my CPU as a Mac machine to get around all of that, but it still requested me to install Silverlight and it gave the file as a .dmg so I gave up. It's really unfortunate, you'd think that there would be some way around it

---

### Post by jblackhall on 2009-06-11
If you've got Moonlight 2.0 preview installed, you should be able to load the player.  Unfortunately you still can't play movies last I heard because MS hasn't released the DRM capabilities to the Moonlight devs.  I dunno if I've read of anyone trying to disguise themselves as a Mac with Moonlight installed.  Unfortunately, I still don't think it'll work.

More: [http://silverlight.net/forums/p/94992/217696.aspx](http://silverlight.net/forums/p/94992/217696.aspx)

---

### Post by sxe4ever on 2009-06-12
Blah, it seems like we're getting so close, yet it's all in vain :-/

---

### Post by toopi on 2009-06-12
While we're at it, why not sign the petition at petitiononline for Netflix on Linux.  Here's the link:
[www.petitiononline.com/Linflix/petition.html](www.petitiononline.com/Linflix/petition.html)

Might make a difference, who knows...  *shrugs*

---

### Post by sxe4ever on 2009-06-12
> **toopi said:**
> While we're at it, why not sign the petition at petitiononline for Netflix on Linux.  Here's the link:
[www.petitiononline.com/Linflix/petition.html]("http://www.petitiononline.com/Linflix/petition.html")

Might make a difference, who knows...  *shrugs*

Doesn't seem too work or it's EXTREMELY slow

---

### Post by janz84 on 2009-07-20
> **jwbwater said:**
> I'm also using vmplayer to run windows xp just for netflix watch instantly.  Just got this working last night, but haven't noticed any problems with the frame rate.

I tried Virtualbox first, but it was too slow to get the job done on my system.

I have a 1920 by 1080 display and a Pentium dual core E2180 (2 MHz) with 3 GB of ram.

The process I followed for installing vmplayer and vmware-tools (which I needed just to get the network interface working) are described in the following links:

[https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

[http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html)

wonder if i could get something like that setup with server 2003 through dreamspark

---

### Post by baceman007 on 2009-10-16
I have been working on the Netflix/Ubuntu 9.04 problem for quite some time.
I offer the following obervations with no implied warranty.
I started with looking at the directions here 
[http://fatbuttlarry.blogspot.com/2009/02/netflix-ubuntu.html](http://fatbuttlarry.blogspot.com/2009/02/netflix-ubuntu.html)
but since this user had the most success with 8.04 I had to keep looking. Which lead me to this forum amongst many other places. 
At any rate here's what I did after trying the moonlight 1.99.5, Coral IETab, and User Agent Switcher combinations and only getting as far as the Active X is not enabled screen. I tried ies4linux as well. 

-- At this point I can get a instant movie to load to the point that I get the black backdrop with the swirling blue loading icon on Netflix in Firefox 3.5 run using Wine 1.1.3 with Silverlight 3 and some Windows Fonts installed as explained below.  

-- I added [http://wine.buggetdedicated.com/apt](http://wine.buggetdedicated.com/apt) edgy 
to the Third-Party Software tab under System -- Administration -- Software Sources and added an authentication certificate for winehq. 
[http://ubuntuforums.org/showthread.php?t=338400](http://ubuntuforums.org/showthread.php?t=338400)
this explains getting the winehq gpg key. If you don't have it you should just get a warning when installing. Adding it should make the warning go away forever. This allows you to install the most recent versions of Wine which may not be the stable releases.

-- I then went to System -- Administration -- Synaptic -- and installed Wine 1.1.3, wine-dev 1.1.3, and wine-gecko 1.0.0. Note: In theory after you add the source and refresh the package list, when prompted, the Update Manager should tell you that there is an update for Wine, or if you use Add/Remove to add Wine and then use the Update Manager (System -- Administration -- Update Manager) it should tell you. Anyway, I just used Synaptic so whatever floats your boat. 

-- I downloaded the Windows version of Firefox 3.5 from [www.Mozilla.com/Firefox3.5](www.Mozilla.com/Firefox3.5), went to Application -- Wine -- Browse C: drive and dropped the *.exe in there. I then double clicked on it and installed it. 

-- Launch Firefox 3.5 using Wine, go to Netflix and log in, then choose something to watch instantly. You will then be told to download Silverlight 3. Save the *.exe file for it and move it into your Wine C: drive as explained in the last step. 

-- Close Firefox and install Silverlight. If you go to Netflix again at this point you will get a font error stating that you must be a Crapple user if you're getting a font error. Of course you're not, but Netflix believes that people only use Windoze and OSXcrament so that's what you get. If they didn't believe this they would have just used something that already works on everyone's systems instead of painting themselves into a corner with Silverlight... I still like Netflix, but the whole Silverlight thing gets on my nerves...  

-- Anyway, to solve this font problem you need to move some Windows fonts into your Wine virtual C: drive\windows\fonts folder. I copied them from my legal copy of Windows in it's C:\Windows\Fonts folder. I have a dual boot setup so this was easy. I'm sure some linux font guru probably has a welcome substitution to this step that doesn't involve having to use Crapple or Microshaft fonts but that's what I did. 

-- Once you do this, at least for me, when I go to Netflix using Firefox 3.5 and Silverlight 3 run through Wine I get the movie to start to load, then my browser freezes and goes grey. Anyway, it's at least promising. 

-- I should mention that I'm using a Toshiba laptop that is using the generic Ubuntu video driver. I was never able to get fglrx to work totally so I went back to the generic. I sometimes get white lines on the right hand side of the screen when I scroll and 2ndary monitor support is not existent so perhaps I have larger problems and someone else, with a Dell for example, may have more luck with my steps. Perhaps the video driver has nothing to do with it at all. Anyway, I hope this helps someone out.

---

