---
title: "blank white screen"
date: 2008-07-20
forum: Multimedia Software
---

### Post by hasek522 on 2008-07-20
I installed the proprietary drive for my ATI graphics card after being prompted to after installing Ubuntu.  After this install i restarted my computer but now when ever i boot to ubuntu i just get a blank white screen with just the cursor showing.

---

### Post by alof8k on 2008-07-20
That means your card isn't supported that well (I guess). I have the same exact problem with my x1650 PRO 512MB AGP when installing the ati fglrx driver.  My searching has led me to try various things and of the two links below, some people have got it to work and some others have not. So try em out:

1) [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) 
2) [http://www.phoronix.com/forums/showthread.php?t=7193](http://www.phoronix.com/forums/showthread.php?t=7193)

And there's also the Ubuntu Wiki which might help: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If all else fails, you could try the Envy program which ALOT of people found helpful from what I see/searched.


Let us know if something works!

---

### Post by david_lynch on 2008-07-20
> **hasek522 said:**
> I installed the proprietary drive for my ATI graphics card after being prompted to after installing Ubuntu.  After this install i restarted my computer but now when ever i boot to ubuntu i just get a blank white screen with just the cursor showing.

The same thing happened to me on my new HP desktop with ATI graphics. I went to the console and uninstalled the fglrx drivers, then my display was back to normal. 

I still wanted the effects, so I went back into synaptic and tried the fglrx-envy package, which ran some setup scripts that took awhile, but then when it was done, after I logged out and in again, I was able to select the desktop effects with no problem.

So, I second the suggestion to try envy.

---

