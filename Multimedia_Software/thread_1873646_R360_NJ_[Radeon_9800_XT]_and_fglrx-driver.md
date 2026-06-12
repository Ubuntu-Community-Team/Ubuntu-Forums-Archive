---
title: "R360 NJ [Radeon 9800 XT] and fglrx-driver?"
date: 2011-11-01
forum: Multimedia Software
---

### Post by Azyx on 2011-11-01
Hi. have read here about my gfx-card. [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I have installed this card: ```
VGA compatible controller: ATI Technologies Inc R360 NJ [Radeon 9800 XT]
```I have earlier only had an old onboard gfx-card, but I installed this cos I want to test Ubuntu 11.10. But when I look at Additional drivers, it say that I don't have any propretary drivers, and it could not find any and the tab 'visual effects' are missing in Appearance.

I have installed fglrx-driver from symantic and when I open ATI Catalyst control center (as root) it says I lack drivers, are not working  or run: 
```
aticonfig
aticonfig: No supported adapters detected
```But arent my ATI-card supported?

Edit. I dont understan the support-side and r300g-drive, if it propreatary drives or open and it's seems to be and old info?

/Cheers

---

### Post by ajgreeny on 2011-11-01
Your card is supported only with the open source driver that you had when you installed.  This is one disadvantage of older ATI cards, though the open source driver is getting better and better.

I doubt that you will be able to run unity-3d, the default in 11.10, nor even unity in 11.04, though the unity-2d version from the repos should work OK in either ubuntu version.

---

### Post by Azyx on 2011-11-01
> **ajgreeny said:**
> Your card is supported only with the open source driver that you had when you installed.  This is one disadvantage of older ATI cards, though the open source driver is getting better and better.

I doubt that you will be able to run unity-3d, the default in 11.10, nor even unity in 11.04, though the unity-2d version from the repos should work OK in either ubuntu version.

so fglrx don't longer support 9800xt as the documentations says, or does they mean that the open drivers support 3d acceleration? How do I check 3d support? Arent there any problem with the install?

---

### Post by ajgreeny on 2011-11-01
Use command ```
glxinfo
``` in terminal and if you get output with the line shown in red below, you have 3d acceleration.  You may need to install **mesa-utils** to get glxinfo to run;  I'm not sure if it is installed in a default system.
```
user@ubuntu1004:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
[COLOR=Red]direct rendering: Yes[/COLOR]
server glx vendor string: SGI
server glx version string: 1.2
```

---

### Post by Azyx on 2011-11-01
> **ajgreeny said:**
> Use command ```
glxinfo
``` in terminal and if you get output with the line shown in red below, you have 3d acceleration.  You may need to install **mesa-utils** to get glxinfo to run;  I'm not sure if it is installed in a default system.
```
user@ubuntu1004:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
[COLOR=Red]direct rendering: Yes[/COLOR]
server glx vendor string: SGI
server glx version string: 1.2
```

I only get this:

```
Azyx@Black:~$ glxinfo
name of display: :0.0
Segmentation fault
```

There must be anything broken in the driver/system! Don't I need to config something in xorg.conf?

---

### Post by Azyx on 2011-11-01
I don't have any Xorg.conf file :(

---

### Post by Azyx on 2011-11-01
Seems like ATI have stopped support my card in fglrx-driver. [http://askubuntu.com/questions/73231/graphic-driver-unknown-when-using-an-ati-radeon-xpress-200m](http://askubuntu.com/questions/73231/graphic-driver-unknown-when-using-an-ati-radeon-xpress-200m)

So I have now get ridd of that ****. glxinfo and glxgears work again after removal of fglrx :)

/Cheers

---

