---
title: "ATI Proprietary Driver won't work"
date: 2011-11-13
forum: Multimedia Software
---

### Post by jasoncruz98 on 2011-11-13
After I installed Ubuntu 11.10, I went over to Additional Drivers and there were two drivers:

1.ATI/AMD Proprietary FGLRX Graphics Driver. 
2.ATI/AMD Proprietary FGLRX Graphics Driver (post-release updates).

Since I would want to run Compiz Fusion, I installed the first one. After I installed the driver, I restarted the computer as I was prompted. Then, suddenly, my desktop changed to Unity 2D and I wasn't even offered a choice between Ubuntu or Ubuntu 3D at startup. 

So, I just ignored the problem and installed CCSM and all the extra packages, but no effects would work with my computer. So, I went to Additional Drivers again and uninstalled the driver, then Compiz worked for me! I could use all the effects like normal.

What I want to know is, isn't the driver supposed to help in 3D Graphics Acceleration? In this case, when I installed the driver, why did I immediately went into fallback mode? Why is Compiz running without using any graphics driver? How did Compiz work then without any drivers installed? What graphics card is Compiz utilising? Is this normal?

If I install the driver after I configure Compiz Fusion, will this situation change and will it improve the graphics? 

Why should I install drivers in the first place when it won't improve anything on my graphics?

---

### Post by MoreOrLess on 2011-11-13
What kind of system is this (at least post output from lspci)? I'm guessing you fell into the hybrid graphics trap..

---

### Post by jasoncruz98 on 2011-11-14
What do you mean by "system"? What is lspci? Can you please explain to me? I'm sorry I don't understand those technical terms because I am new to Ubuntu.

---

### Post by MoreOrLess on 2011-11-14
[http://www.google.com/search?q=lspci](http://www.google.com/search?q=lspci)

---

### Post by aeronutt on 2011-11-14
Pretty common problem for those with dual graphics (myself included).  For my hardware combo (Intel integrated SandyBridge graphics and AMD discrete graphics chip) there is no fix. So the usefulness of the proprietary driver is dependant on the hardware you have, hence the request to show the output of the command lspci.

---

### Post by Johnny Buffalkill on 2011-11-14
> What do you mean by "system"? What is lspci?By "system", he's just looking for your hardware, specifically your GPU.  

lspci is a program that lists everything connected to your PCI bus (lspci = list PCI)  If you open terminal and type "lspci" at the prompt, it will list quite a bit of your relevant hardware, and from there people might be able to figure out why it isn't working.  Apparently if you have hybrid graphics set up, FGLRX doesn't like this.  lspci would identify that.  The google query MoreOrLess posted will give alot more information about lspci and will be more accurate than my summary.

To your original question, the difference between the drivers, the "post release updates" version is a later version of the proprietary driver that was released by ATI after Oneiric's original release.  Which one works better probably depends on your hardware, desktop environment etc.

---

