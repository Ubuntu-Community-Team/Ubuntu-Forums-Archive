---
title: "Linksys WUSB54Gv4 continuously disconnects"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by dnehdnd on 2010-06-09
Hello. I am new to all things Linux. I hope to have things running as smoothly as I once did with Windows.

I've recently downloaded, installed Ubuntu 10.04 (june 5 2010)

As title suggests, this is about my USB wireless adapter Linksys WUSB54G ver.4 periodically failing. Now, the exact problem AND solution was posted on this thread:

[http://www.backports.ubuntuforums.org/showthread.php?t=1472475&page=3](http://www.backports.ubuntuforums.org/showthread.php?t=1472475&page=3)

Essentially, I have to try a new kernel or something. I downloaded the kernel 2.6.34 at [http://kernel.org/](http://kernel.org/) which is supposed to solve my networking problem. But above thread suggests building my own kernel somehow ([https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)) and some of its steps are unfortunately not straightforward as copy-and-paste and i'm afraid i can't go on after trying to mimic command prompts a few times.

I tried referring to other sites, like 

[http://www.linuxplanet.com/linuxplanet/tutorials/6853/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6853/1/)

but their suggested steps aren't exactly the same, or maybe they are really but i'm too dumb to see it.

I think I managed to copy the config file (i hope i chose the right one) and put it to the extracted folder of new kernel I just downloaded, but "Build the linux-image and linux-header .deb files" ? ugh :(


thanks in advance for all the help.

---

### Post by iponeverything on 2010-06-09
Building from kernel.org sources for an ubuntu system requires fair amount of experience to get right. I have rebuilding kernels for years, and I still miss details that will cause my first builds to fail. 

It is much easier to grab one of ubuntu kernel build trees and work from there.

[http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)

Grab the kernel source deb install it along with the headers and modify the kernel configuration in the way that you require install your patches - but make sure that it does not conflict with the ubuntu patches, and rebuild the kernel deb from the deb source tree like you would rebuild any other deb from source. Its is fairly easy, clean and details are handled by the .deb build requirements for the kernel.

Doing it from the kernel.org tree is possible, good experience and if you have the right kind of personality -- maybe even fun. But in most cases it will be anything but strait forward.

---

### Post by dnehdnd on 2010-06-09
> 
Grab the kernel source deb install it along with the headers and modify the kernel configuration in the way that you require install your patches - but make sure that it does not conflict with the ubuntu patches, and rebuild the kernel deb from the deb source tree like you would rebuild any other deb from source. Its is fairly easy, clean and details are handled by the .deb build requirements for the kernel.

I know I am being really naive, but seeing how I know nothing about Linux or kernel, it is pretty hard to imagine how I might go about 'modifying the kernel configuration in the way that I require' or 'installing my patches' or 'making sure there's no conflicts with ubuntu patches' and 'rebuilding the kernel deb from deb source tree' ... unless I am supposed to go about blindly mimicking other command prompts again somehow. if anyone could illuminate this further, I'd really appreciate it.

---

### Post by b k on 2010-06-09
Hi there, perhaps you may wish to try this (if you have administration  rights and can temporarily live without power saving).

Go to Applications > Accessories > Terminal

Code:
[COLOR=Blue]sudo gedit /etc/rc.local[/COLOR]   (then type your  password and press Enter)

add the following line at the* end* of the opened file (*just above*  the exit 0 line):

[COLOR=Blue]iwconfig wlan0 power off[/COLOR]

[COLOR=Red]save[/COLOR] and close

reboot

No garantee though if it will work for you. 
(If it does not work the above procedure can be repeated and the added  line removed to reverse the change -[COLOR=Red] but leave the  exit 0 line untouched[/COLOR]).

Thanks to papukaija at posts #14 and #16 at this link  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549585](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549585)

Good luck and let us know if it works.

---

### Post by iponeverything on 2010-06-10
> **dnehdnd said:**
> I know I am being really naive, but seeing how I know nothing about Linux or kernel, it is pretty hard to imagine how I might go about 'modifying the kernel configuration in the way that I require' or 'installing my patches' or 'making sure there's no conflicts with ubuntu patches' and 'rebuilding the kernel deb from deb source tree' ... unless I am supposed to go about blindly mimicking other command prompts again somehow. if anyone could illuminate this further, I'd really appreciate it.

I felt it a safe assumption that if you wanted to rebuild the kernel that you had reason for doing so like adding a special patch or modifying the configuration to suite a special case. If you don't need to rebuild the kernel, then don't. Just grab an rc and try it out to see if addresses the issues that you are having.

Looking at tread you referenced in initial post, there is no reason for you to build from scratch and there is perfectly good release candidate to test with.

---

### Post by dnehdnd on 2010-06-13
Thanks for the tips and assistance. 

B K, I followed your workaround and it seems to work well. I should stick to it until newer kernel becomes available for me.

---

### Post by Fernando Negro on 2011-12-29
I can confirm that - as of December 2011, and using only the official Ubuntu 10.04 lucid repositories - one can easily solve the problem, simply by [switching to a different kernel]("http://ubuntuforums.org/showthread.php?p=11572146#post11572146").

---

