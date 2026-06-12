---
title: "Has Kubuntu Resolved the Intel Graphics Issues?"
date: 2010-09-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2010-09-24
Hello everyone. I am probably going to test the release candidate for Maverick, but I am curious as to the current status of KDE in Kubuntu 10.10.

My laptop (Dell Latitude e6410) has an integrated Intel graphics card which has a problem with the lanczos and blur filters. This causes desktop effects to freeze, and in addition to that whenever desktop effects are enabled there is heavy artifacts on my screen and it's just a horrible experience. The KDE developers are currently blaming the video drivers.

I'm thinking that one of three things will fix this, otherwise any distribution using KDE 4.5 will probably have a lot of graphics issues (though most nvidia users seem to be fine). I am thinking that either including KDE 4.5.2 in Maverick's final release may fix it if the KDE developers make their code work around the problem (doubtful), or perhaps the Kubuntu developers may patch the code themselves to fix this. Either way, I am afraid that this bug may kill Kubuntu 10.10 for a lot of people if it's not fixed, and it's not even Kubuntu's fault!

Does anyone know the current status on if these issues may be fixed? I currently use Arch on my laptop but I'm considering trying out Kubuntu 10.10 to see how they deal with KDE 4.5's shortcomings. I am curious to hear if any of you using Intel graphics are having issues with KDE in Kubuntu.

Sources: 
[https://bugs.kde.org/show_bug.cgi?id=243181](https://bugs.kde.org/show_bug.cgi?id=243181) (KDE Bug Report)
[http://blog.martin-graesslin.com/blog/2010/09/driver-dilemma-in-kde-workspaces-4-5/](http://blog.martin-graesslin.com/blog/2010/09/driver-dilemma-in-kde-workspaces-4-5/) (KDE Developers Blog)

---

### Post by kansasnoob on 2010-09-24
Exactly what Intel GPU?

Please post the output of:

```
lspci | grep VGA
```

I'm battling some new Intel problems in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1579475](http://ubuntuforums.org/showthread.php?t=1579475)

But as I state there, "Most importantly I'm really outside my "comfort zone" here."

IOW I'm floundering about like a fish out of water :)

---

### Post by jlacroix on 2010-09-24
> **kansasnoob said:**
> Exactly what Intel GPU?

Please post the output of:

```
lspci | grep VGA
```

I'm battling some new Intel problems in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1579475](http://ubuntuforums.org/showthread.php?t=1579475)

But as I state there, "Most importantly I'm really outside my "comfort zone" here."

IOW I'm floundering about like a fish out of water :)
```
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile GEM 20100328 2010Q1
```

Is that what you were looking for?

---

### Post by kansasnoob on 2010-09-24
Well it's different than what I'm used to seeing:

> lance@lance-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)


I'm no xorg guru, I'm also just trying to muddle thru :)

---

### Post by Reiger on 2010-09-24
@above: No of course that OpenGL vendor string or whatever it is does not result from lspci|grep vga. I mean if it did this would be a serious flaw in grep, that line has no &#8220;VGA&#8221; in it at all! :P

---

### Post by kansasnoob on 2010-09-24
> **Reiger said:**
> @above: No of course that OpenGL vendor string or whatever it is does not result from lspci|grep vga. I mean if it did this would be a serious flaw in grep, that line has no “VGA” in it at all! :P

Why not just run:

```
lspci | grep VGA
```

And then post the full output?

---

### Post by jlacroix on 2010-09-24
I posted the wrong output. This is probably what you were looking for:

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

```

---

### Post by perspectoff on 2010-09-24
Not just Kubuntu. Happens for me in Ubuntu, too. 

Had to do the i915.modeset=0 workaround.

---

