---
title: "Blur does not work on Kubuntu 11.04"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bigbrovar on 2011-04-04
I just installed the beta version of Kubuntu 11.04 which ships with kde 4.6.1, I noticed that the blur effect which works fine with Kubuntu 10.10 no longer works. When I checked system settings I can see that blur is enabled but the actual effect does not work (like non of the semi transparent goodies  ) and disabling the effect shows no difference what so ever.

here are some information about my hardware
My laptop is running the Intel Arrandale graphic chip. 
On Kubuntu 10.10 I am using the Intel X driver version 2.12
On Kubuntu 11.04 beta I am using Intel X driver version 2.14

The kernel version on 10.10 is 2.6.35 while 11.04 is 2.6.38.

Can anyone confirm to me if the intel arrandale driver has some functionality blacklisted in kde 4.6.1? I would really appreciate feed back on this so I know whether this is an isolated issue, a kubuntu bug or an upstream bug.

---

### Post by geraniumk on 2011-04-06
I have the same experience here. My laptop uses an Intel GME965/GLE960 video controller and the only thing that still doesn't work is the blur effect.
I use Kubuntu Natty beta 1 as OS.
However, when I use the video drivers from the xorg.edgers I have a beautiful blur effect.

Perhaps you tried already too but to get these drivers add in Kpackagekit or Synaptic the repository 
[B][noparse]ppa:xorg-edgers/ppa[/noparse]

[/B]You can undo this by installing "ppa-purge". After you did that, in a terminal run:
**sudo ppa-purge xorg-edgers**

This will restore the official situation.

I hope they will make it in time!

---

### Post by geraniumk on 2011-04-06
Sorry the smily didn't belong there. The name of the repository should be

[B]ppa:xorg-edgers/ppa
[/B]

---

### Post by x-shaney-x on 2011-04-06
Hmm, I also have the same hardware and the same problem - blur enabled but not actually blurring.

I just tried adding the xorg-edgers ppa, updated and rebooted but still no blur here :(

---

### Post by geraniumk on 2011-04-07
I hope your verdict comes to soon: did you reboot? On my computer it works.

---

### Post by kio_http on 2011-04-07
Confirmed on Intel 945G graphics chipset.

---

### Post by x-shaney-x on 2011-04-07
> **kio_http said:**
> Confirmed on Intel 945G graphics chipset.
Are you confirming blur doesn't work or that adding the edgers repo DOES work?

@ geraniumk

I did reboot but not helped for me.

---

### Post by kio_http on 2011-04-07
> **x-shaney-x said:**
> Are you confirming blur doesn't work or that adding the edgers repo DOES work?

@ geraniumk

I did reboot but not helped for me.

Blur does not work even with edgers ppa driver.

Used to work fine on maverick. When changing plasma theme also sometime taskbar is not updated properly until after user logs out.

If this issue affects you add yourself to [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/753370").

---

### Post by kio_http on 2011-04-07
I have traced the problem to [this]("http://ubuntuforums.org/showthread.php?t=1723748").

---

### Post by geraniumk on 2011-04-15
I see there is progress being made. In this thread earlier there was a link to launchpad [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/753370](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/753370) . But now launchpad points to bugs.kde.org. [http://bugs.kde.org/show_bug.cgi?id=270942](http://bugs.kde.org/show_bug.cgi?id=270942)

I read there: 
If you want to have it fixed for natty, please contact Kubuntu devs asap. Please reference me and also this bugreport.

Does anyone of you know how to do that?

---

### Post by geraniumk on 2011-04-15
I took the liberty to email Johnathan Riddle. I wrote to him:
> Dear Johathan,
    
    I am no developer. But I stumbled onto a bug in Kubuntu Natty. You     can read about it here:[INDENT][https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/753370](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/753370)[/INDENT]Since yesterday Launchpad points to:[INDENT][http://bugs.kde.org/show_bug.cgi?id=270942](http://bugs.kde.org/show_bug.cgi?id=270942)[/INDENT]Someone named ***Martin Gräßlin*** writes     there:[INDENT]       If you want to have it fixed for natty, please contact Kubuntu devs asap. Please **reference me** and also this bugreport [http://bugs.kde.org/show_bug.cgi?id=270942](http://bugs.kde.org/show_bug.cgi?id=270942) .      [/INDENT]I am sorry to have taken your time as I understand that you must be     more than busy these days.  
    I wish you lots of success with Natty Narwhal!

---

### Post by geraniumk on 2011-04-18
Eureka! Fixed! Even without xorg.edgers. Only a few moments ago with the latest updates blur works.

As you can see on this second page of this thread I asked Johnathan Riddle if he could patch this. And he did.

I hope we will have a fantastic release.

---

### Post by x-shaney-x on 2011-04-18
Yes I noticed it was working earlier today but I am using edgers at the moment so wasn't sure if it was that or not.

I have noticed that the blur effect does seem much heavier than I last remembered and changing the strength doesn't seem to have much effect but hey, I'm probably just being picky :)

---

### Post by x-shaney-x on 2011-04-21
And todays update has taken blur away again :(

---

### Post by geraniumk on 2011-04-23
On my laptop the Kickoff menu (air-netbook plasma theme) suddenly isn't transparent anymore after the updates of two days ago.
Just when things were going so well.

---

