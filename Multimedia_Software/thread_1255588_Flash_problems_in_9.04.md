---
title: "Flash problems in 9.04"
date: 2009-09-01
forum: Multimedia Software
---

### Post by okayneil on 2009-09-01
Hey guys, 

I just did a fresh install of ubuntu 9.04 and forgot that there was a problem with flash being choppy when in fullscreen mode. I know there is a fix for this somewhere I just cant find it.

Any help?

---

### Post by Tclarkie on 2009-09-01
how did you install it

---

### Post by blur xc on 2009-09-01
did you right click, select setting, and un-check the enable hardware acceleration check box?

BM

---

### Post by okayneil on 2009-09-01
> **Tclarkie said:**
> how did you install it

> **blur xc said:**
> did you right click, select setting, and un-check the enable hardware acceleration check box?

BM

No...where is that setting? I installed it on its own, no dual boot, normal ubuntu install.

---

### Post by blur xc on 2009-09-01
> **okayneil said:**
> No...where is that setting? I installed it on its own, no dual boot, normal ubuntu install.

Go to youtube or any website w/ flash, right-click on the flash content and there will be the menu.

With the vast number of "Why doesn't my Flash work?" posts on these forums, I can't believe there's not a Flash sticky somewhere that show how to uninstall all the open source swfdec (sp?) and gnash plugins, and then how to install Flash and optimize it.

I had to google it to find that tid-bit of information.

BM

---

### Post by okayneil on 2009-09-01
> **blur xc said:**
> Go to youtube or any website w/ flash, right-click on the flash content and there will be the menu.

With the vast number of "Why doesn't my Flash work?" posts on these forums, I can't believe there's not a Flash sticky somewhere that show how to uninstall all the open source swfdec (sp?) and gnash plugins, and then how to install Flash and optimize it.

I had to google it to find that tid-bit of information.

BM

No thats not the fix im looking for. There is a different one (this one doesnt work btw)

Flash is still choppy....

plus i have all different flash options deleted, im only using flash non free.

---

### Post by blur xc on 2009-09-01
> **okayneil said:**
> No thats not the fix im looking for. There is a different one (this one doesnt work btw)

Flash is still choppy....

plus i have all different flash options deleted, im only using flash non free.

From this thread- [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Way down in the troublshooting section-

> On occasion, installing Adobe Flash Player and/or watching online Flash streams successfully isn't as simple as it might ordinarily be. If you have tried installing it already, and are having issues, read on. First of all, please disable any ad-blocking Firefox extensions you have installed, such as Adblock Plus, as they can sometimes interfere with the Flash content you actually want to see. If you are still having issues after disabling the extension(s), you should now completely purge Adobe Flash Player from your system, along with any other packages which may be interfering with it, reinstall only Adobe Flash Player, restart your web browser, and then test Flash performance again. Will both 32-bit and 64-bit users copy and paste this command into the terminal:

```
sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

Still no joy? I would suggest following the instructions below for your particular Ubuntu version and architecture.

BM

---

### Post by okayneil on 2009-09-02
Still not having any luck. I tried a few things but nothing seems to have really worked. 

Re-install?

---

### Post by bootdoc on 2009-09-02
I put this in my /etc/apt/sources.list 

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

and have had no probs with flash since.

---

### Post by michael37 on 2009-09-02
> **blur xc said:**
> From this thread- [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Way down in the troublshooting section-



BM


This is outdated information.  flashplugin-nonfree provides an old version of adobe flash.

The correct sequence is:

1. Go to System/Software Sources and add a Third-Party APT line:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
2. sudo apt-get update
3. Run the following command (MODIFIED from previous post)
sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install adobe-flashplugin

---

### Post by michael37 on 2009-09-02
P.S. Whatever I said works for 32-bit.  64-bit requires a different procedure.  Are u running 32-bit or 64-bit?

---

### Post by okayneil on 2009-09-03
Im using 32 bit but this is what i get after following your steps : 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
Package flashplugin-nonfree is not installed, so not removed
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package nspluginwrapper is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate

> **michael37 said:**
> This is outdated information.  flashplugin-nonfree provides an old version of adobe flash.

The correct sequence is:

1. Go to System/Software Sources and add a Third-Party APT line:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
2. sudo apt-get update
3. Run the following command (MODIFIED from previous post)
sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install adobe-flashplugin

---

### Post by okayneil on 2009-09-03
Bump!

---

### Post by michael37 on 2009-09-04
> **okayneil said:**
> Im using 32 bit but this is what i get after following your steps :

Are you absolutely sure you added a new repository???

If not, then click here:

[http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb)

That will install the updated flash plugin using GDebi.

---

### Post by okayneil on 2009-09-06
It sort of half fixed the problem, playback is not choppy but now is just..hmm how do i put this...crap. 

Thanks for your help :)

---

### Post by michael37 on 2009-09-07
> **okayneil said:**
> It sort of half fixed the problem, playback is not choppy but now is just..hmm how do i put this...crap. 

Thanks for your help :)

Test your flash at [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

Flash player version (in About) should be 10.0.32.18.  

Shockwave for Linux doesn't exist (and noone uses it anyway)

---

### Post by okayneil on 2009-09-07
> **michael37 said:**
> Test your flash at [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

Flash player version (in About) should be 10.0.32.18.  

Shockwave for Linux doesn't exist (and noone uses it anyway)

yup thats all correct, flash is installed, think my graphics card is just shite.

---

### Post by woedend on 2009-09-07
What graphics card are you using?  Your bumpy playback will be the fault of your graphics card, most likely, not flash.  This is a common but fixable issue with intel cards, and with other cards most likely as well.

---

### Post by okayneil on 2009-09-07
> **woedend said:**
> What graphics card are you using?  Your bumpy playback will be the fault of your graphics card, most likely, not flash.  This is a common but fixable issue with intel cards, and with other cards most likely as well.

Conexant High Definition SmartAudio HD2

---

### Post by woedend on 2009-09-07
that's your video card?

---

### Post by okayneil on 2009-09-08
> **woedend said:**
> that's your video card?

sorry dude, i think this is it : Intel® Graphics Media Accelerator 950

---

### Post by overdrank on 2009-09-08
> **okayneil said:**
> sorry dude, i think this is it : Intel® Graphics Media Accelerator 950

Hi and with the intel graphics you may look at the link in my signature about Intel and Jaunty. This may solve your other [issue]("http://ubuntuforums.org/showthread.php?t=1181135") also.

---

### Post by woedend on 2009-09-08
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)
fixed my issue when I used Jaunty.

---

### Post by RJARRRPCGP on 2009-09-09
Please see this thread:

[http://ubuntuforums.org/showthread.php?t=1258604&page=2](http://ubuntuforums.org/showthread.php?t=1258604&page=2)

---

