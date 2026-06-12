---
title: "Server not shutting down cleanly"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MAFoElffen on 2011-04-08
REF: Ubuntu Server Natty 11.04beta1 32bit. Clean install w/ LAMP, SSH, SAMBA< Print and CUPS  On a test box that previously had v10.10 w/ same packages with no problems.

System not shutting down cleanly-- If I try:
```
sudo shutdown 1 
```Sys shutsdown, then reboots.  If I try:
```
sudo shutdown 1 -H 
```shuts down the sys, but is locked-up with
```
System halted
``` as last line on screen, with the advanced [pwer button blocked-out/inop on the PC.

I don't see that "shutdown" has changed on the man page...

Anyone else having this? Or should I submitted this to launchpad?

---

### Post by BkkBonanza on 2011-04-08
I don't know about shutdown but I've always used **sudo poweroff** cleanly. According to it's man page it just calls shutdown "with appropriate parameters", whatever those might be.

---

### Post by MAFoElffen on 2011-04-09
> **BkkBonanza said:**
> I don't know about shutdown but I've always used **sudo poweroff** cleanly. According to it's man page it just calls shutdown "with appropriate parameters", whatever those might be.
???? 11.04beta1 reports no man page for poweroff AND no such command poweroff... am I missing something?

...also forgot to mention this-- If I use a reboot flag (-r) on "shutdown" it reboots fine into the console... If I use the normal:```
sudo shutdown 0
```it reboots into the rescue mode menu, where it just keeps looping into from there.

If I start a GUI desktop (xubuntu-desktop)```
sudo start gdm
```and chose "Shutdown" it down shutdown everything and powerdown... But that seems a round-about way to get a server sys down.

I'm thinking now that maybe this might be a launchpad issue, but not really sure on how to dump what or submit what file on something like this...  I mean it's on a shutdown...  Don't know of anyway to dump a file when the system is hsutdown or shutting down.  Doesn't the syslog rename and archive syslogs on boot?  I'm thinking that it might be to react... let it crash in the 3 ways mentioned above, then submit those 3 logs.  Anyone here have experience with that?

EDIT-- Submitted as launchpad Bug #755771

---

### Post by MAFoElffen on 2011-04-10
Okay, so I'm thinking that versions previous to Server 11.04beta1 (in 10.10) that shutdown had the -P flag assummed(?), but now it has to be specified for it to take affect.
```

shutdown 1 -H ... halt
shutdown 1 -h ... system decides on halt or powerdown
shutdown 1 -P ... powers down

```I'm good with that. :popcorn:

---

### Post by cariboo on 2011-04-10
Just to add my 2 cents, I use:

```
sudo halt
```

to shut down my server, whenever I do hardware upgrades, otherwise it's always on. For when it needs to be rebooted because of a kernel update I use:

```
sudo reboot
```

I don't have a gui on my server, as it is headless, and I do everything remotely.

---

### Post by d3v1150m471c on 2011-04-10
natty is a beta. if you just installed it i strongly recommend reinstalling 10.04 or even maverick especially if you're running a server. You'll want your clients to come to a stable bug free environment and probably not a beta that is still working out its issues.

---

### Post by MAFoElffen on 2011-04-10
> **d3v1150m471c said:**
> natty is a beta. if you just installed it i strongly recommend reinstalling 10.04 or even maverick especially if you're running a server. You'll want your clients to come to a stable bug free environment and probably not a beta that is still working out its issues.
Thanks all!

I have 5 boxes here (servers and desktops) and extra parts to throw together together 4 more.  I have things set up in virtual for some things, but it "really" is not the same. All my boxes here at home are all "personal." (although one is an online resume type of project)  

I learn hands-on. I love to do testing, work out problems and do new things that haven't been done before.  There is always something new in technology to learn or has changed.  There is also usually more than one way to do the same thing and I welcome and am grateful to learning those "other ways."

As for "beta"... LOL, that's is the "point" really isn't it?  I have many other boxes here that are running what is "stable."  Those usually are sitting there getting used for my work, but are now somewhat boring... the "challenge and adventure" has worn thin on them.  "Change" is my hobby.

I'll say this here so I don't have to explain it again-- Why did I install all 3 standard GUI desktops on a beta server base?  Yes it isn't realistic and it chews up resources, but it's a test box and it could be done.  I wanted to explore the possibilities.  It is also setup for remote ssh and serial console... just because I wanted to test "more" parts of a system to see what still worked and what didn't... what changed from how it was... and what was new.

So I'm playing and having fun.  The Server Edition of Natty does need to be tested.  If not, it will not reach "stable."  There is enough here testing the Natty Desktop Editions.

---

### Post by cariboo on 2011-04-10
+1 for server testing, we rarely see any posts on it here

---

