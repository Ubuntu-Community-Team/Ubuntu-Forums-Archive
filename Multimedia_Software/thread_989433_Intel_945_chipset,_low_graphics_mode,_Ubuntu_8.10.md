---
title: "Intel 945 chipset, low graphics mode, Ubuntu 8.10"
date: 2008-11-21
forum: Multimedia Software
---

### Post by cameron3200 on 2008-11-21
Hello, I'm trying to run Ubuntu 8.10 on an Acer 9410-4933. However whenever I try to log in, Ubuntu has to start in low graphics mode. I get the message: 
"(EE) intel(0): No valid FB address in PCI config space
(EE) Screen(s) found, but none have a usable configuration"

The notebook has an Intel 945 graphics chipset.
 I have searched the error and have not found any threads regarding this issue, any tips?
 Also, I'm not sure which info is needed, so if you need more info please ask and I'll do my best to get that info to you ASAP.

Thanks in advance!

---

### Post by cameron3200 on 2008-11-22
Anyone?:(

---

### Post by Franko30 on 2008-11-23
Hi,

got an (almost) similar Problem:

Have the same graphics chip (lspci gives Intel 945GM/GMS, 943/940GML)), but in my case the screen stays dark... Everything worked fine in 8.04...

With this thread:

[http://ubuntuforums.org/showthread.php?t=985498](http://ubuntuforums.org/showthread.php?t=985498)

I was able to get to some low graphics mode with 800x600 (using the vesa driver), but that's it. Changing back to intel gives me the blank screen again, using the i810 driver gives me the

> Ubuntu is running in low graphics mode
(...)
(EE) No devices detected.

error message.

Any suggestions?

Thanks

Franko30

---

### Post by ipburbank on 2008-11-23
I had some issues like this too, different error, but basicly I had an error with the nvidia xorg settings. did you upgrade or re-install? re-installing is what it took for me, the problems started after an upgrade.

---

### Post by Franko30 on 2008-11-23
> **ipburbank said:**
> I had some issues like this too, different error, but basicly I had an error with the nvidia xorg settings. 

Hmmm - but here we deal with Intel chip problems.


> **ipburbank said:**
> did you upgrade or re-install? re-installing is what it took for me, the problems started after an upgrade.


Tried both, no luck.

Cheers

Franko30

---

### Post by cameron3200 on 2008-11-23
I wanted to use 8.04 LTS but the install disc would just freeze on a  chopped up screen where you can barely recognize the Ubuntu logo.
The 7.10 disc did the same.

I have the i810 drivers installed.

I get correct resolution not low graphics resolution. When I go to change the display settings the only option for refresh rate is 0hz.

This leads me to believe this is more of an issue with the software for the display rather than the graphics chipset.

---

### Post by cameron3200 on 2008-11-23
As a temporary solution I'm using the vesa driver until the 'Intel' driver has some more of it's bugs resolved with this newer version of xorg.

At least there are no start-up errors with the vesa driver.

---

### Post by bonfire89 on 2008-11-23
yeah, I learned my lesson to not do a fresh install without running the live cd on this one as I am having the same problems. I just figured 8.04 worked fine, can't get worse.

---

### Post by hfzorman on 2008-12-31
I'm using an Intel 945 chipset too on a Dell with 768MB RAM and Intel Pentium IV @ 2.8 Ghz. With Ubuntu Hardy Heron there was no problem with compiz, As I have tried the Ubuntu Intrepid Ibex Live CD it didn't worked (stayed on black screen after initiating GDM) and I have decided to install it. I have made Ubuntu work, but using metacity instead of compiz. It seems compiz or some driver doesn't works correctly on this Ubuntu version.

---

### Post by cameron3200 on 2008-12-31
This issue relates to the issues with the "intel" driver in xorg. Not compiz, not being able to use compiz is just a side effect of having low graphics. If you have it working on yours could you please post your xorg.conf file?

Also this is an issue with Intrepid Ibex (8.10) which uses a different intel driver in xorg. I appreciate any comments to this issue as long as they are relevant.

---

### Post by bobdole123 on 2009-04-25
Same problem here. Would very much appreciate some help with it. I have the same laptop as OP.

Using 9.04 OS.

Trying to use the newest xorg intel driver and it crashes with this error. Once I go into "low" graphics mode, the correct resolution is displayed, but everything is choppy and I cant use any of the desktop effects.

Any help would be appreciated.

---

### Post by Franko30 on 2009-05-21
Hi,

still the same problem with Ubuntu 9.04.

Franko30

---

### Post by CronAcronis on 2009-06-02
Does anybody have this problem on x86_64 arch?

---

### Post by cameron3200 on 2009-10-07
As Karmic is supposed to use new Intel drivers, I will try it once it is finished. Just a few more weeks :)

---

