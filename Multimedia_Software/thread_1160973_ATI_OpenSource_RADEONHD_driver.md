---
title: "ATI OpenSource RADEONHD driver"
date: 2009-05-16
forum: Multimedia Software
---

### Post by frogotronic on 2009-05-16
Hello,

  I have a basic question(s) regarding the opensource ATI drivers.  I am currently using Hardy Heron and the proprietary FGLRX 9.1 drivers.  All is well.

  I'm thinking about upgrading to Jaunty - BUT I have an x2300 Mobility Radeon video card (based on x1300 -> based on R500 series cards).  This card won't work with the new xorg 1.6 + FGLRX 9.4 environment.  Therefore, I'd need to switch to the opensource drivers.

Q1) Would I used the ATI driver (xserver-xorg-video-ati) or the RADEONHD driver (xserver-xorg-video-radeonhd)?  It seems to me that the best driver would be the RADEONHD driver.

Q2) Will the RADEONHD driver permit (a) openGL rendering, (b) 3D acceration and (c) use of compiz?

  Sorry this is a long post, but I often find the discussion regarding FGLRX vs OpenSource confusing.

Lastly, are there any good "Howto's" to install the current RADEONHD driver on Hardy, so that I can 'try it out' before upgrading to Jaunty, or can I simply install xserver-xorg-video-radeonhd package via Synaptic?

Thanks much,
- CH

:popcorn:

---

### Post by pme 72 on 2009-05-16
I recently upgraded my 8.10 installation to 9.04. My video card is ATI Radeon x1550 also based on the x1300 series. lshw -C display reports the card as Product: RV505. No changes were required for my upgrade however I was running opensource drivers in 8.10. Compiz runs well for me but I just ask it to do basic functions like rotate the cube with the mouse wheel. 

The radeonHD drivers are not installed on my system so I can not help you out with Q2.

---

### Post by frogotronic on 2009-05-17
Hi,

   Thanks "pme 72" - I guess you're running the xserver-xorg-video-ati drivers.  Can you use openGL applications?  (like Google Earth)

- CH

---

### Post by lilychef on 2009-05-17
Hey, there -- I just bought an X1300 which won't work with Jaunty as I had it configured... How do you install the open source driver from the command prompt?  Somebody gave me this erroneous line from my previous post... Thanks:

sudo dpkg-reconfigure -phigh xserver-xorg

Came back Unrecognized Command

---

### Post by frogotronic on 2009-05-17
> **lilychef said:**
> Hey, there -- I just bought an X1300 which won't work with Jaunty as I had it configured... How do you install the open source driver from the command prompt?  Somebody gave me this erroneous line from my previous post... Thanks:

sudo dpkg-reconfigure -phigh xserver-xorg

Came back Unrecognized Command

```
sudo apt-get install xserver-xorg-video-radeonhd
```

or if that doesn't work, try this post...
[http://www.digitalself.org/2008/06/17/radeonhd-git-on-ubuntu-hardy-with-dri-3d-support/](http://www.digitalself.org/2008/06/17/radeonhd-git-on-ubuntu-hardy-with-dri-3d-support/)

---

### Post by lilychef on 2009-05-17
> **cement_head said:**
> ```
sudo apt-get install xserver-xorg-video-radeonhd
```

This didn't work... Unrecognized command again

> or if that doesn't work, try this post...
[http://www.digitalself.org/2008/06/17/radeonhd-git-on-ubuntu-hardy-with-dri-3d-support/](http://www.digitalself.org/2008/06/17/radeonhd-git-on-ubuntu-hardy-with-dri-3d-support/)

Don't understand this.  Will this work for my X1300?   FOrgive me -- I'm still very new to this... Thanks

---

### Post by frogotronic on 2009-05-17
> **lilychef said:**
> This didn't work... Unrecognized command again



Don't understand this.  Will this work for my X1300?   FOrgive me -- I'm still very new to this... Thanks

You might have a more serious issue than a video driver

try 

```
sudo apt-get install -f
```

see if that does anything

---

### Post by lilychef on 2009-05-17
More serious?  All I did was turn the machine off, swap cards, and turn it back on again....  See, this is what I don't understand about Ubuntu.... Windows is pretty cut and dry about this stuff.... Easy-peasy....  I realize I'm not on Windows anymore (and no worries - I'm pretty much sold on the uniqueness, speed, and simplicity of the Ubuntu interface), but I feel like if somebody's going to bother with releasing an OS like Ubuntu, they should offer some built-in support that doesn't necessitate us to learn a new language and go off on a wild goose chase to find answers to issues... Knowmsain?

I'll try your suggestion, but should I?   Is it going to risk messing up my previously stable install?  I just don't know anymore..... :confused:

---

### Post by lilychef on 2009-05-17
On another note, and maybe this warrants a new thread in a different forum, but why are so many peeps sticking with prior versions of Ubuntu?  Is it because it takes so much work to make their current one stable?  Ha!  I noticed SEVERAL improvements in speed, etc. when I upgraded to Jaunty from Intrepid..... except for the hardware issues when I tried to improve my machine.... Just wondering... As a matter of fact, consider this question rhetorical, and I will post the identical question in the general section....  Simply consider it food for thought....

---

### Post by frogotronic on 2009-05-18
> **lilychef said:**
> On another note, and maybe this warrants a new thread in a different forum, but why are so many peeps sticking with prior versions of Ubuntu?  Is it because it takes so much work to make their current one stable?  Ha!  I noticed SEVERAL improvements in speed, etc. when I upgraded to Jaunty from Intrepid..... except for the hardware issues when I tried to improve my machine.... Just wondering... As a matter of fact, consider this question rhetorical, and I will post the identical question in the general section....  Simply consider it food for thought....

are you sure you are at the command prompt?

Applications>Accessories>Terminal

---

### Post by pme 72 on 2009-05-18
I am not sure which drivers are activated, ati, radeon and vesa are all installed according to Synaptic. There is no driver listed in the xorg.config file. The radeonhd driver is not installed. 

When I try to open SuperTuxKart my system freezes and that program does require Open GL. It ran fine in 8.10 with the default open source drivers. I found installation instructions for Google Earth but they look to be a little beyond my current skill level. Wish I could be more help.

---

### Post by frogotronic on 2009-05-18
> **pme 72 said:**
> I am not sure which drivers are activated, ati, radeon and vesa are all installed according to Synaptic. There is no driver listed in the xorg.config file. The radeonhd driver is not installed. 

When I try to open SuperTuxKart my system freezes and that program does require Open GL. It ran fine in 8.10 with the default open source drivers. I found installation instructions for Google Earth but they look to be a little beyond my current skill level. Wish I could be more help.

Might try this guide...

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by pme 72 on 2009-05-18
That is interesting. The Radeon HD driver is not an option as my card is RV505. I do have some 3D. CannonSmash runs OK in the simple mode. I can always boot into XP in I want to play SuperTuxKart. That is the only feature I lack from my upgrade from 8.10. The stability of the open source driver across system upgrades is still more important to me than the availability of 3D.

---

### Post by pme 72 on 2009-05-20
Maybe the radeonhd driver would work. The documentation you pointed me to said it would work for R520 and later cards. Mine is listed as RV505. I do not know if that means mine is earlier than the R520 or later. I am hesitant to change given the number of posts about issues with video drivers. Mine seem to work just fine.

---

### Post by growled on 2009-05-20
I think the radeon driver is installed by default. It also pulls in the ati package. Games wouldn't work for me either so I installed the radeonhd driver through Synaptics and then added this line to my /etc/fstab file under Device....

Driver  "radeonhd"

Games work perfectly now.

---

### Post by frogotronic on 2009-05-20
> **growled said:**
> I think the radeon driver is installed by default. It also pulls in the ati package. Games wouldn't work for me either so I installed the radeonhd driver through Synaptics and then added this line to my /etc/fstab file under Device....

Driver  "radeonhd"

Games work perfectly now.

Hi Growled,

  That's awesome news!  Are you using Jaunty?

- CH   :p

---

