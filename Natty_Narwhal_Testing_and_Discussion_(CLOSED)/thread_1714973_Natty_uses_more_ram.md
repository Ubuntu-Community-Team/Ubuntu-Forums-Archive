---
title: "Natty uses more ram?"
date: 2011-03-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by macstevejb on 2011-03-26
So I have just installed Ubuntu 11.04 and have unity running, but I am noticing that my Ram usage has increased by some 500mb compared to 10.10.

Had thought this might be down to Unity but it's the same using standard Gnome desktop and I also tried Xubuntu 11.04 with the same increase in RAM usage.

Can it be that Natty, in all it's manifestations, is such a memory hog?

Thoughts appreciated?

regards :D

---

### Post by rapiertg on 2011-03-26
None of this symptoms here. Check system monitor if there are any process using unnaturally huge ammount of ram.

Its still alpha, maybe some memory leaks.

regards.

---

### Post by cecilpierce on 2011-03-26
> **macstevejb said:**
> So I have just installed Ubuntu 11.04 and have unity running, but I am noticing that my Ram usage has increased by some 500mb compared to 10.10.

Had thought this might be down to Unity but it's the same using standard Gnome desktop and I also tried Xubuntu 11.04 with the same increase in RAM usage.

Can it be that Natty, in all it's manifestations, is such a memory hog?

Thoughts appreciated?

regards :D

Same here mine is using 1.27 gigs and I noticed something called "beam" thats taking a lot of it, what is that ?

---

### Post by ssam on 2011-03-26
beam.smp is part of couchdb

---

### Post by clivejo on 2011-03-26
I have noticed that Nautilus seems to be hogging a lot of memory. On boot its using about 140MiB, this increases when I start opening devices or copying files.  Why does it need this amount of memory, is it caching something?

---

### Post by Atermoon on 2011-03-26
Only 390mb ram used here. Running Chrome with 7 tabs and 6 Nautilus windows with different folders from 3 different hard disks open.
If anything I would say it's using less ram than Maverick but to be honest I haven't checked my ram usage in months.

---

### Post by VinDSL on 2011-03-26
> **macstevejb said:**
> Thoughts appreciated?
It hasn't always been that way.

When I first ran A2, mem usage was quite normal.

Then, somewhere along the line, one of the nVidia updates almost doubled my mem usage.

Mem usage has remained high, through A3, but...

My understanding is, this situation is about to be corrected.

If you're running an nVidia card, hang in there!

If not, I don't know what to tell you...  ;)

---

### Post by macstevejb on 2011-03-26
ok that makes sense...I do have an nvidia card and have the proprietary drivers installed for 3D acceleration in order to use unity.

Hope something can be done about this before final release

---

### Post by cariboo on 2011-03-26
Have a look at bug #[lpbug]725434[/lpbug], there is a fix on the way.

---

### Post by VinDSL on 2011-03-26
> **cariboo907 said:**
> Have a look at bug #[lpbug]725434[/lpbug], there is a fix on the way.
Yes, interesting development(s) at hand!  I subscribed to that bug some time ago.

For the sake of discussion, when this mem problem first cropped up, Natty (essentially) became unusable for me.

That is, Natty booted ok, but...

And, as soon as my swap partition started to populate, BOOM!  Dead in the water!  End of session!

Since then (after about a week of updates) my swap partition started working like a champ!

Actually, my swap partition is now working better in Natty, than any other distro I've tried!

Here's a screenie (as I type)...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-26-mar-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-26-mar-2011.png")[/INDENT]


Look at that puppy!  LoL!

Almost a perfect 50/50 split -- and a textbook example of the importance of swaps...  ;)

---

### Post by VinDSL on 2011-04-09
Whoa, baby!  Yes!!!

I haven't seen "normal" RAM (and CPU) usage, like this, in weeks n' weeks!


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-9-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-9-apr-2011.png")[/INDENT]


Yeah Team...  :D

---

### Post by KegHead on 2011-04-09
Hi!

No problems here!

But..I'm running a low end Atom 330 desktop w/2gb ram.

KegHead

---

### Post by terry_gardener on 2011-04-09
if you are running a NVIDIA card then the fix was released last night.

new version of the libcairo2 package. 

mine has reduced by about half.

---

### Post by fjgaude on 2011-04-09
> **VinDSL said:**
> Whoa, baby!  Yes!!!

Yeah Team...  :D

Please, you can say what the name of the wiget is, the one that covers the right side of your screen shot?

Thanks!

---

### Post by terry_gardener on 2011-04-09
> **fjgaude said:**
> Please, you can say what the name of the wiget is, the one that covers the right side of your screen shot?

Thanks!

it is conky check the conky thread in community cafe

---

### Post by fjgaude on 2011-04-09
thanks!

---

### Post by mc4man on 2011-04-09
This bug, (which has been a continuing issue in natty in varying degrees), has been reopened due to again being a bit more significant and widespread.
[https://bugs.launchpad.net/bugs/720446](https://bugs.launchpad.net/bugs/720446)

---

### Post by Quackers on 2011-04-09
More ram in use here over the last 2 weeks or so. It has reduced a little in the last 2 days, but still slightly higher than it was. However as I'm now using gnome-shell, System Monitor does not show compiz as running. That would account for most of it, I suspect.

---

### Post by fabricator4 on 2011-04-09
> **mc4man said:**
> This bug, (which has been a continuing issue in natty in varying degrees), has been reopened due to again being a bit more significant and widespread.
[https://bugs.launchpad.net/bugs/720446](https://bugs.launchpad.net/bugs/720446)

Those running Unity 2D may also be affected:
[https://bugs.launchpad.net/bugs/723956](https://bugs.launchpad.net/bugs/723956)

I managed to get the RAM usage of module unity-2d-places up over half a GB in testing

Chris

---

### Post by mc4man on 2011-04-09
Ultimately, while this should be fixed, find it not to be a big deal really, certainly not on more modern hardware (2GB+) and now with nvidia managed better,  not that much even on an older p4 1GB (though bears watching after extended time online

Actually find I'm getting  more caching on 11.04 which is a good thing.

---

### Post by d3v1150m471c on 2011-04-09
welcome to a bloated UI. i switched to blackbox because gnome3 doesn't look much different. my 1.6ghz athlon uses less than 200mb's of ram on boot and idles at 2% cpu usage.

---

### Post by VinDSL on 2011-04-09
> **fjgaude said:**
> Please, you can say what the name of the wiget is, the one that covers the right side of your screen shot?

> **terry_gardener said:**
> it is conky check the conky thread in community cafe

> **mc4man said:**
> This bug, has been reopened due to again being a bit more significant and widespread.

[https://bugs.launchpad.net/bugs/720446](https://bugs.launchpad.net/bugs/720446)

> **mc4man said:**
> Ultimately, while this should be fixed, find it not to be a big deal really [...]
Nice **segue**!  :D

> 
To move smoothly and unhesitatingly from one state, condition, situation, or element to another: "Daylight segued into dusk." 

Yes, the "wiget" on the right side is a combination of Conky (a simple real-time analysis program), mixed with conkyForecast (a weather module), and Lua (to make it visually attractive).

This is always running on my desktop; constantly monitoring all local conditions - time, date, weather, CPU, RAM & HDD usage, network traffic, music player, et cetera.

I'm also running eMail & IM clients, a browser (or two). I'm shelled into,  various production web servers around the world, monitoring & controlling them in the background, blah, blah, blah.

Accordingly, I have a finger on the pulse of everything happening in my environment, e.g. my little bubble in life.

Basically, I'm sitting at the bridge of The Starship Enterprise!  LoL!

Moving along...

I HAVE noticed there is a significant mem leak in Compiz!

When your 'eyes' are opened, and you are gazing upon the situation, it becomes perfectly obvious, e.g. Compiz (or something under its control) is constantly chewing away at your memory.

In the Lua Community, we call this "Garbage Collection":  
[INDENT]*Extra credit reading*:  [http://lua-users.org/wiki/GarbageCollectionTutorial](http://lua-users.org/wiki/GarbageCollectionTutorial)
[/INDENT]
Yes, if you:

[LIST]
[*]Have a lot of RAM.
[*]Reboot frequently.
[*]Turn off your PC, when idle.
[*]Et cetera
[/LIST]

...mem leaks will be insignificant.

However, if you leave your machine running 24/7/365, mem leaks will be a deal breaker for you.

So, I cannot agree that this is "not to be a big deal really."

Thanks for listing that Bug, mc4man!  I'll add myself to it.

IMO, ALL mem leaks need to be squashed ASAP...  ;)

---

### Post by mc4man on 2011-04-09
> **d3v1150m471c said:**
> welcome to a bloated UI. i switched to blackbox because gnome3 doesn't look much different. my 1.6ghz athlon uses less than 200mb's of ram on boot and idles at 2% cpu usage.

Not at all - I boot to 230 MB w/ nvidia, 170 w/ nouveau 3d. (unity login).
 And anyway I have ram in the machines to be used, not to be sitting there doing nothing

---

