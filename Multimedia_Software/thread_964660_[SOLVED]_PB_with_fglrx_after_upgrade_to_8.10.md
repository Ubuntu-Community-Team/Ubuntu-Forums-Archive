---
title: "[SOLVED] PB with fglrx after upgrade to 8.10"
date: 2008-10-31
forum: Multimedia Software
---

### Post by rtorres on 2008-10-31
Hi.

After upgrading, I'have no desktop effects. I can't activate them.

fglrx for my ATI X1300 are recognizen and installed, but.... 

only root can execute programs with accelerated 3d.

as a normal user:
$ fglrxinfo 
Segmentation fault

$ sudo fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.1.8087 Release

And all apps executed by root run smoothly... but executed by any other user segfaults...

OD ubuntu 8.10
desktop i386 running on amd64 platform

02:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)


Any help will be wellcome 8)

Rtorres

---

### Post by rtorres on 2008-10-31
deleted bye rtorres--- it's a duplicate...

---

### Post by rtorres on 2008-10-31
I don't understand what's happening.

I can remember using ubuntu8.10-beta and being able to use 3d acceleration (booting from cd)

and have used fglrx in 7.10 wo problems.

Are ther a problem with device permissions?? ¿How can I check it?

thnx
rtorres

---

### Post by overdrank on 2008-10-31
Hi and please do not make multiple threads on the same issue. Moved and merged :)

---

### Post by cro on 2008-10-31
You say 'moved and merged' - but for those of us coming late to the party, 'moved and merged' to where exactly?

---

### Post by overdrank on 2008-10-31
> **cro said:**
> You say 'moved and merged' - but for those of us coming late to the party, 'moved and merged' to where exactly?

Located at the top of the page  Multimedia & Video :)

---

### Post by rtorres on 2008-10-31
I think it's more a problem of modules, but maybe Multimedia & video is a good place to be...
Any way, I'm interested in cad apps.... :(

More info....
This card ATI Radeon X1300 works with "radeon" driver when starting from the ubuntu CD (live).
And it's capable of doing desktop animations... even advanced ones...

So I changed the driver in xorg.conf to use "radeon" 
but when I select desktop animations, the system installs again fglrx.

What makes me think it's a permisions problem is that root can execute apps like fgl_gears (or something like that) and if a normal user tries to do it, the program segfaults.

Tryed also with strace, but no useful info... at least for me... :)

thnx
rtorres

---

### Post by docomo on 2008-10-31
The [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/810") say this:

> ATI "fglrx" video support

The ATI video driver in 8.10 drops support for video cards with r300 based chips (the Radeon 9500 - X600 Series of cards). If you have such a card, please use "Hardware Drivers" at System/Administration to disable it before the upgrade. Please see bug 284408 for more information 

I have a Radeon 9600 and I haven't upgraded yet because I would like to see this issue resolved first.

Here is the [bug page]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408")

---

### Post by rtorres on 2008-10-31
Hi docomo.

Thanks for your response.


I think thar this bug doesn't applies to my card. 
lspci says it's an
ATI Technologies Inc RV516 [Radeon X1300 Pro]

It's a big problem... desktop effects are not so important, but 3d applications that use opengl are important...

thnx
rtorres

---

### Post by rtorres on 2008-11-03
Hi again.

Looking fo rthis problem, I've found new symptoms...

I deinstalled all fglrx debs. And reinstalled them aftera reboot.

Then logged in and tryed to activate desktop effects.

Again...screen flicking and a problem. Desktop effects where not activated a a messsage box appeared.

fglrx module was loaded into the kernel.

Looking at /var/log/syslog I found this lines:
Nov  3 11:13:58 xxxx kernel: [  265.148055] __ratelimit: 12 callbacks suppres
sed
Nov  3 11:13:58 xxxx kernel: [  265.148071] glxinfo[7036]: segfault at 0 ip 0
0000000 sp bf8107ac error 4 in glxinfo[8048000+5000]
Nov  3 11:13:58 xxxx kernel: [  265.224892] glxinfo[7039]: segfault at 0 ip 0
0000000 sp bfc15ccc error 4 in glxinfo[8048000+5000]

So... the problem is more complicated... glxinfo is segfauling....

Keep looking....
rtorres

---

### Post by rtorres on 2008-11-03
Maybe my problem is SOVLED.

looking at why root can execute fglrxinfo and a normal user can't.... I used strace.

Strace output indicated that root and user where looking at DIFFERENT dinamic libraries!!!!!!

So I looked at environment variables and found that user had LD_LIBRARY_PATH=/usr/lib/xorg
and root didn't.

So next was to look at who was setting this var... I found that /etc/ati/ati-fglrx.sh was doing it.
I modified this file and deleted the sentences that set the variable.

Reboot....


and....

Everything is working fine (at least until now).

I don't know if this variable is used for somethig asti-related, but by system works without it.


I don't know how to send this info to the ati package maintainers...
This package: xorg-driver-fglrx works with /etc/ati (is the only one), but the modifies file doesn't belong to it.... maybe a previous version used it???

Thnx.
rtorres

---

