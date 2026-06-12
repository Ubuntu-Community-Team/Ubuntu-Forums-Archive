---
title: "Is this a workaround for ATI radeon under Jaunty??"
date: 2009-06-01
forum: Multimedia Software
---

### Post by KaYnemO on 2009-06-01
Hey hey

Just stumbled upon this link here: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Anyone tried this yet? It'd be nice if someone could share the experience !

---

### Post by MichaelSammels on 2009-06-01
Not tried this, but the vesa or ati always worked for me.

---

### Post by KaYnemO on 2009-06-01
> **MichaelSammels said:**
> Not tried this, but the vesa or ati always worked for me.


Hmm... I dunno - I too want 3D, compiz etc. The proprietary drivers used to give that to a certain extend.

Found this though:
[http://ubuntuforums.org/archive/index.php/t-1135074.html](http://ubuntuforums.org/archive/index.php/t-1135074.html)

Don't know whether they fixed the sound :)

---

### Post by mcduck on 2009-06-01
> **KaYnemO said:**
> Hey hey

Just stumbled upon this link here: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Anyone tried this yet? It'd be nice if someone could share the experience !

Depends on *what Radeon model* you are talking about.

---

### Post by KaYnemO on 2009-06-01
> **mcduck said:**
> Depends on *what Radeon model* you are talking about.

I'd be happy with ATI Radeon Mobility x1600

---

### Post by mcduck on 2009-06-02
> **KaYnemO said:**
> I'd be happy with ATI Radeon Mobility x1600
For Radeon x1600 the open-source "radeon" driver is currently the best one available (Actually pretty much the *only* one). And that's what is used by default.

The latest versions of the proprietary fglrx driver don't support this card any more.

I'm actually running radeon driver on my laptop with Mobility Radeon X1600 and I'd consider it to be working very well. No pixel shader support so some Compiz effects that used to work with fglrx don't work any more, but on the other hand no video problems and suspending the machine works reliably.'


edit: quote from that guide:
> Which cards does ATI no longer support? The ATI Radeon 9500-9800, X300-X2100, Xpress. See the complete list here. If your card is on that list, you are restricted to the 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty! This guide currently is for installing 9.5. !!!SO BE CAREFUL!!!
..so that guide definitely isn't for Mobilty Radeon X1600.

---

### Post by KaYnemO on 2009-06-02
> **mcduck said:**
> For Radeon x1600 the open-source "radeon" driver is currently the best one available (Actually pretty much the *only* one). And that's what is used by default.

The latest versions of the proprietary fglrx driver don't support this card any more.

I'm actually running radeon driver on my laptop with Mobility Radeon X1600 and I'd consider it to be working very well. No pixel shader support so some Compiz effects that used to work with fglrx don't work any more, but on the other hand no video problems and suspending the machine works reliably.'


edit: quote from that guide:

..so that guide definitely isn't for Mobilty Radeon X1600.

Hmmm... too bad... seriously... I've been a linux advocate for six years now and I can truly see how linux becomes more and more sophisticated and at the same time user-friendlier. So it sucks that I cannot anymore take advantage of the newer distros because of the stupid video card :(

---

### Post by mcduck on 2009-06-02
> **KaYnemO said:**
> Hmmm... too bad... seriously... I've been a linux advocate for six years now and I can truly see how linux becomes more and more sophisticated and at the same time user-friendlier. So it sucks that I cannot anymore take advantage of the newer distros because of the stupid video card :(

What is the problem you are having? Like I said, I have the same graphics chip on my laptop and I haven't had any problems (apart from the Blur-plugin in Compiz not working) running 9.04..

---

### Post by Stochastic on 2009-06-03
Moved to Multimedia & Video.

I also would recommend the open source driver.  Since Jaunty my ATI Radeon Xpress 200m has been quite happy with the open source driver and full compiz functionality (including dual monitor support).

---

### Post by bastienauneau on 2009-06-03
I have an Acer with ATI X1300 and I got very slow graphics and more than poor performances for 3D using Jaunty. I took the chance for a big clean up and reverted back to Intrepid, which I like.

Stochastic, I would be interested to see your xorg.conf file, I begin to think that I might would have had been able to make it better without downgrading ??

---

### Post by sehe on 2009-06-03
I just took the leap and installed Jaunty anyway on my ATI laptop.

It warned me in big letters that the fglrx driver was not going to be supported, but I took the 'risk' and installed anyway. So now I'm automatically using the free and opensource ATI driver. I must say, I don't notice any difference.

I have always been, and still am, running a full Compiz Fusion setup with full effects (great for propaganda purposes :)) and everything works like before - even the benchmark figures are okay. (I don't have the numbers ready since my laptop is at home).

Only one explanation coming to my mind: the free ati driver has been way improved to the point I don't notice any difference anymore.

$0.02

---

### Post by KaYnemO on 2009-06-03
> **sehe said:**
> I just took the leap and installed Jaunty anyway on my ATI laptop.

It warned me in big letters that the fglrx driver was not going to be supported, but I took the 'risk' and installed anyway. So now I'm automatically using the free and opensource ATI driver. I must say, I don't notice any difference.

I have always been, and still am, running a full Compiz Fusion setup with full effects (great for propaganda purposes :)) and everything works like before - even the benchmark figures are okay. (I don't have the numbers ready since my laptop is at home).

Only one explanation coming to my mind: the free ati driver has been way improved to the point I don't notice any difference anymore.

$0.02

hmmm... well... maybe I should try the opensource driver again. 

I'll get back to you all.

---

### Post by ssri on 2009-06-03
> **sehe said:**
> I just took the leap and installed Jaunty anyway on my ATI laptop.

It warned me in big letters that the fglrx driver was not going to be supported, but I took the 'risk' and installed anyway. So now I'm automatically using the free and opensource ATI driver. I must say, I don't notice any difference.

I have always been, and still am, running a full Compiz Fusion setup with full effects (great for propaganda purposes :)) and everything works like before - even the benchmark figures are okay. (I don't have the numbers ready since my laptop is at home).

Only one explanation coming to my mind: the free ati driver has been way improved to the point I don't notice any difference anymore.

$0.02

Hmm, for those who says the opensource drivers work, please state which ATI card/chip you have.  The opensource drivers included in Jaunty's livecd displayed the same artifacts (tearing and refresh dust/lines) under default blank and modified xorg.confs.  I heard that the rewrite of the opensource drivers have been promising, especially for my card (ATI Mobility Radeon x2300): [http://www.phoronix.com/forums/showthread.php?t=17438](http://www.phoronix.com/forums/showthread.php?t=17438) and [http://www.digitalself.org/2008/06/17/radeonhd-git-on-ubuntu-hardy-with-dri-3d-support/](http://www.digitalself.org/2008/06/17/radeonhd-git-on-ubuntu-hardy-with-dri-3d-support/).  I might upgrade to Jaunty after hearing this news.  However, I'm currently busy writing a paper that I want to submit soon.  Not worth tinkering with a working, stable system now.

---

### Post by Tokyo_Joe on 2009-06-03
I'm using a Radeon x800 and switched to the Open Source driver when I upgraded to Jaunty. And in almost every respect, performance improved. Now, I don't play any 3D games so it might be suffering there, but video plays much more smoothly, without the 'tearing' I got in Intrepid. Also I can have my desktop spinning round on a cube in surreal animated landscape without any noticable problem (not that I do, silly cubes...).

The only problem, which is a little annoying, is that I've lost my maximum resolution, 1920x1080. I get 1400xsomething maximum or 1368 or thereabouts if I want it in widescreen (which of course, I do since I'm using it on my 42" 1080p Aquos).

---

### Post by zeiz on 2009-06-04
I have ATI Radeon X700 "Sapphire" and I cannot even login after upgrade 8.10 to 9.04. 
The login screen is broken and completely frozen, only power button works.
Perhaps another problem I have is my monitor that is SyncMaster2253bw that has 1680x1050_60 resolution.
Could somebody advise how to switch to open source or vesa driver under 9.04?
Many thanks.

---

