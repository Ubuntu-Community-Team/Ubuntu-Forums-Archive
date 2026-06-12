---
title: "Opera"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by Redsandro on 2009-10-08
I love Opera. I use it on all my Windows- and Ubuntu machines.
But on this specific Xubuntu  (9.04) machine, it freezes annoyingly often. On average, it freezes every 20 seconds for 5 seconds. During this, the system monitor shows a constant CPU usage of 100%, while normally this averages between 10 - 40 %.

It happens a lot 'onAction' on pages with javascript, but also randomly like here halfway typing this message a few times or when I start scrolling a new webpage for the first time. This is very annoying and even though this is my slowest computer, it should have no problem because Opera can pretty much run on a dorito.

I run Opera:```
Version		9.63
Build		2474
Platform	Linux
System		i686, 2.6.28-15-generic
Qt library	3.3.8b
```But I am positive previous versions did the same.

I run Xubuntu```
Release		9.04 (jaunty)
Kernel		Linux 2.6.28-15-generic
GNOME		2.26.1 (Huh? This is the system monitor from XFCE4 speaking)

```

Hardware:```
Memory:		512 MB
Processor:	AMD Athlon(tm) XP 2400+
```

---

### Post by Claus7 on 2009-10-08
Hello,

does your firefox browser works ok? What versions of ubu do you use in your other machines?

edit: take a look here, it might help you:
[http://ubuntuforums.org/showthread.php?t=1137127](http://ubuntuforums.org/showthread.php?t=1137127)

Regards!

---

### Post by Redsandro on 2009-10-08
I never use firefox, so a quick test for the occasion shows that the CPU graph in my panel does the same for firefox. It goes to 100% repeatedly. The system monitor shows that firefox exceeds 70% but combined with the other apps this makes 100%.

The BIG difference is, firefox doesn't freeze here. I can continue scrolling and typing during the cpu peak.

For my other machines I use Ubuntu 9.04, Ubuntu 8.04 and Windows 7. Another difference is that those are all Intel machines. This one is AMD.

---

### Post by Claus7 on 2009-10-08
Hello,

I do not really remember back in the days of jaunty, how much cpu I was using. I solved the issue by ipv6 and dns tweaking. 

Usually, someone uses xubuntu with an old machine, because the resources are scarce and very limited. Could we know if the specs of your pc is too low in order to handle firefox and the like. What else do you use which takes 30% of your cpu?

You might choose to run a lighter browser for this machine as well.

Regards!

---

### Post by Redsandro on 2009-10-08
It was all those other processes combined, not really a single big identifyable process or program. I am not at that computer anymore, but if you give me a command I can use to print the usage of everything in the console, I will quote it next time I use the computer. Can *ps* print a single snapshot?

I think that computer is strong enough. I used Opera on Windows XP on that same machine without problems. Except that it was version 9.21 or 9.5 at that moment. [SIZE="1"](The computer was running XP when it was someone else's, I had a user account. But when they gave me the computer I put Xubuntu on it. Now it's a desktop machine and media center. It plays any movie, series, videostream, emulator or Unreal Tournament 1999 type game perfectly. And I think those all are more system demanding than using Opera.)[/SIZE] I know the way *buntu is built, stuff is bound to be a little bit slower than XP, but I don't believe it's that big of a difference at all.

---

### Post by Claus7 on 2009-10-08
Hello,

so it seems that it is something else, if you are able to do so many things with that pc. Also I have to inform you that with xubuntu on it, it is supposed to be quicker than with xp. Xubuntu uses far less resources than ubuntu and ubuntu uses much less than xp. So it is supposed to be quicker!

The command I would suggest you to try is:
```
ps ux
```
that way you will have a snapsot of what is running the moment you press that command. In case you think that is not enough you can try and check for yourself, pressing this command some times more.

In addition to the above command you can also hit top and see more or less the same things, yet with this command the output is refreshing until you cancel it with Ctrl+c.

Opera now is at its 10th version. So you could try also installing this one and see if it is better for you.

Regards!

---

### Post by Redsandro on 2009-10-08
You're right about Opera 10, I use it pretty much everywhere else but I thought maybe on that machine it would get worse.

When I'm back there with some time, first I'll try **Opera 10**. If the freezes remain, I'll post **ps ux** or some **top** screenshots to figure this out.



In the meantime I really want to reply on the speed thing, yet you could concider it **off topic:** [SIZE="1"](I mention it because some people find it annoying if it goes offtopic)[/SIZE]

My question is: Really?
Here's my reply in the [*_why do you prefer Ubuntu over Windows_*]("http://ubuntuforums.org/showthread.php?t=643102") topic:

> **Redsandro said:**
> 
[QUOTE=Stan_1936;7850823]- The system runs faster with Ubuntu than it does with Windows.
I hear that a lot, but is that actually true?

I use Linux for over a decade now and I'm an Ubuntu fan because it's so easy. I always have one Windows license on my main workstation and [x]Ubuntu on the rest (server, media center, desktop). I like free, reliable, customizable, stable (and did I say customizable?) software.

But I've never ever had an out of the box Ubuntu on a previous out of the box Windows machine that was equally fast or even faster. I think it's a myth.

I think it's because Ubuntu just has a lot of scripts that require real time interpretation. A lot of the applications also. They cannot be compiled or optimized, where in Windows pretty much everything is.

Funny detail: I play games through wine. I do think the games run a bit faster than on Windows![/QUOTE]

Customizability has it's price. For example, **Gnome** has big *Python* written functionality. Very tweakable but real time interpretation is real slow. Even if it uses less resources. The in house music player **Rhythmbox** is so slow. Big playlists make it a terrible player compared to Winamp or Foobar 2k. Same for XFCE4's **Listen**. Especially notable on slower computers [SIZE="1"](like the machine mentioned even though it's not a 'darn slow' one)[/SIZE]. No, foobar2000 on my P3 300 is faster than Listen on the AMD 2400+, and it has a ton of more functionality.

That's why I run foobar2000 and some more explicitly-notable-faster-in-windows-apps in *Buntu through wine. So there is no problem.

Don't get me wrong, I love linux anyhow, but it annoys me that everyone sais that Ubuntu is faster especially since I've seen the difference on 6 (unexaggerated number) different computers througout the years.

I think linux can be faster, if you use a customized optimized Gentoo on it. But Ubuntu? Not when I'm around..

---

### Post by Claus7 on 2009-10-08
Hello,

first of all since it is your thread I do not know why someone should complain about anything, yet I might be wrong.

What I mean is that ubu is faster just for one thing:
the minimum requirements it needs in order to run for basic things are less than those of xp. Simple as that...

I think that using more than that you will need many more resources. E.g. if I use cairo with opengl my system is getting very slow. Which is normal I think...

Anyway, check this out (opera 10). I'm using it in a machine with 8.04 and it works pretty nicely.

Regards!

---

### Post by Redsandro on 2009-10-08
Thanks, yeah I will check it out and I hope that Opera 10 solves it! I will get back to you.

> **Claus7 said:**
> the minimum requirements it needs in order to run for basic things are less than those of xp.
Oh that is definitely true. But that's not necessarily as being faster overall.

[SIZE="1"]Offtopic:
In some forums I'm a member of, moderators chop away offtopic posts. Maybe I'm a bit paranoid :P[/SIZE]

---

### Post by Redsandro on 2009-10-09
Uhh.. I didn't expect this, one quick look around and it seems that Opera 10 doesn't have this problem anymore, even though it's a bigger download.

That's pretty cool. I wish I'd tried that before bothering people on the forum. :P

Anyway, I attached two screens from opera9 hang times. Also around 70%. So fun detail: Opera9 and Firefox share the same processor peaking, with other processes totalling at 100%, but Opera freezes and Firefox does not.

Opera 10 so far does not do any processor peaking at all, but I might need to get back on that if I had the time to play around with Opera 10 some more on this machine.

---

### Post by Claus7 on 2009-10-09
Hello,

glad you solved your problem. You see from time to time a process to peak while is active. Some programs are buggy, some others are not so compatible with each other...

No bother at all. If you already knew the answer, you would not bother to ask in the first place. 

Happy browsing,
Regards!

---

