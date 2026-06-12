---
title: "Common Problems / Frequently Asked Questions About Testing"
date: 2010-10-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-10-12
Here are answers to some commonly asked questions and solutions to common problems when testing pre-release Ubuntu versions. It will be updated during the testing period as necessary, so you may want to check back. Feel free to post suggestions for things that you think should be included (I won't promise to include them all, since making the document unnecessarily long typically discourages people from reading). 

[list] [*]**How can I upgrade to Natty?**

There's basically no point in upgrading to Natty at this point. It exists as a release in the archive, but isn't open for development, the Debian auto-sync hasn't started, and you can't really do anything useful. Unless you're a toolchain hacker or have special interest in a particular Debian sync issue, it's going to stay this way until after UDS.

That said, if you just want to feel like an early adopter, you can upgrade by replacing all instances of "maverick" in your /etc/apt/sources.list with "natty", and issuing ```
sudo apt-get update && sudo apt-get dist-upgrade
```

Other methods such as using Update Manager will not be working until around Alpha 1. Be advised that "apt-get dist-upgrade"ing isn't a supported upgrade method for regular upgrades; it's only used in the early stages of a development cycle since it's the only way to upgrade during those periods.


[*]**I already have a testing installation. Do I have to reinstall the latest alpha / beta / RC when it comes out?**

If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the alpha / beta / RC, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix.

The milestone releases (alphas, betas and the RC) are slightly stabilized snapshots of the package archive at pre-decided dates, so they reflect the latest state of Natty on those dates. If you're up to date, you already have the latest packages. If you have to reinstall, and have an old disc image, you may want to [use zsync]("https://help.ubuntu.com/community/ZsyncCdImage") to avoid having to download the whole image.


[*]**If I install the alpha / beta / RC now, do I need to reinstall the final version when it's released? **

You don't have to (Update Manager will let you upgrade to the final version), but you may want to, if one or more of the below apply:

[list]
[*] You have tweaked your testing installation to a point where you're not aware of its exact components and configuration 


[*] You have replaced essential components of your installation with versions from external repositories / PPAs


[*] You have used package installation scripts or similar tools which are not trusted by the Ubuntu development community


[*] You have applied hacks / workarounds for testing purposes for good reason (prompted during structured testing, bug triage etc.), which may cause problems during daily usage of a stable installation


[*] You're affected by potential corner cases that may require a reinstall to fix (which will be documented in the release notes)[/list]


[*]**Update Manager offers a "Partial Upgrade". What should I do?**

[Read this]("http://ubuntuforums.org/showthread.php?t=1343434").


[*]**When / at what time will the alpha / beta / RC be released?**

Take a look at [the release schedule]("https://wiki.ubuntu.com/NattyReleaseSchedule"). There's no specific time of the day for releases; just wait for the official release announcement, which will be mirrored immediately in the forum with a sticky thread as well.
 

[*]**I'm trying to report a bug, but I'm redirected to [this page]("http://help.ubuntu.com/community/ReportingBugs"). What's going on?**

That's intentional; you'll understand what's going on once you read that page :)


[*]**I'm trying to report a bug, but I don't know which package it belongs to. What should I do?**

Take a look at the [Bugs/FindRightPackage page on the wiki]("wiki.ubuntu.com/Bugs/FindRightPackage"), and try invoking Apport's (currently rather primitive) symptom-based reporting mode by issuing ```
ubuntu-bug
``` with no arguments. If those don't help, feel free to start a thread, or join the #ubuntu-bugs channel on [the Freenode IRC network]("help.ubuntu.com/community/InternetRelayChat") to ask for assistance.


[*]**My testing installation is badly broken. Is there a way to roll back to the stable release, or a relatively stable point in the development branch?**

No. You'll have to fix your installation or do a fresh install.


[*]**I haven't been getting updates for a while. Is it that there's nothing new in Natty, or is there a problem with the servers?**

The archive mirror you're using is probably lagging behind. You can see the status of the mirrors at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors). Also note that there will be relatively few updates during the freeze periods leading to alpha, beta and RC releases.


[*]**I downloaded the daily CD image, but it's oversized and I can't burn it on a CD.**

The daily images get built automatically, and due to the rapid and asynchronous nature of uploads to the development branch, no effort can be made to make them fit on a CD on a daily basis; such an effort is only made for the milestones. Note that you can still use oversized CD images for testing in a virtual machine.


[*]**Is testing Natty in a virtual machine useful?**

For testing kernels, X, and anything that interacts directly or at a low level with hardware, it's hard to produce useful bug reports. If filing bug reports from virtual machine installs, don't forget that they will be reports about Ubuntu failing to work on that particular virtual machine, and don't forget to indicate that you're testing on a virtual machine in your bug report. While virtual machines are a valid use case, bugs from real hardware are much more useful. If, however, you're only looking to test high-level functionality such as userspace applications, user interfaces, documentation, translations and so on, virtual machines are mostly fine.[/list]

---

### Post by ssam on 2010-10-14
is it worth adding that oversized cd images can still be used for live USB sticks.

---

### Post by Crazedpsyc on 2010-11-10
Is there a torrent for the daily release? Will there be one for b1?

---

### Post by cariboo on 2010-11-10
There normally aren't torrents for the Live CD. If you don't want to download it several times, use zsync to keep it up to date. Zsync only updates the changes that have been made since the last full download. Use the following command:

```
zsync http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso.zsync
```

change the version to the one you are using. 

**Note** Run zsync in the same directory as the daily iso you downloaded.

---

### Post by Crazedpsyc on 2010-11-10
Thanks, I suppose that'll do

---

### Post by gacb on 2010-12-17
So far, I don't like Unity much. It's great for users who do more surfing and messaging than working, but a work machine it isn't.

I work both from an office and on the road, hence I use a laptop and there isn't enough room to put all the applications I need in the panel, and it's slower to essentially run applications from the bin.

---

### Post by jerrylamos on 2010-12-19
> **gacb said:**
> So far, I don't like Unity much. It's great for users who do more surfing and messaging than working, but a work machine it isn't.

I work both from an office and on the road, hence I use a laptop and there isn't enough room to put all the applications I need in the panel, and it's slower to essentially run applications from the bin.

Yea, verily.  I want the whole screen for applications and don't need any extra "eye candy" code getting in the way.

BTW, sometimes I run Tiny Core which does have big hieroglyphics for tools etc but as soon as I fire up Firefox it gets the whole screen instantly overlaying all the "Unity" type egyptian hieroglyphics. No extra "autohide" code needed. The alphabet conveys a whole lot more information....

Now if you like eye candy, then try Kubuntu. Put the unity type stuff on Kubuntu and "keep it simple stupid" for us application people.  Maybe Lubuntu will turn into that.

Jerry

---

### Post by cariboo on 2010-12-19
This really isn't the place for opinions. If you want to post your opinion of Unity, there are threads in the [Cafe]("http://ubuntuforums.org/showthread.php?t=1636946") where you can do so.

---

### Post by Denja on 2011-01-09
> **cariboo907 said:**
> There normally aren't torrents for the Live CD. If you don't want to download it several times, use zsync to keep it up to date. Zsync only updates the changes that have been made since the last full download. Use the following command:

```
zsync http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso.zsync
```change the version to the one you are using. 

**Note** Run zsync in the same directory as the daily iso you downloaded.

[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#333333][FONT=Ubuntu Beta]if I used update-manager -d to upgrade from Ubuntu 10.10 64bit maverick [/FONT][/COLOR][/LEFT][/FONT][/COLOR]
I then downloaded the daily image using the following command:

```
zsync http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso.zsync
```

Where would be the directory of the image upgrade?
And if this is irrelevant with the zsync process how can I zsync the image i just dowloaded in my home directory to keep my desktop update?

Thank you

---

### Post by cariboo on 2011-01-09
> **Denja said:**
> [COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#333333][FONT=Ubuntu Beta]if I used update-manager -d to upgrade from Ubuntu 10.10 64bit maverick [/FONT][/COLOR][/LEFT][/FONT][/COLOR]
I then downloaded the daily image using the following command:

```
zsync http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso.zsync
```

Where would be the directory of the image upgrade?
And if this is irrelevant with the zsync process how can I zsync the image i just dowloaded in my home directory to keep my desktop update?

Thank you

The image would be in whatever directory you run the command in.

All zsync does is keep the daily image up to date, it doesn't update any packages, you still have to use update-manager or synaptic to update the packages. Personally I update 2 - 3 times a day.

---

### Post by nm_geo on 2011-01-13
> **cariboo907 said:**
> The image would be in whatever directory you run the command in.

All zsync does is keep the daily image up to date, it doesn't update any packages, you still have to use update-manager or synaptic to update the packages. Personally I update 2 - 3 times a day.

Good information here has saved me lots of time.  By the way, boo are you still running that b43 driver with BC4312 chip?  I had to revert to the older driver to get my wireless back up the STA just would not install properly.

---

### Post by cariboo on 2011-01-13
There was a new bcmwl-kernel-source package released a week ago. I had a strange problem with the b43 driver, where I could get a solid but slow connection to my Linksys WRT54GS running dd-ddwrt, but when connecting to my Linksys WRT310N it would connect, then drop the connection, and never connect again until a reboot.

---

### Post by offline247 on 2011-01-20
Not sure where to post this, but hope it's not the wrong section(new at this), here is my feedback&questions

Alpha related problem:
~ while installing a fresh clean distribution you can choose to update to newest packages(download while install), which might end up in errors, since there are new install releases already available(distro, not software packages)
~ many previosly used softwares still don't have source or repos ready for natty thus limiting the usage of old softwares you been used to, but there are still new ones, or some ready to use, also if upgrading from 10.10 some of them will remain installed and working, but not able to upgrade.
~ in case of old ntfs partitions, to make them automount at login you will need both: ntfs configuration tool and mount manager, but will only use the first one. for some reason netheir are starting if only one of them are installed, but works perfectly if both installed.
~ suggestion: don't update while installing fresh version, wait to have a system up and running, then upgrade to newest.
Unity related problems:
~ main issues after a fresh install, is that the 3D card doesn't install automatically, and since unity depends on 3D drivers it won't load.
~ unity also depends on some functions in compiz for better visual effects(this causes an issue with the point above)
~ unity brings a lot of new indicators, but also depends on many softwares, specially the ones that are installed as default, thus, removing one/any/all to be replaced, or not, might end in impossibility of upgrading in the future, e.g.: transmission ~ simple bittorrent client / removing it just to replace with a more complex one, or something you are used to(more familiar) or just because you don't want to ever use torrent site/format/function, and so on, will end up in hanging unity, thus stoping other softwares linked to unity(mainly all the default installed softwares)
~ unity will remove the old top panel, replacing it with new panel and functions, thus making harder to locate installed softwares, thou the top left corner screen there's an ubuntu icon which will open the /usr/share/applications folder that contains all the icons/links to your softwares, you can either use them from there, copy or shortcut them to desktop, or link it to main unity(left~side screen big panel) but only after you started the software
~ since unity redesigns the panels, softwares that have "close/minimize to notification area" function, will no longer drop at their usual place

It does worth giving it a try, but as suggested at install, not on a production PC, and be ready to use terminal to be saved more then usual. With all the above seems kinda impossible to test, but there are ways, be that using Classic desktop or standard(with unity), so here are some of my steps in which i had to use both desktops but at end is ready for use any if necesary:

~ after downloading and burned dvd or usb(my choice of test) boot from device to start
~ follow carefully the steps suggested, but make sure to uncheck the download packages while install(default should be uncheck)
~ after install and first reboot you'll be taken to login screen in wich you can choose(see bottom option after you click your user) classic or standard(default),this works on both, suggested login in standard, so log in the fresh clean desktop
~ here you will encounter first error saying something about unity can't load, lack of 3D, don't panic, if unity crashes first time, old(classic) will kick in.
~ for your safety do the following, go to System > Preferences > Startup Applications, and add "gnome-terminal", without quotes ofcourse, this will start terminal at each login
~ by now the "new restricted drivers found" message should pop up, meaning the video card has been identified and ready to be installed, but before starting to install this, go to Applications > Ubuntu Software Center and search for Advanced desktop effects settings or ccsm, install but don't start it, if it doesn't let you just use terminal: sudo apt-get update && sudo apt-get install ccsm , after you finished is safe to install new video drivers(use recomended or latest) and needs to be rebooted.
~ after reboot it's finally time to get the newest packages/update, in standard desktop unity might crash so i suggest classic desktop(or use the terminal), go to System > Administration > Update Manager, it will show a new window with PArtial Upgrades or Cancel buttons, cancel it, refresh your update database(press Check button) and at new popup window use partial. do not force another update/upgrade after it's finished, just reboot
~ at next reboot repeat the above step(update/reboot) until there are no more packages left to update(you will need a total of at least 3 reboots to finish updating all), when all done and no more packages left, reboot
~ by now you should be ready to use any or both desktops(classic&standard)

Small NOTE: if at any step you don't get unity or normal panels in any of the desktops, type in terminal: "gnome-panel"

Questions:
~ will unity always depend on the defaults softwares? because removing in example above does cause o problem.
~ can gdm-guest-session be removed or renamed, or better yet accesed from outside, LAN or internet?

Hope this helps,
~Think about it~
OffLine 24/7

---

### Post by loukingjr on 2011-02-10
I was just curious about something that's been going on since I first installed Xubuntu 11.04 in VirtualBox. Every time I boot it gives me a "something crashed" message although it doesn't say what. It doesn't seem to be affecting anything. Is there a crsh log somewhere I can check to see what exactly is crashing?

thanks.

---

### Post by cariboo on 2011-02-10
Have a look in /var/crash, there may be something there.

---

### Post by loukingjr on 2011-02-11
> **cariboo907 said:**
> Have a look in /var/crash, there may be something there.

well, it seems to be the network manager. I'm posting this in case it means anything to anyone.

ProblemType: Crash
Architecture: i386
Date: Fri Feb 11 02:59:45 2011
DistroRelease: Ubuntu 11.04
ExecutablePath: /usr/sbin/NetworkManager
ProcCmdline: NetworkManager
ProcCwd: /
ProcEnviron: PATH=(custom, no user)
ProcMaps:
 00110000-00150000 r-xp 00000000 08:01 134926     /usr/lib/libnl.so.1.1
 00150000-00151000 ---p 00040000 08:01 134926     /usr/lib/libnl.so.1.1
 00151000-00152000 r--p 00040000 08:01 134926     /usr/lib/libnl.so.1.1
 00152000-00155000 rw-p 00041000 08:01 134926     /usr/lib/libnl.so.1.1
 00155000-00158000 r-xp 00000000 08:01 262346     /lib/libuuid.so.1.3.0
 00158000-00159000 r--p 00002000 08:01 262346     /lib/libuuid.so.1.3.0
 00159000-0015a000 rw-p 00003000 08:01 262346     /lib/libuuid.so.1.3.0
 0015a000-0016d000 r-xp 00000000 08:01 262353     /lib/libz.so.1.2.3.4
 0016d000-0016e000 r--p 00012000 08:01 262353     /lib/libz.so.1.2.3.4
 0016e000-0016f000 rw-p 00013000 08:01 262353     /lib/libz.so.1.2.3.4
 00177000-00199000 r-xp 00000000 08:01 135093     /usr/lib/libsmime3.so
 00199000-0019b000 r--p 00021000 08:01 135093     /usr/lib/libsmime3.so
 0019b000-0019c000 rw-p 00023000 08:01 135093     /usr/lib/libsmime3.so
 0019c000-001cb000 r-xp 00000000 08:01 134939     /usr/lib/libnspr4.so
 001cb000-001cc000 r--p 0002e000 08:01 134939     /usr/lib/libnspr4.so
 001cc000-001cd000 rw-p 0002f000 08:01 134939     /usr/lib/libnspr4.so
 001cd000-001cf000 rw-p 00000000 00:00 0 
 001cf000-001e8000 r-xp 00000000 08:01 262324     /lib/libselinux.so.1
 001e8000-001e9000 r--p 00018000 08:01 262324     /lib/libselinux.so.1
 001e9000-001ea000 rw-p 00019000 08:01 262324     /lib/libselinux.so.1
 001ea000-00227000 r-xp 00000000 08:01 278629     /lib/libpcre.so.3.12.1
 00227000-00228000 r--p 0003c000 08:01 278629     /lib/libpcre.so.3.12.1
 00228000-00229000 rw-p 0003d000 08:01 278629     /lib/libpcre.so.3.12.1
 0022f000-00231000 r-xp 00000000 08:01 134995     /usr/lib/libgmodule-2.0.so.0.2800.0
 00231000-00232000 r--p 00002000 08:01 134995     /usr/lib/libgmodule-2.0.so.0.2800.0
 00232000-00233000 rw-p 00003000 08:01 134995     /usr/lib/libgmodule-2.0.so.0.2800.0
 00233000-00247000 r-xp 00000000 08:01 134949     /usr/lib/libnssutil3.so
 00247000-0024a000 r--p 00014000 08:01 134949     /usr/lib/libnssutil3.so
 0024a000-0024b000 rw-p 00017000 08:01 134949     /usr/lib/libnssutil3.so
 00255000-00256000 r-xp 00000000 00:00 0          [vdso]
 00256000-00261000 r-xp 00000000 08:01 153252     /usr/lib/NetworkManager/libnm-settings-plugin-keyfile.so
 00261000-00262000 r--p 0000a000 08:01 153252     /usr/lib/NetworkManager/libnm-settings-plugin-keyfile.so
 00262000-00263000 rw-p 0000b000 08:01 153252     /usr/lib/NetworkManager/libnm-settings-plugin-keyfile.so
 002e3000-00306000 r-xp 00000000 08:01 278084     /lib/libm-2.12.2.so
 00306000-00307000 r--p 00022000 08:01 278084     /lib/libm-2.12.2.so
 00307000-00308000 rw-p 00023000 08:01 278084     /lib/libm-2.12.2.so
 0033d000-00340000 r-xp 00000000 08:01 135003     /usr/lib/libplc4.so
 00340000-00341000 r--p 00002000 08:01 135003     /usr/lib/libplc4.so
 00341000-00342000 rw-p 00003000 08:01 135003     /usr/lib/libplc4.so
 0034b000-00352000 r-xp 00000000 08:01 134728     /usr/lib/libgudev-1.0.so.0.1.0
 00352000-00353000 r--p 00006000 08:01 134728     /usr/lib/libgudev-1.0.so.0.1.0
 00353000-00354000 rw-p 00007000 08:01 134728     /usr/lib/libgudev-1.0.so.0.1.0
 0036f000-003ae000 r-xp 00000000 08:01 137565     /usr/lib/libnm-util.so.1.6.0
 003ae000-003af000 r--p 0003f000 08:01 137565     /usr/lib/libnm-util.so.1.6.0
 003af000-003b0000 rw-p 00040000 08:01 137565     /usr/lib/libnm-util.so.1.6.0
 003b0000-004ae000 r-xp 00000000 08:01 137351     /usr/lib/libgio-2.0.so.0.2800.0
 004ae000-004af000 ---p 000fe000 08:01 137351     /usr/lib/libgio-2.0.so.0.2800.0
 004af000-004b1000 r--p 000fe000 08:01 137351     /usr/lib/libgio-2.0.so.0.2800.0
 004b1000-004b2000 rw-p 00100000 08:01 137351     /usr/lib/libgio-2.0.so.0.2800.0
 004b2000-004b3000 rw-p 00000000 00:00 0 
 005a8000-005bd000 r-xp 00000000 08:01 278094     /lib/libpthread-2.12.2.so
 005bd000-005be000 ---p 00015000 08:01 278094     /lib/libpthread-2.12.2.so
 005be000-005bf000 r--p 00015000 08:01 278094     /lib/libpthread-2.12.2.so
 005bf000-005c0000 rw-p 00016000 08:01 278094     /lib/libpthread-2.12.2.so
 005c0000-005c2000 rw-p 00000000 00:00 0 
 005c8000-005d2000 r-xp 00000000 08:01 262336     /lib/libudev.so.0.10.0
 005d2000-005d3000 r--p 0000a000 08:01 262336     /lib/libudev.so.0.10.0
 005d3000-005d4000 rw-p 0000b000 08:01 262336     /lib/libudev.so.0.10.0
 00613000-0076d000 r-xp 00000000 08:01 278080     /lib/libc-2.12.2.so
 0076d000-0076e000 ---p 0015a000 08:01 278080     /lib/libc-2.12.2.so
 0076e000-00770000 r--p 0015a000 08:01 278080     /lib/libc-2.12.2.so
 00770000-00771000 rw-p 0015c000 08:01 278080     /lib/libc-2.12.2.so
 00771000-00774000 rw-p 00000000 00:00 0 
 00794000-007d9000 r-xp 00000000 08:01 132105     /usr/lib/libgobject-2.0.so.0.2800.0
 007d9000-007da000 r--p 00044000 08:01 132105     /usr/lib/libgobject-2.0.so.0.2800.0
 007da000-007db000 rw-p 00045000 08:01 132105     /usr/lib/libgobject-2.0.so.0.2800.0
 0080f000-0082b000 r-xp 00000000 08:01 278077     /lib/ld-2.12.2.so
 0082b000-0082c000 r--p 0001b000 08:01 278077     /lib/ld-2.12.2.so
 0082c000-0082d000 rw-p 0001c000 08:01 278077     /lib/ld-2.12.2.so
 008cb000-008d4000 r-xp 00000000 08:01 153255     /usr/lib/NetworkManager/libnm-settings-plugin-ifupdown.so
 008d4000-008d5000 r--p 00008000 08:01 153255     /usr/lib/NetworkManager/libnm-settings-plugin-ifupdown.so
 008d5000-008d6000 rw-p 00009000 08:01 153255     /usr/lib/NetworkManager/libnm-settings-plugin-ifupdown.so
 0093a000-0094e000 r-xp 00000000 08:01 135014     /usr/lib/libpolkit-gobject-1.so.0.0.0
 0094e000-0094f000 r--p 00013000 08:01 135014     /usr/lib/libpolkit-gobject-1.so.0.0.0
 0094f000-00950000 rw-p 00014000 08:01 135014     /usr/lib/libpolkit-gobject-1.so.0.0.0
 00968000-00985000 r-xp 00000000 08:01 134493     /usr/lib/libdbus-glib-1.so.2.1.0
 00985000-00986000 r--p 0001c000 08:01 134493     /usr/lib/libdbus-glib-1.so.2.1.0
 00986000-00987000 rw-p 0001d000 08:01 134493     /usr/lib/libdbus-glib-1.so.2.1.0
 009a3000-00a78000 r-xp 00000000 08:01 262299     /lib/libglib-2.0.so.0.2800.0
 00a78000-00a79000 r--p 000d4000 08:01 262299     /lib/libglib-2.0.so.0.2800.0
 00a79000-00a7a000 rw-p 000d5000 08:01 262299     /lib/libglib-2.0.so.0.2800.0
 00a89000-00a90000 r-xp 00000000 08:01 278096     /lib/librt-2.12.2.so
 00a90000-00a91000 r--p 00006000 08:01 278096     /lib/librt-2.12.2.so
 00a91000-00a92000 rw-p 00007000 08:01 278096     /lib/librt-2.12.2.so
 00ade000-00ae0000 r-xp 00000000 08:01 135005     /usr/lib/libplds4.so
 00ae0000-00ae1000 r--p 00001000 08:01 135005     /usr/lib/libplds4.so
 00ae1000-00ae2000 rw-p 00002000 08:01 135005     /usr/lib/libplds4.so
 00aeb000-00b26000 r-xp 00000000 08:01 262212     /lib/libdbus-1.so.3.5.3
 00b26000-00b27000 r--p 0003a000 08:01 262212     /lib/libdbus-1.so.3.5.3
 00b27000-00b28000 rw-p 0003b000 08:01 262212     /lib/libdbus-1.so.3.5.3
 00b4c000-00b4f000 r-xp 00000000 08:01 134996     /usr/lib/libgthread-2.0.so.0.2800.0
 00b4f000-00b50000 r--p 00003000 08:01 134996     /usr/lib/libgthread-2.0.so.0.2800.0
 00b50000-00b51000 rw-p 00004000 08:01 134996     /usr/lib/libgthread-2.0.so.0.2800.0
 00b51000-00c5c000 r-xp 00000000 08:01 134941     /usr/lib/libnss3.so
 00c5c000-00c5f000 r--p 0010a000 08:01 134941     /usr/lib/libnss3.so
 00c5f000-00c61000 rw-p 0010d000 08:01 134941     /usr/lib/libnss3.so
 00e13000-00e38000 r-xp 00000000 08:01 137568     /usr/lib/libnm-glib.so.2.4.2
 00e38000-00e39000 r--p 00024000 08:01 137568     /usr/lib/libnm-glib.so.2.4.2
 00e39000-00e3a000 rw-p 00025000 08:01 137568     /usr/lib/libnm-glib.so.2.4.2
 00f11000-00f22000 r-xp 00000000 08:01 278095     /lib/libresolv-2.12.2.so
 00f22000-00f23000 r--p 00010000 08:01 278095     /lib/libresolv-2.12.2.so
 00f23000-00f24000 rw-p 00011000 08:01 278095     /lib/libresolv-2.12.2.so
 00f24000-00f26000 rw-p 00000000 00:00 0 
 00f69000-00f6b000 r-xp 00000000 08:01 278083     /lib/libdl-2.12.2.so
 00f6b000-00f6c000 r--p 00001000 08:01 278083     /lib/libdl-2.12.2.so
 00f6c000-00f6d000 rw-p 00002000 08:01 278083     /lib/libdl-2.12.2.so
 08048000-080ec000 r-xp 00000000 08:01 153244     /usr/sbin/NetworkManager
 080ed000-080ee000 r--p 000a4000 08:01 153244     /usr/sbin/NetworkManager
 080ee000-080ef000 rw-p 000a5000 08:01 153244     /usr/sbin/NetworkManager
 080ef000-080f0000 rw-p 00000000 00:00 0 
 09e12000-09e69000 rw-p 00000000 00:00 0          [heap]
 b67b4000-b67b5000 ---p 00000000 00:00 0 
 b67b5000-b6fb5000 rw-p 00000000 00:00 0 
 b6fb5000-b6fb6000 ---p 00000000 00:00 0 
 b6fb6000-b77be000 rw-p 00000000 00:00 0 
 b77c5000-b77cc000 r--s 00000000 08:01 132942     /usr/lib/gconv/gconv-modules.cache
 b77cc000-b77ce000 rw-p 00000000 00:00 0 
 bf9ef000-bfa10000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:    NetworkManager
 State:    S (sleeping)
 Tgid:    359
 Pid:    359
 PPid:    1
 TracerPid:    0
 Uid:    0    0    0    0
 Gid:    0    0    0    0
 FDSize:    32
 Groups:    
 VmPeak:       25120 kB
 VmSize:       25116 kB
 VmLck:           0 kB
 VmHWM:        4300 kB
 VmRSS:        4300 kB
 VmData:       16828 kB
 VmStk:         136 kB
 VmExe:         656 kB
 VmLib:        7148 kB
 VmPTE:          36 kB
 VmSwap:           0 kB
 Threads:    3
 SigQ:    0/5885
 SigPnd:    0000000000000000
 ShdPnd:    0000000000000000
 SigBlk:    0000000000000000
 SigIgn:    0000000000001000
 SigCgt:    0000000180014283
 CapInh:    0000000000000000
 CapPrm:    ffffffffffffffff
 CapEff:    ffffffffffffffff
 CapBnd:    ffffffffffffffff
 Cpus_allowed:    1
 Cpus_allowed_list:    0
 Mems_allowed:    1
 Mems_allowed_list:    0
 voluntary_ctxt_switches:    132
 nonvoluntary_ctxt_switches:    140
Signal: 6
Uname: Linux 2.6.38-2-generic i686
UserGroups:

---

### Post by loukingjr on 2011-02-13
I noticed there are two lines that made me wonder...

ProcEnviron: PATH=(custom, no user)
UserGroups: 	

should there be a user and a UserGroup?
maybe that's why it NetworkManager crashes on boot?

---

