---
title: "Linux kernel excessive power consumption - high importance"
date: 2011-04-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-04-26
The Linux kernel (upstream) bug of excessive power usage has now been confirmed by Ubuntu Kernel Team to be of high importance in Natty (11.04) and forthcoming Oneiric (11.10).
The bug has been arisen in the development of kernel 2.6.38 and it still persists in the 2.6.38 release version and in the RC versions of the kernel 2.6.39.

Read more:
[http://www.phoronix.com/scan.php?page=news_item&px=OTM3NQ](http://www.phoronix.com/scan.php?page=news_item&px=OTM3NQ)

---

### Post by dino99 on 2011-04-26
i've seen that too but as this bug have appeared in the early 2.6.38 cycle, have made a comparison with 2.6.39:

2.6.38 on maverick i386
2.6.39 on natty i386 : use less ram but have a higher cpu activity

---

### Post by PeterBBB on 2011-04-26
However, the comment that the bug has "high importance" sits uneasily with 
"It doesn't appear that they are devoting any resources to getting the issue resolved" 
from the Phoronix link!

---

### Post by screaminj3sus on 2011-04-26
They are probably waiting until it gets fixed in 2.6.39 and are going to backport it to 2.6.38 and release it as an update. Its really too late to do anything before release.

---

### Post by kaldor on 2011-04-26
I won't be able to use Natty on my main machine (A laptop with a 1 hour battery, oh joy) since it has bad enough power management as it is. Plus it gets too hot.

I'll be watching this thread for a while for any updates. Really a huge shame that this major regression wasn't fixed before release.

---

### Post by nanog on 2011-04-26
Its sad that it took so long for this to receive attention as it will likely end up in the 11.04 final release. There were several dev forum posts about power consumption that received little response. There was also a bug report that received little attention from other testers: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

We need less "I always do a fresh install" and "I am sure this will be fixed"  and more TESTING.

---

### Post by nanog on 2011-04-26
Its a kernel bug. Until a git bisect reveals the bug there is little ubuntu developers can do about it. And frankly, with a bug of this severity its best for ubuntu to work with upstream.

IMO, this bug should delay release.

---

### Post by kaldor on 2011-04-26
> **nanog said:**
> IMO, this bug should delay release.

Could not agree more. This could cause problems for a lot of people. Like I've mentioned, I am unable to use it on my main machine because of this.

---

### Post by M4570D0N on 2011-04-26
There was a thread in here discussing this already 2 days ago:
[http://ubuntuforums.org/showthread.php?t=1718433](http://ubuntuforums.org/showthread.php?t=1718433)

---

### Post by VinDSL on 2011-04-26
It's a simple matter to revert to 2.6.37.6-natty, until they provide a fix (upstream).

Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/)


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-26-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-26-apr-2011.png")[/INDENT]


End of problem.  ;)

---

### Post by Harry33 on 2011-04-26
> **VinDSL said:**
> It's a simple matter to revert to 2.6.37.6-natty, until they provide a fix (upstream).
Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/)
...
End of problem.  ;)

For some laptop model owners that may be the only option to proceed.

---

### Post by kaldor on 2011-04-26
> **Harry33 said:**
> For some laptop model owners that may be the only option to proceed.

That's no issue for people like us; but this is a horrible thing to need to do for average users to have a functional laptop. Delaying Natty until a backport is ready would be very useful in my opinion.

---

### Post by PeterBBB on 2011-04-26
> **nanog said:**
> Its a kernel bug.

FWIW, I have tested 2.6.32 and 2.6.38 kernels [x86_64] in Debian 6 with a power meter and the power consumption is exactly the same both on idle, and full power, 65 and 145 watts respectively with either kernel on this desktop m/c. The machine has AMD processor with Nvidia chipset & Nvidia graphics. I do get the feeling that the problems are occurring with Intel kit and/or AMD graphics. Maybe the issue is drivers/modules rather the the kernel core itself?

---

### Post by kaldor on 2011-04-26
> **PeterBBB said:**
> FWIW, I have tested 2.6.32 and 2.6.38 kernels [x86_64] in Debian 6 with a power meter and the power consumption is exactly the same both on idle, and full power, 65 and 145 watts respectively with either kernel on this desktop m/c. The machine has AMD processor with Nvidia chipset & Nvidia graphics. I do get the feeling that the problems are occurring with Intel kit and/or AMD graphics. Maybe the issue is drivers/modules rather the the kernel core itself?

I have an Intel processor and NVIDIA Geforce 8400m. I noticed a big Heat increase on Natty, but no battery issues. I was using Nouveau, though.

I haven't tried natty on my laptop since the second beta. But, since I hear so many issues about the battery issue, I'm concerned about upgrading.

---

### Post by nanog on 2011-04-26
Or you could just stay on maverick...until this is fixed.

---

### Post by kaldor on 2011-04-26
Tell that to the many new people who will be trying Ubuntu in two days ;)

---

### Post by Synthetic Sam on 2011-04-26
I have just upgraded to Natty on a Vaio NR32S, C2D (T1550), Geforce 8400m and I can report that there is a huge heat increase in comparison to Maverick.

---

### Post by kaldor on 2011-04-26
> **Synthetic Sam said:**
> I have just upgraded to Natty on a Vaio NR32S, C2D (T1550), Geforce 8400m and I can report that there is a huge heat increase in comparison to Maverick.

Same graphics card as me. Major increase using 11.04 Nouveau compared to 10.10 NVIDIA driver. Which drivers did you use, and which do you have now?

---

### Post by tlcstat on 2011-04-26
Greetings,
My computer was overheating into shutdown. I installed lm-sensors so that I could monitor the temperature. Fixed the problem by uninstalling two progams.
DRI 3d Acceleration
indicator-weather

After I removed these two programs my system cooled back to normal and I haven't had a problem since. 
Certainly there could be other programs that are not properly using this kernel. Or vis-versa. (not sure which).
tlcstat

Greetings,
Just some system temp info.

tlcstat@tlcstat-Ubuntu:~$ bash st
\1. VNSTATD
2. TD
3. MacChanger
4. Sensors f
5. Conky
6. Boot55
Please choose a script [1,2,3,4,5 or 6]? 4
acpitz-virtual-0
Adapter: Virtual device
temp1: +159.8°F (crit = +230.0°F) 

coretemp-isa-0000
Adapter: ISA adapter
Core 0: +152.6°F (high = +212.0°F, crit = +212.0°F) 

tlcstat@tlcstat-Ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 11.04
Release: 11.04
Codename: natty
tlcstat@tlcstat-Ubuntu:~$ 

tlcstat

---

### Post by 23dornot23d on 2011-04-26
I had a problem a week ago .... with a definate increase while running firefox 4 .....
may be unrelated but the temps went down significantly swapping to chrome ....

my laptop runs at 58 to 61 usually .... this week has been a exceptionally hot week in France ..... 
but the temperature difference was quite worrying .... one night it got to 72 degrees .... 
playing scrabble ...... lols ..... ( between 10pm and 12pm - it really should be cooling at night time )

I had to shut it down .... as something was obviously not right ...... firefox and plugin-container were
taking most of the processing .... 

I restarted in 10.10 and continued the game in firefox the temp stayed constant at 58 to 60 ....... as it should do.

Its only after seeing this thread I thought it best to mention it again ......

Here is the Link and screenshots that I took when I noticed .... [LINK]("http://ubuntuforums.org/showpost.php?p=10695405&postcount=446")

hope it helps in some way work out what is causing it .....

I swapped the [kernel and downloaded Firefox 4]("http://ubuntuforums.org/showpost.php?p=10697891&postcount=453") from the web as I did not want the additional plugins for the global menu ..... 

and after these 2 things I found my temps came down ...... ( oh one more thing I have done since then - I stopped conky too )

```

but its still hotter than normal at 64 degrees ....... when playing scrabble in firefox ..... 
as [soon as I drop out the temps drop back to 59 degrees]("http://img706.imageshack.us/img706/2379/screenshot30gc.jpg")
This has been running all night ..... now 5 hours ..... 

but the 5 degree increase was just while firefox 4 and a scrabble flash game in Facebook were being played and nothing else 
```

---

### Post by Synthetic Sam on 2011-04-27
> **kaldor said:**
> Same graphics card as me. Major increase using 11.04 Nouveau compared to 10.10 NVIDIA driver. Which drivers did you use, and which do you have now?
I'm using the proprietary drivers on both Maverick and Natty.

---

### Post by Synthetic Sam on 2011-04-27
Just installed on my desktop, and the CPU temps seem to be the same as with Maverick, and my UPS reports same power usage as before the upgrade.

Temperature increase must be hardware specific. This computer is Intel Processor (Q6600) with ATI HD4850.

---

### Post by Reiger on 2011-04-27
For me it's mostly the temperatures that worry me (laptop) with the ATI 4540 card. At boot, before I log in I switch the power profile for the card from 'default' to 'low':
```

echo low > /sys/class/drm/card0/device/power_profile

```

---

### Post by psusi on 2011-04-27
> **23dornot23d said:**
> 
I had to shut it down .... as something was obviously not right ...... firefox and plugin-container were
taking most of the processing .... 

That would be Flash.  Thank Adobe and all of the idiot web developers that use their crappy software.

---

### Post by 23dornot23d on 2011-04-27
I did not solve the problem with the newer kernel and the removal of firefox 4 ......

Today I noticed the fan was going like mad again ..... all I was doing was altering a theme 
have hardly done anything graphic wise today to cause it to get so hot ...... up at 71 degrees again ..... 

I have now stopped using 11.04 ........ as my main system ..... back to using 10.10 now ......

The version 10.10 does not do this .......this is what I am in now ...... its actually flickering between 57 - 58 degrees ..... 
uname -a
Linux keith-laptop 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux


I have two monitors running and currently running firefox 3.6.16 ..... its been another hot day here again but there is a definite difference [COLOR=Red]**between 10.10 @58**[/COLOR] degrees - even running 3D on this max I get it to is 64 degrees and it drops back to 60. 
and [COLOR=Red]**11.04 ..... climbing 71 +**[/COLOR] ....... not sure why though ..... yet ...... and I have made sure that the graphics card is not in performance mode .... its in adaptive ..... 

I will keep watching the processes ..... when I run it just to test things out ...... in 11.04 ......
( is it just Laptops with Nvidia Cards - we once had something similar to this before with graphics cards and temps )

My system is a laptop Acer Aspire 7720 with a Nvidia Graphics card GS9300 M

The graphics card driver is 260.19.06 on 10.10 ........ on startup fresh 58 to 60 degrees
(had htop running all the way through a game tonight in 10.10 never went above 60 ..... 
have recorded at stages the process use so will compare them to the other one tomorrow night) 


The graphics driver on the 11.04 is   .... ( 270.41.03   )  ...... on startup fresh 61 to 62 degrees
by the way I know there is the 270.41.06 .... had that one running too .... with no difference ......

---

### Post by Reiger on 2011-04-27
Try putting the thing in a &#8220;low&#8221; power profile explicitly? (power_method = profile and power_profile = low)

---

