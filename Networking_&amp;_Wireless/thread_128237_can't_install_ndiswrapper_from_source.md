---
title: "can't install ndiswrapper from source"
date: 2006-02-11
forum: Networking &amp; Wireless
---

### Post by joehill on 2006-02-11
I've been following the instructions on the wiki ([https://wiki.ubuntu.com/WifiDocs/Ndiswrapper?action=show&redirect=HowToSetUpNdiswrapper#head-43b2e2295bcf52aef4217347410f0c605a5c1c0e](https://wiki.ubuntu.com/WifiDocs/Ndiswrapper?action=show&redirect=HowToSetUpNdiswrapper#head-43b2e2295bcf52aef4217347410f0c605a5c1c0e)) and I've got it to build the modules and utils .deb files.  Now, when I follow the instructions to install them (sudo dpkg -i ndiswrapper-modules-[your kernel]_[current version]-1_i386.deb ndiswrapper-utils_[current version]-1_i386.deb) I get this output:

> ~$ sudo dpkg -i ndiswrapper-modules-2.6.12-10-386_1.9-1_i386.deb ndiswrapper-utils_1.7-1_i386.deb
(Reading database ... 154142 files and directories currently installed.)
Unpacking ndiswrapper-modules-2.6.12-10-386 (from ndiswrapper-modules-2.6.12-10-386_1.9-1_i386.deb) ...
Selecting previously deselected package ndiswrapper-utils.
Unpacking ndiswrapper-utils (from ndiswrapper-utils_1.7-1_i386.deb) ...
dpkg: error processing ndiswrapper-utils_1.7-1_i386.deb (--install):
 trying to overwrite `/usr/share/doc/ndiswrapper-utils/changelog.gz', which is also in package ndiswrapper-modules-2.6.12-10-386
dpkg: dependency problems prevent configuration of ndiswrapper-modules-2.6.12-10-386:
 ndiswrapper-modules-2.6.12-10-386 depends on ndiswrapper-utils-1.7; however:
  Package ndiswrapper-utils-1.7 is not installed.
dpkg: error processing ndiswrapper-modules-2.6.12-10-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ndiswrapper-utils_1.7-1_i386.deb
 ndiswrapper-modules-2.6.12-10-386

Since it looks like it wants the utils to be installed first, I do this: 

> ~$ sudo dpkg -i ndiswrapper-utils_1.7-1_i386.deb (Reading database ... 154160 files and directories currently installed.)
Unpacking ndiswrapper-utils (from ndiswrapper-utils_1.7-1_i386.deb) ...
dpkg: error processing ndiswrapper-utils_1.7-1_i386.deb (--install):
 trying to overwrite `/usr/share/doc/ndiswrapper-utils/changelog.gz', which is also in package ndiswrapper-modules-2.6.12-10-386
Errors were encountered while processing:
 ndiswrapper-utils_1.7-1_i386.deb


I thought maybe the "/usr/share/doc/ndiswrapper..." was from a previous installation but when I remove it it just gets reinstalled again and I get the same message.  After this process, ndiswrapper-utils shows up as a broken package.

I'd be grateful for any suggestions.

---

### Post by bscbrit on 2006-02-11
I think from the information you have provided that you are trying to install 2 different, conflicting versions of ndiswrapper - 1.7 and 1.9.  Let me look a little further and see if I can resolve this conflict.

---

### Post by bscbrit on 2006-02-11
No, you are using the correct versions.  ndiswrapper-utils 1.7 is NOT installing, as you know, because of : /usr/share/doc/ndiswrapper-utils/changelog.gz.  Try deleting this file manually (sudo rm -f /usr/share/doc/ndiswrapper-utils/changelog.gz) and then re-installing ndiswrapp-utils_1.7.  Once that has been successfully achieved, try installing the latest modules file: ndiswrapper-modules-2.6.12-10-386_1.9-1_i386.deb.

Hope this helps.

---

### Post by joehill on 2006-02-11
Thanks for the suggestions, bscbrit.  I've actually succeeded a couple times in getting the utils to install, but when I try to install the modules I always get this same error message ("trying to overwrite `/usr/share/doc/ndiswrapper-utils/changelog.gz', which is also in package ndiswrapper-utils") *even when that file doesn't exist*.

Just now I installed the utils (I got this error message, removed changelog.gz, the second time it worked), then I tried installing the modules and I got the message.  So I deleted the same file and I *still* get the message even though the file doesn't exist.

---

### Post by bscbrit on 2006-02-11
This might seem like a silly question - but you have tried the version of ndiswrapper that comes with the repos haven't you?  It works perfectly for me straight from synaptic on 2 very different machines; a desktop and a laptop.  I haven't had to download any updated versions.  If you haven't tried it, you really should.  It might save you a lot of work. :) 

But, other than that, you can see why people say you shouldn't mix packages unless you really have to.  If it hasn't been packaged for Ubuntu it can cause all sorts of headaches - but you already know that!

I'm still trying to think of a solution but I don't hold out much hope....

---

### Post by joehill on 2006-02-11
Well, I finally got it installed--I decided to download it again from sourceforge and start with a clean directory and for some reason it worked this time.  No idea what I did differently the first time.

In answer to your good question (sorry, long answer), the reason I wanted to compile the new one in the first place was that I had tried the original one and been unable to get it to work with two wireless cards.  Actually, my internal card (on the Acer Travelmate 2303, using the Inprocomm 2220 chipset) worked for a while and then stopped working, then started, then stopped, and I haven't been able to get it working for a couple weeks now.  Fed up with wasting hours and days trying to get ndiswrapper to work (and having read somewhere that some kernel people want to stop supporting ndiswrapper anyway--is this true?), I carefully studied the Ubuntu wiki list of cards along with several other lists and bought a new card reported to work out of the box without ndiswrapper.  Well, I can't get it to work, with or without ndiswrapper.  One can only assume that wireless card manufacturers all hate Linux and constantly change the chipsets in their cards just to spite us.  I thought maybe the newest version of ndiswrapper would support either one of these cards better, but neither card works at this point.

---

### Post by joehill on 2006-02-11
Thanks again bscbrit for all your helpful input.  We may not live in a very Linux world (yet) but at least the good people on the Ubuntu forum make the Linux world a better place.

Update: I finally decided to bypass the drivers on the ndiswrapper wiki and just go with the one directly from the manufacturers' web site and, after rebooting, my new card is working now.  Now I'm just crossing my fingers that it will work longer than my internal one did.

---

### Post by bscbrit on 2006-02-12
Well done - I'll keep my fingers crossed as well for a while.

The problem is not so much that manufacturer's keep changing the cards' specifications but simply that they consider the details proprietory information which they will not release to Linux driver writers. Until they start producing their own drivers for Linux then I suspect that ndiswrapper is here to stay, regardless of what others may wish.  In concept it is similar to the use of wine or cedega - provide a linux environment in which a piece of window's software can function although they are all very different items of software from each other.

Perhaps we should have spent more time trying to configure the correct drivers rather than trying to make ndiswrapper compile :D I had a similar experience - the downloaded driver simply would not work but the one on the window's disk (which I was strongly advised not to use) worked first time and has kept working ever since on 2 separate machines.

I'll keep an eye out for you in case any problems arise but, if not, I will see you around the forums.

---

### Post by joehill on 2006-02-13
Thanks.  It's still working for the most part.

Just to clarify, what I meant by manufacturers constantly changing chipsets is that they will market the SAME MODEL (in my case Linksys Wireless G WPC54GS, which is listed in Ubuntu's wiki as working straight out of the box) with a variety of chipsets.  But the one I received, same model number, uses a different chipset, and the only way to find this out is to take the shrinkwrap off the box and look at the tiny print on the back of the card, which states that it's actual Linksys Wireless G WPC54GS "Version 2.1," which uses a different chipset than Version 2 or Version 1.  Same with my Belkin card, ver. 2, which works although apparently ver. 1 and ver. 3 don't.  In each case, the only way to find out which model you're getting is to open up the package.

That's what I mean about manufacturers hating Linux--I'm sure they have reasons for selling cards with 4 different chipset under the identical name (and this is the case with almost every wireless card I've come across) but they're definitely not thinking about Linux users when they do this.  Note to manufacturers: clearly label which chipset you're using, or at the very least use different model numbers for cards with different chipsets!

---

### Post by bscbrit on 2006-02-14
No matter if they change the chipset, it will either use the same driver, or the results of 'lspci -n' will be different.  It is the results of the latter which will give you the starting point to identify the correct driver for your card, as per:

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

That is how one determines which of the mulitple drivers that usually appear on the driver installation disk for windows should be used.

---

