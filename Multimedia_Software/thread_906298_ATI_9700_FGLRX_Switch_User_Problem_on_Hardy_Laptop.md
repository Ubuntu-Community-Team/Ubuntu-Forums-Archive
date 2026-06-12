---
title: "ATI 9700 FGLRX Switch User Problem on Hardy Laptop"
date: 2008-08-31
forum: Multimedia Software
---

### Post by Sweevo on 2008-08-31
I'm looking for a bit of help getting to the bottom of a problem that I've had on my laptop ever since using the ATI proprietary FGLRX drivers on Hardy.

To be brief, my issue is that if I log into a session and then use the switch user option, the display becomes corrupt - here's a screenshot to illustrate the problem:

[ATTACH]83491[/ATTACH]

The only way out of this is to press CTRL + ALT + F7 to switch back to my first session. Switching back works perfectly without any corruption.

If I log out of the first session and then log into the second user, this also works fine, but again I can't use switch user from the second account due to the display corruption.

My hardware is an MSI Megabook M510C Laptop with an ATI Mobility Radeon 9700 - [http://msicomputer.co.uk/index.php?func=proddesc&prod_no=643&maincat_no=135]("http://msicomputer.co.uk/index.php?func=proddesc&prod_no=643&maincat_no=135")

I'm using the Catalyst 8.8 drivers, installed by following the manual steps here: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

All previous versions of the Catalyst drivers that I've tried since installing Hardy have had the same problem. I even get the same problem on a clean install of Hardy. However the Open Source ATI drivers don't suffer with the same problem, they switch user perfectly.

Here's a copy of my xorg.conf: [ATTACH]83492[/ATTACH]

And here are the results of fglrxinfo:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.1.7873 Release

```

And the results of glxinfo | grep direct:

```
direct rendering: Yes

```

I'm not currently using Compiz, although when I do it works fine.

Here's a zipped copy of my Xorg.0.log: [ATTACH]83494[/ATTACH]

The last two lines are where I tried to switch user.

Any help would be gratefully received!

Thanks

Sweevo

P.S. I'm a relatively new Linux user, so please be gently with me :)

---

### Post by whitethorn on 2008-10-06
I have the same problem, only my graphic card is an ATI Radeon 9600 Pro Turbo. I haven't been able to get my graphics to work properly.  Hopefully someone knows what to do about this.

---

### Post by doobydave on 2008-11-04
I have not had joy with my agp 9600 pro card ever since breezy badger.

The switch user issue i remember being present in all fglrx .

I'm waiting for a fix in the open source driver to appear which would be the best solution.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/89024](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/89024)

---

