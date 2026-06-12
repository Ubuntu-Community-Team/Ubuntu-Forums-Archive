---
title: "SVN and Myth specific fix ?"
date: 2008-07-08
forum: Mythbuntu
---

### Post by drifting on 2008-07-08
I am confused as hell when it comes to the fixes etc. And I tried to read what SVN was about, but left knowing less than I started.

I am using two DVB-S cards in the UK for FreeSat, and a single Nova-T 500 for Freeview. The listings on EIT from Freeview are perfect, but FreeSat only has Now & Next, which is all it seems Myth supports. After hunting I found mention of a fix? but how to install it eludes me. Do I just wait for a fix to come down via normal updating ? or is that months away ?

This is what I currently have.

paul@vs:~$ dpkg -s mythtv | grep Version
Version: 0.21.0+fixes16838-0ubuntu3.1

Another quick question if I may ? Can I install Mytbuntu over the top of my current working system ? Been using it on my Frontends with great success.

Regards Paul.

---

### Post by ian dobson on 2008-07-08
Hi,

You could go over to using weekly builds by adding

#Myth fixes
deb [http://weeklybuilds.mythbuntu.org/mythbuntu/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu/ubuntu) hardy multiverse universe restricted main

To your /etc/apt/sources.list file.

The a apt-get update, apt-get upgrade -V

the -V option means so the version numbers that are installed/will be installed.

Regards
Ian Dobson

---

### Post by drifting on 2008-07-09
Thanks for the reply, but my backend is not running mythbuntu, only my frontends, does that matter? Hence My question about installing Mythbuntu over the top.

Regards Paul.

---

### Post by Lindsay.Mathieson on 2008-07-09
> **drifting said:**
> Thanks for the reply, but my backend is not running mythbuntu, only my frontends, does that matter? Hence My question about installing Mythbuntu over the top.

Regards Paul.

Install mythbuntu over a existing backend not from the repository? I presume you compiled from source?

Not recommend at all.

---

### Post by drifting on 2008-07-09
No, I got my Mythtv from the repository, just that it was not Mythbuntu, so no control centre etc.

Regards Paul.

---

### Post by Lem on 2008-07-12
As an aside, how well is freesat working? Are you able to play the HD channels?

---

### Post by drifting on 2008-07-12
Yes and no, yes they play sort of with a pause even second, still have to work out if it's the frontends or backend, I would imagine that my frontends are just not man enough being just 486's with 512.
Wished I could get this listing business sorted, wonder when the guys from Mythbuntu will have time to update the weekly builds. Not that I am complaining wished I could work out how to do it myself.

Paul.

---

### Post by ian dobson on 2008-07-12
Hi,

Just give them afew days. I've heard that they'll be compiling a new weekly build within a week or so and that was 2-3 days ago.


Regards
Ian Dobson

---

### Post by laga on 2008-07-13
If it's not done by Tuesday, yell at me.

---

### Post by drifting on 2008-07-13
Would never do that ;-) far too polite, but it would be nice to be able to setup recording a little further than the next program.

Regards Paul.

---

### Post by drifting on 2008-07-16
> **laga said:**
> If it's not done by Tuesday, yell at me.

Consider yourself yelled at !

Regards Paul.

---

### Post by laga on 2008-07-16
Packages are upload and should appear soon.

---

### Post by theophile on 2008-07-16
Are the weekly builds generally safe? I am [having a problem with the backend segfaulting](http://ubuntuforums.org/showthread.php?t=861439) and am hoping that maybe upgrading will solve it. I don't want to risk hosing the system, though.

---

### Post by laga on 2008-07-16
Oops. The package failed to build. I'll take a look ASAP.

---

### Post by laga on 2008-07-17
Okay, it was just mythplugins that failed. I've uploaded a fixed package.

---

### Post by mrand on 2008-07-21
> **laga said:**
> Okay, it was just mythplugins that failed. I've uploaded a fixed package.
Howdy laga,

What should "mythfrontend --version" respond with for the July 20th (fixes17845) build?  

I built a second box that I can experiment with a little more, and I've found the same thing as my production box: when updated by the weekly -fixes, the --version number doesn't change.  I even tried forcing a reinstall, and when that didn't work, I removed move things and installed again.  Still no dice.


```
$ sudo aptitude reinstall mythtv-frontend
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages will be REINSTALLED:
 mythtv-frontend
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and
0 not upgraded.
Need to get 0B/1954kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 138252 files and directories currently installed.)
Preparing to replace mythtv-frontend
0.21.0+fixes17845-0ubuntu0+mythbuntu1 (using
.../mythtv-frontend_0.21.0+fixes17845-0ubuntu0+mythbuntu1_i386.deb)
...
Unpacking replacement mythtv-frontend ...
Setting up mythtv-frontend (0.21.0+fixes17845-0ubuntu0+mythbuntu1) ...

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

$ mythfrontend --version
Please include all output in bug reports.
MythTV Version   : 17416
MythTV Branch    : branches/release-0-21-fixes
Library API      : 0.21.20080304-1
Network Protocol : 40
Options compiled in:
 linux profile using_oss using_alsa using_arts using_jack
using_backend using_dbox2 using_dvb using_firewire using_frontend
using_hdhomerun using_iptv using_ivtv using_joystick_menu
using_libfftw3 using_lirc using_opengl_vsync using_opengl_video
using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmcw
using_xvmc_vld using_glx_proc_addr_arb using_bindings_perl
using_bindings_python using_opengl using_ffmpeg_threads
using_libavc_5_3 using_live
```

My production box is the same way, except that it shows an even older version:

```
Please include all output in bug reports.
MythTV Version   : 16838
MythTV Branch    : branches/release-0-21-fixes
Library API      : 0.21.20080304-1
Network Protocol : 40
```

I'd be more than happy to provide any logs, feedback, reinstall, or whatever to help resolve this.

   Marc

---

### Post by laga on 2008-07-21
Oops. I always forget to fix this.. yes, the version number is incorrect. The next build will have it fixed.

---

