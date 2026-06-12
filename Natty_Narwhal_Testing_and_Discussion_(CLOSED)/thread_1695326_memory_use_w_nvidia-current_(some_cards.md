---
title: "memory use w/ nvidia-current (some cards?"
date: 2011-02-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-02-25
On a p4, AGP nvidia 7800 am seeing a significant _use_ of memory when using the latest nvidia-current, xserver ect. as compared to nouveau 3d and the previous working nvidia-current (way back when

Ex. after fresh boots
```
doug@doug-alienware:~$ free -m (nouveau
             total       used       free     shared    buffers     cached
Mem:          1000        326        674          0         47        131
-/+ buffers/cache:        147        852
Swap:            0          0          0

doug@doug-alienware:~$ free -m (nvidia-current
             total       used       free     shared    buffers     cached
Mem:          1000        738        262          0         47        167
-/+ buffers/cache:        523        476
Swap:            0          0          0

```

On a 8000 series laptop can't yet tell though probably a significant increase, can't revert to nouveau, (unity/compiz crash) for some reason so am doing a fresh install
(and on laptop doesn't really matter, have loads of ram.

---

### Post by mc4man on 2011-02-25
Confirmed here on a 2nd machine, fresh install updated. This machine has an ok amount of ram (3 gig) so the increase of 300%+ at boot doesn't particularly matter at all

And it may turn out not to matter on older, ram challenged machines like my p4 (1 gig), a few days of testing should show, w/ some of the current memory leaks  should become apparent if an issue w/  a day or so uptime

Is basically the same for Desktop and Classic logins, typical use @ boot on 3gig machine

```
A2 updated fully inc. X nouveau 3d
doug@doug-XPS-M1330:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3021        412       2608          0         42        165
-/+ buffers/cache:        205       2815
Swap:            0          0          0

A2 fully updated, mesa 3d removed, nvidia-current installed
doug@doug-XPS-M1330:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3021        852       2169          0         41        200
-/+ buffers/cache:        610       2411
Swap:            0          0          0

```

for those interested attached 2 logs showing the increases are somewhat across the board, took several reports, attached shows averages for all processes

---

### Post by VinDSL on 2011-02-26
In a word, "Yes!" 

Mem usage is quite high on my system rig (see my sig).

Allow me to put a face on it...  :)

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-26-feb-10-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-26-feb-10-2011(2).png")[/INDENT]


My memory meter is (basically) pegged -- and it stays that way (80-100%) the whole time I'm running Natty.

Heh!  I'm *hoping* this will be addressed, before the final is released.

My *fear* is, 'they' don't know about it...

---

### Post by mc4man on 2011-02-26
After a day and a half uptime on the p4 found it quite easy to basically max the memory out and bring performance to a crawl. 
Though with a little care i guess one could make due, have decided here to revert back to the inferior mesa 3d drivers.

On a 3 gig laptop the starting increase is not a factor, so as things stand now I'd say 2 gig and higher no big deal, 1 gig could be a sig. issue, less than a gig, forget about it.

There was something in the changelog referring to system memory that shouldn't be a factor here, but not sure.
Did file bug, no response as of yet
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434)

(very disappointed, do accept my p4 is nearing end of useful life but other than this setback was/is running quite well in natty, -actually better than maverick

---

### Post by VinDSL on 2011-02-26
> **mc4man said:**
> Did file bug, no response as of yet
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434)
~Cool

That should get their attention!

I subscribed.  We'll see where it goes...

---

### Post by VinDSL on 2011-02-26
BTW, as a basis of comparison...

Here's the same proggies, running on the same machine, under Ubu 10.10 (fully patched & modded / Liquorix kernel).


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-26-feb-2011(3)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-26-feb-2011(3).png")[/INDENT]


As you can see, there's a h-u-g-e difference in the amount of  resources used.  

Plus, this thing flies like the wind on Maverick!  ;)

---

### Post by ktp on 2011-02-26
I am seeing the same thing also.

<off-topic>
VinDSL, you have some nice wallpapers.  You should get them into ubuntu wallpaper collection/package. =)
</off-topic>

---

### Post by VinDSL on 2011-02-26
> **ktp said:**
> <off-topic>
VinDSL, you have some nice wallpapers.  You should get them into ubuntu wallpaper collection/package. =)
</off-topic>
Thanks, ktp!

I may do that...  ;)

---

### Post by VinDSL on 2011-02-26
> **mc4man said:**
> After a day and a half uptime on the p4 found it quite easy to basically max the memory out and bring performance to a crawl.[...]
Sounds like we're all in the same boat.

I take the increasing slowness, and declining performance, as long as I can.

When 11.04 finally becomes unresponsive, I shell out and reboot.

I can usually play this game for a half-day, before it gets on my nerves, then I switch back to 10.10 (this is a dual-boot box) for the remainder of the day.

BTW, where do you guys set your swappiness?

I set my swappiness to " 0 ".  Seems to work best on my rig.

When swappiness is set to a 'normal' value, the performance is even worse!

---

### Post by VinDSL on 2011-03-03
I don't know what they did -- which update cured the problem -- probably the xorg updates, but...

After doing the latest round of updates, mem is now under control, and Natty is usable (once again) for the first time, since my post above.

I've actually used Natty for an 1 hr. 35 min. without running out of memory.

Performance is good -- no locked screens -- no slowness!

Yeah Team!!!  :D

---

### Post by mc4man on 2011-03-04
> **VinDSL said:**
> I don't know what they did -- which update cured the problem -- probably the xorg updates, but...

After doing the latest round of updates, mem is now under control, and Natty is usable (once again) for the first time, since my post above.

I've actually used Natty for an 1 hr. 35 min. without running out of memory.

 
Actually nothing has changed in terms of mem in use at login, as mentioned it is workable with 1 GB and somewhat irrelevant with 2 GB+. The scenario of running the mem out or going significantly into swap was more of something that had to be forced than seen in general use. 
(though obviously the 'margin' is very low on 1 GB.

More likely you've 'cleaned' up some local issues.

Can say now it's not xserver, nvidia-current, or compiz at fault per se, though atm the actual cause is unknown.

---

### Post by VinDSL on 2011-03-04
> **mc4man said:**
> Can say now it's not xserver, nvidia-current, or compiz at fault per se, though atm the actual cause is unknown.
When I booted up tonight, I was back to the same-old, same-old.

This is even more of a mystery, now.

Thinking back to this morning, the only difference in my normal routine is, I logged in, and made a pot of coffee, before opening any proggies.

That is, 11.04 sat idle, at the desktop, for about 10 minutes, before I used it.

I know this is a stretch, but I'm grasping for an explanation as to why everything worked fine, this morning, for a couple of hours.

Hrm...

Back to the drawing board!  :D

---

### Post by mc4man on 2011-03-04
> Hrm...
You could keep an eye on the bug report, though don't hold breath

Atm you may wish to try a fresh A3 install, things should be manageable as long as you don't run a huge  bunch of  apps at once. (you still may use the swap slightly, if so and it causes unacceptable slowdowns then disable it. (comment out in fstab
Also disable any unneeded stuff from the startup applications

Or, for the moment, use nouveau (mesa 3d drivers

(i have lightly entertained upping the ram here, decided not to, what was once an excellent gaming machine is now just an old machine, though it stills runs in natty quite well

---

### Post by mc4man on 2011-03-04
getting a bit closer to tracking down, we'll see what develops...

---

### Post by VinDSL on 2011-03-04
> **mc4man said:**
> Atm you may wish to try a fresh A3 install [...]
Downloading, as we 'speak'... :D

---

### Post by mc4man on 2011-03-04
Found the 'problem' package, (libcairo2), while reverting does return use to normal it doesn't represent an  acceptable temp solution.
Hopefully it will be possible to resolve at some point.

---

### Post by ktp on 2011-03-04
nice detective work!!!  I am going to keep it installed now since I got lots of memory on this computer, but good to know.

---

### Post by VinDSL on 2011-03-06
Well...  This is an interesting development!  :D

I installed Ubu 11.04 A3 a few hours ago -- nVidia common, Adobe Flash, the whole enchilada, and...

The memory usage has not subsided, but...

Memory management is working like a swiss watch!

With A2, my 1GB RAM was almost always pegged, and as soon as swap was invoked, this machine became unresponsive -- along with my HDD activity light being lit up solid.  I had to shell out, and dance on the keyboard to shut it down.  For the most part, A2 has been unusable for the past week or two.

With A3, the RAM usage in various programs is the same, but when it goes to swap, everything operates normally.  If I wasn't staring at my Conky output, I wouldn't even know I was into swap.

Besides that, after a few hours of runtime, the physical RAM usage (-/+buffers/cache)  is around 35% (Hello!?!?!) swap is 52%, and this machine is performing like a champ.

LoL!  Will small wonders never cease?

```

vindsl@Zuul:~$ cat /proc/meminfo
MemTotal:        1025164 kB
MemFree:          410844 kB
Buffers:           15636 kB
Cached:           169676 kB
SwapCached:        64868 kB
Active:           198380 kB
Inactive:         358716 kB
Active(anon):     136416 kB
Inactive(anon):   238512 kB
Active(file):      61964 kB
Inactive(file):   120204 kB
Unevictable:          88 kB
Mlocked:               0 kB
HighTotal:        139208 kB
HighFree:            280 kB
LowTotal:         885956 kB
LowFree:          410564 kB
SwapTotal:       1050620 kB
SwapFree:         500220 kB
Dirty:               484 kB
Writeback:             0 kB
AnonPages:        311412 kB
Mapped:            62028 kB
Shmem:              3056 kB
Slab:              20792 kB
SReclaimable:       8320 kB
SUnreclaim:        12472 kB
KernelStack:        2640 kB
PageTables:         6420 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1563200 kB
Committed_AS:    2550512 kB
VmallocTotal:     122880 kB
VmallocUsed:       55004 kB
VmallocChunk:      53244 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       57336 kB
DirectMap4M:      851968 kB
vindsl@Zuul:~$ 

```

I'm afraid to turn this thing off... it's running so nicely!

---

### Post by mc4man on 2011-03-21
As a small update to - 
noting that this is pretty much irrelevant to 2Gb or greater machines and can be manageable on a 1GB machine (particularly if the remaining small mem leaks are closed), though certainly not ideal

The 'issue' is caused by libcairo2, which now includes gl support. This support is not currently needed, it's basically for wayland

The difference at login for fresh boot is quite a bit - as seen here (though on this machine doesn't matter, was just easier to produce a libcairo2 without gl

```
libcairo2 w/ gl
free -m
             total       used       free     shared    buffers     cached
Mem:          3021        828       2193          0         38        187
-/+ buffers/cache:        602       2419
Swap:          283          0        283

libcairo2 w/out gl
free -m
             total       used       free     shared    buffers     cached
Mem:          3021        472       2549          0         38        187
-/+ buffers/cache:        246       2775
Swap:          283          0        283


```

---

### Post by mc4man on 2011-03-25
I suspect that there will be a new libcairo upgrade  shortly that disables the gl backend  in cairo (unless it's somehow resolved otherwise on nvidia end or by dynamically loading
This seems like quickest solution for natty

Have been using for 4 days or so and returns mem use w/ nvidia drivers to normal so marking as solved

---

### Post by jennybrew on 2011-03-25
A very interesting post. Thanks.

As an aside its sometimes possible to be fooled by memory use.
Many applications or processes will grab all the memory they possibly can. No problem provided they give it back when required. One of the worst offenders in this respect seems to be be SqlServer and it has fooled us on numerous occasions. (It behaves perfectly when asked to give back its large helping of memory)

Thanks again ..worth knowing

---

### Post by mc4man on 2011-03-25
@ jennybrew
what I find to be a useful tool at times, particularly for looking at possible mem leaks (which this is not), is pidstat, part  of the sysstat package
(a lot of useful things in sysstat, the various man pages are nice because though show some examples, ect.

---

### Post by VinDSL on 2011-03-26
> **mc4man said:**
> I suspect that there will be a new libcairo upgrade  shortly [...]

Have been using for 4 days or so and returns mem use w/ nvidia drivers to normal so marking as solved
That's nice to know.  Thanks!

Actually, I haven't been worried about it too much.

I knew 'they' would fix it -- they always do, but...

The (physical) mem usage in this machine is always around 666MB, and the '666' is what's worrying me.  ;)

---

### Post by thiebaude on 2011-04-04
My mem use is still high. Is it safe to remove libcairo2?

---

### Post by mc4man on 2011-04-04
> My mem use is still high. Is it safe to remove libcairo2?
Absolutely not

This issue has solutions and can be fixed now if they choose to in a couple of ways. Atm I think it's not while some add. solutions are being looked at/attempted.
(there is a strong desire to keep a gl enabled cairo even though the benefit to a typical user is nil.

(you could rebuilt cairo for yourself without gl support but it's a significant build in terms of deps and time

---

### Post by VanR on 2011-04-04
Off topic I know, but someone please tell me how to get that cool sidebar with the CPU usage and weather and so forth on the right side of the desktop. I didn't know you could have that on Ubuntu.

---

### Post by Harry33 on 2011-04-04
> **thiebaude said:**
> My mem use is still high. Is it safe to remove libcairo2?

Well well.
Removing such an important and central part of the desktop would remove almost completely the Gnome Desktop and GTK+2 with applications depending on those, like browsers, Libreoffice ...
So no graphical user interface left, you could always use console in recovery mode. :)

---

### Post by VinDSL on 2011-04-09
Officially fixed!  ;)

Linkage:  [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434)

> This bug was fixed in the package cairo - 1.10.2-2ubuntu2

---------------
cairo (1.10.2-2ubuntu2) natty; urgency=low

  * Don't turn the gl backend on for natty since it creates issues for nvidia
    users and is only used for wayland (lp: #725434)
  * debian/control,
    debian/libcairo2.symbols,
    debian/rules:
    - updated for the non-gl build
  * debian/control: Breaks on wayland
 -- Sebastien Bacher <seb128@ubuntu.com> Fri, 08 Apr 2011 18:27:43 +0200

---

### Post by gnomeuser on 2011-04-09
> **VinDSL said:**
> Officially fixed!  ;)

Linkage:  [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434)

Not really fixed as much as worked around. We are going to have to revisit this one in Ocelot I suspect as we desperately need the foundations for Wayland to make its way to the distribution. We cannot let nvidia hold that up forever.

---

### Post by VinDSL on 2011-04-09
> **gnomeuser said:**
> Not really fixed as much as worked around. We are going to have to revisit this one in Ocelot I suspect as we desperately need the foundations for Wayland to make its way to the distribution. We cannot let nvidia hold that up forever.
Yes, absolutely!  And, a poor choice of words, on my part.

If they had released Natty without this workaround, it would have caused much wailing and gnashing of teeth.

It was the lesser evil...  ;)

---

### Post by mc4man on 2011-04-09
> choice of words ,,
I wouldn't call it a solution or workaround - more like it was made right for natty.
If a 'fix' that could have been carried forward had been worked out that would have been a positive, as far as natty the support wasn't needed in the first place

---

