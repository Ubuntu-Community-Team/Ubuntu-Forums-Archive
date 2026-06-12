---
title: "can't get winff to work"
date: 2014-07-22
forum: Multimedia Software
---

### Post by UncleMonty on 2014-07-22
Error message: Could not find either ffmpeg or avconv.

I am using ubuntu 14.04

Advice please.

---

### Post by mc4man on 2014-12-05
Install libav-tools

---

### Post by Yellow Pasque on 2014-12-06
> **mc4man said:**
> Install libav-tools

That should be installed automatically if using the winff from the repo, no?
winff depends on winff-gtk2 or winff-qt. Both of those depend on libav-tools or ffmpeg (at least here on Debian).

---

### Post by GrouchyGaijin on 2014-12-06
You can add this ppa for ffmpeg:
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
and then just use ffmpeg instead of trying to go through the winff front end

---

### Post by Rob Sayer on 2014-12-06
Winff is in the ubuntu repos ... it's there on this netbook running Mint 17 which is 14.04 underneath and it was there in the repos in 12.04.  I had it on my kubuntu 12.04 machine and I got it from there.

I suspect you got it from a 3rd party ppa and didn't install the dependencies when you installed winff.

3rd party ppas are something to avoid unless you really know what you're doing.  I'd never install from an external ppa when it was in the repos unless there was a new version that had something I couldn't live without.  That rarely happens.  Especially with winff which is rather old.

If you did install it from an 3rd party source I'd:

- open synaptic package manager.  If you don't have synaptic package manager install it.  It may seem weird at first for novices but it's fantastic.  It's perhaps the main reason I'm going to stick to debian based Linux distros.
- uninstall winff
- delete the 3rd party ppa you used to install winff.  In synaptic it's under settings->repositories.
- install winff.

Unfortunately I doubt you'll find winff any better than something like avidemux, which chokes on input files very rarely, much less often than winff has for me.  It may be worthwhile if it has a device preset you want but I wasn't impressed with it.

No harm in trying though.  Unlike in Windows you can install media programs in linux without the installer messing up your registry (which linux doesn't actually have) without warning.  In linux if the install process wants to remove something already there it's probably a depency for another program.  If I get that message I don't install without lookiing into what's going on.

Of course in windows the stupid install process just remaps your codecs orr whatever anyway.  There are lots of messed up windows setups out there just for that reason.

OK, I'm going into a windows rant.  I don't even have any windows anymore ... I overwrote my last windows partition when I installed Mint 17 on my laptop last weekend.

---

### Post by mc4man on 2014-12-06
> **Temüjin said:**
> That should be installed automatically if using the winff from the repo, no?
winff depends on winff-gtk2 or winff-qt. Both of those depend on libav-tools or ffmpeg (at least here on Debian).
Right - I've never really used winff
So then if on opening it can't find try opening Edit > Preferences & finding it for winff, screen (click on the ... button if need be & browse to select

Edit: deleting ~/.winff is something that could also be tried...

---

### Post by andrew.46 on 2014-12-06
> **Rob Sayer said:**
> Unfortunately I doubt you'll find winff any better than something like avidemux, which chokes on input files very rarely, much less often than winff has for me.  It may be worthwhile if it has a device preset you want but I wasn't impressed with it.

WinFF has 2 variables that often lead to errors:

[LIST=1]
[*]The version of FFmpeg / avconv used by the application
[*]The syntax of the presets file
[*]
[/LIST]

When both of these aspects are adequately addressed WinFF can be a useful, if not somewhat limiting, media converter.

---

### Post by mc4man on 2014-12-07
After a couple of days with winff & several installs of different packages I'd say the #1 thing to do first when having these type issues is delete the ~/.winff folder.
And if ever updating winff then at the very least delete ~/.winff/presets.xml, every time.
(-winff creates that preset file on first run. When winff updates/upgrades that file is not overwritten or replaced. Deleting it creates a new preset file using the packages new one on next winff run.

---

