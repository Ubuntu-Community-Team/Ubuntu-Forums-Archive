---
title: "Blank Screen during boot. DOS works fine."
date: 2011-02-14
forum: Multimedia Software
---

### Post by nolanjurgens on 2011-02-14
I have an Acer Aspire One AOA110 (SSD version that came w/ Linpus Lite) that my brother gave to me several months back when it stopped working. I've been trying various ways to revive it or make it useable, but haven't had any luck so I figure it's time to look to the community for ideas. I have already updated the BIOS to the latest (v3310) version, so I don't think it's the common issue these netbooks have where they don't even post. I'm kind of thinking the GPU died halfway or something. If I could just get it to work in a command line only mode, I'd be happy.

The netbook will post fine, but when I try to boot into Linux, the screen will go blank part way through the boot process. I don't ever remember hearing sound afterwards so I don't know if just the screen is blank or if the computer is locked up as well. I have tried several distros, but all of them seem to run into the same issue. Some with text based installers (Debian) get all the way through the install, but won't get all the way through the boot process. I'm only trying to get to a command line, not into X or anything graphical. Arch Linux also uses a text based installer, but I couldn't even get into the installer before the screen goes blank. I've tried changing some of the kernel options such as nomodeset, vesa and framebuffers options, but didn't have much luck with them either. I've also tried some older versions of Ubuntu (I think back to either 8.04 or 8.10) and tried the text installs, but I can't remember if I couldn't get into the installer or if I just couldn't boot, I want to say I couldn't even install. Mind you it's not random, it's always at the same point for a particular distro.

So the other small twist to this all is that FreeDOS works fine, besides not being able to get the sound card or network card working. I can play games, set different resolutions in ZSNES, etc. This seems a little odd to me, but I'm hoping it makes perfect sense to someone reading this.

Thanks for sticking with me so far, but here's what I'm looking for. I want to be able to run Linux with a command line interface, but I can't find the right distro/settings/whatever that it stays in the video mode (vesa?/framebuffer only?/I'm not even sure what to search for) where I keep the display and get to a command line. Any thoughts on what's happening when the screen goes blank or what I can do to get Linux working on here again? Thanks.

---

### Post by hsoulen on 2011-02-16
I don't yet have any solutions for you, but maybe a question that might help.

Have you tried running any of these distros (Ubuntu specifically) from the live CD? If so what is the result?

Hank

---

### Post by nolanjurgens on 2011-02-17
Yeah. I've tried them all live. Screen goes blank during boot. Another distro I tried since posting is NASLite, which is a FTP server on a single floppy and not much else and even that blanks the screen before I get to a command line. My only hope now is that there's some specific option to set when building the kernel that will make it work, and someone knows what it is and can let me know. Otherwise the netbook is just gonna have to live its life out as a DOS machine.

---

### Post by hsoulen on 2011-02-17
> **nolanjurgens said:**
> Yeah. I've tried them all live. Screen goes blank during boot. Another distro I tried since posting is NASLite, which is a FTP server on a single floppy and not much else and even that blanks the screen before I get to a command line. My only hope now is that there's some specific option to set when building the kernel that will make it work, and someone knows what it is and can let me know. Otherwise the netbook is just gonna have to live its life out as a DOS machine.

Well crap. I am sorry this is the case, my wife has one of these netbooks and it runs Linux Mint with no issue so I am starting to lean toward a problem with your motherboard/chipset.

Have you had a look in the BIOS to see if there are any options related to graphics? Amount of memory to allocate etc? If I remember correctly there is probably not but maybe worth a look.

If all you are looking for is a command-line linux install you can always try Slackware or for that matter minix and just use Lynx for browsing.

Good Luck, sorry I could not be more helpful.

Hank

---

### Post by nolanjurgens on 2011-02-17
Thanks for responding. I just realized I forgot to mention that this netbook used to run Ubuntu Netbook Remix without any issues, then just one day it wouldn't boot up and the screen would go blank during boot like it does now. So there is a hardware issues there for sure. But it's not totally dead so I'm trying to work around it the best I can. I've looked through all the BIOS settings and there's not much there to change.

---

