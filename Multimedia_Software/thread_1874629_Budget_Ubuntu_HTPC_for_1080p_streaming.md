---
title: "Budget Ubuntu HTPC for 1080p streaming"
date: 2011-11-03
forum: Multimedia Software
---

### Post by colicab on 2011-11-03
Hi,

I have a HTPC build in mind to run Ubuntu with XBMC or other media center software on.

These are the specs I head in mind

**Case** Antec NSK2480
**Mobo** ASRock H61M-ITX
**CPU** Intel Pentium Processor G630T
**Memory** Kingston 2x2GB, DDR3-1066
**HD** 80GB Drive (I have this one already)


I think for 1080p streaming the hardware is sufficient. However, I'm quite new at using Ubuntu and haven't used XBMC (only heard great things about it). 

I would love some advice on this build concerning compatibility with Ubuntu and XBMC.

Perhaps someone has experience with these components running Ubuntu....?

Thanks!

---

### Post by Munk3y on 2011-11-03
Your setup will likely work fine. However, I personally wouldn't build an ITX HTPC unless I was using some sort of nVidia ION system. I've built a bunch of them and they work great, be it Linux or Windows. Intel hasn't really been known for their high performance GPUs.

---

### Post by colicab on 2011-11-04
Thanks for the reply. 

Could you perhaps give a little more detail about why not to use ITX without nVidia ION...?

Would a better alternative be a µATX board? And if so, any recommendations for an affordable one with HDMI, eSATA and USB3.0?

---

### Post by cubicsilver on 2011-11-04
This setup should work Awesome!!

Phoronix did a review of a similar asrock board(mATX)with the same chipset and it peformed quite well. [http://www.phoronix.com/scan.php?page=article&item=asrock_h61m&num=1]("http://www.phoronix.com/scan.php?page=article&item=asrock_h61m&num=1")

I was tempted to buy that board myself, until I seen this board: BIOSTAR TH61ITX+RCH ... similar to the asrock and only a 6 dollars more; comes with a remote.  :D  

Another possibility is the asus media gate (ASUS AT3IONT-I) It's an Atom processor with an ION chipset.  Comes with a remote, wireless n, hdmi, and is passively cooled.  $160 ($130 after rebate) *Newegg*

From what I can tell most people with the intel hd seem to be satisfied with performance. And the advantage to this setup is with an 1155 processor it would be more powerful than an atom/ion combo while close to the same price range.  You have the option to install an inexpensive nvidia card in the availible slot if the intel graphics are not cutting it for you.

---

### Post by Munk3y on 2011-11-07
> **colicab said:**
> Thanks for the reply. 

Could you perhaps give a little more detail about why not to use ITX without nVidia ION...?


The reason I use the nVidia ION systems are because I've never had any real problems with the drivers. They can play up to full HD 1080p video with no problems too.

> **colicab said:**
> Would a better alternative be a µATX board? And if so, any recommendations for an affordable one with HDMI, eSATA and USB3.0?

It really depends on your needs and wants. I went with fanless ITX systems and put them in a really small box. There's no real noise and it looks like it belongs in my entertainment center area. It's also extremely low power and so we can leave it on all the time without it really affecting our electric bill much. 

A µATX system, you will have a more powerful system that takes more power and also make noise due to CPU fans and the like. It'll have better upgradability though, which is always nice. So, you've got some pros and cons of each... hopefully that will help you decide. Unfortunately, I don't have a recommendation for the µATX system because I've always gone ITX.

---

### Post by papibe on 2011-11-07
> **colicab said:**
> I think for 1080p streaming the hardware is sufficient.

AFAIK, may be.

In order to have smooth 1080p playback you need video hardware acceleration. That processor does support it, however IMHO support for it is a little behind than for Nvidia cards.

If you were going to build a Windows system, you would have no problems because of the Windows DXVA2 libraries.

In Linux, using Nvidia's VDPAU has been (for years) the more stable and usable way to reproduce HD video. XBMC supports for it is great. I have setup two HTPC using Nvidia cards, and it is very easy.

For acceleration on Intel HD graphics you need the VAAPI libraries. I believe VLC can manage that, but it is still experimental on XBMC. [Here]("http://forum.xbmc.org/showthread.php?t=86581")'s some tricks to set VAAPI on XBMC. Despite that, I'm pretty confident that it'll become stable pretty soon (may be it's even working on the unstable/SVN version of XBMC).

In short, I just wanted to share that getting an Nvidia card for video acceleration is pretty safe. You can even get a inexpensive Geforce 210 for around $40 and get full acceleration.

Just some thoughts,
Regards.

---

### Post by colicab on 2011-11-09
Looking  on other forums and asking advice I recently found someone who has just about the same build (same MoBo and similar Pentium chip) who uses it for 1080p streaming.
[http://forum.xbmc.org/showthread.php?p=927960#post928069](http://forum.xbmc.org/showthread.php?p=927960#post928069)

So this gives me confidence the hardware is sufficient to support what I need.

On the other hand, like you said, the argument of VAAPI is recurring in the threads I read about this kinda build with XBMC. So, I will definitely keep in mind to add an nVidia card.

Thanks.

---

