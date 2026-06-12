---
title: "Mythbuntu beta: That was disappointing."
date: 2009-10-15
forum: Mythbuntu
---

### Post by GuiGuy on 2009-10-15
No doubt about Linux. It's a wonderful way to spend a few hours to get nowhere ;)

[LIST]
[*]Attempted clean install of beta 9.10 (mythbuntu)
[*]installer hangs at 80% (Scanning Mirrors)
[*]Try again, this time with network disabled
[*]Install finishes
[*] SHut down, plug network in
[*]Reboot. Backend tries to start:
[/LIST]
> 
This application is not compatible with the installed mythtv libraries. Please recompile after a make distclean


Which application?? The backend? And who or what is distclean. In any case, I can't compile anything. Bitter experience has shown that whenever I try to 'make' anything on a linux box it ends in tears. 

In the meantime, a little box at the top of the screen is telling me there are several hundred files to be updated, all for the measly price of another 350M data transfer. I figure, why not? and do it. 

As I am watching the activity list I see that there are a bunch of 404s (Failed/ file not found). 

It finishes and then tells me that a number of files couldn't be downloaded because they couldn't be found. Brilliant!!

Among the 404 files are, of course, the critical myth backend files :confused:

I try another mirror, but it makes matters worse. 

Now, who's going to tell me to get the daily build? After all, it's only another 600M? That be ok if I wasn't in Australia where data in regional areas cost an arm and a leg. 

I'll count my blessings. At least I didn't foolishly attempt an upgrade of an existing 9.04 front end. (My backend is on mythdora :biggrin:)

Anyway, I'll look again a month or so after the stable version is released. Time for breakfast :P

Good luck, and yes, I know it's a beta. :)

---

### Post by rosswj on 2009-10-16
[LIST]
[*]> installer hangs at 80% (Scanning Mirrors)
[/LIST]
If it's any consolation, I'm having the exact same issue. Interestingly I'm also in Australia, so perhaps that may the cause?

---

### Post by the Goat on 2009-10-16
> **GuiGuy said:**
> No doubt about Linux. It's a wonderful way to spend a few hours to get nowhere ;)
. . .
and yes, I know it's a beta. :)

You are complaining about beta software not being 100% finished.  Yea you totally convinced me, Linux sucks!

Why don't you try installing the stable version and get back to us?

---

### Post by GuiGuy on 2009-10-16
> **the Goat said:**
> You are complaining about beta software not being 100% finished.  Yea you totally convinced me, Linux sucks!

Why don't you try installing the stable version and get back to us?

Two things; 

1) it was sort of tongue in cheek.
2) If you'd read my post it should have become obvious I did a clean install. Didn't it imply that I didn't upgrade anything? Given the cost of hard disks these days, waddaya reckon?

Oh, and 3), I forgot that fanboys don't have a sense of humour. Clearly my fault so my apologies to the fan boys out there if they got overexcited about what they thought was another opportunity to flame. 


At least my Australian compatriot got it. 

Cheers.

---

### Post by GuiGuy on 2009-10-16
> **rosswj said:**
> [LIST]
[*]
[/LIST]
If it's any consolation, I'm having the exact same issue. Interestingly I'm also in Australia, so perhaps that may the cause?

I read in [whirlpool]("http://www,whirlpool.net.au") that there were some major outages in Melbourne and elsewhere yesterday. Our ISP was offline for about an hour around noon. Maybe that was the reason. 

I got the daily build over night (off peak) and will try again later today.

---

### Post by GuiGuy on 2009-10-16
> **rosswj said:**
> [LIST]
[*]
[/LIST]
If it's any consolation, I'm having the exact same issue. Interestingly I'm also in Australia, so perhaps that may the cause?

I tried again this morning with the overnight build. No problems. Scanning of mirrors went OK. 

Only downside there is no remote support in this build. When it comes to choosing your remote, everything is greyed out.

---

### Post by SiHa on 2009-10-17
> Only downside there is no remote support in this build. When it comes to choosing your remote, everything is greyed out.


Have you tried```
sudo dpkg-reconfigure lirc
```?

I use a homebrew serial receiver, and since 8.04 at least, the Mythbuntu install doesn't list it as an available option, so have to do this after the install.

---

### Post by superm1 on 2009-10-17
> **GuiGuy said:**
> I tried again this morning with the overnight build. No problems. Scanning of mirrors went OK. 

Only downside there is no remote support in this build. When it comes to choosing your remote, everything is greyed out.
There was a bug with the updates one of those days.  Just run Mythbuntu Control Centre post-install and everything should be fine.

---

### Post by GuiGuy on 2009-10-17
> **superm1 said:**
> There was a bug with the updates one of those days.  Just run Mythbuntu Control Centre post-install and everything should be fine.

yes, thanks. That worked fine after an "update" 

Cheers

---

### Post by GuiGuy on 2009-10-17
> **SiHa said:**
> Have you tried```
sudo dpkg-reconfigure lirc
```?

I use a homebrew serial receiver, and since 8.04 at least, the Mythbuntu install doesn't list it as an available option, so have to do this after the install.

Thanks for the reply. Didn't need to do that. I was able to resolve the issue from the control panel after a apt-get update. 

Cheers

---

