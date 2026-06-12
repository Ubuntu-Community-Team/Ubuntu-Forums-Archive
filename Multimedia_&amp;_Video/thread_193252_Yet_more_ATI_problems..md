---
title: "Yet more ATI problems."
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by BoomAM on 2006-06-09
Hi.

Ive spent the better part of today trying to get the ATI drivers, any version, to install. Ive tryed 5+ methods that ive found around the web, methods from the Ubuntu Wiki, methods found on these forums, and none of them work.
I still cant get the thing installed!
At first i thought it was just me putting in the code wrong, so i set Package Manager to install the stuff for me instead. But that didnt make a difference either.
Ive tryed both the ones off the Package Manager, and the ATI ones, which just error when i 'open' them.
Im not too fussed which gets installed, preferably the 'better' ones of the ATI and the open source ones though. :p

If it helps, if i search for fglrx in Package Manager, i get the following listed as installed:
fglrx-control
fglrx-kernal-source
linux-restricted-modules-2.6.15-23-386
xorg-driver-fglrx
xserver-xorg-driver-ati

Hardware in question is a IBM Thinkpad Z60M with a ATI Mobility X600.

Also, if possible, can someone tell me the difference between the i386 kernel and the i686 one? Would there be any benefit for me to set the package manager to install the i686 stuff that it lists?
The i686 stuff is listed as being for the CPU that im using, yet for some reason, Ubuntu has installed the i386 stuff?

Thanks in advance all. :)

---

### Post by deadgobby on 2006-06-09
[QUOTE=BoomAM]Hi.

Ive spent the better part of today trying to get the ATI drivers, any version, to install. Ive tryed 5+ methods that ive found around the web, methods from the Ubuntu Wiki, methods found on these forums, and none of them work.
I still cant get the thing installed!
At first i thought it was just me putting in the code wrong, so i set Package Manager to install the stuff for me instead. But that didnt make a difference either.
Ive tryed both the ones off the Package Manager, and the ATI ones, which just error when i 'open' them.
Im not too fussed which gets installed, preferably the 'better' ones of the ATI and the open source ones though. :p

If it helps, if i search for fglrx in Package Manager, i get the following listed as installed:
fglrx-control
fglrx-kernal-source
linux-restricted-modules-2.6.15-23-386
xorg-driver-fglrx
xserver-xorg-driver-ati

Hardware in question is a IBM Thinkpad Z60M with a ATI Mobility X600.

Also, if possible, can someone tell me the difference between the i386 kernel and the i686 one? Would there be any benefit for me to set the package manager to install the i686 stuff that it lists?
The i686 stuff is listed as being for the CPU that im using, yet for some reason, Ubuntu has installed the i386 stuff?

Thanks in advance all. :)[/QUOTE]

 There is a bug with the the ATI video with Dapper. Have you tried
Try Edited file /etc/X11/xorg.conf and replaced the "ati" driver with "vesa". The vesa driver works with just about any hardware, but it's a noticeably slow driver.
This was from a artical on Distro whatch.
[http://distrowatch.serve-you.net/wee...=20060605#news](http://distrowatch.serve-you.net/wee...=20060605#news)
Gobby

---

### Post by Turin Turambar on 2006-06-09
I must say that I'm more than pissed to have these bugs still around. I mean, they took 3 more months to polish the OS and now everyone with ATI cards are experiencing this sort of problem - fglrx not working!

Hello?? If XORG 7.0 is the problem, then they should've had used 6.9 instead. It's ridiculous to include xorg fglrx driver that doesn't work at all.

---

### Post by BoomAM on 2006-06-09
Dead link. ;)
So if im understanding correctly, its a known bug, with no actual work around bar the VESA one?
Im asuming that the problem is being looked into and that a fix is probably on the way? 
If so, i can live with it how it is, with this mesa driver until then, i dont need 3D for the moment.

Any ideas on the 386/686 thing i asked about? :)


Thanks for the quick replys guys/gals, very much appriciated. :)

---

### Post by Turin Turambar on 2006-06-10
386 works with ALL systems based on *86 proc. The 686 does not, so Ubuntu team opted for something that works for *everyone*.

---

### Post by BoomAM on 2006-06-10
What benefits would the i686 kernal bring over the i386 one?
Im using a P-M 2.0Ghz bty.

---

### Post by Turin Turambar on 2006-06-11
[QUOTE=BoomAM]What benefits would the i686 kernal bring over the i386 one?
Im using a P-M 2.0Ghz bty.[/QUOTE]

Normally, kernel 686 should run faster on 686 machines (e.g. your proc.), but I think that's not so noticable to the human eye. ;)
I have AMD XP2600+ so I should use k7 kernel instead, but it's not worth the hassle.

---

### Post by BoomAM on 2006-06-11
How much of a 'hassle' is it to change over anyway?
Im gonna see if i can find a guide somewhere on it...

---

### Post by MKR. on 2006-06-11
[QUOTE=BoomAM]How much of a 'hassle' is it to change over anyway?
Im gonna see if i can find a guide somewhere on it...[/QUOTE]

sudo apt-get install linux-*86

Replace the asterisk with your kernel (386, 486, 586, 686). When you reboot, you'll see the new kernel as the default in GRUB; the older kernel will still be available in case something goes wrong.

---

### Post by BoomAM on 2006-06-11
Thanks.
I installed the 686 kernel a few mins ago. :p
Seems slightly faster. Loads noticably faster.

What advantage, if any, does compiling my own Kernel bring?
I was just looking at this guide:
[http://ubuntuforums.org/showthread.php?t=85064&highlight=386+686](http://ubuntuforums.org/showthread.php?t=85064&highlight=386+686)

Thanks for the help bty ppl. :)

---

### Post by Turin Turambar on 2006-06-11
Well done. But I'm on the dial-up, so installing the new kernel would take about 3-4 hours. :(

Compiling a custom kernel requires some knowledge. I do not recommend it if you are inexperienced.

---

### Post by BoomAM on 2006-06-11
What advantages would compiling my own bring?

---

