---
title: "Nvidia drivers 310.40 screen tearing"
date: 2013-04-02
forum: Multimedia Software
---

### Post by The Squig on 2013-04-02
hi.

So after having struggled with the nvidia drivers not liking my dual monitor setup i went back to the nouveau drivers which actually work pretty well nowdays.

Yesterday however i decided to try the netflix app and found that the free drivers didnt work well with that so i installed the closed 310.40 driver from nvidia.
With the closed drivers im getting a lot of screen tearing which is becoming frustrating. it happens when playing videos but also during regular desktop use like scrolling down a webpage for instance. 

Anyone got any ideas on how to get rid of the tearing? I found some old fix where disabling composite in xorg.conf would help but after trying it i found that all my desktop envoirements need it to run and im not particulary interested in switching out my DE.

system:
ubuntu 12.10 32bit
Desktop: cinnamon
graphicscard: gtx 560ti

---

### Post by ManamiVixen on 2013-04-02
Nouveau driver..... Radeon x1950.... Are you sure as to what drivers you are using?

---

### Post by The Squig on 2013-04-02
yah, havent been on the forums for several years so my signature is out of date. edited my post

---

### Post by ManamiVixen on 2013-04-02
Well first off, never use the drivers provided by Nvidia on their site. They will break your computer.

So  to get a working system again, remove the driver you got from Nvidia's  site, then use the xorg-edgers PPA which will install Nvidia 313.26, the  newest driver.

```
sudo add-apt-repository ppa:xorg-edgers/ppa && sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install nvidia-313
```

---

### Post by The Squig on 2013-04-02
Ty for the reply :)

i did in fact install the 310 driver using nvidias installer but it worked alright except for the fact that i was getting screentearing.

Anyways i uninstalled it and tried out your install method. installed fine and updated my kernel and some packages but im still unfortuneatly experiancing the same problem with tearing :(


edit:

ok so i tried disabling my secondary display and as far as i can tell im not gettin any tearing issues while its disabled. So i guess im back to my old problem with general twinview issues. I was on linux mint debian edition before and found that the 295 driver worked a lot better in that regard but it wont install on any newish kernels unfortuneatly :/

---

### Post by bogan on 2013-04-03
Attention **Manamivixen**,

Please do not Post False, Misleading and blatantly Predudiced statements disguised as advice:> Well first off, never use the drivers provided by Nvidia on their site. They will break your computer.By doing so you devalue what might otherwise be genuine valid suggestions.

My personal experience is that I have had far more problems downloading from Xorg-edgers  PPA, than I have ever had using the Nvidia.com downloaded binary driver files.

The only real problem I have had was with the notorious 240.50 version, and that affected the Ubuntu ppa versions as well.

Even the widely quoted reason for avoiding the nvidia, com downloads, that you would need to reinstall them after every kernal update is no longer true, as v 340 onwards is compatible with DKMS and gets automatically updated.

Which is not to say that I would advice its use to self labelled 'noobies', though I would to anyone who is willing to RTfM.

Chao!, **bogan.**

---

### Post by pr4vus on 2013-06-25
> **ManamiVixen said:**
> Well first off, never use the drivers provided by Nvidia on their site. They will break your computer.

So  to get a working system again, remove the driver you got from Nvidia's  site, then use the xorg-edgers PPA which will install Nvidia 313.26, the  newest driver.

```
sudo add-apt-repository ppa:xorg-edgers/ppa && sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install nvidia-313
```

i think that this statement is incorrect. i just installed the brand spanking new 319.32 from NVIDIA website on 12.04 with 3.7.0 kernel and it works like a charm.

---

### Post by artbio on 2013-06-25
I was having the same problem. The suggestions from this webpage -> [http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu](http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu) fixed the problem for me. No more video taring! I am using the nvidia 319 driver from the xorg edgers ppa. With the nouveau drivers I can't output to a second monitor from my laptop. So the nvidia drivers are the only option for me.

---

### Post by The Squig on 2013-06-25
> **artbio said:**
> I was having the same problem. The suggestions from this webpage -> [http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu](http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu) fixed the problem for me. No more video taring! I am using the nvidia 319 driver from the xorg edgers ppa. With the nouveau drivers I can't output to a second monitor from my laptop. So the nvidia drivers are the only option for me.

Ty that looks promising, im away over the summer so i cant try it out atm but ill give it a go when i get back. Since I made this post ive concluded that:

 1. this is a twinview issue, i have no issues when only using one(1) display.
 2. While not solved ive noticed some improvment with the latest drivers. (3.19 ~3.20 ish i think)

as for the installtion methods. I prefer the installer since it's easier to try out older versions and simple to uninstall. Generally though its probably a better idea to just install the deb package from either edgers ppa or the default repository, but i've never had anything but minor hassles with the installer which ive used for abhout 1½ years now :)

---

### Post by artbio on 2013-06-25
If both monitors don't support the exact same refresh rate you probably are going to have the same problems. I had to disable the laptop display which is very small at 15 inch. So I am now using only the external 24 inch display. However this doesn't bother me at all!

As for installing the debs it's just as easy. Run this in a terminal.

sudo apt-get install nvidia-319

this will also install the nvidia-settings and nvidia-persistenced

To uninstall:

sudo apt-get purge nvidia-319 nvidia-settings nvidia-persistenced (this also removes config files)

Or use Synaptic Package Manager. I find it very usefull. You can browse the packages you have installed. You can check dependencies and much more!

apt-get --help

to check what options are available to you.

Good luck!

---

