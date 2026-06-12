---
title: "Madwifi Atheros Hardy i686"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by luiznetto on 2009-11-17
I just re-installed Hardy Heron (8.04) i686 on one of my laptops that was running Hardy Heron i386 before. The wireless card is Atheros AR5007EG, and it was working with the driver madwifi-ng-r2756+ar5007. I guess if I try to reinstall this driver, it won't work, because this driver is for i386. This site:

[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

tells me that I need to install linux-restricted-modules and madwifi-tools; so I need to do the following:

1- Download linux-restricted-modules and madwifi-tools onto this laptop that I'm using right now

2- Copy linux-restricted-modules and madwifi-tools onto a USB flash drive;

3- Remove the flash drive from this laptop, insert it in the other laptop, copy the files, and install them in the other laptop.

So, which command should I use, just to download the files without installing them? I tried:

$ sudo apt-get -d linux-restricted-modules madwifi-tools
$ sudo apt-get --download-only linux-restricted-modules madwifi-tools
$ sudo apt-get --download-only install linux-restricted-modules madwifi-tools
$ sudo apt-get install --download-only linux-restricted-modules madwifi-tools

And none of them works. If anyone knows how to just download those packages without installing them, I'd appreciate it.

Thanks in advance,
Luiz

I finally did the following:

$ mkdir madwifi
$ sudo apt-get install --download-only linux-restricted-modules madwifi-tools

and I expected the packages to be downloaded to my ~/madwifi directory. At the end I got the message:
Download complete and in download only mode

I expected to find the packages in the ~/madwifi directory, but the directory was empty? Where the heck did the packages go?

---

### Post by snl2587 on 2009-11-18
Try this:

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

I've been using this for more than a year...the only thing to remember is you'll have to redo it after kernal updates.

---

### Post by luiznetto on 2009-11-19
Thank you for trying to help, but perhaps you don't realize that the page you refer to is full of dead links, just like the page where I downloaded my driver initially from:

[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

I noticed lots of pages that refer to madwifi mentioned in these forums were also removed.

Meanwhile, I managed to download some drivers: madwifi-0.9.4.tar.gz and madwifi-hal-0.10.5.6-current.tar.gz. Which one of these would work on my system? I'm afraid to install them because I don't know how to remove those tarballs in case they don't work.

I installed Arch Linux on that laptop last night. They do have a package that works: madwifi-0.9.4.4096-1-i686,pkg.tar.gz, which can be found at

[http://mirror.twilightlair.net/arch/extra/os/i686/](http://mirror.twilightlair.net/arch/extra/os/i686/)

It works on that Arch, but I can't use Arch because, they try to be a purely i686 system, and so I tried to open a CD that I had recorded in command line, and I couldn't open it, because it had been recorded on an i386 system, and I really don't want to waste all the time in the tremendous amount of work necessary to make Arch open my i386 folders.

Trying to install the above package probably won't work, since it was built for Arch, not for Ubuntu.

Perhaps I'll migrate to Linux Mint when I have a chance, they're less prudish in packing restricted formats or supporting all kinds of hardware (after all, they're European).

Well, all I can tell you is this: life is hard for you when you have an Atheros wireless card and use Linux. I don't know why they make our life so difficult. After all, I bought that laptop on the assumption that I could use any operating system that I like on it - or else I wouldn't have bought it in the first place.

Luiz

---

