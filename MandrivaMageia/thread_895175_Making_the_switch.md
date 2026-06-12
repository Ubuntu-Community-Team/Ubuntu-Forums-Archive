---
title: "Making the switch"
date: 2008-08-19
forum: Mandriva/Mageia
---

### Post by PegMonster on 2008-08-19
Hi

I installed Mandriva One yesterday to replace Kubuntu gutsy (tried Hardy, but went back to Gutsy after all the probs) and boy am I impressed.
I was going to install Debian, but I am a little on the novice side and lacking the time to configure everything to be how I want it.

Now, I must say that Mandriva, out of the box, is the sharpest looking distro I have ever tried. Everything looks smooth and integrates well. My only problem is now I have to throw the training wheels on again.

Shortly after installing, I did a quick search on how to update my system, which included the kernel and about 280mb of packages. All went to plan until I rebooted. No X? Luckily I got out of it by changing the xorg config video driver from nvidia to nv. Unfortunately I am stuck with this setup until I find a solution. Although this is not what I am asking about here.

What I am asking, after my little drama, is how hard would it be to make the switch to Mandriva? I don't know anything about rmp or it's tools, but I have come across people talking of dependency issues and "rpm hell". Obviously with the kernel upgrade I have to do some tweaking to get things back to normal, but I have never had to do this in *buntu, so I don't really know what I am in for.

And apart from that, what else can I expect Mandriva throw at me to make my life more difficult?

As I said before, I am impressed with Mandriva's look, but it also detected and configured my hardware (notebook) better than any other distro I have used. On those basis' alone I am keen to give Mandriva a bit of a go.

Thanks in advance for your input.

PegMonster

---

### Post by TeaAge on 2008-08-20
I think the switch isn't that difficult.
You only have to accpect, that some things works diffrent ;)

For example your nvidia problem.
With the updates a new kernel was installed but it looks like not the new nvidia kernel-modul (don't know why), that's a bit nasty, i think it would be better if Mandriva normally uses the dkms-nvidia modul, but that's not the point.

All Mandriva Tools also works in the prombt.
So you just have to type
```

drakx11

```
and easily reconfigure your graphic-card. After that everything works fine.

IMHO urpmi is one of the best rpm packagemanager. And never had problems with dependencies.

Rpmdrake, the GUI for urpmi, is also very nice if you really work with it.
But one issue could be, that one of the drop-down-menus is set to "Applications with GUI" and you are wondering why it's not finding the applications you want to.
Take a look to the manual
[http://club.mandriva.com/xwiki/documentation/2008-spring/Mastering-Manual-EN.html/Mastering-Manual.html/software-management.html](http://club.mandriva.com/xwiki/documentation/2008-spring/Mastering-Manual-EN.html/Mastering-Manual.html/software-management.html)

You would be impressed how powerful rpmdrake is.

And, take a look at the whole control center of Mandriva and make your self familiar with it. It's also very powerful and useful.
[http://club.mandriva.com/xwiki/documentation/2008-spring/Mastering-Manual-EN.html/Mastering-Manual.html/advanced.html](http://club.mandriva.com/xwiki/documentation/2008-spring/Mastering-Manual-EN.html/Mastering-Manual.html/advanced.html)

I think, that are the main differences. 

If you have problems, maybe take a look at the whole manual
[http://club.mandriva.com/xwiki/documentation/2008-spring/Mastering-Manual-EN.html/Mastering-Manual.html/index.html](http://club.mandriva.com/xwiki/documentation/2008-spring/Mastering-Manual-EN.html/Mastering-Manual.html/index.html)
or at the wiki [http://wiki.mandriva.com](http://wiki.mandriva.com) or pose your question here or at forum.mandriva.com.

Hope that will help you.

Regards,
TeaAge

---

### Post by AdamWill on 2008-08-20
It's strange that the NVIDIA driver stopped working for you on an official update - we have a system to handle this so it should work, and I haven't seen wide reports of this happening to others (we did have several issues with it in the previous release). Did you change kernel flavour after installing, or anything like that?

In general you'll find some differences between Ubuntu and Mandriva for sure, but it shouldn't be anything too huge for you to handle. The major thing to remember with Mandriva is that you should try and do everything the 'official' way first. :) Mostly when people get into trouble it's because they try and do something outside the official tools - using packages from random websites or trying to build from source instead of using the official repositories, for instance, or trying to do all sorts of manual stuff to set up a network connection that would work perfectly through the Mandriva network configuration tool.

Definitely have a look at the most essential pages on the Wiki, here's a few:

[http://wiki.mandriva.com/en/2008.1_Notes](http://wiki.mandriva.com/en/2008.1_Notes)
[http://wiki.mandriva.com/en/2008.1_Errata](http://wiki.mandriva.com/en/2008.1_Errata)
[http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software](http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software)
[http://wiki.mandriva.com/en/Installing_proprietary_video_card_drivers](http://wiki.mandriva.com/en/Installing_proprietary_video_card_drivers)

That should get you going for now.

---

### Post by PegMonster on 2008-08-20
Thanks to you both for your replies.

Those links are very handy.

As for my video card problem, I tried using the configuration tool but it wouldn't repair the damage.

Could that have been caused by having the backports repository enabled?

I ended up just reinstalling and doing a system upgrade but this time without the backports repository enabled and it now works fine. (?)

It looks as though Mandriva is a system that wants you to use the gui as much as possible. Does this limit my ability to learn? Normally it would be considered a good idea to know and control a system through the terminal.

A question about the control centre.
The 'official' way would be to set things up via the Mandriva control centre, but in instances where there are other tools on the system which do the same or similar job (time and date, for example) can I kill or damage my system by using those instead. Not that I plan to, just curious.

Thanks again.

PegMonster

---

### Post by AdamWill on 2008-08-20
Yep, having backports enabled might have caused it. If you want to update the driver from /backports you should follow this guide:

[http://wiki.mandriva.com/en/Updating_proprietary_drivers_from_backports](http://wiki.mandriva.com/en/Updating_proprietary_drivers_from_backports)

but in general don't update the driver unless you're actually having problems with it, it'll keep things simpler.

It's not exactly that MDV wants you to use the GUI as much as possible. We want you to always have the *ability* to use the GUI if you choose, and this is usually the most straightforward way to get things done. It's certainly fine to go in and hack about at the console if you like, you just have to understand that if you do that you might break stuff and it won't be our fault. =) But generally speaking, yeah, Mandriva is perfectly conduicive to you editing things directly, and as long as you do it properly it'll work fine.

You're not going to hurt anything by changing something fairly trivial like time and date with a third party tool, no. It's more things like hardware drivers you should really handle via the MDV tools.

---

### Post by PegMonster on 2008-08-21
> We want you to always have the *ability* to use the GUI if you choose

We?

Does that mean you are on the development team?




PegMonster


Edit:
Just noticed your sig.
And just read your announcement on DistroWatch for the 2009 beta2 release.
I suppose that explains it then :)

---

### Post by wxnker on 2008-08-21
> It looks as though Mandriva is a system that wants you to use the gui as much as possible. Does this limit my ability to learn? Normally it would be considered a good idea to know and control a system through the terminal.
This is one of the strong sides of Mandriva. There are easy to use GUI tools for most tasks you'll ever need. This gives you the option to choose between the GUI and the command line approach. In Mandriva the command line is more like an option. It's not something you're forced to use very often if you don't want to. But you can still choose to do everything from the command line if you want to, of course. :)

Seen from a CLI perspective the main difference will be the switch from APT-GET to URPMI (and DEB to RPM). No big deal really. Both work really well. Adam and Teaage both gave you some very good links for this, but here are a few of the URPMI alternatives to common APT-GET commands.

To become root "su", (sudo is not used by default in Mandriva like in Ubuntu)

**Update package list**
apt-get update => urpmi.update -a
**Upgrade packages**
apt-get upgrade => urpmi --auto-select -a
**Update package list + Upgrade packages**
urpmi --auto-update -a
**Install **
apt-get install package-name =>urpmi package-name
**Uninstall**
apt-get uninstall package-name => urpme packagename

It's been a while since I've used apt-get, so I hope the apt ones are correct.

Regards,
wxnker

---

### Post by AdamWill on 2008-08-21
Peg: yeah, for my sins, I am ;). Actually I initially came on board to do community relations (which is what I'm doing here), but I picked up packaging just to fix a couple of things last year, and I now seem to maintain several dozen packages...=)

---

### Post by PegMonster on 2008-08-21
> Peg: yeah, for my sins, I am ;)


:D


A little off topic, but I have had a look at some screenies of the upcoming 2009 and I think that you guys have made KDE4 look great. I'm tempted to try the beta but I should probably wait for the final. I don't want to be scared off by the bugs, and I am a little too novice to do bug reporting.


PegMonster

---

### Post by wxnker on 2008-08-22
2009 final will be out early October I think, so it's not so far away. :)

When new to Mandriva I would recommend using the stable version (2008 spring) for now. You could try the beta on a spare partition or from a live CD though. It's pretty sweet.

---

### Post by asha00asha on 2008-08-22
I really appreciate him. He did a good job. Those links are also useful to me. I want to know more about it render more information.
-------------------------
Asha pabet

[Colorado Drug Addiction](http://www.drugaddiction.net/colorado)

---

### Post by AdamWill on 2008-08-22
Heh, looks like Ubuntuforums gets these kind of "please-click-the-sig-link" spams too...I hate them.

---

