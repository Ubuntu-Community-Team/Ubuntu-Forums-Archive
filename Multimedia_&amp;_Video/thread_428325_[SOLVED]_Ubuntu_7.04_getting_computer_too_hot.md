---
title: "[SOLVED] Ubuntu 7.04 getting computer too hot"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Jaxilian on 2007-04-30
I installed Ubuntu 7.04 on my laptop (Ati X600 chip) and everything worked like a charm. I got Beryl to work and just about every hardware part on it worked perfectly.....BUT one thing.

The laptop gets superhot when I am playing my game World of Warcraft. I mean it gets so hot that I burned myself real bad when I accidently touched the metal connectors on the back of it.
The computer has turned itself off a couple of times cause of the heat.

Well...you might think I played too long or that it was hardware related, but then I tried with Windows. I thought I'd install it because I wanted to see the difference.

I played constantly for 5 hours and there was not the same heat. Sure it was warm, but I wasn't even close of burning myself.

This incident kinda leads me towards whether if Ubuntu can permanently damage my computer or not. I run Windows XP now cause I don't wanna risk anything getting broken.
The FPS ingame was a lot better too. In Windows I got 60fps and in Ubuntu with Wine I got 5-20fps (it was playable though) :lolflag: 

Anyone with same experience as me? :(

---

### Post by noneofthem on 2007-05-06
Same problem here. Laptop gets very very hot after a while. Especially when doing a lot with video and/or 3D applications/games. No solution found yet.

---

### Post by Wiebelhaus on 2007-05-06
these are hardware issues , Ubuntu has excellent power regulating ,Vista on the other hand has HP/comaq defecating on themselves (check the news) if there's an air compressor around disassemble and blow out the fans , heatsink , copper vent , clean and reapply thermal grease, or take it to a shop and ask them to do it , keep the laptop off of blankets , table cloth , pillows and make an effort to keep it clean.

---

### Post by rockingmtranch on 2007-05-06
Not sure if this is any help. Last night I went into my nvidia settings (desktop) and noticed that the fan on my 7600 GT sped up. It never slowed back down. I'll try to investigate this further.

---

### Post by Jaxilian on 2007-05-08
> **sx66gns said:**
> these are hardware issues , Ubuntu has excellent power regulating ,Vista on the other hand has HP/comaq defecating on themselves (check the news) if there's an air compressor around disassemble and blow out the fans , heatsink , copper vent , clean and reapply thermal grease, or take it to a shop and ask them to do it , keep the laptop off of blankets , table cloth , pillows and make an effort to keep it clean.

Hmm....as far as my computergoes. Ubuntu doesn't seem to handle the heat so well. Now when I run windows on it, It never gets hot. It gets hot, but never so you burn yourself on the keys or the metal connectors on the back...like when Ubuntu runs on it. It's a laptop that I have so I can't do much about it.

Ubuntu runs great on it and everything works, everything but the heat regulating. damn shame cause I wanted to run Ubuntu.

---

### Post by Jaxilian on 2007-06-08
hmm The heat on my Compaq Evo N610C is also getting superhigh when running Ubuntu.
If I leave it on for a full day, I will burn myself on it. That never happened when running Windows.

Can any explain this? I don't like the idea of linux making my computers into possible firestarters.

---

### Post by Chappy7777 on 2007-06-08
I have an old Toshiba Tecra Laptop from the stone age that gets hot enough running Windows 98. I can't change the OS since my wife dropped it and scmucked the corner where the CD player is, and I can no longer close the CD well enough to run it. Fortunately I just use it for playing MP3s when I do my radio show sat am.Anyhow, it gets warm, but since it's plastic it conducts the heat better than the aluminum cases. What I do with mine is place it on an upside down wooden tangerine box, :) and it's not touching me and gets a good airflow underneath. The main thing is that airflow. The bottom needs to be off the table, lap, whatever. I know you can buy "trays" or whatever, that sit on your lap, under the laptop, and they allow the air to move, and keep you from frying your lap. Best idea is to put a couple of flat frozen cooler packs between you and the laptop. That will keep it cool. I would be more concerned w/melting the laptop than w/cooking my legs. I am too awake to cook myself. 

All I can think of is that 7.04 is using a lot more CPU and/or video than XP does, since that's where the heat comes from. Also, I never have heat probs w/mine in the winter, as I live in Ontario and it's often -30 outside.
When I get to the studio sat am, I'm the 1st one there, and it's about 40* in there. No concern w/overheating anything at those temps.

Keeping cool,
Chappy

---

### Post by TmP on 2007-06-09
I also have a Toshiba Tecra laptop, but it is getting too hot.

Especially in the hard drive compartment.

Also, after I installed Feisty, I had some issues with restarting the machine. The screen would go blank and do sth in the background. If I tried to shut the computer down in stead of trying to restart it, the disks would stop suddenly with a laud click. A kernel update fixed the second problem but the rest remains.

It's time to go back to Windows for a few weeks. We'll see if it will be fixed.

---

### Post by djmaxmalta on 2007-06-09
> **flodis said:**
> Hmm....as far as my computergoes. Ubuntu doesn't seem to handle the heat so well. Now when I run windows on it, It never gets hot. It gets hot, but never so you burn yourself on the keys or the metal connectors on the back...like when Ubuntu runs on it. It's a laptop that I have so I can't do much about it.

Ubuntu runs great on it and everything works, everything but the heat regulating. damn shame cause I wanted to run Ubuntu.
i have a laptop 2 but the thing is that ubuntu dosent super hear my ventilation just keeps it cooler then windows it has turnd off after 2 and a half days on with blender 3d running

but windows with flight simulatior or san andreas or fifa 07 yes it has been know to power surge my fan!! and in malta the average heat is 35 - 45 degrees celsius so ubuntu might be designed for northen african or mediteranan wheater?

---

### Post by naraic on 2007-06-10
I'm also having that problem on my Compaq N610c. When I type  "acpi -t" into terminal, it shows "Thermal 1" Temperature to be around 70degrees C. Its too hot to have on my knees and even after being idle with the screen closed, the problem persists.
:icon_frown:

naraic

---

### Post by djmaxmalta on 2007-06-10
> **naraic said:**
> I'm also having that problem on my Compaq N610c. When I type  "acpi -t" into terminal, it shows "Thermal 1" Temperature to be around 70degrees C. Its too hot to have on my knees and even after being idle with the screen closed, the problem persists.
:icon_frown:

thanks for the therminal code and yes mine came 64 thermal 1 adn thermal 2 is 79, but mine ide with music and firefox and messingers running for a while and okay some updates its when ur running some multimedia app that it heats up

---

### Post by RobMBaker on 2007-06-10
Have the people that are reporting problems actually had a look inside their heat-sinks? I realise that if Windows isn't causing a problem, you're reluctant to think it's a hardware issue, but it could be a bit of both i.e. Ubuntu happens to be more CPU-intensive for certain tasks, and so will accentuate any cooling issues you have.
Two of my flatmate's laptops recently had this same problem, but in Windows, as there was a build-up of fluff inside the copper-tube heatsink.

It's worth a try, right?

Also, I have a Toshiba Satellite Pro L20, and regularly leave it on all day with no ill effects. I have also used it to generate massive archives with 7-zip for several hours at a time, in the Aussie-summer heat; without any problems - even with the CPU at 100% the whole time. Granted, my Thermal 1 temperature goes up from about 52C to maybe 56 after a while (I've not looked at the actual T after an hour).

---

### Post by RobMBaker on 2007-06-10
I just realised - those who report problems: are your fans running full-whack when it's really hot, or is that your concern; that the CPU's getting hot without the fans kicking in?

If the fans are running at max speed, then obviously it's a hardware issue; as the OS would already be doing all it can to cool the thing down. I did see a thread on here a while ago about modding your Ubuntu thermal-control parameters, but I forget where, sorry.

---

### Post by Jaxilian on 2007-06-12
yea and if you have like I have, a wireless card on top of that heat.....well...I burn my lap easily.

My other laptop which is a newer one, still gets very hot and that has builtin wireless. I'd say if you burn your fingertops on the keyboard keys...well then it's way way too hot.

Dunno if it's related to 3D acceleration on the ATi chips that both laptops have.

---

### Post by Jaxilian on 2007-06-12
> **RobMBaker said:**
> Have the people that are reporting problems actually had a look inside their heat-sinks? I realise that if Windows isn't causing a problem, you're reluctant to think it's a hardware issue, but it could be a bit of both i.e. Ubuntu happens to be more CPU-intensive for certain tasks, and so will accentuate any cooling issues you have.
Two of my flatmate's laptops recently had this same problem, but in Windows, as there was a build-up of fluff inside the copper-tube heatsink.

It's worth a try, right?

Also, I have a Toshiba Satellite Pro L20, and regularly leave it on all day with no ill effects. I have also used it to generate massive archives with 7-zip for several hours at a time, in the Aussie-summer heat; without any problems - even with the CPU at 100% the whole time. Granted, my Thermal 1 temperature goes up from about 52C to maybe 56 after a while (I've not looked at the actual T after an hour).

Don't need to look inside. I compared Windows installation with Ubuntu installation and played the same game for the same amount of time and even just browsing internet for the same amount of time on both installations.
Windows = doesn't even get hot at all. (well only if I feel the blowout hole)
Ubuntu = dangerously hot. meaning I really get burnmarks on my fingers

---

### Post by eye208 on 2007-06-12
> **flodis said:**
> laptop (Ati X600 chip)
Which video driver are you using?

The OSS "ati" driver will resort to software rendering for many operations as it does not fully support the X600 GPU. This will cause the CPU to heat up.

The proprietary "fglrx" driver ... well, no one knows exactly how it works since it is closed source. It is certainly not as well optimized as the Windows driver, hence the difference in FPS. It probably does some software rendering too. ATI has put much more effort in Direct3D support than OpenGL. WoW probably uses Direct3D on Windows.

Add that to the CPU overhead caused by emulating the Windows API, sound etc. for WoW, then you get an idea where the heat might be coming from.

It is certainly not an issue of Linux or Ubuntu itself. I am running it on a P4 with Intel graphics in my office, and that machine is silent even under load, i.e. the fans have no difficulty keeping it cool.

No matter what is causing the heat on your side, if the computer is turning itself off, then there's a thermal design problem involved as well.

---

### Post by Jaxilian on 2007-06-12
> **eye208 said:**
> Which video driver are you using?

The OSS "ati" driver will resort to software rendering for many operations as it does not fully support the X600 GPU. This will cause the CPU to heat up.

The proprietary "fglrx" driver ... well, no one knows exactly how it works since it is closed source. It is certainly not as well optimized as the Windows driver, hence the difference in FPS. It probably does some software rendering too. ATI has put much more effort in Direct3D support than OpenGL. WoW probably uses Direct3D on Windows.

Add that to the CPU overhead caused by emulating the Windows API, sound etc. for WoW, then you get an idea where the heat might be coming from.

It is certainly not an issue of Linux or Ubuntu itself. I am running it on a P4 with Intel graphics in my office, and that machine is silent even under load, i.e. the fans have no difficulty keeping it cool.

No matter what is causing the heat on your side, if the computer is turning itself off, then there's a thermal design problem involved as well.


I'm using the "fglrx" driver. (the only that works)
It's not just when playing WoW under Wine that it gets hot. It's also when I am just browsing the web, but have Desktop effects activated.
This is not normal.
and no...there no thermal design problem with my computer as Windows runs great on it. I can run WoW on it with Windows for several days in a row if I wanted to without it getting hot.

---

### Post by RobMBaker on 2007-06-12
Are you using an out-of-the-box install of Ubuntu, or have you done any serious kernel modification, or anything like that? i.e. have you fiddled around (intentionally or not) with the power-management?

And did you say whether the fans come on full before the computer turns itself off, or not? Because even if the CPU is running at 100% (not overclocked) all the time, the cooling should be able to dissipate the heat.

Maybe it's an issue with your GPU - mine is only a crappy Ati Xpress 200M ... but I do run it with 3D acceleration on (with fglrx) with no problems. But again, the hardware should be able to dissipate the heat, as long as the software is correctly telling it what to do.

---

### Post by eye208 on 2007-06-12
> **flodis said:**
> I'm using the "fglrx" driver. (the only that works)
It's not just when playing WoW under Wine that it gets hot. It's also when I am just browsing the web, but have Desktop effects activated.
From openSUSE's XGL FAQ:
> **Direct rendering does not work when running Xgl, but it does on Xorg. Why are OpenGL applications not accelerated?**
Do not intermix hardware acceleration and direct rendering. OpenGL applications will be hardware accelerated on Xgl if the driver supports pBuffers or FBOs, like the nvidia and fglrx drivers do. [color=red]Direct rendering on the other hand is impossible to implement at the moment[/color], the necessary extensions for implementing that feature are not even specified yet, let alone being implemented.
Direct rendering implies hardware acceleration, but not the other way round. Direct rendering is a bit faster than indirect rendering, but indirect rendering is not as bad as it sounds.
**How can I check whether I have direct rendering on Xorg?**
Direct rendering is active if running glxinfo|grep direct on top of Xorg (not Xgl!) shows you "Yes". On top of Xgl this will always show you "No". Unfortunately, for Xorg having direct rendering is a synonym for having accelerated graphics, and it is more difficult to detect whether hardware accleration is available than it is to detect direct rendering.
Running Compiz/Beryl is similar to running a game. It is not much different from Vista's "Aero" which will also heat up the system. There are two things you can do. Either turn off desktop effects or use ATI's "PowerPlay" feature to lower the card's clock speed.

> This is not normal.
and no...there no thermal design problem with my computer as Windows runs great on it. I can run WoW on it with Windows for several days in a row if I wanted to without it getting hot.
You did not get my point. If any type of software can bring your computer down just by generating heat, then its thermal design is flawed.

---

### Post by Jaxilian on 2007-06-12
> **RobMBaker said:**
> Are you using an out-of-the-box install of Ubuntu, or have you done any serious kernel modification, or anything like that? i.e. have you fiddled around (intentionally or not) with the power-management?

And did you say whether the fans come on full before the computer turns itself off, or not? Because even if the CPU is running at 100% (not overclocked) all the time, the cooling should be able to dissipate the heat.

Maybe it's an issue with your GPU - mine is only a crappy Ati Xpress 200M ... but I do run it with 3D acceleration on (with fglrx) with no problems. But again, the hardware should be able to dissipate the heat, as long as the software is correctly telling it what to do.


Yes I am using out-of-the-box install of Ubuntu 7.04 and no I haven't fiddled anything with the kernel or powermanagement.
The fans are working are keep spinning up and down depending on what I do.

---

### Post by Jaxilian on 2007-06-12
> **eye208 said:**
> From openSUSE's XGL FAQ:

Running Compiz/Beryl is similar to running a game. It is not much different from Vista's "Aero" which will also heat up the system. There are two things you can do. Either turn off desktop effects or use ATI's "PowerPlay" feature to lower the card's clock speed.


You did not get my point. If any type of software can bring your computer down just by generating heat, then its thermal design is flawed.

Ok so then Ubuntus thermal design is flawed.

Either Vista with aero or XP causes any serious heat on my computer.....just Ubuntu.

---

### Post by eye208 on 2007-06-12
> **flodis said:**
> Ok so then Ubuntus thermal design is flawed.
My laptop (Radeon Mobility X700) is running it just fine.

---

### Post by trippinnik on 2007-06-12
Can we get some actual data on temperatures?  Try using one of the gnome applets for this.  I've used this one [http://computertemp.berlios.de/](http://computertemp.berlios.de/) and it has an option to log the results to a txt file.  It will monitor CPU, HD and GPU (if your GPU has this option).  There's also a thread here about setting trip points for your CPU and what action to have the computer take at certain temps.  

Since we are also comparing the temps from windows, you can use utilities to track the temps there as well.  I'm not arguing that it's not happening, but some numbers could be helpful.  You'll want to search for the Max and Normal Operating temps for you CPU and GPUs.

---

### Post by nine01a on 2007-06-12
Strangely enough, Ubuntu 7.04 seems to run a lot hotter than Gentoo does. It's even more strange that I the newer kernels have improved thermal management or something and on Gentoo, I'm using a 2.6.14-nitro2 kernel. Makes me wonder.

---

### Post by noneofthem on 2007-06-12
My problem is that my laptop even gets hot when I am doing nothing with it. I just have to wait and it will go to 42 degrees C. I know that is not too bad technically. However at temperatures over 40 degrees my laptop begins to be really slow and buggy. When playing 3D games like Open Arena I have to even switch it of for a couple of minutes every 20 minutes or so. Otherwise it will freeze and I will only get it to work again by switching it off with the power button! This is pretty bad and I hope there will be a fix soon!

none of them

---

### Post by RobMBaker on 2007-06-12
40 degrees is pretty cold! (on a warm day, anyway)
I have my Toshiba Satellite Pro idling at around 54C ... with no problems. My BIOS controls the active (fan) cooling; and Ubuntu is set to never use passive control (throttling).

I had a (long) read of this bug report last night, which some of you may find a fix in:-
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/22336](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/22336)

Does anyone know if Windows uses passive temperature control or not? If it does, it could just be a hardware flaw that Windows is working around (quite effectively, I might add). Really though, I always try to get laptops/desktops with good BIOS control of cooling etc.

I hope that link to the bug report gets some of you up and running again - you might want to search the posts for "powernowd", as that seemed to be a source of a few people's grief.

---

### Post by RobMBaker on 2007-06-12
OK, I just did a little test-run, to see if it is a generic Ubuntu fault.

I just put a full Ubuntu installation .iso into a maximum-compression 7z archive; which uses full cpu for about half an hour on my machine.
I've been watching Thermal 1 temperature, with "watch acpi -V", and it's gone from 52C (idle) up to fluttering between 59/60C every 20secs or so. My cpu fan isn't even going crazy; it's *just* audible to me. Then when the cpu usage drops back to 1 or 2%; my temp drops off to 54C within a few seconds (maybe 7 or 8).

So, my machine works fine. The (possibly) relevant settings I'm using are:
1) My BIOS is set to use a "Performance" cooling policy, rather than "Silent"
2) cat /proc/acpi/thermal_zone/*/trip_points returns the following:
[INDENT]critical (S5):           110 C
passive:                 125 C: tc1=2 tc2=3 tsp=40 devices=0xc1a34874 
[/INDENT]

As you can see, it appears mine is never going to use passive cooling; not with a cut-in temp that's higher than critical!
This makes me think that maybe the problem is down to bad Ubuntu drivers for your specific cooling hardware or something i.e. Ubuntu can't turn the fan on when it needs to?

One other question: flodis, are you using active or passive cooling? i.e. what do you get when you "cat /proc/acpi/thermal_zone/*/cooling_mode"? Mine is set to "passive", which I assume leaves active cooling to the BIOS. I assume that if it's on "active" and that Ubuntu can't control it very well, that may be the cause of problems.

---

### Post by trippinnik on 2007-06-12
Wow 40 C?  That's definetly not too hot.  I am pretty certain it is running at a similar temp in Windows.  As to is slowing down, maybe you have a trip point set too low and the CPU is being underclocked.  I doubt this, it seems that Ubuntu already has sensible settings for this on CPUs.  Some other reasons for slowdowns are background tasks, memory holes, or something related to the GPU.  Are you using the flgrx? Have you turned on power management for the GPU in those drivers?  Do you have Beagle running? Have you tried playing games with beryl turned off? Do you have Tracker installed?

---

### Post by Jaxilian on 2007-06-13
> **RobMBaker said:**
> OK, I just did a little test-run, to see if it is a generic Ubuntu fault.

I just put a full Ubuntu installation .iso into a maximum-compression 7z archive; which uses full cpu for about half an hour on my machine.
I've been watching Thermal 1 temperature, with "watch acpi -V", and it's gone from 52C (idle) up to fluttering between 59/60C every 20secs or so. My cpu fan isn't even going crazy; it's *just* audible to me. Then when the cpu usage drops back to 1 or 2%; my temp drops off to 54C within a few seconds (maybe 7 or 8).

So, my machine works fine. The (possibly) relevant settings I'm using are:
1) My BIOS is set to use a "Performance" cooling policy, rather than "Silent"
2) cat /proc/acpi/thermal_zone/*/trip_points returns the following:
[INDENT]critical (S5):           110 C
passive:                 125 C: tc1=2 tc2=3 tsp=40 devices=0xc1a34874 
[/INDENT]

As you can see, it appears mine is never going to use passive cooling; not with a cut-in temp that's higher than critical!
This makes me think that maybe the problem is down to bad Ubuntu drivers for your specific cooling hardware or something i.e. Ubuntu can't turn the fan on when it needs to?

One other question: flodis, are you using active or passive cooling? i.e. what do you get when you "cat /proc/acpi/thermal_zone/*/cooling_mode"? Mine is set to "passive", which I assume leaves active cooling to the BIOS. I assume that if it's on "active" and that Ubuntu can't control it very well, that may be the cause of problems.

I'll check and get back here with info.
Anyone know a good program on Windows that displays temp? I thought I run that 1st and then reinstall with Ubuntu. My Compaq one I have still ubuntu on so I can give ya that info later tonight.

---

### Post by trippinnik on 2007-06-13
a google search netted me this: [http://www.pcworld.com/downloads/file/fid,7309-order,1-page,1-c,systemresourcestuneup/description.html](http://www.pcworld.com/downloads/file/fid,7309-order,1-page,1-c,systemresourcestuneup/description.html)
you could give that a try or search around a bit.

---

### Post by daradib on 2007-06-13
Same problem here with a desktop. I have ATI Radeon X800 (using fglrx driver, since I get 1 fps 3D with open source driver) and a dual core AMD Athlon64 X2. My processor gets really hot whenever I do anything related to video rendering (such as any OpenGL game, even the simplest ones with bad graphics, Google Earth, or video transcoding). This is weird, since my processor didn't get this hot in Windows for more complicated 3D games. Just want to see who much work my processor is doing vs. my video card.

---

### Post by kushelmex on 2007-06-13
my Vaio just gets hotter when im using virtual box i guess thats normal , with normal use the temperature is nice

---

### Post by trippinnik on 2007-06-14
Is everyone here using the Radeon Proprietary driver? fglrx
[http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features](http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features)
There's a good bit on the Thinkwiki (really for thinkpads but good support about radeon cards) about powersaving and clock rate adjustment for the GPU.

---

### Post by Error1312 on 2007-06-14
I also have problems with heat when playing games (through wine, I might add). I'm using the latest nvidia drivers though, no fglrx. There are no problems when playing games in Windows. 

With normal use, the temperature stays stable at about 61°C, which is perfectly fine. However, when running Guild Wars the heat almost instantly rises to more than 70°. 

I'm not sure but I have the idea that the fans refuse to start. Is there any way to manually force the fans to run at 100%?

---

### Post by stchman on 2007-06-14
What CPU do you have?  Vista or XP is probably better setup for CPU throttling with your CPU.  I would not think that the video card would have much to do with it.  Maybe Vista or XP turn the fan on more.

---

### Post by Error1312 on 2007-06-14
These are the specifications: [http://nl.asus.com/products.aspx?l1=5&l2=23&l3=522&l4=17&model=1036&modelmenu=2]("http://nl.asus.com/products.aspx?l1=5&l2=23&l3=522&l4=17&model=1036&modelmenu=2")

---

### Post by Jaxilian on 2007-06-15
Still haven't tested the heat, but I will tonight.

Here is my computer:[ click here]("http://www.tweak.dk/tests2.php?id=573") (not english, but maybe you'll see the specs anyway)

---

### Post by Jaxilian on 2007-06-16
> **RobMBaker said:**
> OK, I just did a little test-run, to see if it is a generic Ubuntu fault.

I just put a full Ubuntu installation .iso into a maximum-compression 7z archive; which uses full cpu for about half an hour on my machine.
I've been watching Thermal 1 temperature, with "watch acpi -V", and it's gone from 52C (idle) up to fluttering between 59/60C every 20secs or so. My cpu fan isn't even going crazy; it's *just* audible to me. Then when the cpu usage drops back to 1 or 2%; my temp drops off to 54C within a few seconds (maybe 7 or 8).

So, my machine works fine. The (possibly) relevant settings I'm using are:
1) My BIOS is set to use a "Performance" cooling policy, rather than "Silent"
2) cat /proc/acpi/thermal_zone/*/trip_points returns the following:
[INDENT]critical (S5):           110 C
passive:                 125 C: tc1=2 tc2=3 tsp=40 devices=0xc1a34874 
[/INDENT]

As you can see, it appears mine is never going to use passive cooling; not with a cut-in temp that's higher than critical!
This makes me think that maybe the problem is down to bad Ubuntu drivers for your specific cooling hardware or something i.e. Ubuntu can't turn the fan on when it needs to?

One other question: flodis, are you using active or passive cooling? i.e. what do you get when you "cat /proc/acpi/thermal_zone/*/cooling_mode"? Mine is set to "passive", which I assume leaves active cooling to the BIOS. I assume that if it's on "active" and that Ubuntu can't control it very well, that may be the cause of problems.

When I try:

cat /proc/acpi/thermal_zone/*/cooling_mode


I get:
cat: /proc/acpi/thermal_zone/*/cooling_mode: No such file or directory

and when I try:
~$ acpi -t
     Battery 1: charged, 100%
No support for device type: thermal

The fans a blowing on maximum speed and still comp gets really hot after a while

---

### Post by themis on 2007-06-16
It may be /proc/acpi/thermal_zone/THRM/cooling_mode

---

### Post by RobMBaker on 2007-06-16
Thanks themis, but it should work with the * there, in case it's not "THRM" :)

And flodis, to be honest; I don't know what's going on if you get those results, sorry :confused:
But if your fans are running at full speed, then it shouldn't overheat ever.

Do you get anything meaningful from "cat /proc/acpi/thermal_zone/*/trip_points"? (I doubt it, if cooling_mode isn't there)
What do you get from "cat /proc/acpi/processor/*/throttling" and "cat /proc/acpi/processor/*/info"? They (if they're there) should tell you what power management is being used for your processor.

---

### Post by Jaxilian on 2007-06-16
> **RobMBaker said:**
> Thanks themis, but it should work with the * there, in case it's not "THRM" :)

And flodis, to be honest; I don't know what's going on if you get those results, sorry :confused:
But if your fans are running at full speed, then it shouldn't overheat ever.

Do you get anything meaningful from "cat /proc/acpi/thermal_zone/*/trip_points"? (I doubt it, if cooling_mode isn't there)
What do you get from "cat /proc/acpi/processor/*/throttling" and "cat /proc/acpi/processor/*/info"? They (if they're there) should tell you what power management is being used for your processor.

**~$ cat /proc/acpi/processor/*/throttling**
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%

**~$ cat /proc/acpi/processor/*/info**
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes

---

### Post by RobMBaker on 2007-06-16
Hmm, they're the same as mine - so I don't know why you get nothing for the ...cooling_mode and ...trip_points files.
Hopefully someone who understands how the acpi system works a bit more thoroughly will see this thread ... :)

---

### Post by Jaxilian on 2007-06-16
> **RobMBaker said:**
> Hmm, they're the same as mine - so I don't know why you get nothing for the ...cooling_mode and ...trip_points files.
Hopefully someone who understands how the acpi system works a bit more thoroughly will see this thread ... :)

I hope so too

---

### Post by Jaxilian on 2007-06-25
bump

---

### Post by Jaxilian on 2007-07-02
bump

---

