---
title: "Unable to run 10.10 installer on GT 240."
date: 2010-10-19
forum: Mythbuntu
---

### Post by shadowlordKT on 2010-10-19
Hi,

I have two systems which were running MythBuntu-9.10.  I upgraded the video cards to nVidia GT 240's recently (since they dual-boot machines), and attempted to install MythBuntu 10.10 on them.

On one system, with a Zotac GT240, the installation went fine.  However, on the other system, with an EVGA GT240, the installer crashes.

Once I put in the CD and boot from it, I can see the MythBuntu splash screen with the 4/5 dots that change color, then the screen becomes all scrambled up.  There are no menus or any way for me select any options (like a text-mode install).

Both systems are Intel E5200's with 2GB RAM.  Although their components are not precisely identical, they have performed pretty similarly; and they work with Windows 7 fine; so I don't think it's a hardware defect on the EVGA GT240 side.

Is there anyway to get past this?

Thanks!

---

### Post by keepitsimpleengr on 2010-10-19
> **shadowlordKT said:**
> &#8943;On one system, with a Zotac GT240, the installation went fine.  However, on the other system, with an EVGA GT240, the installer crashes.&#8943;Is there anyway to get past this?&#8943;

I just built a [new system]("http://ubuntuforums.org/showthread.php?t=1587584") with EVGA GT240 and it would not install.  Ubuntu and Xubuntu also would not install.

I ended up installing 10.04 and then an online upgrade.

See the bug at [https://bugs.launchpad.net/bugs/661939]("https://bugs.launchpad.net/bugs/661939") and mark it as affecting you,

Good luck!

---

### Post by LowSky on 2010-10-19
try the alternate install of Ubuntu, and then add the Mythbuntu packages from synaptic. I'm not a fan of downloading an old version just to sit through a even longer update
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by shadowlordKT on 2010-10-19
> **keepitsimpleengr said:**
> I just built a 
See the bug at [https://bugs.launchpad.net/bugs/661939]("https://bugs.launchpad.net/bugs/661939") and mark it as affecting you,

I marked the bug as affecting me.  I see we both have the same model of video card.

> **LowSky said:**
> try the alternate install of Ubuntu, and then add the Mythbuntu packages from synaptic. I'm not a fan of downloading an old version just to sit through a even longer update
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

Thanks for the tip.  I'm going to give the alternate installer a shot now.

---

### Post by keepitsimpleengr on 2010-10-19
> **shadowlordKT said:**
> 
Thanks for the tip.  I'm going to give the alternate installer a shot now.

Let me know if you can get the alternate 10.10 Ubuntu to install.  I tried both ubuntu and xubuntu with no luck at all.   :sad:

---

### Post by superm1 on 2010-10-20
Alternate install will yield the same result post install.  You're better bet is to try picking the 'nomodeset' option in the F6 menu.

---

### Post by keepitsimpleengr on 2010-10-20
> **keepitsimpleengr said:**
> Let me know if you can get the alternate 10.10 Ubuntu to install.  I tried both ubuntu and xubuntu with no luck at all.

There is a text based install.  You'll find it on the miniCD install for ubuntu.  For the amd64 it's about 16MB.  A fast internet connection is a good idea, as well as a good mirror's URL.  If you are not DHCP, you'll need a gateway and nameserver IP address.  Everything will be downloaded from the internet for the install.

The Minimals are at [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

Good Luck! \\:D/

Note: No desktop with this install.

---

### Post by m42technic on 2010-11-08
I've had this same problem with the same exact video card, with numerous versions and install options. I also had the same situation with the Fedora 14. I'm getting the idea this could be a problem with Nouveau possibly?

---

### Post by mugs on 2010-11-29
Hi, I am having this issue too.  I was able to install it by running it with nomodeset, but when I reboot to use it, it does the same thing, can I start it the first time setting nomodeset, and if so, can I then install the NVIDIA drivers and have it work from now on?  Thanks.

---

### Post by nickrout on 2010-11-30
that should work.

---

### Post by mugs on 2010-12-01
It did.

---

### Post by Cripton on 2010-12-17
It works for me also, i have an XFX gt240, same problem, same solution..

---

### Post by leobaby on 2011-01-23
I have this same problem on a machine with an EVGA GT 240 512. Following the instructions at [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18") provided a workaround.

---

### Post by m42technic on 2011-03-19
I'm guessing from looking at the bug report that this issue may still exist in 11.04? Unless there is a downstream bugfix?

---

### Post by drkages on 2011-10-02
> **m42technic said:**
> I'm guessing from looking at the bug report that this issue may still exist in 11.04? Unless there is a downstream bugfix?

Did you try this method in Ubuntu 11.04, was it successful as well?

---

