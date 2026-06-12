---
title: "Will this video card work?"
date: 2005-11-06
forum: Multimedia &amp; Video
---

### Post by Eleaf on 2005-11-06
Hello everybody!  I was going to update a pc somebody gave me.  I may add a new motherboard and a new video card.  I was wondering if the   Chaintech XGI Volari V3 (128 mb) would work well with linux.  What I'm wanting is for it to work at a nice resolution with **Direct Rendering** at 24 or 32 bits.  All the cards I have used have been very old around 8 mb and direct rendering only works at 16 bits.

Also, considering this card isn't ati or nvidia, it probably uses a different driver and I was wondering if ubuntu has a solid driver so I can use this card at full power.

Does anybody know if it will work?  Here is a link to it.  [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1043623&Tab=0&NoMapp=0](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1043623&Tab=0&NoMapp=0)
:smile:

---

### Post by Teroedni on 2005-11-06
If you were looking for a serious gaming graphics card, you came to the wrong review. But, if you are looking for a budget solution for multimedia or home theater applications, the XGI Volari V3XT is an excellent option. The processor runs cool enough to only need passive cooling, and the silence is ideal for an HTPC situation where even the faintest hum of fans may interfere with video or music playback.
review
[http://www.bigbruin.com/reviews05/xgivolariv3xt/index7.php](http://www.bigbruin.com/reviews05/xgivolariv3xt/index7.php)


The volari v3 have only driver for suse or redhat, so it may be a little bit difficult to get it working in Ubuntu, but it is possible.
Only a whole work because of rpm ......
If yoour after gaming card then a geforce 4 mx is much better

from slashdot
review of a newer xgi
[http://hardware.slashdot.org/article.pl?sid=05/05/04/1321259&tid=152&tid=137](http://hardware.slashdot.org/article.pl?sid=05/05/04/1321259&tid=152&tid=137)

---

### Post by Eleaf on 2005-11-07
[QUOTE=Teroedni]If you were looking for a serious gaming graphics card, you came to the wrong review. But, if you are looking for a budget solution for multimedia or home theater applications, the XGI Volari V3XT is an excellent option. The processor runs cool enough to only need passive cooling, and the silence is ideal for an HTPC situation where even the faintest hum of fans may interfere with video or music playback.
review
[http://www.bigbruin.com/reviews05/xgivolariv3xt/index7.php](http://www.bigbruin.com/reviews05/xgivolariv3xt/index7.php)


The volari v3 have only driver for suse or redhat, so it may be a little bit difficult to get it working in Ubuntu, but it is possible.
Only a whole work because of rpm ......
If yoour after gaming card then a geforce 4 mx is much better

from slashdot
review of a newer xgi
[http://hardware.slashdot.org/article.pl?sid=05/05/04/1321259&tid=152&tid=137](http://hardware.slashdot.org/article.pl?sid=05/05/04/1321259&tid=152&tid=137)[/QUOTE]

Ok, thanks!  But I wanted to know if anybody has succesfully been able to get this to work with Ubuntu, you know, before I go buying it... = P

---

### Post by Teroedni on 2005-11-08
okey :)
maybe someone have tried this card in Ubuntu?


Also for a list of graphicscard which are tried in Ubuntu here is a link
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)
unfortunally your card is not listed

---

### Post by Eleaf on 2005-11-12
Alright, thanks!  Has anybody else had any experience with this?

---

### Post by sturgeonman on 2005-12-06
I have this card working under Ubuntu. It is not at full power though. I cant seem to find a driver that will get me past 1024x768 at 85hz. Other than that it does work fine, but I'm not playing games or video, yet!

---

### Post by sledmouth on 2005-12-16
I just purchased the XGI V3XT (Newegg.com) and am unable to get the sis driver to work with it with xorg 6.8.2. 

I get the following in Xorg.0.log:

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 root@crested.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF]
Current Operating System: Linux mucky64 2.6.12-10-amd64-generic #1 Fri Nov 18 11:51:07 UTC 2005 x86_64
Build Date: 10 October 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Fri Nov 18 11:51:07 UTC 2005
.
.
.
(--) PCI:*(1:0:0) unknown vendor (0x18ca) unknown chipset (0x0040) rev 2, Mem @ 0xe0000000/28, 0xf4000000/18, I/O @ 0xd000/7
.
.
.
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
        SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
        SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
        SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
        SIS340
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.

Fatal server error:
no screens found

```


```
sol@mucky64 log $ lspci |grep -i vga
0000:01:00.0 VGA compatible controller: XGI - Xabre Graphics Inc Volari V8 (rev 02)

```

I tried with both the sis driver provided by breezy as well as that from the sis developer's page: [http://www.winischhofer.net/sis/sis_drv.o_xorg_6.8.2_amd64_240605-1.tar.gz]("http://www.winischhofer.net/sis/sis_drv.o_xorg_6.8.2_amd64_240605-1.tar.gz")

I suspect that I need to upgrade xorg.
Any clues?

---

