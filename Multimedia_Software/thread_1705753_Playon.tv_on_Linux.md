---
title: "Playon.tv on Linux"
date: 2011-03-12
forum: Multimedia Software
---

### Post by cnickl on 2011-03-12
Hi,

Has anyone ever tried to run Playon.tv under wine or VirtualBox?  I would like to get rid of my cable TV and I'm looking into alternatives.  I don't have a Windows machine anywhere and would have to run the Playon.tv server on my ubuntu machine.

Thanks, Chris

---

### Post by cnickl on 2011-03-13
well,  I guess I sort of solved the problem (or question for that matter)

Playon.tv will not run in Wine.  It needs the .NET framework and I'm not sure if thats something that can be done in Wine.

I installed it in my VirtualBox running WinXP.  Just had to make sure that the network is set to "Bridged Adapter" so that Playon.tv can actually set up the server.

---

### Post by zeddock on 2011-04-02
If I have Netflix account, does my virtualbox guest need to be running to use playon on another device to get the netflix content?

Seems like THAT content comes from what PlayOn calls Netflix channel.  So wouldn't they stream it directly to me?

I just don't want to have to leave a pc on at home while I am away, and I want netflix, etc on my xoom tablet while I travel.


zeddock

---

### Post by jocampo on 2011-07-20
@zeddock

Yes, the PC running PlayOn needs to be up and running while you watch NetFlix or any other channel. PlayOn is basically an streaming server so needs to be online all the time.

@cnickl
What specs do you have on your VM, like RAM and which CPU the main host is using.

I am running Win 7 as VM and having some issues with the "Bridge" networking. It can configure it as NAT, but the VM cannot see my network if I change to Bridge, which is a must for PlayOn.

---

### Post by sullivanjc on 2011-11-12
Does anyone know of an alternative *for* Linux that would let me stream the free Hulu site to a Roku or perhaps ABC and CBS site for full episodes?

I run Playon on my work laptop right now but would like to put something on my Linux machine at home instead

---

### Post by degarb on 2012-02-04
Hey, found this in google, thanks to index.  

Playon.tv basically gives you free tv, unlimited channels with plugins, hulu free.  Streams to wii.  

It even works fine on my xp 1.6 atom wireless.  I just do not want to burn up this machine.  I do have a spare 3.4 ghz p4 running Ubuntu and hardwired to router.

I installed playon.tv on virtualbox under Ubuntu.  I used the bridge network trick.  It works.  However, the video is choppy, which I wouldn't think it should be choppy, considering it is a faster machine and hardwired.

I increased ram on vm, video ram on vm, enabled 3d.  I don't know how to get this virtual machine to run this smoothly. If I cannot get fixed, I may or will remove linux off the machine and go xp--which is sad.  But it will save me about $40 a month, which adds up to like 0k over a 100 year lifetime with a 60 year working span, not considering interest.  (6k per decade x 10= 60k .  Then divide this by profitable working years which is roughly half a lifetime.)

---

### Post by jsavga on 2013-01-20
I know this is an old thread, but has anyone figured out a way to make this work without having to run Windows on a VM? 

Recently a workaround for Netflix was made, it would be great if such was made for playon.tv

---

### Post by degarb on 2013-01-22
> **jsavga said:**
> I know this is an old thread, but has anyone figured out a way to make this work without having to run Windows on a VM? 

Recently a workaround for Netflix was made, it would be great if such was made for playon.tv

Yes, I bought a quad core and running window.  Largely because on dual core, the vm takes such a hit, that playon didn't work, while it works fine on windows on dual core.   I wan't playon videos to load in as few seconds as possible.

Playon now offers a ton of first rate conten**_t NOT _**available on just Roku.

Playon requires IE 6+, flash for windows, and dotnet.  The scripts are lua based.  Obviously, playon doesn't wish to create, write an entire browser.  They probably lack the technical expertise to rewrite to work with chrome and python.    THe community here needs to work on voice recognition software (better than the android).

(I refuse anyhow to use an os without a start button, min/max windows buttons, visible scrollers and task bar. I find working on the androids excruciating at best.  Windows 8 looks like a Fisher Price OS to my eyes.  LXDE Ubuntu with tweaks is okay, but still forces upgrades that break older systems and lacks most programs I need for daily use.   )

---

### Post by jsavga on 2013-01-27
I was prefering a solution without having to run Windows (even in a VM). Something such as the netflix workaround that uses wine, etc.

---

### Post by siafulinux on 2013-04-12
I was able to get Playon.tv to run under Wine using Playonlinux. Problem is that while the program loads and stays in the "system tray" it won't open a connection. Nothing can connect to it. The "Current running status" stays between "Searching" and "Inititializing". 

To get it running I created a virtual drive under Playonlinux then installed:

[LIST]
[*]Microsoft .NET Framework (Popped up when installing Playon.tv).
[*]Internet Explorer 8
[*]Windows Media Player 10
[*]Core Fonts
[*]Microsoft Visual C++ 
[/LIST]

Anyone got any ideas why the app won't "run" under Playonlinux?

[ATTACH=CONFIG]241248[/ATTACH]

Thanks

---

### Post by degarb on 2013-04-12
> **siafulinux said:**
> I was able to get Playon.tv to run under Wine using Playonlinux. Problem is that while the program loads and stays in the "system tray" it won't open a connection. Nothing can connect to it. The "Current running status" stays between "Searching" and "Inititializing". 

To get it running I created a virtual drive under Playonlinux then installed:

[LIST]
[*]Microsoft .NET Framework (Popped up when installing Playon.tv).
[*]Internet Explorer 8
[*]Windows Media Player 10
[*]Core Fonts
[/LIST]

Anyone got any ideas why the app won't "run" under Playonlinux?

[ATTACH=CONFIG]241248[/ATTACH]

Thanks

Interesting hints.   So, you almost got it working, but not?
 
  Since, the virtual machine video transcoding performance hit is a huuuuge downside to linux, I haven't bothered installing Linux on the new machine.  I like the thousands of movies/shows that playon.tv allows that roku, does not.   I am guessing most ahk scripts (another missing essential of linux) might work in vm, as would dragon dictate.   My next windows-only task is to get some wireless security pin hole cameras that will stream out on web, privately, so I can check on my house from smart phone.

---

### Post by siafulinux on 2013-04-12
Okay I was able to get the server running. I redid the virtual drive (the previous one I was trying different things) and installed the above but a version of Mono was also required this time around. Everything works, my Roku can find the server, but... the videos will not play. I get an error now that says, "Video Playback Failure". It's instant, almost like it's not trying. So... one step closer but still not working.

Edit: Btw, on the previous install no hard drive space or memory was showing in the "System Check" section. This time it is showing hard drive space but displaying "Error" for memory. If I open the Task Manager it shows physical memory but says none is available. This might be the cause of the video playback issue.

As for performance, everything runs smoothly as far as menu access goes and there isn't any slow down that I've noticed in general usage of my Linux desktop.

[ATTACH=CONFIG]241256[/ATTACH]
[ATTACH=CONFIG]241255[/ATTACH]

Edit, Edit: I also changed the version of Wine I was using in this install. I went to 1.5.27 instead of 1.3.19.

---

### Post by siafulinux on 2013-04-12
Just a quick update. When I switched Wine to version 1.4 hard drive space was no longer available and the server stopped running. Perhaps we just have to wait for a new version of Wine to come out? 

[ATTACH=CONFIG]241258[/ATTACH]

---

