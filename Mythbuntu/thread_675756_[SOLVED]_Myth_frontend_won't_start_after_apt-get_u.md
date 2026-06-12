---
title: "[SOLVED] Myth frontend won't start after apt-get upgrade"
date: 2008-01-23
forum: Mythbuntu
---

### Post by martin.amberg on 2008-01-23
Hello everyone,

I've been running a myth FE/BE solution on a mythbuntu 7.10 for some time now and yesterday I made the mistake of fixing what isn't broken. Classic. But I'm still trying to learn linux so I'll be doing alot of mistakes. Bare with me.

What I did was a apt-get update, and then apt-get upgrade where it upgraded quite a lot of packages. So when restarting everything worked fine except for the frontend that crashes back to the login screen and then restarts, and crashes and so on.

When looking in the frontend log I see this:
Starting mythfrontend.real..
2008-01-23 07:30:57.707 Current Schema Version: 1160
2008-01-23 07:30:57.708 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-01-23 07:30:57.708 Enabled verbose msgs:  important general
2008-01-23 07:30:58.217 Connecting to lcd server: localhost:6545 (try 1 of 10)
2008-01-23 07:30:58.350 Total desktop dim: 1024x768, with 1 screen[s].
2008-01-23 07:30:58.351 Using all screens (currently 1)
2008-01-23 07:30:58.351 Total width = 1024, height = 768
2008-01-23 07:30:58.352 Switching to square mode (Titivillus)
mythfrontend.real: Fatal IO error: client killed

I have tried to remove ubuntu-mythtv-frontend package and reinstall it but with no luck. 

I have noticed that if I try to do a new upgrade it states that it will upgrade ubuntu-mythtv-frontend package and it needs to get 0B/181kb if I choose to install it it says that it is replacingubuntu-mythtv-frontend 0.20.2+fixes15422-0ubuntu0~mythbuntu1 with .../ubuntu-mythtv-frontend_0.20.2+fixes15422-0ubuntu0~mythbuntu1_all.deb
But if I do a apt-get upgrade again it still says that it needs to do the same upgrade again... and again... and again...

I have been playing around with different kernel versions lately but have switched back to the default 7.10 installation. Could I have messed something up when doing this?

Thanks for any help and advice.

---

### Post by Anubis on 2008-01-23
/usr/bin/mythfrontend.real: symbol lookup error: /usr/lib/libmyth-0.20.2.so.0: undefined symbol: stat64

Those updates broke my FE as well.

Launchpad bug 185108 in mythtv "/usr/bin/mythfrontend.real: symbol lookup error: /usr/lib/libmyth-0.20.2.so.0: undefined symbol: stat64" [Undecided,New] [https://launchpad.net/bugs/185108](https://launchpad.net/bugs/185108)

:confused:

---

### Post by martin.amberg on 2008-01-23
Ok, thanks for the info Anubis, I'm not sure this is the same problem since I don't see this error in my log? But I might just be missing something.

Anyways. I tried to change the repository from the uk mirror of 0.20.2 Fixes to the us version and did a new update/upgrade. And now it updated a lot of new packages and mythbuntu frontend to fixes15513. Still the same problem though :(

Any help or advice how to get my frontend running again is most appreciated.

---

### Post by Anubis on 2008-01-23
The recent updates fixed it so that now the frontend does not crash, but it starts in the photo browser, and I have to back out to the main menu, annoying.:confused:

Can't have removable media mounted or myth will go to photo browser mode.

Since when?

---

### Post by superm1 on 2008-01-23
> **martin.amberg said:**
> Hello everyone,

I've been running a myth FE/BE solution on a mythbuntu 7.10 for some time now and yesterday I made the mistake of fixing what isn't broken. Classic. But I'm still trying to learn linux so I'll be doing alot of mistakes. Bare with me.

What I did was a apt-get update, and then apt-get upgrade where it upgraded quite a lot of packages. So when restarting everything worked fine except for the frontend that crashes back to the login screen and then restarts, and crashes and so on.

When looking in the frontend log I see this:
Starting mythfrontend.real..
2008-01-23 07:30:57.707 Current Schema Version: 1160
2008-01-23 07:30:57.708 mythfrontend version: 0.20.20070821-1 [www.mythtv.org]("http://www.mythtv.org")
2008-01-23 07:30:57.708 Enabled verbose msgs:  important general
2008-01-23 07:30:58.217 Connecting to lcd server: localhost:6545 (try 1 of 10)
2008-01-23 07:30:58.350 Total desktop dim: 1024x768, with 1 screen[s].
2008-01-23 07:30:58.351 Using all screens (currently 1)
2008-01-23 07:30:58.351 Total width = 1024, height = 768
2008-01-23 07:30:58.352 Switching to square mode (Titivillus)
mythfrontend.real: Fatal IO error: client killed

I have tried to remove ubuntu-mythtv-frontend package and reinstall it but with no luck. 

I have noticed that if I try to do a new upgrade it states that it will upgrade ubuntu-mythtv-frontend package and it needs to get 0B/181kb if I choose to install it it says that it is replacingubuntu-mythtv-frontend 0.20.2+fixes15422-0ubuntu0~mythbuntu1 with .../ubuntu-mythtv-frontend_0.20.2+fixes15422-0ubuntu0~mythbuntu1_all.deb
But if I do a apt-get upgrade again it still says that it needs to do the same upgrade again... and again... and again...

I have been playing around with different kernel versions lately but have switched back to the default 7.10 installation. Could I have messed something up when doing this?

Thanks for any help and advice.
On a mythbuntu box, ubuntu-mythtv-frontend is not necessary.  Additionally, the issue with the constantly upgrading package is a problem with launchpad's PPA system.  It should be addressed in the next release of Launchpad (and in a future weekly build).

As for the client killing itself, try starting mythfrontend with more verbose options to catch the issue.  You can also install apport-gtk (and reboot) to build a crash report.

---

### Post by martin.amberg on 2008-01-23
Thanks alot for the info superm1!

Right now I would have loved to try the more verbose version of FE but in my eager to get my FE working again I have tried to remove all of the myth packages (yes db also) and will try to install a stable release from scratch. We'll see how this turns out, probably with a complete reinstallaton of the server :(

Well... hopefully I'll learn something...

---

### Post by Anubis on 2008-01-23
> **martin.amberg said:**
> Thanks alot for the info superm1!

Right now I would have loved to try the more verbose version of FE but in my eager to get my FE working again I have tried to remove all of the myth packages (yes db also) and will try to install a stable release from scratch. We'll see how this turns out, probably with a complete reinstallaton of the server :(

Well... hopefully I'll learn something...

Completely unnecessary.:confused:

You don't want to reinstall at minor bumps in the road.

---

### Post by nofear07 on 2008-01-26
I'm trying to get mythbuntu setup.  It installs fine, reboot, install nvidia driver, reboot, install updates, reboot and now no FE.  Is this the same issue?  If so what do I need to do to fix it.  I really want to get this fixed.

---

### Post by rooster13 on 2008-01-27
I'm struggling with the same Fatal IO Error situation.

The setup was working fine till now, today I somehow got stuck while watching tv. Picture and sounds were fine, but my remote stopped working. Then I just ctrl-alt-backspaced since even the keyboard wasn't working in mythtv, apparently it worked with X ;). After this, when ever trying to start myth tv (or the setup) I end up to graphical login screen (from which the mythtv user automatically logins and fails again in a loop). All logs even in '-v all' mode contain no other related info but the fatal io error-line

I admit doing some tuning in the db (changing visible flags in channels) while mythtv was running, but even reverting all changes didn't fix the problem, so I assume that's not the cause.

If anyone has any idea what might be resulting this FATAL IO error, all help appreciated. 

Cheers.

---

### Post by rgering on 2008-01-28
Greetings,

Let me start by saying that I am not an Ubuntu user (I happen to run Fedora myself), but I just spent the better part of an evening resolving what appears to be an identical problem, so I signed up for an account in the hope that my findings can help you out.

My guess is that your atp-get included an updated **xorg-x11-server-Xorg** package, as two security updates have been released for it over the last two weeks. My problems started after I ran "yum update" in Fedora, which basically does the same as an apt-get.

As with any good problem, that is only part of it :-)  The root cause is the fact that the **xorg-x11-server-Xorg** update replaced **libglx.so**, and this is something your NVIDIA driver didn't take kindly to (mine sure didn't!), as it expected to find its own copy which it put there when the driver was was installed.

Fortunately NVIDIA has released a driver update (169.09) which takes away that problem. From its release highlights:

[INDENT]*Fixed a bug that caused the X driver to crash if the X.Org GLX extension module was loaded intead of NVIDIAs.*[/INDENT]

Installing the newer NVIDIA driver should fix the problem for two reasons:

1. The core NVIDIA driver can deal with a replaced libglx.so module.

2. Installing the NVIDIA driver causes the replaced module to be re-replaced with an NVIDIA specific version.

Hope this helps!

- Richard.

---

### Post by rooster13 on 2008-01-28
Thanks a lot!!! The new drivers did the trick!

---

### Post by rgering on 2008-01-28
I'm glad to hear it. Thanks for the feedback!

Cheers,

- Richard.

---

### Post by josh2112 on 2008-02-18
Thanks Fedora buddy!  That solved it.

The instructions on [NVIDIA's webpage]("http://www.nvidia.com/object/linux_display_ia32_169.09.html") worked fine.  The installer gave me some error about "libglx.so not a symbolic link" or something but I ignored it and everything worked out.

---

