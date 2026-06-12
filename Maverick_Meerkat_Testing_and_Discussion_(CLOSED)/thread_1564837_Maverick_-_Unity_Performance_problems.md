---
title: "Maverick - Unity Performance problems"
date: 2010-08-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2010-08-31
I am trying to run Unity under Maverick on an Aspire One. Its runs Netbook Remix O.K although it only has 512Mb of memory and being one of the original Aspire Ones it has a slow SSD drive, it also runs OK with Gnome.
 
Trying to run Unity is a problem. It seems to spend most of its time writing to disk, performance is abysmal. It is completly unusable. Has anyone else seen this problem or is it an issue with my install?

---

### Post by MacUntu on 2010-08-31
[https://bugs.launchpad.net/unity/+bug/604777](https://bugs.launchpad.net/unity/+bug/604777)

I guess with just 512 MiB RAM your system must be toast after some minutes (at most).

---

### Post by Peter09 on 2010-08-31
Yep - poor little thing goes all red in the face and looks very puffed.

---

### Post by kerry_s on 2010-08-31
totally useless here to, just locks up like i'm moving to fast for it.

---

### Post by kerry_s on 2010-08-31
try this mournings updates, it's still slow, but its not locking up on me yet.

---

### Post by cimh on 2010-08-31
I have been following ubutnu, lubuntu and the unity version thru the alphas. One thing is clear to me is that lubuntu and ubuntu are pretty rock solid even in the alpha stage but unity has a long way to go and feels very much like an early stage alpha

This isnt surprising cos it looks like a new concept and presumably the developer have a lot more work to do on it.

I understood that the 10s fast boot target was to be transferred to the netbook unity version yet currently it is the slowest booting of the 3 versions on my netbook. it uses the most memory and is the most sluggish. 

Lubuntu
boot time:
button to desktop=20s
button to wifi up=25s
chrome launch = 1.6s
disk space= 2.2G
memory usage (running chrome and terminal and typing free -m)=285k

Ubuntu
button to desktop=23s
button to wifi up=25s
chrome launch = 1.9s
disk space= 3.8G
memory usage =334k


Unity netbook ed.
button to desktop=28s
button to wifi up=29s
chrome launch = 2.5s
disk space= 4.8G
memory usage =961k and 99k swap.

This is on a ssd based netbook (eee 901)

I'm sure these tests are very unscientific but they mirror my feeling that in terms of speed of response, the lxde version is fastest, gnome second (just) and unity quite a way behind in 3rd.

One of the problems with the unity desktop is that I dont find it easy to close programs so I wonder if some of the memory is blocked by programs staying open in the background. 

Great to see new ideas being tried tho. - 

cimh
901 (cpu: atom 1.6, 4 & 16GBssds, 1G RAM)

---

### Post by glaze on 2010-09-01
Unity is so slow on my Acer Aspire One A150 that it's completely useless. Mostly related to Intel 945GME. I've tested it on Ubuntu Netbook Alpha 3 and almost Beta (2010-09-01). I think I'm going to install Xubuntu instead. Also, the new launcher layout consumes more screen space than 10.04's. I don't want to see the quick launch icons all the time.

---

### Post by NightwishFan on 2010-09-01
Tried it a few weeks back on Maverick and it seems no different for me. I am running Intel Series 4 Mobile.

As for 512mb of RAM that should be sufficient. If free -m says otherwise I think I can round up a solution.

---

### Post by cariboo on 2010-09-01
I've been using Unity since it was released, I'm not seeing high ram usage either:

```
free -m
             total       used       free     shared    buffers     cached
Mem:           993        937         56          0          3        723
-/+ buffers/cache:        210        783
Swap:         1905        290       1615
```

It has been using some swap, but it doesn't seem to affect performance. As you can see with chromium-browser and a terminal open it's using 210MB ram.

---

### Post by rockin_goliath on 2010-09-07
I am also having performance issues on my Dell Mini 9. It is completely unusable to me, and I have to switch back to Lucid.

It could be because Unity seems to rely on compositing, but there is so way I can see to turn that off.

Also, does anyone know why when you click "system" in Unity, it does not show all of the preferences? Pretty hard to configure the mouse and Ubuntu One when the items are not there. However, they DO show up when I log in to a normal Gnome session.

---

### Post by cariboo on 2010-09-07
> **rockin_goliath said:**
> I am also having performance issues on my Dell Mini 9. It is completely unusable to me, and I have to switch back to Lucid.

It could be because Unity seems to rely on compositing, but there is so way I can see to turn that off.

You can't turn of composting, as Unity depends on mutter to draw the screen

> Also, does anyone know why when you click "system" in Unity, it does not show all of the preferences? Pretty hard to configure the mouse and Ubuntu One when the items are not there. However, they DO show up when I log in to a normal Gnome session.

Have you checked if there is a bug reported about the two problems you ran into?

---

### Post by kerry_s on 2010-09-20
> You can't turn of composting, as Unity depends on mutter to draw the screen

i know a little old but.

you can disable mutter composting, it still runs fine. you just add "mutter --replace --no-composite" to the startup.

use "ps -ef | grep mutter" to check if it worked.

---

### Post by MacUntu on 2010-09-21
That doesn't seem to turn off compositing.

---

### Post by droewors on 2010-09-21
My "upgrade" to Meerkat with unity has been very similar.
(I went with Meerkat as it supports scrolling on the magicmouse I have spare)

The unity interface is extremely slow ("Has it crashed...oh wait were back on...")
It similarly does not show up all options in an app search as mentioned above. And I furthermore have the issue of being unable to start an app when it is found in the list. A single or double click on the app icon just changes the window. Unfortunately I can just keep going on and on...point is, its beta.

I have removed unity but then I have no desktop...So I re-installed it. :)
How would I go about getting a lucid desktop to run instead of unity.
Once unity has itself sorted I may go back.

Thanks in advance for any help

---

### Post by cariboo on 2010-09-21
You can select gnome-desktop from the login screen. If you have auto login enabled you may have to remove /etc/gdm/custom.conf, to get to the login screen.

---

### Post by kerry_s on 2010-09-21
> **MacUntu said:**
> That doesn't seem to turn off compositing.

i get that feeling to.
perhaps it's not implemented yet? could be they just added it to "mutter --help" for future release?

anyways didn't stop the lock ups for me, so i tried the "export CLUTTER_VBLANK=none" even though i didn't have the white screen problem, that seems to help some, takes longer to lock up.

---

### Post by zekopeko on 2010-09-21
> **kerry_s said:**
> i get that feeling to.
perhaps it's not implemented yet? could be they just added it to "mutter --help" for future release?

anyways didn't stop the lock ups for me, so i tried the "export CLUTTER_VBLANK=none" even though i didn't have the white screen problem, that seems to help some, takes longer to lock up.

What do you mean by "lock up"?

---

### Post by kerry_s on 2010-09-21
> **zekopeko said:**
> What do you mean by "lock up"?

total freeze, have to hold the power button to turn off the computer. it's totally random & only happens when i move the mouse over the dock, for example: i can just use the win key(Super_L) & select the # to launch programs & it will never freeze, but if i move the mouse down the dock, there's a chance it will freeze, so i been moving in from the side instead of down the dock.
i have the intel 950 vid, which is bad with composting. the normal work around would be "export LIBGL_ALWAYS_INDIRECT=1" but that would make mutter not load, only the backgrounds there.

still looking around for a fix, but hopping it'll just work itself out. :)

---

### Post by Peter09 on 2010-09-26
Well my performance problems seem to be getting a bit better now, the interface is usable and, although it uses more memory than the remix version, my little Aspire One (512Mb) just manages it. 

Still not impressed with the look and feel though - hoping that that things do improve.

---

### Post by kerry_s on 2010-09-26
> Still not impressed with the look and feel though - hoping that that things do improve.

i don't know about that, there running out of time, release is like 3 weeks away. i very much doubt look & feel is there main problem, priority should be to make it work, still a lot of things that crash, for example just closing firefox will crash the ui, notifications are off screen when booting with non native resolution, etc...

---

### Post by cariboo on 2010-09-26
I saw on one one of the mailing list that the unity devs got a freeze exemption, so things could still change up until the release.

It looks like mutter is causing the extra ram usage, if you boot up gnome-desktop, ram usage drops.

---

### Post by MacUntu on 2010-09-26
Rome wasn't built in a day - give Unity some time to rock. ;)

---

### Post by droewors on 2010-09-27
> **cariboo907 said:**
> You can select gnome-desktop from the login screen. If you have auto login enabled you may have to remove /etc/gdm/custom.conf, to get to the login screen.

Thanks. I selected the gnome desktop from the login screen options and have regained control of my netbook. Unity in its current incarnation brings my 1.6 GHz 1GB RAM atom to its knees.

I hope the Unity team get it sorted, though performance issues aside I wonder if I am going to like it... let see. *fingers crossed*
-DW

---

### Post by cariboo on 2010-09-27
Are you sure you don't have other problems? I have basically the same setup. Atom 270 1Gb ram, Unity runs quite well for me, on two installs. one that has been upgraded since alpha 2, and an update from Lucid that I did this past Friday.

---

### Post by droewors on 2010-09-27
> **cariboo907 said:**
> Are you sure you don't have other problems? I have basically the same setup. Atom 270 1Gb ram, Unity runs quite well for me, on two installs. one that has been upgraded since alpha 2, and an update from Lucid that I did this past Friday.

Mine is a beta update from a stock standard Lucid that was running well. Like I said in an earlier post, the only reason I updated was for the "out of the box" scrolling for the apple magicmouse.

When it runs windows 7 starter it flies. Similarly under the gnome desktop. Could possibly be a graphics driver issue??
In any case its not the complete solution I would expect from Ubuntu. It should "just  work", and I don't believe I have some rare crazy netbook with weird hardware, but will be happy to be proven otherwise ;) (Asus P1005)

---

### Post by cariboo on 2010-09-27
> **droewors said:**
> Mine is a beta update from a stock standard Lucid that was running well. Like I said in an earlier post, the only reason I updated was for the "out of the box" scrolling for the apple magicmouse.

When it runs windows 7 starter it flies. Similarly under the gnome desktop. Could possibly be a graphics driver issue??
In any case its not the complete solution I would expect from Ubuntu. It should "just  work", and I don't believe I have some rare crazy netbook with weird hardware, but will be happy to be proven otherwise ;) (Asus P1005)

Except for the fact that this is still a beta, and beta versions don't always work the way you expect them to.

---

### Post by droewors on 2010-09-27
> **droewors said:**
> ...point is, its beta.


> **cariboo907 said:**
> Except for the fact that this is still a beta, and beta versions don't always work the way you expect them to.

Indeed. *fingers crossed* it works out fine.

---

